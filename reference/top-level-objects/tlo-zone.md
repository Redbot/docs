---
tags:
    - tlo
---
# `Zone`

<!--tlo-desc-start-->
Used to find information about a particular zone.
<!--tlo-desc-end-->
## Forms
<!--tlo-forms-start-->
### {{ renderMember(type='currentzone', name='Zone') }}

:   Retrieves the current zone information

### {{ renderMember(type='zone', name='Zone', params='N') }}

:   Retrieves information about a zone by zone ID. If this zone is the current zone, then
    this will return [currentzone].

### {{ renderMember(type='zone', name='Zone', params='ShortName') }}

:   Retrieves information about a zone by short name. If this zone is the current zone, then
    this will return [currentzone].
<!--tlo-forms-end-->

## Usage

```
/echo ${Zone.Type}
```

Returns an integer representing the zone you are currently in.

```
/echo ${Zone.Indoor}
```

Returns TRUE if you're indoors, FALSE if not.

```
/echo ${Zone[zonename].ID}
```

Returns the ID of _zonename_, even if you aren't in the zone.

```
/echo ${Zone[zoneid].ShortName}
```

Returns the short name of the zone with ID _zoneid_.

<!--tlo-linkrefs-start-->
[zone]: ../data-types/datatype-zone.md
[currentzone]: ../data-types/datatype-currentzone.md
<!--tlo-linkrefs-end-->
