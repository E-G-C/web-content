---
title: "VS Code"
linkTitle: "VS Code"
date: 2023-10-17
# weight: 100
description: Things to keep handy
---

## Auto save

First of all and for you own good, enable the auto save feature in VSCode. To do
so, either:

- Go to `File > Auto Save` or
- Press `Ctrl + Shift + P` and type `auto save` and select
  `File: Toggle Auto Save` or

## Compact Folders

The File Explorer, renders single child folders in a compact form. In such a
form, single child folders will be compressed in a combined tree element.

Setting `explorer.compactFolders` controls this behavior. By default, this
setting is turned on.

## VSCode to no open last workspace

Do not open last workspace or windows, open the preferences, set the settings
below:

`"window.restoreWindows": "none"`

or modify the shortcut with the option `-n` see the [documentation here]
(https://code.visualstudio.com/docs/editor/command-line) for example:

```cmd
"C:\Program Files (x86)\Microsoft VS Code\Code.exe" -n
```

or alternatively run VSCode with `code -n` see more
[here](https://stackoverflow.com/questions/49692748/re-open-vscode-without-last-workspace-or-last-files)

## Duplicate profiles in VSCode

> This allow to simulate multi monitor support in VSCode

In the latest version, it is much simpler. In a window of the project you want
to duplicate, open the command panel (Command + Shift + P in Mac or Ctrl +
Shift + P in Ubuntu), then type `dupl` (and select
`Workspaces: Duplicate As Workspace in New Window`), this will duplicate your
workspace in a new window. Now you can have 2 windows of the same project at the
same time.

## Change VSCode UI font

- Set the font with the extension
  [fonted](https://marketplace.visualstudio.com/items?itemName=degreat.fonted)
- Zoom in (make the font larger) with the extension
  [Zoom](https://marketplace.visualstudio.com/items?itemName=Tyriar.zoom)

## Select and replace all occurrences of a variable name

This comes handy in PowerShell where there isn't `F2` to refactor. To replace a
variable name in Visual Studio Code, you can follow these steps:

- Select the variable you want to replace.
- Use the `editor.action.selectHighlights` command to select all occurrences of
  the variable. The default key mapping for this command is `Ctrl+Shift+L`
- Type the replacement name to replace all occurrences of the variable with the
  new name.

## Horizontal split

Ctrl + Shift + P (Command Palette) Toggle Vertical/Horizontal Editor Layout.

## Jupyter Notebook

You can write and execute PowerShell code in a Jupyter Notebook. To do so, you
need to install the extension `Polyglot Notebooks` then add a cell with the
language `#!pwsh` (first line).

Sometimes the output of a cell is too long and you want to word wrap it. Search
in VSCode settings for `wrap` and look the option `Notebook > Output: Word`.
