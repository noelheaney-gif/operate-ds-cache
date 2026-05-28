# operate-ds-cache

Cached CSS and HTML snippets for the Operate Design System, used by the `operate-prototype-builder` Cowork skill.

## Purpose

The main DS reference site (`operate-shell-components.netlify.app/llms.txt`) is too large to fetch reliably — the base64 avatar data causes responses to truncate before the CSS blocks are reached. This repo breaks the DS into small individual files so the skill can fetch exactly what it needs, reliably, every time.

## How it works

The skill fetches each file individually using raw GitHub URLs:
```
https://raw.githubusercontent.com/YOUR-ORG/operate-ds-cache/main/tokens.css
https://raw.githubusercontent.com/YOUR-ORG/operate-ds-cache/main/top-nav.css
... etc
```

## Keeping this up to date

When the DS site is updated:
1. Go to `operate-shell-components.netlify.app`
2. Find the updated component section
3. Copy the CSS and HTML snippets verbatim
4. Update the relevant file here and commit

## Files

| File | Contents | Status |
|------|----------|--------|
| `tokens.css` | Full `:root` DS token block | ✅ Verified from llms.txt |
| `top-nav.css` | Top navigation CSS | ⚠️ Needs Chrome verification |
| `top-nav.html` | Top navigation HTML snippet | ✅ Verified from llms.txt |
| `sidebar.css` | Side navigation CSS | ⚠️ Needs Chrome verification |
| `sidebar.html` | Side navigation HTML snippet (Emily Carl persona) | ⚠️ Needs Chrome verification |
| `page-header.css` | Page header CSS | ⚠️ Needs Chrome verification |
| `page-header.html` | Page header HTML snippet | ⚠️ Needs Chrome verification |
| `widget-shell.css` | Widget shell (collapsible container) CSS | ⚠️ Needs Chrome verification |
| `list-view.css` | List view / table CSS | ⚠️ Needs Chrome verification |
| `list-view.html` | List view HTML snippet | ⚠️ Needs Chrome verification |
| `buttons.css` | Button component CSS | ⚠️ Needs Chrome verification |

## Verification status

Files marked ⚠️ were built from DS token knowledge and patterns. They should be verified against the live DS site using Claude in Chrome before being used in customer-facing prototypes.

To verify: open Chrome, connect Claude in Chrome, and ask: "Please fetch the CSS for the [component] from operate-shell-components.netlify.app and compare it against the file at [path]. Update the file if anything differs."
