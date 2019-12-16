# smarty-tmlanguage

This repository contains TmLanguage files that can be consumed by [Smarty 3](https://www.smarty.net/docs/en/) editors and plugins such as [Visual Studio Code](https://github.com/Microsoft/vscode), [Sublime Text](https://www.sublimetext.com), [Atom](https://atom.io), and possibly others.

Latest version of the grammar can be also found as a [VSCode extension](https://marketplace.visualstudio.com/items?itemName=Modix.mx-smarty).

<img src="https://cdn.jsdelivr.net/gh/Modix/smarty-tmlanguage/screenshot.png" width="100%" />

## Installation
``` sh
npm install @modix/smarty-tmlanguage --save
```

## Known restrictions

Currently, the following features of Smarty 3 are not implemented:

- Ternary operator (`{$a ? $b : $c}`)
- Line-breaks within modifiers
- `nocache` pseudo attribute (`{$var nocache}`)
- Method calls with parentheses (`$smarty->clearAllCache()`)
- Object property accesstor `->`
- Object method chaining (`{$object->method1($x)->method2($y)}`)
- Opening and closing `{strip}` everywhere

The rules have a high understanding of the structure of the document, or with other words, they are very restrictive. This means, if you close a block (e.g. `{/if}`) without to open it, the highlighter will show that with wrong colorization, because in the case of the `{/if}`, it assumes that you try to divide nothing by the unquoted string "if", since this operation has higher priority than an unallowed `{/if}` statement.

The same counts if you open an `{if}` in a HTML comment, but close it outside, or if a HTML tag is not closed correctly (e.g. `{if $link !== ''}<a href="...">My Link</a{/if}`).