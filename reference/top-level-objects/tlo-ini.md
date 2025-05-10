---
tags:
    - tlo
---
# `Ini`

<!--tlo-desc-start-->
Reads value(s) from an ini file located in a relative or absolute path.
<!--tlo-desc-end-->
## Forms
<!--tlo-forms-start-->
### {{ renderMember(type='string', name='Ini', params='filename,section,key,default') }}

:   The _section_, _key_, and _default_ do not need to be given. If _section_ or _key_ are not given, multiple values are read.

    _Section_ and _key_ may be set to -1 to skip them and give a new value.

    If the ini is located in a directory other than the root Macros directory is located, you can use
    a DOS-style filepath (relative or absolute) to locate the ini. If the macro accessing the ini
    is in the same non-root directory, you will still to provide the (relative or absolute) filepath.

### {{ renderMember(type='ini', name='Ini') }}

:   When passed with no parameters to Ini[] the more robust form of the Ini TLO is used.  See below and the reference
    to the [Key](../data-types/datatype-inifilesectionkey.md) datatype for further usage.
<!--tlo-forms-end-->

## Usage

If sample.ini contains:

```ini
[SectionOne]
key1=foo
key2=bar
[SectionTwo]
key3=foobar
```

```
/echo ${Ini[sample.ini,SectionOne,key1]}
```

foo

```
/echo ${Ini[sample.ini,SectionOne]}
```

key1|key2||

```
/echo ${Ini[..\sample.ini]}
```

SectionOne|SectionTwo||

If sample.ini is in \Macros\iniTest folder:

```
/echo ${Ini[sample.ini]}
```

NULL

```
/echo ${Ini[iniTest\sample.ini]}
```

SectionOne|SectionTwo||

# `Ini` (Robust Usage)

The above form of Ini usage is usable or most tasks, but a more robust usage exists.  In the more robust form `${Ini}` returns 
an [IniType](../data-types/datatype-ini.md) instead of a string.  This allows for dealing with duplicate keys as well as looping through a section by index.

## Examples

If sample.ini contains:

```ini
[SectionOne]
key1=foo
key=bar
key=foobar
```

```
> /echo ${Ini.File[sample].Section.Count}
1
> /echo ${Ini.File[sample].Section[SectionOne].Key.Count}
3
> /echo ${Ini.File[sample].Section[SectionOne].Key[key].Count}
2
> /echo ${Ini.File[sample].Section[SectionOne].Key[key1].Value}
foo
> /echo ${Ini.File[sample].Section[SectionOne].Key[key].ValueAtIndex[2]}
foobar
> /echo ${Ini.File[sample].Section[SectionOne].Key.ValueAtIndex[2]}
bar
```
<!--tlo-linkrefs-start-->
[ini]: ../data-types/datatype-ini.md
[string]: ../data-types/datatype-string.md
<!--tlo-linkrefs-end-->
