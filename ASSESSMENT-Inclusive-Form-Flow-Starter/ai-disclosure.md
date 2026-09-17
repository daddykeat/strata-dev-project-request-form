AI Disclosure

AI permission level: AI-Assisted with Disclosure

Scope of AI use

AI (Claude) was used for review and feedback only, after the form, styles, field inventory, and test record were already written and tested. Specifically, Claude:

Suggested edge cases to test against the form's constraints (a one-character name, a malformed email address, a blank phone number with Phone/Text selected, a past target date).
Suggested the fictional test data used during testing (e.g. Jordan Doe, jordan@example.com).
Asked clarifying questions about task flow, including cross-checking that the field inventory's stated constraints (minlength="2", required fields, etc.) matched what was actually implemented in index.html, and that the fictional test data table matched the query-string evidence recorded in Test 14.

Claude did not write or generate any of the HTML, CSS, field-inventory content, or test narrative. No personal or confidential information was shared with the AI at any point; all test data is fictional.

What I did myself

I decided what data was necessary to collect and documented the sensitivity/minimization reasoning for each field in the field inventory. I implemented the form markup, styles, and design tokens. I ran every test recorded in test-record.md myself, including the HTML/CSS validation, contrast measurements, keyboard navigation, and viewport checks, and verified any AI-suggested edge case or test value before using it. I wrote and explain every submitted choice reflected in the field inventory and test record.