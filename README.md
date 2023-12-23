<h1 align="center">
smartercolumn.nvim
</h1>

<p align="center">
<a href="https://github.com/HacksPloiter/smartercolumn.nvim/stargazers">
    <img
      alt="Stargazers"
      src="https://img.shields.io/github/stars/HacksPloiter/smartercolumn.nvim?style=for-the-badge&logo=starship&color=fae3b0&logoColor=d9e0ee&labelColor=282a36"
    />
  </a>
  <a href="https://github.com/HacksPloiter/smartercolumn.nvim/issues">
    <img
      alt="Issues"
      src="https://img.shields.io/github/issues/HacksPloiter/smartercolumn.nvim?style=for-the-badge&logo=gitbook&color=ddb6f2&logoColor=d9e0ee&labelColor=282a36"
    />
  </a>
  <a href="https://github.com/HacksPloiter/smartercolumn.nvim/contributors">
    <img
      alt="Contributors"
      src="https://img.shields.io/github/contributors/HacksPloiter/smartercolumn.nvim?style=for-the-badge&logo=opensourceinitiative&color=abe9b3&logoColor=d9e0ee&labelColor=282a36"
    />
  </a>
</p>

![demo](https://user-images.githubusercontent.com/74842863/219844450-37d96fe1-d15d-4aaf-ae57-1c6ce66d8cbc.gif)

## 📃 Introduction

A Neovim plugin which hides your colorcolumn when not needed.

This repo is a clone of original smartcolumn.nvim plugin but enhanced with more features and freedom.
Please note that I'll be committing changes to this repo as per my personal need so feel free to fork it and change the code as per your requirement.

## ⚙️ Features

By enabling this plugin it is assumed that the default colourcolumn behaviour is intended to be overriddeen. Both the underlength and the overlength colorcolumn is enabled as default. Both can be managed separetely. If underlength colorcolumn is disabled but overlength colorcolumn is enabled, the plugin will bring colorcolumn only when the length of line (depending on the scope), crosses the specified limit. Limit can be overriddeen in the configuration.

You can:

- hide or show underlength colorcolumn for specific filetype
- hide or show overlength colorcolumn for specific filetype
- customise the colour of above two, with colour hex.
- set custom colorcolumn value for different filetype
- specify the scope where the plugin should work

## 📦 Installation

1. Install via your favorite package manager.

- [lazy.nvim](https://github.com/folke/lazy.nvim)

```Lua
{
  "HacksPloiter/smartercolumn.nvim",
  opts = {}
},
```

- [packer.nvim](https://github.com/wbthomason/packer.nvim)

```Lua
use "HacksPloiter/smartercolumn.nvim"
```

- [vim-plug](https://github.com/junegunn/vim-plug)

```VimL
Plug "HacksPloiter/smartercolumn.nvim"
```

2. Setup the plugin in your `init.lua`. This step is not needed with lazy.nvim
   if `opts` is set as above.

```Lua
require("smartercolumn").setup()
```

## 🔧 Configuration

You can pass your config table into the `setup()` function or `opts` if you use
lazy.nvim.

The available options:

- `colorcolumn` (strings or table) : screen columns that are highlighted. This overrides cc specified anywhere else. If left blank gets the existing cc value. If left blank and not specified anywhere else, sets 81 as the cc.
  - `"81"` (default)
  - `{ "81" }`
- `disabled_filetypes` (table of strings) : the `colorcolumn` will be disabled
  under the filetypes in this table
  - `{ "help", "text", "markdown" }` (default)
  - `{ "NvimTree", "lazy", "mason", "help", "checkhealth", "lspinfo", "noice", "Trouble", "fish", "zsh"}`
- `scope` (strings): the plugin only checks whether the lines within scope
  exceed colorcolumn
  - `"file"` (default): current file
  - `"window"`: visible part of current window
  - `"line"`: current line
- `custom_colorcolumn` (table or function returning string): custom
  `colorcolumn` values for different filetypes
  - `{}` (default)
  - `{ ruby = "120", java = { "180", "200"} }`
  - you can also pass a function to handle more complicated logic:
  ```lua
  custom_colorcolumn = function ()
     return "100"
  end
  ```
- `underlengthcc = "true"` (true/false string)
  - `"true"`  (enables highlighting of colorcolumn even when it is underlength)
  - `"false"` (disables highlighting of colorcolumn when it is underlength)
- `underlengthhex = "#00FFFF"` (underlength cc colour hex value)
- `overlengthcc = "true"` (true/false string)
  - `"true"`  (enables highlighting of colorcolumn even when it is overlength)
  - `"false"` (disables highlighting of colorcolumn when it is overlength)
- `overlengthhex = "#f92672"` (overrlength cc colour hex value)

### Default config

```Lua
local config = {
   colorcolumn = "81",
   disabled_filetypes = { "help", "text", "markdown" },
   custom_colorcolumn = {},
   scope = "file",
   underlengthcc = 'true',
   underlengthhex = "#00FFFF",
   overlengthcc = 'true',
   overlengthhex = "#f92672",
}
```
