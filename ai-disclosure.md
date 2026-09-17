AI Disclosure

AI permission level: AI-Assisted with Disclosure

Tool

Claude (Anthropic), used in a review/coaching conversation after the form, styles, field inventory, and test record were already written and tested.

Purpose

Claude was used for review and feedback only — never to implement, test, or generate submitted content. Specifically, Claude:

Suggested edge cases to test against the form's constraints (a one-character name, a malformed email address, a blank phone number with Phone/Text selected, a past target date).
Suggested fictional test data to use during testing (e.g. Jordan Doe, jordan@example.com).
Asked clarifying questions about task flow and cross-checked finished files against each other for internal consistency (e.g. that the field inventory's stated constraints such as minlength="2" and required fields matched what was actually implemented in index.html, and that the fictional test data table matched the query-string evidence recorded in Test 14).
Adopted / rejected suggestions

All of Claude's suggestions were adopted: the four invalid-value edge cases and the fictional test data set above were used as suggested, and no correction from the cross-check step required disagreement or rejection. No suggestion was rejected during this process.

Verification

Every suggested edge case and test value was verified by actually running it through the form myself before it was recorded as a result — the pass/fail outcomes in test-record.md reflect my own testing, not Claude's claims. No personal or confidential information was shared with Claude at any point; all test data used is fictional.

What I did myself

I decided what data was necessary to collect and documented the sensitivity/minimization reasoning for each field in the field inventory. I implemented the form markup, styles, and design tokens, and merged in my Module 1 design-system decisions. I ran every test recorded in test-record.md myself — including HTML/CSS validation, contrast measurements, keyboard navigation, and viewport/zoom checks. I wrote and explain every submitted choice reflected in the field inventory and test record.