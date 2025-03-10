---
tags:
    - command
---
# /hotbutton

## Syntax

**/hotbutton** _name_ **[**_color_**]** **[**_line_**:][**_cursor_**:]**_text_**]**

## Description

Extends the built in /hotbutton command with multiple lines support, cursor attachment, and "names with spaces" (in quotes) support.

## Examples

|  |  |
| :--- | :--- |
| **Example** | **Description** |
| /hotbutton TheName 14 1:0:/echo hi | Where 14 1:0: in this case means use color 14, then place /echo hi on LINE 1 and NO Cursor Attachment. |
| /hotbutton TheName 14 1:/echo hi | Where 14 1: in this case means use color 14, then place /echo hi on LINE 1. |
| /hotbutton TheName 1:0:/echo hi | Where 1:0: in this case means place /echo hi on LINE 1 and NO Cursor Attachment. |
| /hotbutton TheName 1:/echo hi | Where 1: in this case means place /echo hi on LINE 1. |
| /hotbutton TheName 0:/echo hi | Where 0: in this case means NO Cursor Attachment. |
| /hotbutton TheName 14 /echo hi | just calls the eq function like before. |
| /hotbutton TheName /echo hi | just calls the eq function like before. |

