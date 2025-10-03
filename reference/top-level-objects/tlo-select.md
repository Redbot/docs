---
tags:
    - tlo
---
# `Select`

<!--tlo-desc-start-->
Object used to determine if a match was made to argument in the given set of values.

!!! warning
    Values must be single words.  Quoted strings do not work, as the parser will drop the quotes and uses spaces as a delimiter.
<!--tlo-desc-end-->
## Forms
<!--tlo-forms-start-->
### {{ renderMember(type='int', name='Select', params='argument,value1[,value2,...]') }}

!!! example
    Given:

    ```
    /declare thing string outer foo
    ```

    The following are true:

    ```
    | Outputs: 1
    /echo ${Select[${thing},foo,bar,baz]}

    | Outputs: 2
    /echo ${Select[${thing},bin,foo,baz]}

    | Outputs: 3
    /echo ${Select[${thing},bin,baz,foo]}

    | Outputs: 0
    /echo ${Select[${thing},bin,bar,baz]}
    ```

!!! example

    ```
    /if (${Select[${Target.Class.ShortName},CLR,DRU,SHM]} > 0) {
        /echo Target is a healer
    }
    ```
<!--tlo-forms-end-->
<!--tlo-linkrefs-start-->
[int]: ../data-types/datatype-int.md
<!--tlo-linkrefs-end-->
