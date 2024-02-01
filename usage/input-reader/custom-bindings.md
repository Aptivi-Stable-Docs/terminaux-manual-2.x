---
description: How to assign your own binding?
---

# 🔌 Custom bindings

TermRead supports custom bindings, which you can assign your `BaseBinding` class containing the following functions you must override:

* `BoundKeys`
  * This holds all the keys to bind your custom action to.
* `DoAction(TermReaderState)`
  * This is the heart of your key binding. You can do anything with the text using the current terminal reader state.

You can also override these:

* `IsExit`
  * If `true`, causes TermRead to assume that the input is done after executing the action that this binding implements.
* `BindMatched(ConsoleKeyInfo)`
  * Specify your own method on how to check to see if the input key matched all the bound keys (`BoundKeys`) in your custom key binding.
* `ResetSuggestionsTextPos`
  * Specifies whether to reset the text position saved for the suggestions. This is usually enabled for custom bindings that have to do with the suggestions.

## Principles

Your keybinding must follow the below principles:

* For text positioning, you must use any function in the `PositioningTools` class.
* For manual console manipulation, you must use any function in the `ConsoleWrapper` class.
* Your bound key must not be already bound to a key that was already bound by either a base or another custom binding, or two bindings execute at the same time, potentially causing conflict.
* To manipulate with text, you must use the `state.CurrentText` property. You must refresh the prompt thereafter.
* To refresh the prompt, you must use the `TermReaderTools.Refresh()` function.

At the end, your base class must look like this at minimum:

```csharp
using System;
using Terminaux.Reader;
using Terminaux.Reader.Tools;

namespace MyApp
{
    internal class MyBinding : BaseBinding, IBinding
    {
        public override ConsoleKeyInfo[] BoundKeys { get; } = 
        {
            // All keys listed below will lead to the below DoAction being executed.
            new ConsoleKeyInfo('\0', ConsoleKey.Key, false, false, false)
        };

        public override void DoAction(TermReaderState state)
        {
            // Your action.
            TermReaderTools.Refresh();
        }
    }
}
```

where:

* `ConsoleKey.Key`
  * Any console key. Consult the [documentation](https://learn.microsoft.com/en-us/dotnet/api/system.consolekey) for more info.
* `\0`
  * A character that must match the corresponding `ConsoleKey.Key`.

{% hint style="info" %}
If you're assigning a key containing `CTRL`, you must assign a character number starting from `0x0`. For example, `CTRL+Y` is `\u0019`.
{% endhint %}

## How to bind

Once you created a base class as mentioned above, you can finally use the `CustomBindings` class to call the `Bind(BaseBinding)` function to add your own binding to the custom binding store, like this:

```csharp
CustomBindings.Bind(new MyBinding());
```

{% hint style="warning" %}
**Warning:** You must call this function once. It does nothing if your binding is already installed.
{% endhint %}

To remove binding, you must use the `Unbind(ConsoleKeyInfo)` command.

## Reader State

When the input reader is invoked by your console application, it creates a state class that is applicable to the current input read. The reader state contains variables that are building blocks for your custom bindings. You can also manipulate with the text positioning using the `PositioningTools` class.

### Variable-based States

The terminal reader state class contains the below most important variables that are documented here, alongside the less important ones.

* `InputPromptLeftBegin` and `InputPromptTopBegin`: Specifies the zero-based X and Y position that indicates the first character of where the first line of the input prompt is being written.
* `InputPromptLeft` and `InputPromptTop`: Specifies the zero-based X and Y position that indicates the first character of the input text in the first line of the input. It includes the left margin and the length of the last input prompt line.
* `LeftMargin` and `RightMargin`: Specifies the left margin and the right margin.
* `CurrentCursorPosLeft` and `CurrentCursorPosTop`: Specifies the current console cursor position relative to the current text position.
* `MaximumInputPositionLeft`: Specifies the maximum zero-based X position of the input that indicates the boundary of the input according to the right margin.
* `LongestSentenceLengthFromLeft`: Specifies the longest sentence length from the leftmost position with respect to the right margin.
* `LongestSentenceLengthFromLeftForFirstLine`: Specifies the longest sentence length from the leftmost position, subtracted from `InputPromptLeft`, in order to get the length for the first line.
* `LongestSentenceLengthFromLeftForGeneralLine`: Specifies the longest sentence length from the leftmost position, subtracted from `LeftMargin`, in order to get the length for a general input line.
* `CurrentTextPos`: Specifies the current text position as a one-based number.
* `InputPromptLastLineLength`: Specifies the last line length from the input prompt text relative to the current console width.
* `InputPromptText`: Specifies the input prompt text.
* `InputPromptHeight`: Specifies the height of the input prompt as simulated by the wrapped line splitter relative to the current console width.
* `CurrentText`: Specifies the current input text being written.
* `PasswordMode`: Specifies whether the reader is in the password mode or not.
* `PressedKey`: Specifies the currently-pressed key.
* `KillBuffer`: Specifies the kill-buffer for use with clipboard-related keybindings, such as Yank and Kill.
* `Settings`: Specifies the reader settings being passed to the reader.
* `CanInsert`: Specifies whether the user can insert a character or not.

You can access the reader settings from the state, whether it's a general settings that Terminaux makes use of or it's an overridden settings instance, using the `Settings` property.

### Positioning tools

Your custom bindings can now change the cursor positioning when manipulating with text so that it becomes easier to make your custom bindings that use positioning tools.

Here are the functions you can use:

* `GoLeftmost()`: Changes the word position to the leftmost position, that is, the first letter.
* `GoRightmost()`: Changes the word position to the rightmost position, that is, the last letter.
* `GoForward()`: Changes the word position a step or a specified number of steps closer to the end of the text.
* `GoBack()`: Changes the word position a step or a specified number of steps closer to the beginning of the text.
* `SeekTo()`: Changes the word position to the selected zero-based position

Once you're done changing positions, if you need to verify that you've changed the position to the correct position, you can use the `Commit()` function.

{% hint style="info" %}
It's not necessary to use the `Commit()` function at the end of each custom binding, because the reader uses this function automatically based on whether to update the position or not.
{% endhint %}

## Writers

You can use the text writers with the current reader settings by using `TextWriterColor`'s `WriteForReader()` and its siblings, passing it the reader settings to take care of the margins.
