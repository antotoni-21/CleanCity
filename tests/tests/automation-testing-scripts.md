# 🤖 Automated Test Scripts

**2025-07-25**

This document contains automated test scripts based on the system functional requirements.

---

## 📂 3.1 User Registration

### ✅ Test Case: TC-A001 – Register with valid information

- **Framework**: Cypress
- **Test File**: `tests/auth/register_valid.cy.js`
- **Related FR(s)**: FR-001, FR-003

#### 🧪 Description
Test user registration with all valid fields.

---

### ✅ Test Case: TC-A002 – Invalid email format

- **Framework**: Cypress
- **Test File**: `tests/auth/register_invalid_email.cy.js`
- **Related FR(s)**: FR-002

#### 🧪 Description
Verify error message for invalid email format during registration.

---

## 📂 3.2 User Login

### ✅ Test Case: TC-B001 – Login with correct credentials

- **Framework**: Playwright
- **Test File**: `tests/auth/login_success.spec.ts`
- **Related FR(s)**: FR-004, FR-007

#### 🧪 Description
Check if users can login and are redirected to intended page.

---

### ✅ Test Case: TC-B002 – Login with wrong password

- **Framework**: Playwright
- **Test File**: `tests/auth/login_invalid_password.spec.ts`
- **Related FR(s)**: FR-005

#### 🧪 Description
Ensure error message is displayed for wrong credentials.

---

## 📂 4.1 Pickup Scheduling

### ✅ Test Case: TC-C001 – Schedule valid pickup

- **Framework**: Cypress
- **Test File**: `tests/pickup/schedule_valid.cy.js`
- **Related FR(s)**: FR-012, FR-013

#### 🧪 Description
Test scheduling pickup with valid inputs 3 days in advance.

---

### ✅ Test Case: TC-C002 – Attempt pickup within 24 hours

- **Framework**: Cypress
- **Test File**: `tests/pickup/schedule_too_soon.cy.js`
- **Related FR(s)**: FR-013

#### 🧪 Description
Ensure error is shown when pickup is scheduled within 24 hours.

---




