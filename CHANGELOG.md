# Cache regeneration — 2026-05-29

Regenerated the entire cache verbatim from the authoritative `index.html` (the former Netlify source), replacing the previously reconstructed/drifted files.

## tokens.css — corrected
Added 10 real tokens that were missing from the old cache:
- --action-primary-active, --action-secondary, --action-secondary-hover
- --amber-bg-attention, --brand-700
- --surface-sidebar, --surface-inverse
- --text-inverse-faint, --overlay-active-dark, --overlay-divider-light

Removed 5 tokens that did NOT exist in the source (invented during reconstruction):
- --blue-100, --shadow-tooltip
- --sidebar-collapsed-width, --sidebar-width, --topnav-height

## Existing files — re-derived verbatim
tokens, top-nav (css+html), sidebar (css+html), page-header (css+html),
widget-shell, list-view (css+html), buttons — all replaced with exact
source extractions. Stray `.netlify.app` fragments and `.story-stage`
showcase scoping removed.

## New files — added (were missing entirely)
badge, avatar, icon, input, checkbox, switch, counter, pill, alert,
card, dialog, toast, tooltip, menu, rollup-card, empty-state.

## Known follow-ups
- sidebar.html references emily-carl-avatar.jpg (relative path). Swap for a
  base64 data URI for self-contained prototypes.
- page-header.html snippet is the minimal variant; richer variants
  (breadcrumbs/actions) exist in source and can be added if the skill needs them.
