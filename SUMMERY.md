# Tailwind Migration Summary

## Changes files

- `contacts_index.jinja` → main template migrated to Tailwind
- `contact.html` → static HTML used for visual comparison and regression check
- `tailwind.config.js` → Tailwind v3 configuration
- `app_ltr.css` → not modified, beacuse is a compiled, and shared across the entire app.

---

## What was done

Most of the UI styling was migrated from custom CSS to Tailwind while preserving the existing visual design.

- Header layout converted to Flexbox
- Help box restyled using Tailwind utilities
- Action bar updated from float-based layout to Flexbox
- Dropdown menus restyled (spacing, hover states)
- Contacts table styling migrated to Tailwind
- Empty state redesigned using Tailwind utilities

---

## Legacy CSS compatibility

The project uses a shared `app_ltr.css` file with some high-specificity and `!important` rules.

To ensure Tailwind works correctly, `important: true` was enabled.  
In some edge cases, legacy styles may still override Tailwind utilities, but the final UI remains visually consistent.

Some legacy class names (e.g. `help-box`, `popup`) could not be removed because JavaScript depends on them as selectors. Tailwind classes were added alongside them to handle styling, even where the legacy CSS partially wins due to specificity.

---

## Classes preserved

Some classes were intentionally kept because they are required for JavaScript interactions (e.g. jQuery selectors).

Examples of preserved class names (used as JS/CSS selectors):

popup,
popup-menu-parent,
index-top,
index-menu,
index-table,
contacts-table,
index-message,
help-box,
close,
checkbox,
hoverable,
cell,
submit,
submit-build-url,
delete,
contacts-index-delete,
company-url,
contact-name,
contact-phone,
header,
action-bar,
dropdown,
dropdown-menu,
table-row,
table-cell,
empty-state,
btn,
btn-primary,
btn-secondary

---

## Notes / trade-offs

- `important: true` used for compatibility with legacy CSS
- `preflight: false` used to avoid resetting global styles
- Dropdown visibility still handled by existing JS/CSS logic
- Icon system remains unchanged (font-based icons + pseudo-elements)
