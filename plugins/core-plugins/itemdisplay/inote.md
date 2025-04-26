---
tags:
   - command
---
# /inote

## Syntax

```eqcommand  
/inote <add|del> <itemno> <comment>
```

## Description
Adds a note to the display window for a the specified item. The _comment_ can contain html `<br>` tags to break the line of text.

## Example

```text
/inote add 19542 This is found on the Great Saphrophyte in EC<br>Rarity is about 1 in 5
```

The text at the end of the additional information in blue on the item display window will be:

```text
Note: This is found on the Great Saphrophyte in EC
Rarity is about 1 in 5
```
