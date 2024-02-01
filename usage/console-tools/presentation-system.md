---
description: Presenting your things to the kernel!
---

# 📽 Presentation System

This API provides you the presentation system used for presenting something to your users in the full-screen view. It's like a presentation in steroids.

## How to present

To present your presentation to your users, you must implement a `Presentation` class instance, which must assign the following variables in the constructor:

* `Name`
  * Presentation name
* `Pages`
  * Presentation pages (List of `PresentationPage` instances)

To implement the `PresentationPage` instances, you must call its constructor with the following variables:

* `Name`
  * Presentation page name
* `Pages`
  * Presentation page elements (List of `IElement` instances)

To implement the page elements, make new instances of the elements. Base elements that Nitrocid KS implements are:

* `TextElement`
  * Static text.
  * The first argument in the element `Arguments` is the string to be printed.
  * Optionally, `InvokeAction` can be specified to take any action after the element is rendered by `IElement.Render()`.
* `DynamicTextElement`
  * Dynamic text.
  * The first argument in the element `Arguments` is the action to which it generates the string, for example, `TimeDateRenderers.Render()`.
  * Optionally, `InvokeAction` can be specified to take any action after the element is rendered by `IElement.Render()`.
* `InputElement`
  * Input.
  * The first argument in the element `Arguments` is the action to which it generates the input string, for example, `TimeDateRenderers.Render()`.
  * Optionally, `InvokeActionInput` can be specified to take any action after the element is rendered by `IElement.Render()`. It is invoked with the written input as the first element in the object list array.
* `MaskedInputElement`
  * Masked input.
  * The first argument in the element `Arguments` is the action to which it generates the input string, for example, `TimeDateRenderers.Render()`.
  * Optionally, `InvokeActionInput` can be specified to take any action after the element is rendered by `IElement.Render()`. It is invoked with the written input as the first element in the object list array.
* `ChoiceInputElement`
  * Single choice input.
  * The first argument in the element `Arguments` is the question, and the remaining arguments are either choice strings or an array of choice strings
  * Optionally, `InvokeAction` can be specified to take any action after the element is rendered by `IElement.Render()`.
* `MultipleChoiceInputElement`
  * Multiple choice input.
  * The first argument in the element `Arguments` is the question, and the remaining arguments are either choice strings or an array of choice strings
  * Optionally, `InvokeAction` can be specified to take any action after the element is rendered by `IElement.Render()`.

{% hint style="info" %}
You can also make your custom `IElement` in your mod code, and no registration is needed.
{% endhint %}

## Controls

The presentation viewer has the following controls:

* `ENTER`
  * Advances to the next page
* `ESC`
  * Bails out from the presentation
  * Has no effect on kiosk and modal presentations
