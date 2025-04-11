## NEOVIM
> **Note**: for clarity, all the shortcuts and keymaping will be inside [`keymaps.txt`](keymaps.txt)

**Basic Usage**

#### Starting Neovim
```bash
# Open Neovim
nvim

# Open a specific file
nvim filename.md

# Open multiple files in tabs
nvim -p file1.md file2.md file3.md
```

#### Essential Mods

> Neovim operates in different modes:

- **Normal Mode** 'n' (default when you open Neovim)

- **Insert Mode** 'i' (for typing text)

- **Command Mode** ':' (accessing by pressing esc and then ':')

### Setting Up Neovim Configuration

Neovim configuration is stored in `~/.config/nvim/` directory:

```bash
# Create Neovim config directory
mkdir -p ~/.config/nvim

# Create init.vim or init.lua file
touch ~/.config/nvim/init.vim
# OR
touch ~/.config/nvim/init.lua
```

## Development Environment Setup


