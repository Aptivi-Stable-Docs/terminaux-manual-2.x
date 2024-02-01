---
description: We need to write to the console
---

# 🖊 Console Writers

Terminaux provides a vast amount of console writers for different purposes, like the progress bar writer, writing console output in color, etc.

### Normal console writers

Starting from `ConsoleWriters`, this namespace provides the following classes:

* `ListWriterColor`
  * Provides you with the necessary functions to let you write the list entries to the console easily.
* `TextWriterColor`
  * Provides you with the necessary functions to allow you to write the text to the console with and without color.
* `TextWriterHighlightedColor`
  * Provides you with the necessary functions to allow you to write the highlighted text to the console with and without color.
* `TextWriterSlowColor`
  * Provides you with the necessary functions to simulate a typewriter writing a requested string to the console with and without color.
* `TextWriterWhereColor`
  * Provides you with the necessary functions to write the text in a specific position to the console with and without color.
* `TextWriterWhereSlowColor`
  * Provides you with the necessary functions to simulate a typewriter that writes a text in a specific position to the console with and without color.
* `TextWriterWrappedColor`
  * Provides you with the necessary functions to allow you to wrap long outputs to pages, also called a pager.

Consult the below page to find out how to use these functions.

{% embed url="https://aptivi.github.io/Terminaux/api/Terminaux.Writer.ConsoleWriters.html" %}

{% hint style="info" %}
The console writers have three variants of writing functions:

* `Write()`: Default colors
* `WriteColor()`: Foreground colors
* `WriteColorBack()`: Foreground and background colors
{% endhint %}

#### Wrapped pager controls

The below wrapped pager controls are available when wrapping is enabled:

* `ESC`: Exits the pager
* `Page Up`: Moves the output by one page backward, but stops at the beginning of the output.
* `Page Down`: Moves the output by one page forward, but stops at the end of the output.
* `Up Arrow`: Moves up by one line
* `Down Arrow`: Moves down by one line
* `Home`: Goes to the first page
* `End`: Goes to the last page
* `Any key`: Moves the output by one page forward and exits if it reaches end of line

### Fancy writers

Alongside these writers, there are also writers that are categorized as "fancy" because they either print so awesome or they print graphics. Some of these writers allow you to supply text and/or a title. They can be found in the `FancyWriters` namespace that provides the below classes:

* `BorderColor`
  * Provides you with the necessary functions to allow you to draw a border somewhere in the console.
* `BorderTextColor`
  * Provides you with the necessary functions to allow you to draw a border somewhere in the console with text inside the box.
* `BoxColor`
  * Provides you with the necessary functions to allow you to draw a box somewhere in the console.
* `BoxFrameColor`
  * Provides you with the necessary functions to allow you to draw a box frame somewhere in the console.
* `CenteredFigletTextColor`
  * Provides you with the necessary functions to allow you to render a string using the provided Figlet font in the middle of the console.
* `CenteredTextColor`
  * Provides you with the necessary functions to allow you to render a string in the middle of the console.
* `FigletColor`
  * Provides you with the necessary functions to allow you to render a string using the provided Figlet font to the console.
* `FigletWhereColor`
  * Provides you with the necessary functions to allow you to render a string using the provided Figlet font to the console at any position you want.
* `InfoBoxColor`
  * Provides you with the necessary functions to allow you to render an information box containing text inside it in the middle of the console. You can make it either modal (having a user press any key to exit) or informational (not waiting for any user input).
* `PowerLineColor`
  * Provides you with the necessary functions to allow you to build PowerLine segments and display them to the console.
* `ProgressBarColor`
  * Provides you with the necessary functions to allow you to render a horizontal progress bar to the console.
* `ProgressBarVerticalColor`
  * Provides you with the necessary functions to allow you to render a vertical progress bar to the console.
* `SeparatorWriterColor`
  * Provides you with the necessary functions to allow you to render a separator including text to the console.
* `TableColor`
  * Provides you with the necessary functions to allow you to render a table to the console.

Consult the below page to find out how to use these functions.

{% embed url="https://aptivi.github.io/Terminaux/api/Terminaux.Writer.FancyWriters.html" %}

The tools for fancy writers can also be found here:

{% embed url="https://aptivi.github.io/Terminaux/api/Terminaux.Writer.FancyWriters.Tools.html" %}

### Miscellaneous writers

Finally, the miscellaneous writers are the writers that don't have any meaningful category. That's when `MiscWriters` comes in. This namespace contains these classes:

* `LineHandleWriter`
  * Provides you with the necessary functions to allow you to render a line of a text file with the compiler-like line handle using the specified line and column to the console.
* `LineHandleRangedWriter`
  * Provides you with the necessary functions to allow you to render a line of a text file with the compiler-like line handle using the specified line and column range to the console. This is used to highlight relevant parts of the entire line

Consult the below page to find out how to use these functions:

{% embed url="https://aptivi.github.io/Terminaux/api/Terminaux.Writer.MiscWriters.html" %}
