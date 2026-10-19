---
tags: meta
---

Persistent file tree in the left sidebar. Uses the built-in `Navigate: Tree` view
(`std.spaceTree`), so no plug is needed.

Obsidian-style look, left sidebar only (page picker and other docks keep the default look):
compact 26px rows, 13px text, no page icons, thin chevrons, indent guide lines,
rounded hover and current-page highlight, sidebar on the panel surface.

A top bar button toggles it. Keyboard: `Cmd-o` / `Ctrl-o` runs `Navigate: Tree` too.

```space-lua
config.set("view.defaults", {
  ["std.spaceTree"] = { dock = "lhs", open = true, width = 280 },
})

actionButton.define {
  icon = "sidebar",
  description = "Toggle file tree",
  run = function()
    editor.invokeCommand("Navigate: Tree")
  end
}
```

```space-style
/* Scope: the tree when docked in the left sidebar. */
.sb-nav-root-lhs {
  --sb-nav-row-height: 26px;
  --tree-step: 16px;
  --tree-guide: var(--ui-surface-border-color);
  --tree-text: color-mix(in srgb, var(--root-color) 82%, var(--panel-background-color));
  --tree-active-bg: color-mix(in srgb, var(--root-color) 9%, transparent);
  /* Row action overlay fades into this color, so match the sidebar. */
  --modal-background-color: var(--panel-background-color);
  background: var(--panel-background-color);
  font-size: 13px;
}

/* Rows */
.sb-nav-root-lhs .sb-tree .sb-nav-row {
  /* Indent comes from nested groups below, not from per-row padding. */
  padding: 3px 6px !important;
  margin: 0 4px;
  gap: 4px;
  border-radius: 4px;
  line-height: 20px;
  color: var(--tree-text);
  contain-intrinsic-size: auto 26px;
}

.sb-nav-root-lhs .sb-tree .sb-nav-row.sb-nav-folder {
  font-weight: 400;
  --sb-nav-band: transparent;
}

.sb-nav-root-lhs .sb-tree .sb-nav-row:hover:not(.sb-nav-selected) {
  background-color: var(--subtle-background-color);
  color: var(--root-color);
}

.sb-nav-root-lhs .sb-tree .sb-nav-row[aria-current="page"] {
  border-radius: 4px;
  background-color: var(--tree-active-bg);
  color: var(--root-color);
  font-weight: 500;
}

.sb-nav-root-lhs .sb-tree .sb-nav-row[aria-current="page"]::before {
  display: none;
}

/* No page icons, like Obsidian. */
.sb-nav-root-lhs .sb-tree .sb-nav-icon {
  display: none;
}

/* Indent guides: each nested group steps right and draws one line. */
.sb-nav-root-lhs .sb-tree ul[role="group"] {
  margin-left: var(--tree-step);
  border-left: 1px solid var(--tree-guide);
}

/* Thin CSS chevron instead of the text triangle. */
.sb-nav-root-lhs .sb-nav-chevron,
.sb-nav-root-lhs .sb-nav-chevron-spacer {
  width: 12px;
  align-self: center;
}

.sb-nav-root-lhs .sb-nav-chevron {
  font-size: 0;
  display: inline-flex;
  align-items: center;
  justify-content: center;
  height: 12px;
  color: var(--subtle-color);
}

.sb-nav-root-lhs .sb-nav-chevron::before {
  content: "";
  width: 5px;
  height: 5px;
  border-right: 1.5px solid currentColor;
  border-bottom: 1.5px solid currentColor;
  transform: rotate(-45deg);
  transition: transform 0.1s ease;
}

.sb-nav-root-lhs [aria-expanded="true"] > .sb-nav-row .sb-nav-chevron::before {
  transform: rotate(45deg);
}
```
