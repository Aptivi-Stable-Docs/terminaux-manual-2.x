---
description: In case you want to set things up
---

# ⚙ Reader Settings

The reader currently has a global settings instance session-wide. However, it can get overridden if you make a new instance of `TermReaderSettings` with some available properties mentioned below set. They get read each time you call this function or you activate a keybinding that uses one of these settings.

Here are the available settings that you can set:

* `PasswordMaskChar` (`CurrentMask` in `Inputs`)
  * Sets the password masking character.
* `HistoryEnabled`
  * Whether the history is enabled or not.
* `LeftMargin`
  * Sets the left margin of the input.
* `RightMargin`
  * Sets the right margin of the input.
* `InputForegroundColor`
  * The foreground color for the input text, as well as the input prompt.
* `InputBackgroundColor`
  * The background color for the input text, as well as the input prompt.
* `Suggestions`
  * Sets a function that you could use to return an array of strings containing auto completion data.
* `SuggestionsDelimiters`
  * Delimiters to split the current input within a function that returns a list of suggestions.
* `TreatCtrlCAsInput`
  * Whether to treat `Ctrl` + `C` as input or not. If enabled, TermRead will process this keybinding as aborting the current input.
