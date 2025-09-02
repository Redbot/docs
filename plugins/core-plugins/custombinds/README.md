---
tags:
  - plugin
resource_link: "https://www.redguides.com/community/resources/mq2custombinds.115/"
support_link: "https://www.redguides.com/community/threads/mq2custombinds.66819/"
repository: "https://github.com/macroquest/macroquest/tree/master/src/plugins/custombinds"
config: "MQ2CustomBinds.ini, MQ2CustomBinds.txt"
authors: "Amadeus, eqmule, BigDorf, Knightly"
tagline: "Allows you to specify custom commands that are executed when specific key combinations are pressed."
search:
  boost: 2
---
# CustomBinds
<!--desc-start-->
Custom commands that are executed when key combinations are pressed.
You may specify a command for when the key is pressed (down), and another for when it is released (up).
<!--desc-end-->
## Commands

<a href="custombind/">
{% 
  include-markdown "plugins/core-plugins/custombinds/custombind.md" 
  start="<!--cmd-syntax-start-->"
  end="<!--cmd-syntax-end-->"
%}
</a>
:    {% include-markdown "plugins/core-plugins/custombinds/custombind.md"
        start="<!--cmd-desc-start-->"
        end="<!--cmd-desc-end-->"
        trailing-newlines=false 
     %} {{ readMore('plugins/core-plugins/custombinds/custombind.md') }}

## Examples

```
/custombind add crylaugh
/custombind set crylaugh-down /cry
/custombind set crylaugh-up /laugh
/bind crylaugh shift+f
```
