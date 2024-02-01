---
description: How do I wrap the console?
---

# 🔌 Console Wrapper

Terminaux provides you with a powerful console wrapper that allows you to customize how the console behaves in your .NET console applications that make use of this wrapper and/or built-in Terminaux features. This wrapper is easy to use, amidst the recent structural improvements to the console wrapper functionality compared to Terminaux 1.x.

One big advantage of using this console wrapper is that you're able to get the console cursor visibility, but only if you're using Terminaux's cursor visibility wrapper. This works on Windows, macOS, Android, and Linux.

To use this console wrapper, just replace all the calls to `Console` with our replacement `ConsoleWrapper` to take advantage of Terminaux's console wrapping feature. However, you can use this wrapper only for the following actions:

* `CursorLeft` (get and set)
* `CursorTop` (get and set)
* `WindowWidth` (get)
* `WindowHeight` (get)
* `BufferHeight` (get)
* `CursorVisible` (get and set)
* `KeyAvailable` (get)
* `TreatCtrlCAsInput` (get and set)
* `Clear()` (with and without background)
* `SetCursorPosition()`
* `Beep()`
* `ReadKey()`
* `Write()`
* `WriteLine()`

{% hint style="info" %}
We'll expand the list of available wrappers soon upon evaluation of the rest of the `System.Console` functions.

**Note that properties and functions that work only for Windows, such as `MoveBufferArea`, and have no good alternative workarounds for macOS and Linux are not going to be wrapped.**
{% endhint %}

## Setting the Wrappers

You can customize the console wrappers so that applications that call the Terminaux console wrapper can make use of your own custom wrapper function by setting the action properties found in `ConsoleWrapperTools`. You can make changes to the following wrappers (all prefixed by the `Action` word in all the properties):

* `IsDumb`
* `CursorLeft`
* `SetCursorLeft`
* `CursorTop`
* `SetCursorTop`
* `WindowWidth`
* `WindowHeight`
* `BufferHeight`
* `CursorVisible`
* `GetCursorVisible`
* `TreatCtrlCAsInput`
* `KeyAvailable`
* `Clear()` (without background)
* `ClearLoadBack()` (with background)
* `SetCursorPosition()`
* `Beep()`
* `BeepSeq()`
* `ReadKey()`
* `WriteChar()`
* `WriteStringNonStandalone()`
* `WriteString()`
* `WriteParameterized()`
* `WriteParameterizedNonStandalone()`
* `WriteLine()`
* `WriteLineStirng()`
* `WriteLineStringNonStandalone()`
* `WriteLineParameterized()`
* `WriteLineParameterizedNonStandalone()`

{% hint style="info" %}
In order for your console wrapper to be usable, all your custom wrapper functions must be fast, as interactive TUIs rely on performance.
{% endhint %}
