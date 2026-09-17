Inclusive Form Flow — Strata Dev Project Request Form

A responsive, accessible front-end prototype of a project-request form for Strata Dev, a freelance web development brand. Built as a native HTML/CSS-only form (no JavaScript, no live data collection) covering purpose and expectations, task/data planning, semantic markup, validation, and documented interaction states.

Live demo

[Add the published GitHub Pages URL here]

Repository contents
File	Purpose
index.html	The form itself: purpose/expectations section (F1), the semantic form with contact, project-detail, and consent fieldsets (F3), the state and recovery specimen (F5), and links to the supporting documentation (F6).
styles.css	Design tokens (color, spacing, type, radius) and component styles — reset, layout, form controls, focus/error/valid/disabled states — extended from the Module 1 design system.
field-inventory-template.html	The task and data plan (F2): one row per form field justifying why it's collected, whether it's required, its control type, submitted name/value, autocomplete purpose, constraint, and sensitivity/minimization decision.
test-record.md	The fictional test data used during testing, plus 14 documented tests covering HTML/CSS validation, keyboard navigation, accessible names, responsive viewports, 200% zoom, tap targets, and full form submission.
ai-disclosure.md	Disclosure of AI (Claude) involvement: tool, purpose, adopted/rejected suggestions, and how each suggestion was verified.
Scope and constraints

This is a nonfunctional prototype built for a course assessment. Native HTML and CSS only — no JavaScript, no server, no real data collection. All test data used is fictional and does not represent a real client. method="get" is used only to allow query-string inspection during testing, per the assignment's temporary-method allowance.

Design system

Colors, spacing, type scale, and radius tokens are extended from the Module 1 design-system specimen, using a two-tier primitive-to-semantic token pattern so form-specific roles (error, success, focus) map onto the same underlying primitives as the rest of the system.