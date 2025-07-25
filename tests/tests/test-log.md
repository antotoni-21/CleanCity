# 🧪 Test Execution Log – CleanCity: Waste Pickup Scheduler

This document logs all manually and automatically executed test cases, their outcomes, environments used, and observations made during the QA process.

---

## 📅 Execution Period
**Start Date**: July 3, 2025  
**End Date**: July 23, 2025  

---

## 👥 Testers
- Anthony Kiptoo Kipkogei
- Elisha Abayi Kigalave
- Rachel Yetunde Nkatha

---

## 🖥️ Test Environment

| Component     | Details                |
|---------------|------------------------|
| Browser       | Chrome 125.0, Firefox 118.0 |
| OS            | Windows 10, Ubuntu 22.04     |
| Tools         | DevTools, Jest, Lighthouse, Screen Readers |
| Display       | Desktop & Mobile (Responsive Mode) |
| Storage       | localStorage (manual data injection) |

---

## 📋 Manual Test Log

| Test ID | Date       | Tester         | Description                            | Result     | Comments/Observations                        |
|---------|------------|----------------|----------------------------------------|------------|-----------------------------------------------|
| TC01    | 2025-07-08 | Anthony Kiptoo | Valid login credentials                | ✅ Pass     | Redirected to dashboard correctly             |
| TC02    | 2025-07-08 | Rachel Nkatha  | Invalid login credentials              | ✅ Pass     | Error message shown as expected               |
| TC03    | 2025-07-08 | Elisha Abayi   | Empty login fields                     | ✅ Pass     | HTML5 validation prevented submission         |
| TC04    | 2025-07-09 | Anthony Kiptoo | Submit pickup request with valid data  | ✅ Pass     | Success message shown                         |
| TC05    | 2025-07-09 | Elisha Abayi   | Submit pickup request with empty date  | ✅ Pass     | Bug: Still submitted, no validation error     |
| TC06    | 2025-07-09 | Rachel Nkatha  | Name field with <2 characters          | ✅ Pass     | Form blocked with validation error            |
| TC08    | 2025-07-10 | Anthony Kiptoo | Filter dashboard by "Eldoret"          | ❌ Fail     | BUG D01: Nairobi results shown instead        |
| TC09    | 2025-07-10 | Elisha Abayi   | Admin Panel: update status             | ⚠️ Partial  | Status updated but UI did not refresh         |
| TC10    | 2025-07-11 | Rachel Nkatha  | Feedback form: Invalid request ID      | ✅ Pass     | Error displayed correctly                     |
| TC11    | 2025-07-11 | Rachel Nkatha  | Awareness page: screen reader test     | ❌ Fail     | BUG D02: Images missing alt-text              |
| TC12    | 2025-07-12 | Anthony Kiptoo | Responsive layout on mobile            | ✅ Pass     | Layout and buttons scaled correctly           |

---

## 🤖 Automated Test Log (Jest + DOM)

| Script ID | Date       | Tester         | Description                                 | Result     | Comments/Observations                      |
|-----------|------------|----------------|---------------------------------------------|------------|---------------------------------------------|
| AT01      | 2025-07-14 | Anthony Kiptoo | Login form loads and handles inputs         | ✅ Pass     | Fields and validation work as expected      |
| AT02      | 2025-07-14 | Anthony Kiptoo | Pickup form submits with valid fields       | ✅ Pass     | Simulated DOM event triggered success state |
| AT03      | 2025-07-15 | Anthony Kiptoo | Pickup form validation with empty name      | ✅ Pass     | Validation message shown                    |
| AT04      | 2025-07-15 | Anthony Kiptoo | Password not secured in localStorage        | ⚠️ Partial  | Password stored in plain text (not hashed)  |

---

## 🧠 Summary

- **Manual tests passed**: 10 / 12  
- **Automated tests passed**: 3 / 4  
- **Critical bugs found**: 2  
- **Testing completed**: July 23, 2025

---

## 📦 Notes

- Testers used Chrome DevTools to simulate responsiveness.
- Lighthouse and ChromeVox used to audit accessibility.
- Automated tests run using Jest + @testing-library/dom inside a JSDOM environment.
- Screenshots stored in: `tests/screenshots/`

---


