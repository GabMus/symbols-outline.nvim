# symbols-outline.nvim

**A tree like view for symbols in Neovim using the Language Server Protocol.
Supports all your favourite languages.**

![demo](https://github.com/simrat39/rust-tools-demos/raw/master/symbols-demo.gif)

### Prerequisites

- `neovim 0.5+`
-  Properly configured Neovim LSP client

### Installation

Using `vim-plug`

```vim
Plug 'simrat39/symbols-outline.nvim'
```

### Configuration

Define a global variable `symbols_outline` as follows:

Only add stuff that you want to override (even in nested tables), or skip this section entirely if you
want to roll with the defaults.

```lua
-- init.lua
vim.g.symbols_outline = {
    highlight_hovered_item = true,
    show_guides = true,
    auto_preview = true,
    position = 'right',
    width = 25,
    show_numbers = false,
    show_relative_numbers = false,
    show_symbol_details = true,
    keymaps = {
        close = "<Esc>",
        goto_location = "<Cr>",
        focus_location = "o",
        hover_symbol = "<C-space>",
        rename_symbol = "r",
        code_actions = "a",
    },
    lsp_blacklist = {},
    symbol_blacklist = {},
    symbols = {
        File = {icon = "", hl = "TSURI"},
        Module = {icon = "", hl = "TSNamespace"},
        Namespace = {icon = "", hl = "TSNamespace"},
        Package = {icon = "", hl = "TSNamespace"},
        Class = {icon = "𝓒", hl = "TSType"},
        Method = {icon = "ƒ", hl = "TSMethod"},
        Property = {icon = "", hl = "TSMethod"},
        Field = {icon = "", hl = "TSField"},
        Constructor = {icon = "", hl = "TSConstructor"},
        Enum = {icon = "ℰ", hl = "TSType"},
        Interface = {icon = "ﰮ", hl = "TSType"},
        Function = {icon = "", hl = "TSFunction"},
        Variable = {icon = "", hl = "TSConstant"},
        Constant = {icon = "", hl = "TSConstant"},
        String = {icon = "𝓐", hl = "TSString"},
        Number = {icon = "#", hl = "TSNumber"},
        Boolean = {icon = "⊨", hl = "TSBoolean"},
        Array = {icon = "", hl = "TSConstant"},
        Object = {icon = "⦿", hl = "TSType"},
        Key = {icon = "🔐", hl = "TSType"},
        Null = {icon = "NULL", hl = "TSType"},
        EnumMember = {icon = "", hl = "TSField"},
        Struct = {icon = "𝓢", hl = "TSType"},
        Event = {icon = "🗲", hl = "TSType"},
        Operator = {icon = "+", hl = "TSOperator"},
        TypeParameter = {icon = "𝙏", hl = "TSParameter"}
    }
}
```

| Property               | Description                                                                    | Type               | Default                  |
| ---------------------- | ------------------------------------------------------------------------------ | ------------------ | ------------------------ |
| highlight_hovered_item | Whether to highlight the currently hovered symbol (high cpu usage)             | boolean            | true                     |
| show_guides            | Wether to show outline guides                                                  | boolean            | true                     |
| position               | Where to open the split window                                                 | 'right' or 'left'  | 'right'                  |
| width                  | How big the window is (relative to the current split)                          | int                | 25                       |
| auto_preview           | Show a preview of the code on hover                                            | boolean            | true                     |
| show_numbers           | Shows numbers with the outline                                                 | boolean            | false                    |
| show_relative_numbers  | Shows relative numbers with the outline                                        | boolean            | false                    |
| show_symbol_details    | Shows extra details with the symbols (lsp dependent)                           | boolean            | true                     |
| keymaps                | Which keys do what                                                             | table (dictionary) | [here](#default-keymaps) |
| symbols                | Icon and highlight config for symbol icons                                     | table (dictionary) | scroll up                |
| lsp_blacklist          | Which lsp clients to ignore                                                    | table (array)      | {}                       |
| symbol_blacklist       | Which symbols to ignore ([possible values](./lua/symbols-outline/symbols.lua)) | table (array)      | {}                       |

### Commands

| Command                | Description            |
| ---------------------- | ---------------------- |
| `:SymbolsOutline`      | Toggle symbols outline |
| `:SymbolsOutlineOpen`  | Open symbols outline   |
| `:SymbolsOutlineClose` | Close symbols outline  |

### Default keymaps

| Key        | Action                                             |
| ---------- | -------------------------------------------------- |
| Escape     | Close outline                                      |
| Enter      | Go to symbol location in code                      |
| o          | Go to symbol location in code without losing focus |
| Ctrl+Space | Hover current symbol                               |
| r          | Rename symbol                                      |
| a          | Code actions                                       |

