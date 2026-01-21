```
+===========================================================================+
|                                                                           |
|   __   _____  ___  ___  ___  ___    ___  ___  ___  ___  ___ ___           |
|   \ \ / / __|/ __|/ _ \|   \| __|  | _ )/ _ \| _ \|   \| __| _ \          |
|    \ V /\__ \ (__| (_) | |) | _|   | _ \ (_) |   /| |) | _||   /          |
|     \_/ |___/\___|\___/|___/|___|  |___/\___/|_|_\|___/|___|_|_\          |
|                                                                           |
|                 Branch-Based Visual Identity for VS Code                  |
|                                                                           |
+===========================================================================+
```

## What is this?

**VS Code Border** automatically colors your VS Code window borders based on your current git branch. Never accidentally commit to the wrong branch again - each branch gets its own unique color identity.

Switch branches? The border color changes. Simple.

## Features

- **Automatic Branch Detection** - Polls git every 5 seconds to detect branch changes
- **Persistent Colors** - Remembers which color belongs to which branch across sessions
- **Full Border Coverage** - Colors window borders, activity bar, sidebar, panels, tabs, and more
- **Customizable Palette** - Define your own color palette in settings
- **Thick Border Mode** - Optional 4px inset border using Custom CSS extension
- **Activity Bar Panel** - Quick view of current branch and color with randomize button
- **Auto Gitignore Management** - Automatically adds `.vscode/settings.json` to `.gitignore` so your branch colors don't pollute your commits

## Installation

### Prerequisites

- [VS Code](https://code.visualstudio.com/) v1.85.0 or higher
- [Node.js](https://nodejs.org/) (for building from source)
- [Git](https://git-scm.com/) (extension requires a git repository)

### From Source

```bash
# Clone the repository
git clone https://github.com/xxgvqxx/vscode-window-identifier.git
cd vscode-window-identifier

# Install vsce if you don't have it
npm install -g @vscode/vsce

# Package the extension
vsce package

# Install in VS Code
code --install-extension vscode-border-0.0.6.vsix
```

### Post-Install

1. Reload VS Code (`Cmd+Shift+P` → "Developer: Reload Window")
2. Open a git repository
3. The extension activates automatically and assigns a color to your branch

## Commands

| Command | Description |
|---------|-------------|
| `VS Code Border: Randomize Color` | Assign a new random color to the current branch |
| `VS Code Border: Enable Thick Border (Custom CSS)` | Enable 4px thick border (requires Custom CSS extension) |

Access via Command Palette (`Cmd+Shift+P` / `Ctrl+Shift+P`)

## Settings

| Setting | Type | Default | Description |
|---------|------|---------|-------------|
| `vscodeBorder.primaryColors` | `array` | Material Design colors | List of hex colors to randomize from |

### Default Color Palette

```json
[
  "#E53935", "#D81B60", "#8E24AA", "#3949AB", "#1E88E5",
  "#039BE5", "#00897B", "#43A047", "#FDD835", "#FB8C00", "#F4511E"
]
```

### Custom Colors Example

```json
{
  "vscodeBorder.primaryColors": [
    "#FF6B6B",
    "#4ECDC4",
    "#45B7D1",
    "#96CEB4",
    "#FFEAA7"
  ]
}
```

## UI Elements Styled

The extension applies your branch color to:

- `window.activeBorder` - Active window border
- `window.inactiveBorder` - Inactive window border
- `activityBar.border` - Activity bar border
- `sideBar.border` - Sidebar border
- `panel.border` - Panel border
- `editorGroup.border` - Editor group border
- `tab.activeBorderTop` - Active tab top border
- `tab.hoverBackground` - Tab hover background (with transparency)
- `tab.hoverBorder` - Tab hover border

## Thick Border Mode

For a more prominent border, enable thick border mode:

1. Install the [Custom CSS and JS Loader](https://marketplace.visualstudio.com/items?itemName=be5invis.vscode-custom-css) extension
2. Run `VS Code Border: Enable Thick Border (Custom CSS)` from the Command Palette
3. Run `Reload Custom CSS and JS` from the Command Palette
4. Restart VS Code when prompted

This adds a 4px inset box-shadow border around the entire workbench.

## How It Works

1. **Activation** - Extension activates when VS Code starts
2. **Branch Detection** - Reads current git branch via `git branch --show-current`
3. **Color Assignment** - Assigns a random color from your palette (or retrieves saved color)
4. **Color Application** - Writes to `workbench.colorCustomizations` in workspace settings
5. **Polling** - Checks for branch changes every 5 seconds
6. **Gitignore Management** - Automatically adds `.vscode/settings.json` to `.gitignore` to prevent workspace settings from being committed

## License

MIT

## Repository

[github.com/xxgvqxx/vscode-window-identifier](https://github.com/xxgvqxx/vscode-window-identifier)
