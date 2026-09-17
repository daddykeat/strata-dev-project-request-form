# Test Record

**Test environment:** Google Chrome, September 16, 2026

Results use three consistent values: **Pass**, **Fail**, and **Known limitation**.

---

## Fictional Test Data

The following fictional values were used during form testing. They are test data only and do not represent a real client.

| Field | Fictional test value |
| --- | --- |
| Name | Jordan Doe |
| Email | jordan@example.com |
| Preferred contact method | Email |
| Phone number | 444-555-9999 |
| Project type | Website redesign |
| Project description | Redesign a fictional small-business website with an updated layout, clearer navigation, and responsive pages. |
| Budget range | $1,000–$2,499 |
| Target timeline / launch date | September 25, 2026 |
| Consent to be contacted | Yes |

Additional deliberately invalid values were used where necessary to test validation and recovery states, including a one-character name, an incorrectly formatted email address, a blank phone number with Phone/Text selected, and a past target date.

---

## Test 1 — Conditional phone number requirement

**What I tested:**  
Selected **Phone** or **Text** as the preferred contact method, left the Phone number field blank, and submitted the form.

**What happened:**  
The form submitted successfully even though no phone number was entered. The query string included `phone=` with an empty value.

**Result:** Known limitation

**Reasoning:**  
The Phone number field is optional in the current HTML because it is only needed when Phone or Text is selected as the preferred contact method. Native HTML and CSS cannot make one field conditionally required based on the value selected in another field. Implementing that behavior would require JavaScript, such as an `addEventListener` that dynamically adds or removes the `required` attribute, or server-side validation. Both are outside the constraints of this assignment.

---

## Test 2 — Required preferred contact method

**What I tested:**  
Completed the other required fields but left all three Preferred contact method radio buttons unselected, then attempted to submit the form.

**What happened:**  
Chrome blocked submission and identified the Preferred contact method radio group as required. Selecting Email, Phone, or Text allowed the requirement to be satisfied.

**Result:** Pass

**Reasoning:**  
The three radio buttons share the same `name="contact_method"`, and the group uses the native `required` attribute. This allows the browser to enforce that one option must be selected before the form can be submitted.

---

## Test 3 — Eyebrow text contrast

**What I tested:**  
Checked the contrast between the header eyebrow text (`#A9C6DD`) and its dark blue background (`#274A63`) using a contrast checker.

**What happened:**  
The measured contrast ratio was **5.25:1**. This passes the WCAG AA minimum contrast requirement of 4.5:1 for normal-sized text.

**Result:** Pass

**Reasoning:**  
The eyebrow is normal-sized text, so it needs a contrast ratio of at least 4.5:1. The verified 5.25:1 ratio exceeds that requirement.

---

## Test 4 — Help text contrast

**What I tested:**  
Checked the contrast between the muted/help text and the page surface (`#F4F6F8`) using a contrast checker.

**What happened:**  
An earlier candidate value (`#7C8894`) measured **3.33:1** and failed WCAG AA for normal text. I replaced it with `#66727E`, which measured **4.53:1** against `#F4F6F8` and passed.

**Result:** Pass

**Reasoning:**  
Help text is displayed at a normal text size, so it must meet the WCAG AA minimum contrast ratio of 4.5:1. The final `#66727E` value passes at 4.53:1 while still remaining visually secondary to the regular body text.

---

## Test 5 — Past target date

**What I tested:**  
Entered a past date in the Target timeline / launch date field and submitted the form.

**What happened:**  
The browser accepted the past date because the date input does not have a `min` value.

**Result:** Known limitation

**Reasoning:**  
A past target date is not meaningful for a prospective project request. However, HTML's `min` attribute requires a static date and cannot automatically represent the current date. Hardcoding today's date would become outdated as the form ages. Enforcing a rolling minimum date would require JavaScript to set the minimum date dynamically or server-side validation, both of which are outside this assignment's constraints.

---

## Test 6 — Name minimum length

**What I tested:**  
Entered a single character into the Name field and attempted to submit the form.

**What happened:**  
Chrome blocked submission and displayed: “Please lengthen this text to 2 characters or more (you are currently using 1 character).”

**Result:** Pass

**Reasoning:**  
The `minlength="2"` attribute enforces a two-character minimum natively. Chrome's built-in validation correctly prevented submission and communicated the exact constraint without requiring custom JavaScript.

---

## Test 7 — HTML validation

**What I tested:**  
Ran the complete `index.html` through the W3C Nu Html Checker.

**What happened:**  
The initial validation found one error: `action=""` was invalid because the `action` attribute must have a non-empty value when present. I removed the empty `action` attribute and kept `method="get"`, allowing the form to submit to the current document by default. I then ran the validator again, and it reported **“No errors or warnings to show.”**

**Result:** Pass

**Reasoning:**  
Removing the empty `action` attribute corrected the invalid markup without changing the intended form behavior. The final `index.html` passes validation with no reported HTML errors or warnings.

---

## Test 8 — CSS validation

