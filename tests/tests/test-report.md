# ✅ Test Execution Report – CleanCity: Waste Pickup Scheduler

## 📌 Project Overview
**CleanCity** is a simulated web application built for QA students to practice full-cycle manual and automated testing. The platform allows users to request waste pickups, report issues, and manage requests through an admin panel. The application contains intentional bugs to enhance learning.

---

## 🔧 Environment

| Component          | Details                      |
|-------------------|------------------------------|
| Browser           | Chrome 125.0 / Firefox 118.0 |
| OS                | Windows 10 / Ubuntu 22.04    |
| Automation Tools  | Jest, @testing-library/dom   |
| Manual Tools      | Chrome DevTools, Lighthouse  |
| Storage           | localStorage (mock database) |
| Device Types      | Desktop, Mobile (responsive) |

---

## ✅ Test Summary

| Category            | Count |
|---------------------|-------|
| Manual Test Cases   | 12    |
| Automated Test Cases| 4     |
| Total Defects Found | 5     |
| High Severity Bugs  | 2     |

---

## 📝 Test Case Coverage

### 🔹 Manual Test Case Summary

| ID   | Feature         | Description                                      | Result     |
|------|-----------------|--------------------------------------------------|------------|
| TC01 | Login           | Valid login redirects to dashboard              | ✅ Pass     |
| TC02 | Login           | Invalid credentials show error                  | ✅ Pass     |
| TC03 | Login           | Missing input shows HTML5 validation            | ✅ Pass     |
| TC04 | Pickup Request  | Submit form with all valid fields               | ✅ Pass     |
| TC05 | Pickup Request  | Skip optional date field                        | ✅ Pass     |
| TC06 | Pickup Request  | Name < 2 chars shows error                      | ✅ Pass     |
| TC08 | Dashboard       | Filter by "Eldoret" shows incorrect results     | ❌ Fail     |
| TC09 | Admin Panel     | Mark request as "Completed" updates UI slowly   | ⚠️ Partial  |
| TC10 | Feedback Form   | Invalid Request ID shows error                  | ✅ Pass     |
| TC11 | Awareness Page  | Missing alt-text on images                      | ❌ Fail     |
| TC12 | Responsive Test | Pages display correctly on mobile               | ✅ Pass     |

---

### 🔹 Automated Test Summary (Jest)

| Script               | Description                             | Result |
|----------------------|-----------------------------------------|--------|
| login.test.js       | Valid and invalid login inputs          | ✅ Pass |
| pickup-form.test.js | Form submission with valid fields       | ✅ Pass |
| pickup-form.test.js | Submission without required fields      | ✅ Pass |
| login.test.js       | Password field remains secure           | ⚠️ Partial |

---

## 🐞 Defect Summary

| ID   | Module        | Description                                      | Severity | Status |
|------|---------------|--------------------------------------------------|----------|--------|
| D01  | Dashboard     | Filter by Eldoret returns Nairobi results        | Medium   | Open   |
| D02  | Awareness     | All images lack alt-text (accessibility issue)   | High     | Open   |
| D03  | Admin Panel   | UI doesn't auto-refresh after status update      | Medium   | Open   |
| D04  | Login         | Password stored in plain text (security flaw)    | High     | Open   |
| D05  | Pickup Form   | Optional fields bypass validation                | Low      | Known  |

---

## 📸 Evidence of Test Execution

Screenshots can be found in /tests/screenshots/:

- login-success.png – Dashboard after successful login
- filter-bug.png – Eldoret filter shows wrong results
- awareness-alt-missing.png – Chrome DevTools showing missing alt attributes
- form-success.png – Pickup submission success message
- admin-delay.png – Status change with delayed UI update

---

## 🧠 Observations & Reflections

- **Manual testing** surfaced edge-case issues faster due to intentional bugs.
- **localStorage**-based state management required repeated resets.
- Accessibility tools helped uncover commonly ignored defects (like alt-text).
- Automated testing made form validation reliable but had limitations on testing visual updates (like Admin Panel refresh).

---

## 📈 Recommendations

- Introduce hashed password handling for secure authentication.
- Fix dashboard filter logic (likely string matching bug).
- Refresh UI state in Admin Panel after update (e.g., re-render or reload).
- Use semantic HTML and accessibility standards (`alt`, `aria-*` attributes).
- Extend test coverage to feedback form and registration page.

---

## 👥 Team & Contributions

| Name                     | Role                         | Tasks Completed                                      |
|--------------------------|------------------------------|-----------------------------------------------------|
| Anthony Kiptoo Kipkogei  | Test Lead, Automation Scripter| Planned, coded Jest scripts, coordinated Git updates|
| Elisha Abayi Kigalave    | Manual Tester, Bug Reporter   | Validated forms, documented bugs                    |
| Rachel Yetunde Nkatha    | UI & Accessibility Auditor    | Responsive & alt-text testing, report generation    |

---

## 📅 Test Execution Timeline

| Week | Milestone                         | Key Deliverables                                      |
|------|----------------------------------|--------------------------------------------------------|
| 1    | Setup & Planning                 | test-plan.md`, `team-roles.md`, initialized repo     |
| 2    | Test Case Design + Early Tests  | test-cases.md`,  `defect-log.md , automation-scripts.md` |
| 3    | Full Execution & Reporting      | Screenshots, test-report.md`, `final-report.md`      |

---

## ✅ Conclusion

The CleanCity QA project was successful in fulfilling all manual testing objectives and demonstrated early progress in automation. Despite encountering intentional and natural bugs, the QA team was able to document, report, and offer improvements while practicing industry-standard testing workflows.


