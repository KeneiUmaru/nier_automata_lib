# NieR: Automata UI Library

A sleek, NieR: Automata-inspired UI library for Roblox. Features smooth animations, text scramble effects, and a clean beige/dark aesthetic.

![Version](https://img.shields.io/badge/version-1.0.0-blue)
![Platform](https://img.shields.io/badge/platform-Roblox-red)

## Features

- 🎮 **NieR: Automata aesthetic** - Authentic beige/brown color scheme
- ✨ **Smooth animations** - Tween-based transitions and hover effects
- 📝 **Text scramble effect** - Glitchy text animations on tab switches
- 🔧 **8 UI elements** - Button, Toggle, Slider, Options, Input, Keybind, Header, Paragraph
- 📐 **Resizable & Draggable** - Full window management
- 🎯 **Programmatic control** - Methods for all elements

## Installation

```lua
local Library = loadstring(game:HttpGet("YOUR_RAW_URL_HERE"))()
```

## Quick Start

```lua
local Library = loadstring(game:HttpGet("URL"))()

-- Create window
local Window = Library.Window.new({
    Title = "My Script"
})

-- Create tab
local Main = Window:CreateTab("Main")

-- Add elements
Main:AddButton({
    Text = "Click Me",
    Callback = function()
        print("Button clicked!")
    end
})

Main:AddToggle({
    Text = "Auto Farm",
    Callback = function(state)
        print("Toggled:", state)
    end
})
```

## Elements

### Button
```lua
local button = Tab:AddButton({
    Text = "Button Name",
    Callback = function()
        print("Clicked!")
    end
})

-- Methods
button:SetText("New Text")
button:SetCallback(newFunction)
button:SetVisible(false)
button:Destroy()
```

### Toggle
```lua
local toggle = Tab:AddToggle({
    Text = "Toggle Name",
    Callback = function(state)
        print("State:", state)
    end
})

-- Methods
toggle:SetText("New Text")
toggle:SetState(true, true)  -- (state, fireCallback)
toggle:GetState()            -- returns boolean
toggle:SetCallback(newFunction)
toggle:SetVisible(false)
toggle:Destroy()
```

### Slider
```lua
local slider = Tab:AddSlider({
    Text = "Slider Name",
    Min = 0,
    Max = 100,
    Default = 50,
    Rounding = 1,        -- Decimal precision
    Suffix = "%",        -- Optional suffix
    Callback = function(value)
        print("Value:", value)
    end
})

-- Methods
slider:SetText("New Text")
slider:SetValue(75, true)    -- (value, fireCallback)
slider:GetValue()            -- returns number
slider:SetCallback(newFunction)
slider:SetVisible(false)
slider:Destroy()
```

### Options (Dropdown)
```lua
-- Single select
local options = Tab:AddOptions({
    Text = "Select Mode",
    Values = {"Easy", "Normal", "Hard"},
    Default = "Normal",
    Callback = function(value)
        print("Selected:", value)
    end
})

-- Multi select
local multiOptions = Tab:AddOptions({
    Text = "Features",
    Values = {"ESP", "Aimbot", "Speed"},
    Default = {"ESP"},
    Multi = true,
    AllowNull = false,       -- Can't deselect all
    Callback = function(values)
        print("Selected:", values)
    end
})

-- Methods
options:SetText("New Text")
options:SetValue("Hard", true)       -- (value, fireCallback)
options:SetValue({"ESP", "Aimbot"})  -- For multi-select
options:GetValue()                   -- returns table
options:SetCallback(newFunction)
options:SetVisible(false)
options:Destroy()
```

### Input
```lua
local input = Tab:AddInput({
    Text = "Player Name",
    Default = "Guest",
    PlaceHolder = "Enter name...",
    Numeric = false,         -- Numbers only
    Censor = false,          -- Hide text (password)
    Callback = function(value)
        print("Typing:", value)
    end,
    Finished = function(value, enterPressed)
        print("Final:", value)
    end
})

-- Methods
input:SetText("New Text")
input:SetValue("NewValue")
input:GetValue()             -- returns string
input:SetCallback(newFunction)
input:SetFinished(newFunction)
input:SetVisible(false)
input:Destroy()
```

### Keybind
```lua
local keybind = Tab:AddKeybind({
    Text = "Toggle Fly",
    Default = "F",
    Mode = "Toggle",         -- "Always", "Toggle", "Hold"
    Callback = function(state)
        print("Active:", state)
    end
})

-- Methods
keybind:SetText("New Text")
keybind:SetKey("G")
keybind:GetKey()             -- returns string
keybind:SetMode("Hold")
keybind:SetCallback(newFunction)
keybind:SetVisible(false)
keybind:Destroy()
```

### Header
```lua
local header = Tab:AddHeader({
    Text = "Section Title"
})

-- Methods
header:SetText("New Title")
header:SetVisible(false)
header:Destroy()
```

### Paragraph
```lua
local paragraph = Tab:AddParagraph({
    Text = "Title",
    Description = "Long description with <b>rich text</b> support."
})

-- Methods
paragraph:SetText("New Title")
paragraph:SetDescription("New description")
paragraph:SetVisible(false)
paragraph:Destroy()
```

## Window Features

### Dragging
Click and drag the title bar to move the window.

### Resizing
Drag the bottom-right corner to resize. Minimum size: 400x300.

### Double-Click to Maximize
Double-click the title bar to maximize/restore the window.

### Close Button
Click the X button to destroy the window.

## Keybind Modes

| Mode | Behavior |
|------|----------|
| `Always` | Fires callback every key press |
| `Toggle` | Toggles state on/off with each press |
| `Hold` | Active while key is held, inactive on release |

## Customization

The library uses these primary colors:
- **Background**: `rgb(181, 174, 154)` - Beige
- **Accent**: `rgb(84, 84, 76)` - Dark brown
- **Text**: `rgb(216, 210, 186)` - Light beige
- **Highlight**: `rgb(78, 75, 66)` - Deep brown

## Requirements

- Sound files (optional):
  - `hover.ogg` - Hover sound effect
  - `clicked.ogg` - Click sound effect

## License

MIT License - Feel free to use and modify.

## Credits

Inspired by the UI design of NieR: Automata by Square Enix & PlatinumGames.
