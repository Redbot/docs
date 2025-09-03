---
tags:
  - live
resource_link: "https://www.redguides.com/community/resources/very-vanilla-mq-live-servers.1974/"
support_link: "https://www.redguides.com/community/threads/very-vanilla-mq-live-servers.77019/"
repository: "https://github.com/macroquest/macroquest"
config: "MacroQuest.ini"
authors: "Plazmic, eqmule, brainiac, rswiders, Lax, ieatacid, dont_know_at_all, Amadeus, dannuic, alynel, Knightly, ChatWithThisName, Sic, Xeniaz, htw"
tagline: "A platform for customization and automation of EverQuest"
quick_start: "https://www.redguides.com/community/resources/multiboxing-everquest-the-red-guide-videos.1603/"
---

# MacroQuest

<!--desc-start-->
MacroQuest is an open source platform for customization, enhancement, and automation of **EverQuest**. It's been modified for use on both official and emulated servers.

On RedGuides, MacroQuest is configured and packaged as "**Very Vanilla MQ**" for [Live](https://www.redguides.com/community/resources/very-vanilla-mq-live-servers.1974/), [Test](https://www.redguides.com/community/resources/very-vanilla-mq-test-server.2218/) and [Emulated](https://www.redguides.com/community/resources/very-vanilla-mq-emulated-servers.60/) servers.  

*The docs here closely track the [official MacroQuest documentation](https://docs.macroquest.org), and the edit button on most pages but this one will send you to the parent repository.*
<!--desc-end-->

## History

*MacroQuest* was conceived in 2002 by Plazmic, who announced it in a forum thread that [received no replies](https://web.archive.org/web/20081205185615/http://www.hackersquest.org/boards/viewtopic.php?t=1550). Its popularity grew upon release, and began the era of the custom macroscript. Since then it's had many maintainers, and two major rewrites:  

* *MacroQuest 2*, which was released in 2004. Led by Lax, a [near complete rewrite](https://web.archive.org/web/20230523234217/https://macroquest2.com/phpBB3/viewtopic.php?f=29&t=4023) that began the era of C++ plugins. See [history of macroquest](main/history-of-macroquest.md) for more on this era.
* *MacroQuest* in 2021, led by brainiac, dannuic and Knightly, who took a 16 year old codebase and [modernized it](https://www.redguides.com/community/threads/macroquest-release-party.80628/), ringing in the era of Lua scripts.  


## Reference

[**Commands**](reference/commands/index.md) (1)  
[**Core Plugins**](plugins/core-plugins/README.md) (2)  
[**Scripts**](../../scripts/index.md)  
[**Config (MacroQuest.ini)**](main/macroquest.ini.md)  
[**Top-Level Objects**](reference/top-level-objects/index.md) (3)  
[**Data Types**](reference/data-types/index.md) (4)  
[**Launcher**](main/macroquest-launcher.md)  
[**Building your own compile**](main/building.md)  
{ .annotate }

1.  Core MacroQuest-only. For more, see [All Commands](../../commands/index.md).
2.  Core MacroQuest-only. For more, see [All Plugins](../../plugins/index.md).
3.  Core MacroQuest-only. For more, see [All TLOs](../../tlos/index.md).
4.  Core MacroQuest-only. For more, see [All Data Types](../../datatypes/index.md).

## Getting Started

Once you've got the basics of MacroQuest's features, you'll probably want to try some scripts and plugins that you've found on the [internet](https://www.redguides.com/community/resources). Here's how to run them:

### Lua

!!! tip "Lua scripts can be started from the Lua window, `/lua gui` to open." 

Alternately, you can start a Lua script with the following command:

`/lua run <script>` e.g. `/lua run eval`

You can stop a Lua script with the following command:

`/lua stop <script>` e.g. `/lua stop eval`

For more on Lua, see [Lua](lua/README.md).

### Plugins

MQ plugins are modular and can be loaded and unloaded on demand.

To load a plugin:

`/plugin <name>` e.g. `/plugin mq2melee`

To unload a plugin:

`/plugin <name> unload` e.g. `/plugin mq2melee unload`

See the [Plugins](../../plugins/index.md) page for an index of all plugins, and [/plugin](reference/commands/plugin.md) for usage.

### Macros

You can load a macro with the following command:

`/macro <name>` e.g. `/macro autobot`

To end a macro, use this command:

`/endmacro`

See [/macro](reference/commands/macro.md) and [/endmacro](reference/commands/endmacro.md).
