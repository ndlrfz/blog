+++
date = '2025-04-20T17:09:46+07:00'
draft = false
tldr = 'Up your productivity with these vim motions and tips.'
title = 'Vim Motions Tips'
+++

## Exit like a pro

* Save and exit => `ZZ`.
* Save without saving => `ZQ`.

## Select inside () (Bracket) and {} (Curly Bracket)

* Select within `()` => `vib`.
* Select within `{}` => `viB`.

## Edit multiple lines at once

Step by step to insert at the beginning of the line:

1. `Ctrl+v` to get visual mode.
2. `I` to insert mode.
3. Enter your HTML tag `<p>`.
4. `ESC`.

Step by step to insert at the end of the line:

1. `Ctrl+v` to get the visual mode and select each line.
2. `$` sign to select to the end of paragraph.
3. `A` to append the closing tag `</p>`.
4. `ESC`.

```html
# AFTER
<p>paragraph one</p>
<p>paragraph two</p>
<p>paragraph three</p>
<p>paragraph four</p>
<p>paragraph five</p>
<p>paragraph six</p>
<p>paragraph seven</p>

# BEFORE
paragraph one
paragraph two
paragraph three
paragraph four
paragraph five
paragraph six
paragraph seven
```

## Toggle between uppercase and lowercase

* Use `~` to toggle the beginning character of the word.
* Use `g + ~ + $` to toggle to the end of paragraph.

## Reindent the whole file

Press `gg` to go to the top, then `=` and `G` to the bottom of the file.

## Jump between (), [], {}, etc

Use the `%` sign to jump between those braces.

## Suspend and restore vim

* Press `Ctrl+z` to suspend vim in the background.
* Type command `fg` to access vim.

## Open URL or file under the cursor

* Move your cursor under the URL and press `gx` to open in the default browser.
* For file, do the same and replace with the `gf`.

## Using vim mark and return to it

Step by step to mark location:

1. Type `m` to mark the current line.
2. Type `a` as the identifier. You can change `a` with any identidier.

Step by step to return to marked line:

1. Press `'` or single quote.
2. Press the identifier, for example `a`.

If you want to mark and jump of different file, use `A` as identifier. So:

* `m` and `A`.
* `'` and `A`.

## Jump to specific line number

Enter the line number, such as `12`, then `G`.

## Join lines

Use `J` to join two lines into single line.
