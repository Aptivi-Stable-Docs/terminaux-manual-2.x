---
description: Getting a color from a text-based color representation.
---

# 🧭 Color Model Parsing

In addition to Terminaux supporting RGB color model, you can also use the CMYK and other color models when creating the color instances, provided that their specifiers that you must use are:

* RGB's specifier is `rrr;ggg;bbb`, `#RRGGBB`, `#RGB`, `0-255`, or `0-15`
* CMYK's specifier is `cmyk:ccc;mmm;yyy;kkk`
* CMY's specifier is `cmy:ccc;mmm;yyy`
* HSL's specifier is `hsl:hhh;sss;lll`
* HSV's specifier is `hsv:hhh;sss;vvv`
* RYB's specifier is `ryb:rrr;yyy;bbb`
* YIQ's specifier is `yiq:yyy;iii;qqq`
* YUV's specifier is `ryb:yyy;uuu;vvv`

To get a color instance from just the specifiers mentioned above, you first have to pick a source specifier. For example, if you want an HSV color instance from its specifier, you must have a string that holds the HSV color specifier as mentioned above. Then, you can call the `HsvParsingTools`'s `ParseSpecifier()` function to get an HSV instance.

The below parsing tools can be used:

* `CmyParsingTools`: Parses the CMY specifier
* `CmykParsingTools`: Parses the CMYK specifier
* `HslParsingTools`: Parses the HSL specifier
* `HsvParsingTools`: Parses the HSV specifier
* `RgbParsingTools`: Parses the RGB specifier
* `RybParsingTools`: Parses the RYB specifier
* `YiqParsingTools`: Parses the YIQ specifier
* `YuvParsingTools`: Parses the YUV specifier
* `ParsingTools`: Parses the general specifiers

Alternatively, if you want to get an RGB instance from any specifier other than RGB, you can use the `ParseSpecifierToRgb()` function in all the parsing tools, except the RGB one, to get an RGB instance derived from the resulting source color model.

{% hint style="info" %}
You have two options if you don't want to rely on exceptions:

* For boolean-based checks, you can rely on the output of the `IsSpecifierValidRgbHash()`, `IsSpecifierConsoleColors()`, and `IsSpecifierValid()` on `ParsingTools`.
* If you want to also check the values, you can consult the `...AndValueValid()` sibling functions.

You can also use the color-model-specific `IsSpecifierValid()` function, such as `RybParsingTools`.
{% endhint %}
