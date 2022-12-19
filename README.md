# ConsoleManagers configs collection
Search for ```point_servercommand``` and all outputs that use it as a ```say``` command to create these. For each messages you are going to want a new block, the blocks MUST match all letters with an messages after ```say```.

It is available to add more messages if you need. For each additional triggers you are going to make, the blocks should be numbered correctly if you are copy/pasting them.

### How to contribute
For making this config, you will want an external tool like [VIDE](http://www.riintouge.com/VIDE/)'s entity lump editor, or an official mapping editor like Hammer, including extension tools like Hammer++. The format is available below.

The largest difference between those tools is whether decompiling is needed or not: Hammer and Hammer++ can load only .vmf files, you must convert to this filename extension using a decompiler like [bspsrc](https://github.com/ata4/bspsrc/releases).

```text
"root"
{
    "spawns" // add a new info_target entity for instructor targets
    {
        "0"
        {
            "origin"        ""      // string of origin for new entity ("x y z")
            "targetname"    ""      // string of targetname for new entity
            "parentname"    ""      // string of parentname for new entity (if applicable)
        }
    }
    "triggers" // add new outputs to an exist entity for additional consoles
    {
        "0"
        {
            "hammerid"      ""      // string of hammerid for exist entity
            "classname"     ""      // string of classname for exist entity
            "output"        ""      // any outputs whatever you want to add
            // e.g. "OnTrigger console:Command:say >>> HELLO <<<:10:1"
        }
    }
    "consoles"
    {
        "CONSOLE"   // required all letters after a "say" command
        {
            "default"       ""      // string of new console messages, replace original messages
            "jp"            ""      // string of the console with Japanese
            "blocked"       ""      // true if it should be blocked, useful for anti-spamming or invisible triggers
            "color"         ""      // color to use in Huds (refer to the color list below)
            "timer"         ""      // integer if it uses identified trigger timing
            "console"       ""      // false if it should hide from console, useful for vscript messages
            "text"          ""      // false if it should not show as GameText Hud
            "hud"           ""      // false if it should not show as CenterHud
            "countdown"     ""      // false if it does not use countdown as Huds
            "holdtime"      ""      // float if it needs to hold GameText Hud more or less than 1 seconds (it has fade-out for 5 seconds)
            "init"          ""      // string if it needs to delete by another console (e.g. boss timer)

            "hint"          ""      // true if it needs to show as env_instructor_hint
            "caption"       ""      // true if the hint needs to do countdown as a hint
            "target"        ""      // string of an object targetname the hint sticks to
            "icon"          ""      // string of an icon for the hint (refer to the hint_icon list below)
            "bind"          ""      // string of a bound key for the hint (refer to the key_listboundkeys list below, "icon" MUST be "use_binding")
            "timeout"       ""      // integer of the timeout for the hint
            "range"         ""      // float of the visible range for the hint
        }
    }
}
```

**ConsoleManagers Color List**

Due to supporting [HTML named colors code](https://htmlcolorcodes.com/color-names/), old colors are renamed to x01 - x10 and the following list compares new names to old one. Some color names are still supported since HTML named colors use them but their colors have huge difference between old and new. It is recommended to use x01 - x10 if you want [csgo colors](https://user-images.githubusercontent.com/115328735/205095791-309eb6e6-973e-4f66-b81d-349273561186.png).

New name|Old name
---|---
x01|{default}
x02|{darkred}
x03|{purple}
x04|{green}
x05|{lightgreen}
x06|{lime}
x07|{red}
x08|{grey}
x09|{yellow}
x0A|{bluegrey}
x0B|{blue}
x0C|{darkblue}
x0D|{grey2}
x0E|{orchid}
x0F|{lightred}
x10|{gold}

It needs no longer curly brackets since the plugin supports removing them and for x0A - x0F, they are available to use lower case alphabets.

Support HEX color code as well. It needs "#" character on the first and make sure the tag has 6-digits excluding "#", otherwise they will not be recognized as HEX color code: 8-digits HEX code is not supported. Make sure the all characters are HEX digits, or it will not work exactly.

**Instructor Icon/Keybind List**
```text
>> hint_icon

icon_alert
icon_alert_red
icon_tip
icon_interact
icon_door
icon_fire
icon_present

// Default is "icon_tip".
// There are some other icons but this list above should be better to use.

>> key_listboundkeys

+forward
+back
+moveleft
+moveright
+use
+reload
+jump

// You can use any other bound key but this list above is famous and useful.
```
You can check all instructor icons used in CS:GO at [here](https://www.reddit.com/r/hammer/comments/be79z1/env_instructor_hint_icons_csgo_sdk/).
