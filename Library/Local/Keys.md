---
tags: meta
---

Obsidian-style shortcuts. Generic only.

```space-lua
command.define {
  name = "Local: Open Dashboard",
  key = "Ctrl-Shift-h",
  run = function()
    editor.navigate("Dashboard")
  end
}
```
