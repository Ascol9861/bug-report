# Bug Report — AE-001

## Title
User can submit the Contact Us form without selecting a file attachment

## Description
The Contact Us page contains a file upload field labeled "Upload File." However, the form can be submitted successfully even when no file is selected, despite the field implying file upload may be expected or required.

## Severity
**Minor**

> *Justification: The bug does not break core functionality — the form still submits successfully and contact data (name, email, subject, message) is captured correctly. No data loss or system crash occurs.*

## Priority
**Medium**

> *Justification: While not severe, this should be fixed because the presence of an "Upload File" field implies a validation rule exists, but it isn't enforced. This creates inconsistent UX and may indicate a missing requirement check upstream that could affect other optional-vs-required field logic on the same form.*

## Status
New

## Reported By
Ascol Parajuli

## Date Reported
June 29, 2026

## Environment
- **Browser:** Chrome (latest)
- **URL:** https://automationexercise.com/contact_us
- **Site:** AutomationExercise.com (public QA practice site)

## Preconditions
1. User is on the Contact Us page.
2. Website is accessible.

## Steps to Reproduce
1. Navigate to the Contact Us page.
2. Enter a valid Name.
3. Enter a valid Email Address.
4. Enter a Subject.
5. Enter a Message.
6. Leave the Upload File field empty.
7. Click Submit.
8. Accept the confirmation popup.

## Expected Result
The system should display a validation message and prevent submission if file upload is mandatory — OR the field should be clearly marked as optional if it is not required.

## Actual Result
The form is submitted successfully without uploading any file, and the success message is displayed — with no indication of whether the upload field was optional or required.

## Suggested Fix
Either:
- (a) Mark the Upload File field as clearly optional in the UI (e.g., "Upload File (optional)"), or
- (b) Add proper validation requiring a file before allowing submission, if upload is intended to be mandatory.

## Recommended Test Case for Regression
| Test Case | Input | Expected Result |
|---|---|---|
| TC-01 | Submit form with file attached | Form submits successfully |
| TC-02 | Submit form without file attached | Form behavior should match field's intended requirement (optional or required) |
| TC-03 | Attempt to upload unsupported file type | System should reject with appropriate error message |
