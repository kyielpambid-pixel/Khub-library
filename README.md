![Khub UI Library Preview](https://github.com/kyielpambid-pixel/Khub-library/raw/main/E10FA7BE-3308-4331-89A5-BA0A8CAFFE67.png)


```markdown
# 🔮 Khub UI Library

**Khub UI Library** — a Roblox Lua UI library built for fast, clean, and modern hub development. Load once, build any script.

Developed by **Kyiel Pambid** · Powered by Khub

---

## ❓ Why use Khub UI Library?

Khub is built for speed and simplicity. No need to design your own GUI — load the library, call the API, and your hub is ready. It ships with:

- Built-in icon dictionary (name-based icons, no `rbxassetid` needed)
- Theme presets
- Floating Khub logo orb with orbit chain animation
- Auto config save/load system
- Key system built in
- Smooth toggle animations
- Violet popup notifications
- Search bar support per tab

---

## ✨ UI Elements

Khub UI Library includes a complete set of UI elements:

- TextButton
- Textbox
- TextLabel
- Slider
- Toggle
- Checkbox
- Dropdown
- Search Bar
- Config Tab (auto save/load)
- Green Info Box (instructions)
- Section divider
- Floating orb toggle

---

## ⚡ Installation

**Load the library:**


 khub library:

```lua
local KHUB = loadstring(game:HttpGet("https://raw.githubusercontent.com/kyielpambid-pixel/Khub-library/refs/heads/main/Khub-library"))()
```

Create a window:

```lua
local Window = KHUB:CreateWindow({
    Title      = "KHUB · Script Hub",
    Subtitle   = "by Kyiel Pambid",
    Logo       = "rbxassetid://127230219966945",
    Background = "rbxassetid://127230219966945",
    Keybind    = Enum.KeyCode.RightShift,
    Folder     = "KHUB_Configs",
    Width      = 560,
    Height     = 380,
})
```

Add a key system (optional):

```lua
Window:CreateKeySystem({
    Title       = "Khub Key System",
    Subtitle    = "Enter your key to continue",
    Placeholder = "Paste your key...",
    Key         = "KHUB-XXXX-XXXX",
    GetLink     = "https://discord.gg/DghhdTkGft",
    OnSuccess   = function()
        -- script that loads after correct key
    end,
})
```

Create a tab:

```lua
local HomeTab = Window:CreateTab({
    Name      = "Home",
    Icon      = "home",
    Order     = 1,
    SearchBar = false,
})
```

Create a section and label:

```lua
HomeTab:Section("Welcome")
HomeTab:Label("Hello, this is Khub UI Library.")
```

Add a button:

```lua
HomeTab:Button({
    Name = "Join Discord",
    Callback = function()
        pcall(function() setclipboard("https://discord.gg/DghhdTkGft") end)
    end,
})
```

Add a toggle:

```lua
HomeTab:Toggle({
    Name = "Auto Aim",
    Flag = "AutoAim",
    Default = false,
    Callback = function(v)
        print("Auto Aim:", v)
    end,
})
```

Add a slider:

```lua
HomeTab:Slider({
    Name    = "Aim FOV",
    Min     = 50,
    Max     = 400,
    Default = 120,
    Flag    = "AimFOV",
    Callback = function(v) end,
})
```

Add a dropdown:

```lua
HomeTab:Dropdown({
    Name    = "Target Mode",
    Options = { "Nearest", "Lowest HP", "Crosshair" },
    Default = "Nearest",
    Flag    = "TargetMode",
    Callback = function(v) end,
})
```

Add a textbox:

```lua
HomeTab:Textbox({
    Name        = "Webhook",
    Placeholder = "Paste webhook URL...",
    Flag        = "Webhook",
    Callback    = function(text, enterPressed) end,
})
```

Add a green instruction box:

```lua
HomeTab:GreenBox("Turn off features before leaving the game.")
```

Create the config tab (auto save/load):

```lua
Window:CreateConfigTab({
    Name  = "Config",
    Icon  = "save",
    Order = 99,
})
```

---

🎭 Built-in Icons

Khub ships with a name-based icon dictionary. Use any of these by name:

```
home   settings   save    user    star    info    search   close
sword  target     shield  bolt    flame   eye     ghost    navigation
box    zap        heart   player  server  config  farm     egg
pet    speed      fly     esp     aimbot  misc    welcome  key
```

Or register your own:

```lua
KHUB:AddIcon("murder", "rbxassetid://6034509993")
KHUB:AddIcon("gun",    "rbxassetid://6034684930")
```

---

🤩 Themes

Khub supports theme presets. Set them in CreateWindow:

```lua
local Window = KHUB:CreateWindow({
    Title = "Khub Hub",
    Theme = "Violet",   -- Default, Violet, Dark, Fire, Ice, Ocean
    ...
})
```

---

🧩 Full API Reference

KHUB:CreateWindow({ ... })

Field Type Description
Title string Window title
Subtitle string Window subtitle
Logo string Logo asset id (shown top-left)
Background string Background image asset id
Keybind Enum.KeyCode Toggle keybind (default: RightShift)
Folder string Config save folder name
Width number Window width (default: 560)
Height number Window height (default: 380)

Window:CreateTab({ ... })

Field Type Description
Name string Tab name
Icon string Icon name or rbxassetid://
Order number Sort order
SearchBar boolean Enable search bar for tab
GreenInfo string Green instruction text
NoGreen boolean Skip green box

Tab Methods

· Tab:Toggle({ Name, Flag, Default, Callback })
· Tab:Button({ Name, Callback })
· Tab:Slider({ Name, Min, Max, Default, Flag, Callback })
· Tab:Dropdown({ Name, Options, Default, Flag, Callback })
· Tab:Textbox({ Name, Placeholder, Default, Flag, Callback })
· Tab:Label("text")
· Tab:Section("title")
· Tab:GreenBox("text")
· Tab:Checkbox({ Name, Flag, Default, Callback })

Window Methods

· Window:CreateConfigTab({ Name, Icon, Order })
· Window:CreateKeySystem({ ... })
· Window:SelectTab(name)
· Window:SetVisible(bool)
· Window:Notify(message, on) — violet popup

Library Methods

· KHUB:AddIcon(name, assetId)
· KHUB:CreateWindow({ ... })

---

🔑 Key System

The Khub key system is built into the library. When enabled, users must enter a valid key before the hub loads.

```lua
Window:CreateKeySystem({
    Title       = "Khub Key System",
    Subtitle    = "Enter your key to continue",
    Placeholder = "Paste your key...",
    Key         = "KHUB-XXXX-XXXX",
    GetLink     = "https://discord.gg/DghhdTkGft",
    OnSuccess   = function()
        loadstring(game:HttpGet("https://your-script-url.lua"))()
    end,
})
```

---

🪐 Floating Orb

When the window is closed, a floating Khub orb appears on screen:

· Khub logo (violet glow pulse animation)
· Orbiting chain dots
· Click to reopen the UI
· Drag to move

Toggle keybind: RightShift (default) · changeable via Keybind in CreateWindow.

---

⚙ Config System

Flags from Toggles, Sliders, Dropdowns, and Textboxes are auto-saved to JSON.

```lua
Window:CreateConfigTab({
    Name = "Config",
    Icon = "save",
    Order = 99,
})
```

Users can:

· Save — save current toggle/slider values
· Load — restore saved config
· Delete — remove saved config
· Refresh — refresh config list

---

🎨 Example

```lua
local KHUB = loadstring(game:HttpGet("https://raw.githubusercontent.com/kyielpambid-pixel/Khub-library/refs/heads/main/Khub-library"))()

local Window = KHUB:CreateWindow({
    Title      = "KHUB · My Script",
    Subtitle   = "by Kyiel Pambid",
    Logo       = "rbxassetid://127230219966945",
    Keybind    = Enum.KeyCode.RightShift,
    Folder     = "KHUB_MyScript",
})

local Home = Window:CreateTab({ Name = "Home", Icon = "home", Order = 1 })
Home:Label("Welcome to my script!")
Home:Button({ Name = "Join Discord", Callback = function() setclipboard("https://discord.gg/DghhdTkGft") end })

local Combat = Window:CreateTab({ Name = "Combat", Icon = "sword", Order = 2 })
Combat:Toggle({ Name = "Auto Aim", Flag = "AutoAim", Callback = function(v) end })
Combat:Slider({ Name = "FOV", Min = 50, Max = 400, Default = 120, Flag = "FOV", Callback = function(v) end })

Window:CreateConfigTab({ Name = "Config", Icon = "save", Order = 99 })
```

---

📜 License

MIT — free to use, modify, and distribute. Credit to Kyiel Pambid appreciated.

💬 Support

· Discord: discord.gg/DghhdTkGft
· GitHub: github.com/kyielpambid-pixel/Khub-library

---

Khub UI Library — built with depth, shipped clean. 🔮

```

---

**Paano gamitin:**

1. Puntahan mo yung GitHub repo mo: [github.com/kyielpambid-pixel/Khub-library](https://github.com/kyielpambid-pixel/Khub-library)
2. Click **README.md** → **pencil icon** (edit)
3. Delete lahat ng laman
4. **I-paste yung buong code sa itaas**
5. Click **Commit changes**

Tapos na. Yung README mo ay parang Lua Land na — polished, complete, may API docs, examples, at support links.

Kung gusto mo ng screenshot sa taas ng README:

```markdown
![Khub UI Screenshot](https://github.com/kyielpambid-pixel/Khub-library/raw/main/screenshot.png)
```
