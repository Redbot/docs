---
tags:
    - tlo
---
# `FindItem`

<!--tlo-desc-start-->
A TLO used to find an item on your character, corpse, or a merchant by partial or exact name match. _See examples below._
<!--tlo-desc-end-->
## Forms
<!--tlo-forms-start-->
### {{ renderMember(type='item', name='FindItem', params='name|id') }}

:   Search for an item using the given item id, or partial name match. Will search character
    inventory and any items stored in key rings (illusion, mount, etc).

    ???+ example

        Looks for an item with the name swirling in it, and prints the ID.

        === "MQScript"

            ```
            /echo ${FindItem[swirling].ID}
            ```

        === "Lua"

            ```lua
            print(mq.TLO.FindItem("swirling").ID())
            ```


### {{ renderMember(type='item', name='FindItem', params='=name') }}

:   Search for an item using exact name match (case insensitive). Will search character inventory
    and any items stored in key rings (illusion, mount, etc).

    ???+ example

        Looks for the Cleric Epic (by exact match) and prints its ID.

        === "MQScript"

            ```
            /echo ${FindItem[=Water Sprinkler of Nem Ankh].ID}
            ```

        === "Lua"

            ```lua
            print(mq.TLO.FindItem("=Water Sprinkler of Nem Ankh").ID())
            ```
<!--tlo-forms-end-->
<!--tlo-linkrefs-start-->
[item]: ../data-types/datatype-item.md
<!--tlo-linkrefs-end-->
