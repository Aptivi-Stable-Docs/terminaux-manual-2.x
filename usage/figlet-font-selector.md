---
description: Select your favorite font from here!
---

# 🖊 Figlet Font Selector

The figlet font selector allows you to flexibly select a Figlet font provided by our own Figlet library, Figletize. It shows you a live preview of the font to show you how your selected font looks like prior to submission.

You can simply invoke the selector on your interactive console application by calling the below function like so:

```csharp
string font = FigletSelector.PromptForFiglet();
```

Usually, this call is followed by getting a figlet font from the above variable and writing it using the `WriteFiglet()` function:

```csharp
var figlet = FigletTools.GetFigletFont(font);
FigletColor.WriteFiglet("Hello!", figlet, ConsoleColors.Green);
```

Additionally, you can press `S` to write the desired font name and quickly switch to that font. If you want to cancel, you can press `ESC`.

More details about `WriteFiglet()` can be found in the below link:

{% content-ref url="console-tools/console-writers.md" %}
[console-writers.md](console-tools/console-writers.md)
{% endcontent-ref %}
