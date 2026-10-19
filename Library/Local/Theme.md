---
tags: meta
---

Modern Obsidian-inspired theme. Light and dark. Original values, written from scratch.
Inspired by the community theme in gorootde/silverbullet-collection (no code reused).

Design rules:
- Performance: CSS variables only. No webfonts, no `@import`, no blur, no filters, no
  animation except short color transitions. System font stacks. Zero JavaScript.
- Accessibility: text pairs meet WCAG AA (4.5:1). Checked for the main text, link, accent,
  and code colors. Keyboard focus ring. `prefers-reduced-motion` respected.
- Readability: 16px text, 1.65 line height, 860px column (about 75 characters).
- Depth by surface lightness, not shadows.
- Developer use: monospace stack with tabular numbers, 2-space tabs, distinct code blocks.

Fonts: "Inter" and "JetBrains Mono" are used only if installed. Otherwise the system fonts apply.
Private tag colors go in the space, not here.

```space-style
/* ---------- Tokens: light ---------- */
html {
  --ui-font: system-ui, -apple-system, "Segoe UI", Roboto, sans-serif;
  --editor-font: "Inter", system-ui, -apple-system, "Segoe UI", Roboto, sans-serif;
  --editor-width: 860px;
  --mono-font: "JetBrains Mono", ui-monospace, "SF Mono", Menlo, Consolas, monospace;
  --radius: 8px;

  --ui-accent-color: #5b3fd9;
  --ui-accent-contrast-color: #fff;
  --root-background-color: #fff;
  --root-color: #1f2328;
  --subtle-color: #5b6370;
  --meta-subtle-color: #5f6673;
  --meta-color: #5f6673;
  --link-color: #4a3fd0;
  --link-missing-color: #9a4d00;
  --subtle-background-color: rgba(31, 35, 40, 0.05);
  --highlight-color: rgba(255, 213, 0, 0.35);

  --ui-surface-border-color: #dedee4;
  --panel-background-color: #f6f6f8;
  --panel-border-color: #dedee4;
  --modal-background-color: #fff;
  --modal-border-color: #dedee4;

  --top-background-color: var(--root-background-color);
  --top-border-color: transparent;
  --top-saved-color: var(--subtle-color);

  --editor-heading-color: var(--root-color);
  --editor-selection-background-color: rgba(91, 63, 217, 0.18);
  --editor-caret-color: var(--ui-accent-color);
  --editor-list-bullet-color: var(--subtle-color);
  --editor-hashtag-background-color: rgba(91, 63, 217, 0.12);
  --editor-hashtag-color: #4a2fc0;
  --editor-hashtag-border-color: transparent;
  --editor-wiki-link-page-background-color: transparent;
  --editor-code-background-color: rgba(31, 35, 40, 0.05);
  --editor-blockquote-border-color: #c9c9d2;
  --editor-table-head-background-color: #f0f0f4;
  --editor-table-head-color: var(--root-color);
  --editor-table-even-background-color: #f8f8fa;
  --editor-frontmatter-background-color: rgba(31, 35, 40, 0.04);

  --editor-code-variable-color: #0b5fa5;
  --editor-code-typename-color: #0f7b57;
  --editor-code-string-color: #9a4d00;
  --editor-code-number-color: #6d35c9;
  --editor-code-atom-color: #b4236e;
  --editor-code-comment-color: #5f6673;

  color-scheme: light;
}

/* ---------- Tokens: dark ---------- */
html[data-theme="dark"] {
  --ui-accent-color: #a78bfa;
  --ui-accent-contrast-color: #1a1033;
  --root-background-color: #131316;
  --root-color: #e6e6ea;
  --subtle-color: #9a9aa6;
  --meta-subtle-color: #8b8b98;
  --meta-color: #8b8b98;
  --link-color: #8ab4ff;
  --link-missing-color: #e0a15a;
  --subtle-background-color: rgba(255, 255, 255, 0.05);
  --highlight-color: rgba(255, 213, 0, 0.28);

  --ui-surface-border-color: #2e2e36;
  --panel-background-color: #1b1b20;
  --panel-border-color: #2e2e36;
  --modal-background-color: #1b1b20;
  --modal-border-color: #2e2e36;

  --top-color: var(--root-color);
  --editor-selection-background-color: rgba(167, 139, 250, 0.28);
  --editor-hashtag-background-color: rgba(167, 139, 250, 0.16);
  --editor-hashtag-color: #cdbdff;
  --editor-code-background-color: rgba(255, 255, 255, 0.06);
  --editor-blockquote-border-color: #3a3a44;
  --editor-table-head-background-color: #23232a;
  --editor-table-head-color: var(--root-color);
  --editor-table-even-background-color: #18181c;
  --editor-frontmatter-background-color: rgba(255, 255, 255, 0.04);

  --editor-code-variable-color: #9ccfff;
  --editor-code-typename-color: #6ee7b7;
  --editor-code-string-color: #f5b97a;
  --editor-code-number-color: #c4a7ff;
  --editor-code-atom-color: #ff9ac1;
  --editor-code-comment-color: #8b8b98;

  color-scheme: dark;
}

/* ---------- Typography ---------- */
#sb-main .cm-editor {
  font-size: 16px;
}

#sb-main .cm-editor .cm-content {
  line-height: 1.65;
}

#sb-main .cm-editor .sb-line-h1 { font-size: 1.75em; font-weight: 700; }
#sb-main .cm-editor .sb-line-h2 { font-size: 1.4em; font-weight: 650; }
#sb-main .cm-editor .sb-line-h3 { font-size: 1.2em; font-weight: 600; }

/* ---------- Developer experience ---------- */
.sb-line-fenced-code,
.sb-line-code,
.sb-code {
  font-family: var(--mono-font);
  font-variant-ligatures: none;
  font-variant-numeric: tabular-nums;
  tab-size: 2;
}

.sb-line-fenced-code {
  background-color: var(--editor-code-background-color);
}

.sb-code {
  border-radius: 4px;
}

/* ---------- Details ---------- */
.sb-hashtag {
  border-radius: 999px;
  padding: 1px 8px;
}

.sb-wiki-link {
  transition: color 0.12s ease;
}

button,
.sb-actions a {
  border-radius: var(--radius);
}

:focus-visible {
  outline: 2px solid var(--ui-accent-color);
  outline-offset: 2px;
}

html {
  scrollbar-width: thin;
  scrollbar-color: var(--ui-surface-border-color) transparent;
}

@media (prefers-reduced-motion: reduce) {
  * {
    transition: none !important;
    animation: none !important;
  }
}
```
