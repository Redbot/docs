---
tags:
    - command
---
# /declare

## Syntax

**/declare** _varname_ **|** _varname[array extents]_ **[** _type_ **]** **[ local | global | outer ]** **[** _defaultvalue_ **]**

## Description

This creates a variable or array of a particular type with a particular scope, and a default value if desired. The parameters must be given in order, but any after _varname_ may be skipped to use the defaults.

**Notes**

* The default type is string
* The default scope is local
* The default value is nothing (empty string, or 0)

These variables can be of any type that exist in MQ2DataVars. The variable will then have access to the members of that type.
