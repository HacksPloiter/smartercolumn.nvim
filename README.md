<h1 align="center">
smartcolumn.nvim
</h1>

<p align="center">
<a href="https://github.com/m4xshen/smartcolumn.nvim/stargazers">
    <img
      alt="Stargazers"
      src="https://img.shields.io/github/stars/m4xshen/smartcolumn.nvim?style=for-the-badge&logo=starship&color=fae3b0&logoColor=d9e0ee&labelColor=282a36"
    />
  </a>
  <a href="https://github.com/m4xshen/smartcolumn.nvim/issues">
    <img
      alt="Issues"
      src="https://img.shields.io/github/issues/m4xshen/smartcolumn.nvim?style=for-the-badge&logo=gitbook&color=ddb6f2&logoColor=d9e0ee&labelColor=282a36"
    />
  </a>
  <a href="https://github.com/m4xshen/smartcolumn.nvim/contributors">
    <img
      alt="Contributors"
      src="https://img.shields.io/github/contributors/m4xshen/smartcolumn.nvim?style=for-the-badge&logo=opensourceinitiative&color=abe9b3&logoColor=d9e0ee&labelColor=282a36"
    />
  </a>
</p>

![demo](https://user-images.githubusercontent.com/74842863/219844450-37d96fe1-d15d-4aaf-ae57-1c6ce66d8cbc.gif)

## 📃 Introduction
  
A Neovim plugin hiding your colorcolumn when unneeded.

## ⚙️ Functions

- The colorcolumn is hidden as default, but it appears after one of lines in the file exceeds the `colorcolumn` value you set.
- The colorcolumn is hidden in the filetypes in `disabled_filetypes`.
- You can set custom colorcolumn value for different filetype.

## 📦 Installation

1. Install via your favorite package manager.

- [lazy.nvim](https://github.com/folke/lazy.nvim)
```Lua
{
  "m4xshen/smartcolumn.nvim",
  opts = {}
},
```

- [packer.nvim](https://github.com/wbthomason/packer.nvim)
```Lua
use "m4xshen/smartcolumn.nvim"
```

- [vim-plug](https://github.com/junegunn/vim-plug)
```VimL
Plug "m4xshen/smartcolumn.nvim"
```

2. Setup the plugin in your `init.lua`. This step is not needed with lazy.nvim if `opts` is set as above.
```Lua
require("smartcolumn").setup()
```

## 🔧 Configuration

You can pass your config table into the `setup()` function.

The available options:

- `colorcolumn`: screen columns that are highlighted
  - type of the value: integer
  - default value: `80`
- `disabled_filetypes`: the `colorcolumn` will be disabled under the filetypes in this table
  - type of the value: table of strings
  - default value: `{ "help", "text", "markdown" }`
- `limit_to_window`: the `colorcolumn` will be displayed based on the visible lines in the window instead of all lines in the current buffer
  - type of the value: boolean
  - default value: `false`
- `custom_colorcolumn`: custom `colorcolumn` values for different filetype. when editing a buffer with a filetype present in this table, the value for that filetype will be used in place of `config.colorcolumn`.
  - type of the value: table of filetype names to integers
  - default value: `{}`

Example: With `custom_colorcolumn = { ruby = 120, java = 200 }` the colorcolumn will appear at 120 characters when editing a buffer with filetype `ruby`, but will appear at 200 characters when editing a buffer with filetype `java`.

  
### Default config

```Lua
local config = {
   colorcolumn = 80,
   disabled_filetypes = { "help", "text", "markdown" },
   custom_colorcolumn = {},
   limit_to_window = false,
}
```
