# 🧪 Manual Testing Scripts – CleanCity

This document outlines the step-by-step manual test procedures used to validate major user flows in the CleanCity Waste Pickup Scheduler application.

---

## 📝 Test 1: Login Functionality

**Precondition**: The user account already exists in localStorage.

**Steps**:
1. Navigate to `index.html`
2. Click on **Login** tab
3. Enter valid email: `user@example.com`
4. Enter password: `password123`
5. Click **Login**
6. Observe if redirected to Dashboard

**Expected Result**: User sees dashboard with their pickup requests.

---

## 📝 Test 2: Pickup Request Submission

**Steps**:
1. Go to **Home** tab
2. Fill the form:
   - Full Name: `Test User`
   - Waste Type: `General`
   - Location: `Nairobi`
   - Date: (Leave blank intentionally)
3. Click **Submit**

**Expected Result**: Pickup request is accepted and success message appears.

**Note**: Missing date field does not block submission (intentional bug D03)

---

## 📝 Test 3: Dashboard Filtering

**Steps**:
1. Navigate to **Dashboard**
2. Select filter: Location = "Eldoret"
3. Click **Apply Filter**

**Expected Result**: Only Eldoret requests appear

**Actual Result**: Nairobi requests are still visible (bug D01)

---

## 📝 Test 4: Admin Panel Update

**Steps**:
1. Click on **Admin Panel**
2. Select a request
3. Set status to "Completed"
4. Click **Update Status**

**Expected Result**: Status changes in the UI

**Bug**: UI does not refresh until manual reload (bug D04)

---

## 📝 Test 5: Awareness Page Accessibility

**Steps**:
1. Open **Awareness** page
2. Use screen reader (e.g., NVDA or ChromeVox)
3. Hover or tab through images

**Expected Result**: Each image should be described

**Actual Result**: No descriptions available (bug D02)

---

## Tools Used:
- Browser (Chrome, Firefox)
- DevTools > Responsive Design
- Lighthouse (Accessibility Tab)
- Manual localStorage management for mock data


