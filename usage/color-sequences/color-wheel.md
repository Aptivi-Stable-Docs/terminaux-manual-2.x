---
description: Here's how you can let the users choose their own colors
---

# 🎨 Color Wheel

The new color wheel, `ColorSelector`, is now available. You can use this brand new color selector to get information about your selected color visually. You can call the `OpenColorSelector()` function in your code to get the new color selector.

The color selector allows you to change the color in the following modes:

* In true color mode, you can change the hue, the lighting, and the saturation by pressing the appropriate key shortcuts to change the colors.
* In 256 and 16 colors mode, you can select a color using the right and the left arrow keys. It shows you color information, including the CMYK, HSL, and grayscale values.

The following controls are available:

| Key            | Action                                                                                           |
| -------------- | ------------------------------------------------------------------------------------------------ |
| `ENTER`        | Accept color selection                                                                           |
| `ESC`          | DIscard changes                                                                                  |
| `H`            | Help page                                                                                        |
| `LEFT`         | Reduce hue (for true color)                                                                      |
|                | Previous color (for 256 and 16 colors)                                                           |
| `CTRL + LEFT`  | Reduce lightness (true color only)                                                               |
| `RIGHT`        | Increase hue (for true color)                                                                    |
|                | Next color (for 256 and 16 colors)                                                               |
| `CTRL + RIGHT` | Increase lightness (true color only)                                                             |
| `DOWN`         | Reduce saturation (true color only)                                                              |
| `UP`           | Increase saturation (true color only)                                                            |
| `TAB`          | Change color mode (true color, 256 colors, and 16 colors)                                        |
| `I`            | Shows the extended color information, including info about color deficiencies.                   |
| `V`            | Shows an info box that visually demonstrates the selected color with all the color deficiencies. |
| `O`            | Increases the opacity                                                                            |
| `P`            | Decreases the opacity                                                                            |

This function returns a `Color` instance containing necessary information. To know more about the structure of the `Color` class, visit the page below to learn more.

{% content-ref url="./" %}
[.](./)
{% endcontent-ref %}
