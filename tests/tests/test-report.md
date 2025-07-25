# CleanCity: Waste Pickup Scheduler  
**QA Final Test Report**  
**Team:** GoGetters  
**Institution:** PLP Academy  
**Date:** 25 July 2025  

---

## Table of Contents
1. [Executive Summary](#executive-summary)  
2. [Test Strategy and Approach](#test-strategy-and-approach)  
3. [Test Environment Details](#test-environment-details)  
4. [Test Execution Summary](#test-execution-summary)  
5. [Defect Analysis and Categorization](#defect-analysis-and-categorization)  
6. [Risk Assessment](#risk-assessment)  
7. [Recommendations and Improvements](#recommendations-and-improvements)  
8. [Test Metrics and KPIs](#test-metrics-and-kpis)  
9. [Appendices](#appendices)  

---

## Executive Summary

The CleanCity application was subjected to a comprehensive QA process involving both manual and automated testing. The goal was to assess form validation, data filtering, UI responsiveness, and accessibility.

### 🔍 Key Findings:
- Filter logic in the dashboard is flawed (critical bug).
- Missing accessibility attributes (alt-text) on Awareness page.
- Admin status updates are delayed in UI.
- Plain-text password storage is insecure.

### ✅ Recommendations:
- Implement password hashing.
- Fix filtering logic and auto-refresh UI.
- Add missing accessibility tags for compliance.

---

## Test Strategy and Approach

### 🎯 Objective:
Ensure functional, responsive, and accessible experience across all pages and workflows.

### 🛠️ Approach:
- **Manual Testing**: Used for UI/UX, boundary, and accessibility validation.
- **Automated Testing**: Performed using Jest and React Testing Library for form logic and login flows.
- **Intentional Bugs**: Verified against known documentation to practice regression and exploratory testing.

---

## Test Environment Details

| Component       | Configuration                        |
|----------------|---------------------------------------|
| Browsers       | Chrome 125.0, Firefox 118.0           |
| OS             | Windows 10, Ubuntu 22.04              |
| Automation Tool| Jest + React Testing Library          |
| Manual Tools   | Chrome DevTools, Lighthouse           |
| Data Layer     | localStorage (client-side only)       |
| Devices Used   | Desktop, Mobile                       |

---

## Test Execution Summary

### 🧪 Manual Testing
| ID   | Description                               | Result  |
|------|-------------------------------------------|---------|
| TC01 | Valid Login                               | ✅ Pass |
| TC02 | Invalid Login                             | ✅ Pass |
| TC04 | Pickup Form - Valid Submission            | ✅ Pass |
| TC06 | Form with Short Name                      | ✅ Pass |
| TC08 | Filter by "Eldoret"                       | ❌ Fail |
| TC10 | Admin Panel Update                        | ⚠ Partial |
| TC11 | Accessibility on Awareness Page           | ❌ Fail |

### 🤖 Automated Testing
- Login input validation  
- Pickup form validation  
- Password field logic  
- Submission flow simulation

---

## Defect Analysis and Categorization

| ID  | Area         | Description                                     | Severity | Status |
|-----|--------------|-------------------------------------------------|----------|--------|
| D01 | Dashboard    | Filtering returns incorrect results             | Medium   | Open   |
| D02 | Awareness    | Missing alt-text on images                      | High     | Open   |
| D03 | Admin Panel  | UI does not auto-refresh on update              | Medium   | Open   |
| D04 | Login        | Password stored in localStorage (plain text)    | High     | Known  |
| D05 | Form         | Optional field skips validation                 | Low      | Known  |

---

## Risk Assessment

| Risk                                | Impact         | Likelihood | Mitigation                      |
|-------------------------------------|----------------|------------|----------------------------------|
| Insecure password storage           | Very High      | Medium     | Implement hashing mechanisms     |
| Broken filter logic                 | Medium         | High       | Refactor filter condition code   |
| Accessibility issues (no alt-text) | High (compliance) | High    | Add `alt` and `aria` attributes  |

---

## Recommendations and Improvements

- **Security**: Encrypt passwords using SHA-256 or bcrypt before storing.
- **UX**: Trigger UI refresh post-status update in Admin Panel.
- **Accessibility**: Add descriptive `alt` text and keyboard navigation.
- **Testing**: Expand automation scripts for Admin and Feedback modules.
- **Architecture**: Introduce backend API for better data handling.

---

## Test Metrics and KPIs

| Metric                       | Value        |
|------------------------------|--------------|
| Manual Test Cases Executed   | 12           |
| Automated Scripts Executed   | 4            |
| Total Defects Identified     | 5            |
| High Severity Bugs           | 2 (40%)      |
| UI Accessibility Score (Lighthouse) | 63%   |
| Test Coverage (Critical Flows) | ~90%       |

---

## Appendices

- 📁 `tests/test-plan.md` – Initial strategy  
- 📁 `tests/test-cases.md` – Full manual test cases  
- 📁 `tests/defect-log.md` – Bug log with descriptions  
- 📁 `tests/automation-testing-scripts.md`  
- 📁 `tests/manual-testing-scripts.md`  
- 📁 `tests/screenshots/` – Visual proof of execution  
- 📁 `tests/final-report.md` – Summarized results  

---

**Prepared by Team CleanSweep – July 2025**



