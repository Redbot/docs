---
tags:
    - command
---
# /goto

## Syntax

```eqcommand
/goto :<labelname>
```

## Description

This moves the macro execution to the location of _:labelname_ in the macro.

## Example

```text
:MyLabel
/if ( ${Me.Moving} ) /goto :MyLabel
/echo I am no longer moving!
```

