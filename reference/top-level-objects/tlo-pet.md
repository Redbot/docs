---
tags:
    - tlo
---
# `Pet`

<!--tlo-desc-start-->
Pet object which allows you to get properties of your pet.
<!--tlo-desc-end-->
## Forms
<!--tlo-forms-start-->
### {{ renderMember(type='pet', name='Pet') }}

:   Provides access to your current Pet. The [pet](../data-types/datatype-pet.md) type extends from spawn, and as such 
    has access to the properties of the [spawn](../data-types/datatype-spawn.md) type as well.
<!--tlo-forms-end-->

## Usage

```
/echo My Pet's Stance is currently set to: ${Pet.Stance}
```

```
/echo My Pet's Name: ${Pet.CleanName}%
```

```
/echo My Pet's Target has gone Berserk! ${Pet.Target.IsBerserk}
```
<!--tlo-linkrefs-start-->
[pet]: ../data-types/datatype-pet.md
<!--tlo-linkrefs-end-->