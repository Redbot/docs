# How to use Actors

General Actor documenation available at [Actors](../../main/features/actors.md). Please refer to the [terminology section](../../main/features/actors.md#terminology) in the other actors document for a glossary of terms.

Plugins are a special case for the actor API as the post office itself is maintained within mq2main.dll and is not exposed at all to any plugins. Instead, plugins will have access to an actor API by including:

```cpp
#include "mq/api/ActorAPI.h"
```

This include provides everything necessary for creating and registering an actor, as well as sending (and receiving) messages. There is one free function (with two overloads) that creates a new actor provided as part of this API:

## AddActor

```cpp
using ReceiveCallbackAPI = std::function<void(const std::shared_ptr<Message>&)>;

DropboxAPI AddActor(const char* localAddress, ReceiveCallbackAPI&& receive);
DropboxAPI AddActor(ReceiveCallbackAPI&& receive);
```

Both of these functions return a `DropboxAPI` object, which serves as the interface to the dropbox functionality needed to operate the actor. If a `localAddress` is not specified, then the canonical name of the plugin is used as the mailbox name (convenient for when you only need one mailbox in a plugin, which should be pretty common).

An important implementation detail is that mailbox names are mutated when they are set to ensure that they are unique in the post office. The `localAddress` specified is the mailbox name *local to the plugin* and not the full mailbox name that is stored in the mailbox. This registration function will prepend the mailbox with the canonical plugin name followed by a colon like so: `myplugin:mymailbox`. This is only important to the plugin author if they need to send messages to mailboxes outside their plugin, otherwise the send functions will handle this implementation detail opaquely.

There is one more free function provided by the API to send "anonymous" messages to actors. The point of using this function is when you want to send a message to a recipient, but don't want to set up an actor and message handler in the local script. The signature is as follows:

```cpp
using ResponseCallbackAPI = std::function<void(int, const std::shared_ptr<Message>&)>;

template <typename T>
void SendToActor(const Address& address, const T& obj, const ResponseCallbackAPI& callback = nullptr);
```

Because the default handling of objects is protobuf, T is assumed to be a protobuf type. There is one exception, this function is specialized for `T = std::string`, which is used as a data container and just serializes the string directly to the message being sent. `Address` is talked about below, and is how you would direct the message to an actor. `Message` is also talked about below and is the actual message being sent to the actor. The callback is optional, and is specified when the receiving actor will send a response to the sent message.

There are three more structures to explore in a plugin, `Address`, `Message`, and `DropboxAPI`.

## Address

An address is a shim to the protobuf-defined address, and follows the same rules as the [terminology section above](#terminology). The API provides this shim as a simple struct where you can set the address parameters directly like this (as an example):

```cpp
postoffice::Address addr;
addr.Server = "test";
addr.Character = "target";
```

The one difference to note is that there is a member of this address called `AbsoluteMailbox`. If this is set to true, then all values of the address are passed as-is without any modification, useful only for sending messages to actors that are created outside the plugin. Otherwise, the mailbox name follows these rules:

- If no mailbox is specified at all, then the plugin name becomes the target mailbox.
- If a mailbox is specified, then the target mailbox becomes `<pluginName>:<mailbox>` as was noted in [the implementation details specified in `AddActor`](#addactor)

## Message

A message consists of 2 parts useful to the plugin author, `Sender` and `Payload`. Both are optional (and are wrapped in `std::optional`), so the author will need to handle the absence of either.

- `Sender`: This is the address of the message sender. It's useful if message handling is dependent on the source of the message.
- `Payload`: This is the actual message payload. It is represented as a string, which is a convenient data storage mechanism that provides bytes and length, and is deserializable directly as a protobuf message. It could be any data that your plugin can handle though, since the handling of it is local to your plugin.

## DropboxAPI

This is the object that is returned when an actor is added to the postoffice via the API. The plugin author should store this somewhere where it can be accessed because they will need to use it to send messages and unregister the actor. The object provides the following functions:

- `Post(address, data, callback)`: Send a message to an address. `data` is what you want to send, which can be any protobuf object or a `std::string`. `callback` is a to be used to handle a response to the message sent; setting this parameter (to something other than `nullptr`) will send a message that expects a response, and will send back an error status if none is received.
- `PostReply(message, data, status)`: This is a method mostly to be used in message handling. `message` is a `std::shared_ptr` of the original message that is expecting a response. `data` is as above, and `status` is a signed 8-bit parameter that defaults to 0 that some actors expect as a response (mostly used as error codes).
- `Remove()`: Remove the actor from the post office. Will unregister the actor, clean up the internal dropbox, and will ensure that any further use of the `DropboxAPI` does nothing.
