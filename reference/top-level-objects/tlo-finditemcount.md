---
tags:
    - tlo
---
# `FindItemCount`

<!--tlo-desc-start-->
A TLO used to find a count of items on your character, corpse, or a merchant by partial or exact name match. _See examples below._
<!--tlo-desc-end-->
## Forms
<!--tlo-forms-start-->
### {{ renderMember(type='int', name='FindItemCount', params='name|id') }}

:   Counts the items using the given item id, or partial name match. Will search character
    inventory and any items stored in key rings (illusion, mount, etc).

    ???+ example

        Echos the number of items in your inventory with the name swirling in it.

        === "MQScript"

            ```
            /echo ${FindItemCount[swirling]}
            ```

        === "Lua"

            ```lua
            print(mq.TLO.FindItemCount("swirling"))
            ```


### {{ renderMember(type='int', name='FindItemCount', params='=name') }}

:   Counts the items using exact name match (case insensitive). Will search character inventory
    and any items stored in key rings (illusion, mount, etc).

    ???+ example

        Echoes the number of Water Flasks you have in your inventory.

        === "MQScript"

            ```
            /echo ${FindItemCount[=Water Flask]}
            ```

        === "Lua"

            ```lua
            print(mq.TLO.FindItemCount("=Water Flask"))
            ```
<!--tlo-forms-end-->
<!--tlo-linkrefs-start-->
[int]: ../data-types/datatype-int.md
<!--tlo-linkrefs-end-->
