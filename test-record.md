# Test Record

**Test environment:** Google Chrome, September 16, 2026

Results use three consistent values: **Pass**, **Fail**, and **Known limitation**.

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