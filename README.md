<h1 align="center">
  <br>
    <img src="assets/icon.png" alt="logo" width="150">
  <br><br>
  Indent Colorizer
  <br>
  <br>
</h1>
<p align="center">
    <a href="https://marketplace.visualstudio.com/items?itemName=tal7aouy.indent-colorizer"><img src="https://vsmarketplacebadge.apphb.com/version-short/tal7aouy.indent-colorizer.svg?style=for-the-badge&colorA=252526&colorB=43A047&label=VERSION" alt="Version"></a>&nbsp;
    <a href="https://marketplace.visualstudio.com/items?itemName=tal7aouy.indent-colorizer"><img src="https://vsmarketplacebadge.apphb.com/rating-short/tal7aouy.indent-colorizer.svg?style=for-the-badge&colorA=252526&colorB=43A047&label=Rating" alt="Rating"></a>&nbsp;
    <a href="https://marketplace.visualstudio.com/items?itemName=tal7aouy.indent-colorizer"><img src="https://vsmarketplacebadge.apphb.com/installs-short/tal7aouy.indent-colorizer.svg?style=for-the-badge&
    colorA=252526&colorB=43A047&label=Installs" alt="Installs"></a>&nbsp;
    <a href="https://marketplace.visualstudio.com/items?itemName=tal7aouy.indent-colorizer"><img src="https://vsmarketplacebadge.apphb.com/downloads-short/tal7aouy.indent-colorizer.svg?style=for-the-badge&colorA=252526&colorB=43A047&label=Downloads" alt="Downloads"></a>
</p>

---

## Installation

All instructions can be found at [INSTALL.md](./INSTALL.md).

A simple extension to make indentation more readable

![ScreenShot](https://raw.githubusercontent.com/tal7aouy/vscode-indent-colorizer/master/assets/screen.png)

Get it here: [Visual Studio Code Marketplace](https://marketplace.visualstudio.com/items?itemName=tal7aouy.indent-colorizer)

It uses the current editor window tab size and can handle mixed tab + spaces but that is not recommended. In addition it visibly marks lines where the indentation is not a multiple of the tab size. This should help to find problems with indentation in some situations.

### Configuration

Although you can just use it as it is there is the possibility to configure some aspects of the extension:

```js
  // For which languages indent-colorizer should be activated (if empty it means all).
  "indentColorizer.includedLanguages": [] // for example ["php", "ts", "python"]

  // For which languages indent-colorizer should be deactivated (if empty it means none).
  "indentColorizer.excludedLanguages": ["plaintext"]

  // The delay in ms until the editor gets updated.
  "indentColorizer.updateDelay": 100 // 10 makes it super fast but may cost more resources
```

_Notice: Defining both `includedLanguages` and `excludedLanguages` does not make much sense. Use one of both!_

You can configure your own colors by adding and tampering with the following code:

```js
  // Defining custom colors instead of default "Colorizer" for dark backgrounds.
  // (Sorry: Changing them needs an editor restart for now!)
  "indentColorizer.colors": [
    "rgba(255,255,64,0.07)",
    "rgba(127,255,205,0.07)",
    "rgba(255,128,210,0.07)",
    "rgba(79,236,236,0.07)",
    "rgba(78,184,237,0.07)",
    "rgba(233,226,74,0.07)",
    "rgba(101,74,233,0.07)",
  ]

  // The indent color if the number of spaces is not a multiple of "tabSize".
  "indentColorizer.errorColor": "rgba(128,32,32,0.6)"

  // The indent color when there is a mix between spaces and tabs.
  // To be disabled this coloring set this to an empty string.
  "indentColorizer.tabmixColor": "rgba(128,32,96,0.6)"
```

Skip error highlighting for RegEx patterns. For example, you may want to turn off the indent errors for JSDoc's valid additional space (disabled by default), or comment lines beginning with `//`

```js
  // Example of regular expression in JSON (note double backslash to escape characters)
  "indentColorizer.ignoreLinePatterns" : [
    "/[ \t]* [*]/g", // lines begining with <whitespace><space>*
    "/[ \t]+[/]{2}/g" // lines begininning with <whitespace>//
  ]
```

Skip error highlighting for some or all languages. For example, you may want to turn off the indent errors for `markdown` and `haskell` (which is the default)

```js
  "indentColorizer.ignoreErrorLanguages" : [
    "markdown",
    "haskell"
  ]
```

If error color is disabled, indent colors will be rendered until the length of rendered characters (white spaces, tabs, and other ones) is divisible by tabsize. Turn on this option to render white spaces and tabs only.

```js
  "indentColorizer.colorOnWhiteSpaceOnly": true // false is the default
```
