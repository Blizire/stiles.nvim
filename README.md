# stiles.nvim

A personal theme for my current neovim configuration. Currently based off of
ellisonleao/gruvbox.nvim

# Prerequisites

Neovim 0.12+

# Installing

Plugins are installed with Neovim's built-in `vim.pack`:

```lua
vim.pack.add({
  "https://github.com/blizire/stiles.nvim"
})

require("stiles").setup()
vim.cmd.colorscheme("stiles")
```

# Basic Usage

Inside `init.vim`

```vim
set background=dark " or light if you want light mode
colorscheme stiles
```

Inside `init.lua`

```lua
vim.o.background = "dark" -- or "light" for light mode
vim.cmd([[colorscheme stiles]])
```

# Configuration

Additional settings for stiles are:

```lua
-- Default options:
require("stiles").setup({
  terminal_colors = true, -- add neovim terminal colors
  undercurl = true,
  underline = true,
  bold = true,
  italic = {
    strings = true,
    emphasis = true,
    comments = true,
    operators = false,
    folds = true,
  },
  strikethrough = true,
  invert_selection = false,
  invert_signs = false,
  invert_tabline = false,
  inverse = true, -- invert background for search, diffs, statuslines and errors
  contrast = "", -- can be "hard", "soft" or empty string
  palette_overrides = {},
  overrides = {},
  dim_inactive = false,
  transparent_mode = false,
})
vim.cmd("colorscheme stiles")
```

**VERY IMPORTANT**: Make sure to call setup() **BEFORE** calling the colorscheme command, to use your custom configs

## Overriding

### Palette

You can specify your own palette colors. For example:

```lua
require("stiles").setup({
    palette_overrides = {
        bright_green = "#990000",
    }
})
vim.cmd("colorscheme stiles")
```

### Highlight groups

If you don't enjoy the current color for a specific highlight group, now you can just override it in the setup. For
example:

```lua
require("stiles").setup({
    overrides = {
        SignColumn = {bg = "#ff9900"}
    }
})
vim.cmd("colorscheme stiles")
```

It also works with treesitter groups and lsp semantic highlight tokens

```lua
require("stiles").setup({
    overrides = {
        ["@lsp.type.method"] = { bg = "#ff9900" },
        ["@comment.lua"] = { bg = "#000000" },
    }
})
vim.cmd("colorscheme stiles")
```

Please note that the override values must follow the attributes from the highlight group map, such as:

- **fg** - foreground color
- **bg** - background color
- **bold** - true or false for bold font
- **italic** - true or false for italic font

Other values can be seen in [`synIDattr`](<https://neovim.io/doc/user/builtin.html#synIDattr()>)
