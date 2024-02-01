---
description: How do you use it?
---

# 💡 Preface

To use this library, you first need to know exactly why do you need to install Terminaux into your console application. If your application is intended to be an interactive one, or if your application shows graphics (text, info box, ...), then Terminaux is the right library for you.

Terminaux provides several terminal actions, like reading an input (was on TermRead), getting color information (was on ColorSeq), and using VT sequences and filtering them (was on VT.NET).

For complete overview of functionality, consult the below pages:

{% content-ref url="input-reader/" %}
[input-reader](input-reader/)
{% endcontent-ref %}

### Reading an input

Just use the `Terminaux.Reader` class that contains:

* `Read(bool interruptible = false)`
* `Read(string, bool interruptible = false)`
* `Read(string, string, bool, bool, bool interruptible = false)`
* `ReadPassword(bool interruptible = false)`
* `ReadPassword(string, bool interruptible = false)`

Each one of these functions creates a reader state, `TermReaderState`, that contains essential information about the current reader state, including, but not limited to:

* Current text
* Input prompt text
* Current text position
* Kill buffer

Any key will append the selected characters to the current text input, and `RETURN` will accept the input. For more information about key bindings, go to the below page.

{% content-ref url="input-reader/keybindings.md" %}
[keybindings.md](input-reader/keybindings.md)
{% endcontent-ref %}

{% content-ref url="color-sequences/" %}
[color-sequences](color-sequences/)
{% endcontent-ref %}

{% content-ref url="color-sequences/color-wheel.md" %}
[color-wheel.md](color-sequences/color-wheel.md)
{% endcontent-ref %}

{% content-ref url="figlet-font-selector.md" %}
[figlet-font-selector.md](figlet-font-selector.md)
{% endcontent-ref %}

### Other console tools

For other console tools that Terminaux provides, you can access the below page:

{% content-ref url="console-tools/" %}
[console-tools](console-tools/)
{% endcontent-ref %}
