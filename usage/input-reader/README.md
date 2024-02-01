---
description: May I read what you've written, please?
---

# 🖱 Input Reader

This functionality is an important part of any interactive console application, because it gives users a chance to input what they want to write to the console.

You can easily use this feature in any interactive console application that uses Terminaux. Just use the `Terminaux.Reader` class that contains:

```csharp
public static string Read(bool interruptible = false)
public static string Read(TermReaderSettings settings, bool interruptible = false)
public static string Read(string inputPrompt, bool interruptible = false)
public static string Read(string inputPrompt, TermReaderSettings settings, bool interruptible = false)
public static string ReadPassword(bool interruptible = false)
public static string ReadPassword(TermReaderSettings settings, bool interruptible = false)
public static string ReadPassword(string inputPrompt, bool interruptible = false)
public static string ReadPassword(string inputPrompt, TermReaderSettings settings, bool interruptible = false)
public static string Read(string inputPrompt, string defaultValue, bool password = false, bool oneLineWrap = false, bool interruptible = false)
public static string Read(string inputPrompt, string defaultValue, TermReaderSettings settings, bool password = false, bool oneLineWrap = false, bool interruptible = false)
```

Each one of these functions creates a reader state, `TermReaderState`, that contains essential information about the current reader state, including, but not limited to:

* Current text
* Input prompt text
* Current text position
* Kill buffer
* Reader settings

Alternatively, you can access the `Input` class, which contains almost all the functions that wrap against the reader, but with some extra input-related functions.

{% hint style="info" %}
If you're making your own mod in Nitrocid KS, it's best to use its own Input class rather than Terminaux's, as the class there actually deals with the screensaver in most circumstances.
{% endhint %}

Any key will append the selected characters to the current text input, and `RETURN` will accept the input. For more information about key bindings, go to the below page.

{% content-ref url="keybindings.md" %}
[keybindings.md](keybindings.md)
{% endcontent-ref %}

You can access the global reader settings by referencing the `GlobalReaderSettings` found in the `Inputs` class.

### History tools

You can now set the history entry list with your array of history entries or clear the history list using the following functions:

* `SetHistory(List<string> History)`
  * Sets the history to the chosen history list
* `ClearHistory()`
  * Clears all history entries

### State tools

You can also check to see if the console reader facility is busy getting input or not. The property, `Busy`, indicates this by returning `true` if there is input to be entered by the user.
