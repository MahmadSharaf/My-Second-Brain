---
{"dg-publish":true,"dg-permalink":"Obsidian/Guides/How to add a font to Obsidian for all devices or for specific language","permalink":"/Obsidian/Guides/How to add a font to Obsidian for all devices or for specific language/","tags":["#obsidian","#how-to","#font"],"created":"2024-10-01T21:54:40","updated":"2024-10-03T09:20:18"}
---

# How to Add a New Font to Obsidian

Following the guide in this [Reddit post](https://www.reddit.com/r/ObsidianMD/comments/15ka1lf/how_to_add_a_new_font_on_mobile/), as below:
1. Convert the font file to CSS through this website https://hellogreg.github.io/woff2base/ or https://www.fontconverter.io/en/css-embedded-font-base64.
2. Make sure the CSS font property contains `font-family: "{fontName}"`
3. Place the generated CSS file in Obsidian snippets folder `.obsidian/snippets`
4. In Obsidian Settings/Appearance
	1. Enable the CSS file, under CSS snippets,
	2. in Text Font, enter the font name placed in the CSS under `font-family`

```css
@font-face {
	font-family: '{font-name}';
	src: url(......)
}
```

While if you want to set a specific font to a specific language, you could use `unicode-range` CSS property, so the font is applied to specific set of characters. For example, for Arabic language that includes every possible Arabic character:

```css
@font-face {
	font-family: '{font-name}';
	unicode-range: U+0600-06FF, U+0750-077F, U+08A0-08FF, U+FB1E-FB4F, U+FB50-FDFF, U+FE70-FEFF;
	src: url(......)
}
```

> [!Tip]- Explanation of the Unicode Ranges
> 1. **Arabic (0600–06FF)**:
> 	- This range includes the basic Arabic letters, diacritics, and some punctuation marks.
>     - Example characters: ا (U+0627), ب (U+0628), ت (U+062A), etc.
> 1. **Arabic Supplement (0750–077F)**:
>     
>     - This range includes additional Arabic letters used in various languages.
>     - Example characters: ٱ (U+0671), ٲ (U+0672), etc.
> 2. **Arabic Extended-A (08A0–08FF)**:
>     
>     - This range includes more letters used in specific Arabic dialects and languages.
> 3. **Arabic Presentation Forms-A (FB1E–FB4F)**:
>     
>     - This range contains ligatures and contextual forms of Arabic letters.
>     - Example ligatures: ﻻ (U+0644 U+0627), ﻷ (U+0644 U+0623), etc.
> 4. **Arabic Presentation Forms-B (FB50–FDFF)**:
>     
>     - This range includes additional ligatures and contextual forms.
> 5. **Special Characters (FE70–FEFF)**:
>     
>     - This range includes additional presentation forms and special characters related to Arabic script.

And you could change the Font size for this specific font by adding `size-adjust` CSS property

```css
@font-face {
	font-family: '{font-name}';
	unicode-range: U+0600-06FF, U+0750-077F, U+08A0-08FF, U+FB1E-FB4F, U+FB50-FDFF, U+FE70-FEFF;
	size-adjust: 120%;
	src: url(......)
}
```
