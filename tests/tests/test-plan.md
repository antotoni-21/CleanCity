# 🧪 CleanCity: Waste Pickup Scheduler - Test Plan

## 1. Overview
The CleanCity application simulates a waste management system for African cities. It is intended for QA students to practice manual and automated testing. This document outlines the initial test strategy, scope, and objectives.

## 2. Objectives
- Ensure major user flows function correctly (request pickup, view dashboard, give feedback).
- Identify and report bugs (functional, UI, accessibility, etc.).
- Practice manual, boundary, and automated testing techniques.
- Provide test coverage for components and common scenarios.

## 3. Scope of Testing

### In Scope
- Waste pickup form validation and submission
- Dashboard request filtering and status display
- Feedback form and request ID handling
- Admin panel request status management
- Awareness page content and responsiveness
- Accessibility testing on key pages
- Testing responsive layouts on various screen sizes

### Out of Scope
- API/backend testing (no real backend; uses localStorage)
- Security penetration testing

## 4. Types of Testing
| Type | Purpose |
|------|---------|
| Functional Testing | Validate core functionality of each user flow |
| Manual Testing | Simulate real user behavior and identify usability bugs |
| Boundary Testing | Test input field limits and edge cases |
| Accessibility Testing | Ensure usability with screen readers and missing alt-text |
| Responsive Testing | Check layout on different devices and screen sizes |
| Regression Testing | Re-test after changes to ensure stability |
| Automated Testing | Use React Testing Library to validate components |

## 5. Testing Tools
- **React Testing Library** – For automated component tests
- **Browser DevTools** – For manual debugging and responsiveness checks
- **Lighthouse** – For performance and accessibility audits
- **Screen Readers** – For testing accessibility (NVDA, VoiceOver)
- **GitHub Issues** – For bug tracking and reporting

## 6. Environments
| Platform | Version |
|----------|---------|
| OS | Windows / macOS / Linux |
| Browsers | Chrome (v100+), Firefox (v90+), Edge |
| Device Types | Desktop, Tablet, Mobile (responsive) |
| Data Storage | localStorage (no external database) |

## 7. Known Intentional Bugs (For Practice)
| Page | Bug |
|------|-----|
| Home | Date field doesn’t trigger validation error |
| Dashboard | Filtering by "Eldoret" shows incorrect data |
| Awareness | All images missing alt-text |
| Admin Panel | UI doesn’t update after status change |
| Forms | Very long text causes layout issues |

## 8. Test Data
- Sample Requests: `REQ001` to `REQ005` with various statuses
- Locations: Nairobi, Kisumu, Mombasa, Eldoret
- Waste Types: General, Recyclable, Hazardous
- Feedback: `FB001` linked to `REQ004`

## 9. Team Roles (Summary)
- Test Lead: Coordinates testing strategy and reviews cases
- Manual Tester: Executes test scenarios and reports bugs
- Automation Engineer: Writes and maintains automated tests
- UX/Accessibility Tester: Tests design and accessibility flaws

## 10. Timeline (Phase 1)
- ✅ Project Repo Initialized
- ✅ `tests/` Folder Created
- ✅ `test-plan.md` Created
- ⏳ Manual test case writing in progress
- ⏳ Automation test setup begins in Week 2

---

✅ **Next Steps**:
- Add detailed manual test cases (e.g., `form-validation.md`, `admin-panel.md`)
- Start basic component test automation with React Testing Library

