---
description: We're listening for any size changes!
---

# ☎ Console Resize Listener

Terminaux also provides you with either a polling-based console resize listener for non-Unix systems or a SIGWINCH-based listener for Unix systems that allows your console application, especially the interactive ones, to listen to every single console resize event for all the platforms. It works on Windows, macOS, Linux, and Android.

{% hint style="warning" %}
If you want to use the resize listener functionality, make sure that your application uses .NET Framework 4.8 or .NET 8.0 or higher and install the `Terminaux.ResizeListener` package due to the changes to the resize listener functionality.

If you can't upgrade your application, stay on 2.3.0 as it provides polling-based listener that works on Linux.
{% endhint %}

{% hint style="info" %}
This listener can be started upon request with `StartResizeListener()`, but can't be stopped until the application is exited either gracefully or ungracefully.
{% endhint %}

## Functions

The console resize listener contains several of the convenience functions that allow you to control the listener.

* `WasResized()`: This function tells you if the console has been resized before or not. If it has been resized before, it returns `true` and sets the cached resized state to `false`.
* `GetCurrentConsoleSize()`: This function gives you a tuple that represents the cached window width and the window height.

{% hint style="info" %}
Upon calling `WasResized()`, it sets the cached resized state to false. You need to either store this value to a local variable or you need to pass `false` to the function to tell it not to reset the state.

The second function gets the console size from the terminal if the listener hasn't started yet. Otherwise, it returns the cached window width and the height in case it's run on a loop, directly or indirectly.
{% endhint %}

## Custom handlers

The console resize listener contains a facility that allows you to set a custom resize handler to change the way how your console application responds to console resizes. This allows you to specify your custom action that gets invoked if the console is resized.

When you start the console resize listener, you'll have an opportunity to specify a custom handler. This way, Terminaux calls your handler if it detects that the console has been resized.

```csharp
public static void StartResizeListener(Action customHandler = null)
```

Your custom handler usually does necessary operations to adapt your application to the resized console size. It gets called every time the resize listener detects that your console has been resized.

{% hint style="info" %}
Your custom handler should satisfy these conditions:

* The handler is static.
* The handler's return value is void.
* The handler's signature should not take any arguments.
*   The handler should, at the very least, re-render the current screen with the following code:

    ```csharp
    if (ScreenTools.CurrentScreen is not null)
        ScreenTools.Render();
    ```
* The handler should be fast in the order of milliseconds (minimum) or microseconds (recommended) in response to the resize.
{% endhint %}

You can also enable or disable the essential handler to be able to control if Terminaux is allowed to run the essential handler that contains the screen refresh code or not. This is useful for situations where you might not want to refresh the screen unless a specific condition is met. `RunEssentialHandler` provides you with this kind of control.

{% hint style="info" %}
You might still want to put code that refreshes the current screen with `ScreenTools.Render()` in your custom resize handler if you've turned off `RunEssentialHandler`. For this very reason, it's turned **on** by default.
{% endhint %}
