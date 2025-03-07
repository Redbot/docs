---
tags:
    - command
---
# /popcustom

## Syntax

```eqcommand
/popcustom [<#color>] [<#seconds>] <message>
```

## Description

Creates an in-game overlay message. See also [/popupecho](popupecho.md).

## Color Chart

| **Number** | **Color** |
| :--- | :--- |
| 1, 3, 8, 9, 11, 17, 19, 21+ | dark grey |
| 2 | light green |
| 4 | dark blue |
| 5 | pink |
| 6, 12 | light grey |
| 7, 10 | white |
| 13 | red |
| 14 | bright green |
| 15 | yellow |
| 16 | bright blue |
| 18 | cyan |
| 20 | black |

## Examples

| **Example** | **Output** |
| :--- | :--- |
| **/popcustom hi there** | Will display "hi there" on the screen just like /popup |
| **/popcustom 13 hi there** | Will display "hi there" on the screen in red, for 3 seconds (/popup's default) |
| **/popcustom 13 5 hi there** | Will display "hi there" on the screen in red, for 5 seconds. |


If you type `/popcustom` with no parameters, it will display the help output for this information.

