# Obsidian UI Library
**Documentation:** https://docs.mspaint.cc/obsidian

**Source code to documentation site:** https://github.com/mspaint-cc/docs.mspaint.cc/tree/main/content/obsidian


## UserPanelBox

This fork adds a tab-level `UserPanelBox` for showing a Roblox profile headshot, greeting, username, and an arbitrary number of information rows.

The raw library source is:

```text
https://raw.githubusercontent.com/IsnowDev7/Obsidian/main/Library.lua
```

Load it from a LocalScript with:

```lua
local repo = "https://raw.githubusercontent.com/IsnowDev7/Obsidian/main/"
local Library = loadstring(game:HttpGet(repo .. "Library.lua"))()

local Window = Library:CreateWindow({
    Title = "Example Window",
    Footer = "UserPanelBox example",
    Icon = "user",
    NotifySide = "Right",
    ShowCustomCursor = true,
})

local Tabs = {
    Main = Window:AddTab("Main", "user"),
}

local InfoTab = Tabs.Main

InfoTab:UserPanelBox({
    Title = "Good Afternoon",
    UserIcon = true,
    Username = true,
    Information = {
        "Executor: Delta",
        { Label = "Map", Value = "Prison Life" },
        { Label = "Players", Value = "12 / 24" },
        { Label = "Ping", Value = "48 ms" },
        { Label = "Status", Value = "Loaded" },
    },
})

-- Replace the information rows later without rebuilding the panel.
InfoTab:UpdateUserPanelBox({
    Information = {
        { Label = "Map", Value = "Jailbreak" },
        { Label = "Cash", Value = "$42,000" },
        { Label = "Server", Value = game.JobId },
    },
})

-- Hide or show the panel when needed.
-- InfoTab:HideUserPanelBox()
-- InfoTab:UserPanelBox({ Visible = true })
```

`UserIcon` accepts `true` for the local player, a `Player` instance, a numeric user ID, or an image/asset string. `Username` accepts `true` for the local username, a `Player` instance, or a custom string. `Information` accepts strings, `{ Label = "...", Value = "..." }` rows, or keyed data tables. The panel keeps the existing warning-box sizing and theme registry behavior for compatibility with the library’s tab layout.
