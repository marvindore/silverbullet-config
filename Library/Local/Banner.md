---
tags: meta
---

Banner image at the top of a page. Add `banner: <image url>` to the page frontmatter.
Pages without `banner` show nothing.

```space-lua
view.define {
  name = "local.banner",
  dock = "page-top",
  frame = "minimal",
  content = function()
    local meta = editor.getCurrentPageMeta()
    if not meta or not meta.banner then
      return nil
    end
    return widget.new {
      markdown = "![banner](" .. meta.banner .. ")",
      cssClasses = { "sb-banner" },
    }
  end,
}
```

```space-style
.sb-banner img {
  width: 100%;
  max-height: 220px;
  object-fit: cover;
  border-radius: 8px;
}
```
