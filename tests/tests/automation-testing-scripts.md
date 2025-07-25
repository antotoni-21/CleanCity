# 🤖 Automated Test Scripts

This document outlines the automated test cases implemented for the application using [your test framework/tool here].

---

## ✅ Test Case: TC-201 – Login with Valid Credentials

- **Framework**: Cypress
- **Test File**: `tests/auth/login_valid.cy.js`
- **Test Suite**: Authentication
- **Priority**: High
- **Tags**: @smoke @login

### 🧪 Description
Verifies that users can log in successfully using valid credentials.

### 📄 Preconditions
- Valid user credentials exist in the system.

### 🚶 Test Steps
1. Visit `/login`
2. Enter valid email and password
3. Click "Login"

### ✅ Expected Result
- Redirect to dashboard (`/dashboard`)
- Welcome message should be visible

### 🧰 Code Snippet
```javascript
describe('Login with valid credentials', () => {
  it('should redirect to dashboard after login', () => {
    cy.visit('/login');
    cy.get('#email').type('user@example.com');
    cy.get('#password').type('Password123!');
    cy.get('button[type="submit"]').click();
    cy.url().should('include', '/dashboard');
    cy.contains('Welcome,').should('be.visible');
  });
});

