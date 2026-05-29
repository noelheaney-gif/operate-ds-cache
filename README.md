# operate-ds-cache

Per-component CSS/HTML cache for the Operate Design System, used by the `operate-prototype-builder` Cowork skill.

## Purpose

This repo breaks the Operate DS into small individual files so the skill can fetch exactly what it needs, reliably, every time — without depending on a large single-page source that truncates on fetch.

## Source of truth

These files are derived **verbatim** from the authoritative DS source: the `index.html` Operate DS builder (the file previously deployed to Netlify). That `index.html` is now the single source of truth. The old `operate-shell-components.netlify.app/llms.txt` reference is retired and should no longer be used.

When the DS changes:
1. Update the authoritative `index.html`.
2. Re-run the extraction against it (see "Regenerating" below).
3. Commit the updated component files here.

## How the skill uses it

The skill fetches each file individually using raw GitHub URLs:

```
https://raw.githubusercontent.com/noelheaney-gif/operate-ds-cache/main/tokens.css
https://raw.githubusercontent.com/noelheaney-gif/operate-ds-cache/main/top-nav.css
... etc
```

## Files

### Foundation
| File | Contents |
| --- | --- |
| `tokens.css` | Full `:root` DS token block (primitives + semantic tokens) |

### Shell
| File | Contents |
| --- | --- |
| `top-nav.css` / `top-nav.html` | Top navigation |
| `sidebar.css` / `sidebar.html` | Side navigation (default variant, Emily Carl persona) |
| `page-header.css` / `page-header.html` | Page header |

### Widgets
| File | Contents |
| --- | --- |
| `widget-shell.css` | Generic widget shell + Radar |
| `list-view.css` / `list-view.html` | List view widget |
| `rollup-card.css` | Roll Up Card widget |
| `empty-state.css` | "Nothing to display" empty state |

### Components
| File | Contents |
| --- | --- |
| `buttons.css` | Buttons (`op-btn`) |
| `badge.css` | Badge (`op-badge`) + top-nav notification badge |
| `avatar.css` | Avatar (`op-avatar`) |
| `icon.css` | Icons (`op-icon`) |
| `input.css` | Inputs (`op-input`) |
| `checkbox.css` | Checkbox (`op-checkbox`) |
| `switch.css` | Switch (`op-switch`) |
| `counter.css` | Counters (`op-counter`) |
| `pill.css` | Pills / chips (`op-pill`) |
| `alert.css` | Alerts (`op-alert`) |
| `card.css` | Cards (`op-card`) |
| `dialog.css` | Dialogs (`op-dialog`) |
| `toast.css` | Toasts (`op-toast`) |
| `tooltip.css` | Tooltip (`op-tooltip`) |
| `menu.css` | Menu (`op-menu`) |

## Notes for prototype use

- **Scoping:** sidebar CSS was scoped to `.story-stage` in the source showcase. That wrapper has been removed here so the styles apply directly in a prototype. Other component CSS was already unscoped.
- **Avatar:** `sidebar.html` references `emily-carl-avatar.jpg` (a relative path from the source). For a self-contained prototype, replace this with a base64 data URI or host the image alongside the prototype.
- **Showcase chrome excluded:** story tags, component-grid cards, copy buttons, the showcase's own routing/sidenav, and the shell diagram are showcase-only and are intentionally NOT in this cache.

## Regenerating

All files are extracted from the authoritative `index.html` by section boundary, dedented from the `<style>`/markup indentation, and stripped of the `.story-stage` showcase wrapper. Re-run the extraction whenever `index.html` changes, then verify brace balance and commit.