**What I tested:**  
Ran the complete `styles.css` through the Nu Html Checker using the “check as CSS” option.

**What happened:**  
The validator completed successfully and reported **“No errors or warnings to show.”**

**Result:** Pass

**Reasoning:**  
The final stylesheet contains valid CSS syntax. Its custom properties, selectors, declarations, and values were accepted by the validator without errors or warnings.

---

## Test 9 — Keyboard navigation and operability

**What I tested:**  
Navigated the entire form using only Tab, Shift+Tab, Space, and Enter, without using a mouse. I checked visible focus on every interactive element, logical tab order, and whether the radio buttons and consent checkbox could be operated using only the keyboard.

**What happened:**  
All interactive elements received a visible focus ring and followed a logical top-to-bottom tab order. The radio buttons and consent checkbox could also be selected and changed successfully using the keyboard.

**Result:** Pass

**Reasoning:**  
The `:focus-visible` rule provides a clear visual focus indicator, while the native HTML form controls provide keyboard operability without custom `tabindex` values or JavaScript.

---

## Test 10 — Accessible names and descriptions

**What I tested:**  
Inspected the contact-method radio buttons, consent checkbox, and phone input using Chrome DevTools’ Accessibility pane. I checked that each control’s computed accessible name matched its visible label and that the phone field’s `aria-describedby` help text was exposed as a description rather than becoming part of its accessible name.

**What happened:**  
All computed accessible names matched their visible labels. The phone field’s help text was correctly associated through `aria-describedby` and exposed as its accessible description.

**Result:** Pass

**Reasoning:**  
Proper label associations give each control an accessible name that matches what sighted users see, while `aria-describedby` provides supplementary instructions separately as an accessible description. This preserves the distinction between a control’s identity and its supporting help text.

---

## Test 11 — Responsive viewport behavior

**What I tested:**  
Tested the completed page at 320px, 768px, and 1280px viewport widths. At each width, I checked for horizontal overflow, clipped or overlapping content, readable text reflow, and usable form controls.

**What happened:**  
At all three viewport widths, no horizontal scrollbar appeared. Text reflowed cleanly, form controls remained within the viewport, and no content was cut off or overlapped. The header and fluid typography also scaled appropriately across the tested widths. During testing, I found that the `.paired-fields` responsive rule was unused because no element in the final HTML used that class, so I removed the dead CSS rather than adding an unnecessary two-column layout.

**Result:** Pass

**Reasoning:**  
The final single-column form remains usable and readable across phone, tablet, and desktop widths without requiring a layout breakpoint. Removing the unused `.paired-fields` rule keeps the stylesheet consistent with the actual interface and avoids retaining unnecessary responsive code.

---

## Test 12 — 200% browser zoom

**What I tested:**  
Zoomed the browser to 200% and reviewed the entire page, including the header, F3 form fields, and F5 state specimens. I checked for horizontal overflow, clipped content, and whether focus indicators and error/valid states remained clearly visible.

**What happened:**  
No horizontal scrollbar appeared. All text and form content remained legible and unclipped, and the focus, error, and valid state treatments remained clearly distinguishable at 200% zoom.

**Result:** Pass

**Reasoning:**  
The layout uses flexible widths and `max-width` constraints, while typography and spacing rely primarily on relative and fluid sizing such as `rem` and `clamp()`. This allows the interface to scale predictably with browser zoom without causing content loss or horizontal overflow.

---

## Test 13 — Radio and checkbox tap targets

**What I tested:**  
Measured the effective tap target for the Preferred contact method radio buttons and the Contact consent checkbox. The visual control itself is 20px (`inline-size:1.25rem; block-size:1.25rem`), but each input and its text are wrapped in a shared `<label class="choice">`. I confirmed the effective interactive label area measured at least 44px and tested activation by clicking the label text rather than the small visual control.

**What happened:**  
The effective clickable/tappable area measured at least **44px**, and clicking the label text successfully selected the associated radio button or checkbox.

**Result:** Pass

**Reasoning:**  
Wrapping each input and its text in a shared `<label>` expands the interactive target beyond the 20px visual indicator. The measured effective target is at least 44px, providing an appropriately sized touch target while allowing users to activate the control from either the indicator or its visible label.

---

## Test 14 — Complete form submission and query string

**What I tested:**  
Filled every field with valid fictional data, including the optional Phone number, Budget range, and Target timeline / launch date fields. I selected a preferred contact method, checked the consent checkbox, submitted the form, and inspected the resulting query string.

**What happened:**  
All nine field names appeared exactly once with the expected submitted values:

- `name=Jordan+Doe`
- `email=jordan%40example.com`
- `contact_method=email`
- `phone=444-555-9999`
- `project_type=redesign`
- `project_description=...`
- `budget=1000-2499`
- `target_date=2026-09-25`
- `contact_consent=yes`

No expected field was missing or duplicated.

**Result:** Pass

**Reasoning:**  
The GET submission correctly serialized every named form control into the query string. This confirms that the `name` attributes and submitted values are wired correctly across the complete form.