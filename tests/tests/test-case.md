# 🧪 CleanCity: Waste Pickup Scheduler-Test Cases



## 🔐 3.1 User Registration

### TC-001 – Register with valid information
- **Precondition:** User is on the registration page
- **Steps:**
  1. Enter valid email: user@example.com
  2. Enter password: Test@1234
  3. Enter confirm password: Test@1234
  4. Enter full name: John Doe
  5. Enter phone number: +1234567890
  6. Click "Register"
- **Expected Result:**
Account is created, user is assigned "User" role, and redirected or shown success message
- **FR:** FR-001, FR-003


### TC-002 – Register with invalid email format
- **Steps:** 
  1. Enter user@ in the email field
- **Expected Result:** "Invalid email format" error is displayed
- **FR:** FR-002


### TC-003 – Register with short password
- **Steps:**
  1. Enter password less than 8 characters (e.g., Test1)
- **Expected Result:** "Password must be at least 8 characters" error is shown
- **FR:** FR-002


### TC-004 – Register with mismatched confirm password
- **Steps:**
  1. Password:Test@1234,
  2.  Confirm password: Test@123
- **Expected Result:** "Passwords do not match" error message
- **FR:** FR-002


### TC-005 – Register with full name less than 2 characters
- **Steps:**
  1. Enter full name: A
- **Expected Result:** "Full name must be between 2 and 50 characters"
- **FR:** FR-002


### TC-006 – Register with invalid phone number
- **Steps:**
  1. Phone: abc123
- **Expected Result:** "Invalid phone number"
- **FR:** FR-002


## 🔑 3.2 User Login


### TC-007 – Login with valid credentials
- **Precondition:** User is registered
- **Steps:**
  1. Enter email: user@example.com
  2. Enter password: Test@1234
  3. Click "Login"
- **Expected Result:** User is logged in and redirected to intended page; session saved in localStorage
- **FR:** FR-004, FR-006, FR-007


### TC-008 – Login with incorrect password
- **Steps:**
  1. Enter valid email,
  2. wrong password
- **Expected Result:** "Invalid credentials" message
- **FR:** FR-005


### TC-009 – Login with unregistered email
- **Steps:**
  1. Email not in system
- **Expected Result:** "Email not found" or generic error
- **FR:** FR-005


### TC-010 – Check localStorage on successful login
- **Steps:**
  1. Login successfully
  2. Open browser developer tools
- **Expected Result:** User session token or identifier is present in localStorage
- **FR:** FR-006


### TC-011 – Redirect to intended page after login
- **Steps:**
  1. Try accessing /profile while logged out
  2. Login when prompted
- **Expected Result:** Redirected to /profile after login
- **FR:** FR-007


## 🚪 3.3 User Logout


### TC-012 – User logs out successfully
- **Steps:**
  1. Click "Logout"
- **Expected Result:** Session is cleared, user redirected to login page
- **FR:** FR-008, FR-009


## 🛡️ 3.4 Role-Based Access


### TC-013 – User role restricted from admin page
- **Precondition:** Logged in as "User"
- **Steps:**
  1.  Navigate to /admin
- **Expected Result:** Access denied or redirect to a "403 Forbidden" or home page
- **FR:** FR-011

### TC-014 – Admin accesses admin-only features
- **Precondition:** Logged in as "Admin"
- **Steps:**
 1. Navigate to /admin
- **Expected Result:** Admin dashboard loads successfully
- **FR:** FR-010, FR-011

### TC-015 – New user has default role "User"
- **Steps:**
  1.  Register a new account
- **Expected Result:** Account role is "User" by default (can be checked in API or user panel)
- **FR:** FR-003, FR-010


## ♻️ 4.1 Pickup Scheduling

---

### ✅ TC-016 – Schedule pickup with valid information  
**Precondition:** User is logged in  
**Steps:**  
1. Navigate to the pickup scheduling form  
2. Select a date 3 days from today  
3. Select waste type: “Recyclable”  
4. Select quantity: “Medium”  
5. Enter special instructions: “Place bags near garage”  
6. Submit request  
**Expected Result:** Pickup request is successfully submitted and shown in request history  
**FR:** FR-012  

---

### ❌ TC-017 – Pickup date is in the past  
**Steps:**  
1. Enter a date that is today or earlier  
**Expected Result:** Error message: “Pickup date must be at least 24 hours in advance”  
**FR:** FR-013  

---

### ❌ TC-018 – Pickup date is less than 24 hours away  
**Steps:**  
1. Select a date/time 10 hours from now  
**Expected Result:** Error message preventing scheduling  
**FR:** FR-013  

---

### ❌ TC-019 – Missing required fields (waste type, quantity)  
**Steps:**  
1. Leave waste type and quantity blank  
**Expected Result:** Error: “Waste type and quantity are required”  
**FR:** FR-012  

---

### ❌ TC-020 – Special instructions exceed 200 characters  
**Steps:**  
1. Enter a 250-character note in special instructions  
**Expected Result:** Error: “Maximum 200 characters allowed”  
**FR:** FR-012  

---

### ✅ TC-021 – Address auto-filled from profile  
**Steps:**  
1. Open scheduling form  
**Expected Result:** Address field is pre-populated with user’s profile address  
**FR:** FR-012

## 🗓️ 4.1 Additional Pickup Scheduling

---

### ✅ TC-022 – View available time slots  
**Steps:**  
1. Select a valid future date  

**Expected Result:**  
List of available time slots is displayed  

**Requirement ID:** FR-014  

---

### ❌ TC-023 – Prevent multiple pickups for same date  
**Precondition:** One pickup is already scheduled for the selected date  
**Steps:**  
1. Try to book another pickup for the same date  

**Expected Result:**  
Error: “You already have a pickup scheduled for this date”  

**Requirement ID:** FR-015  

---

## 📋 4.2 Request Management

---

### ✅ TC-024 – View request history  
**Steps:**  
1. Navigate to “My Requests”  

**Expected Result:**  
List of past and pending pickup requests is shown with status and details  

**Requirement ID:** FR-016  

---

### ✅ TC-025 – Cancel a pending pickup  
**Precondition:** Pickup request status is “Pending”  
**Steps:**  
1. Click “Cancel” on a request  

**Expected Result:**  
Request status changes to “Cancelled”  

**Requirement ID:** FR-017  

---

### ❌ TC-026 – Try to cancel completed pickup  
**Precondition:** Pickup is already marked as “Completed”  
**Steps:**  
1. Attempt to cancel  

**Expected Result:**  
Action blocked, message: “Only pending pickups can be cancelled”  

**Requirement ID:** FR-017  

---

### ✅ TC-027 – Modify pickup before 24 hours  
**Precondition:** Pickup is scheduled more than 24 hours from now  
**Steps:**  
1. Edit quantity and waste type  

**Expected Result:**  
Update is saved successfully  

**Requirement ID:** FR-018  

---

### ❌ TC-028 – Modify pickup within 24-hour window  
**Precondition:** Pickup is scheduled in less than 24 hours  
**Steps:**  
1. Try to edit pickup  

**Expected Result:**  
Edit option disabled or warning shown  

**Requirement ID:** FR-018  

---

### ✅ TC-029 – Display request status  
**Steps:**  
1. View requests in history  

**Expected Result:**  
Each request shows status: Pending, Confirmed, Completed, or Cancelled  

**Requirement ID:** FR-019  

---

## 🚚 4.3 Request Tracking

---

### ✅ TC-030 – Real-time status updates  
**Precondition:** Pickup request is active  
**Steps:**  
1. Refresh dashboard or open tracking view  

**Expected Result:**  
Status updates automatically without full reload  

**Requirement ID:** FR-020  

---

### ✅ TC-031 – Receive notification for status changes  
**Steps:**  
1. Schedule a pickup and wait for status to change  

**Expected Result:**  
User receives in-app or email notification  

**Requirement ID:** FR-021  

---

### ✅ TC-032 – Leave feedback after pickup  
**Precondition:** Pickup status is “Completed”  
**Steps:**  
1. Open the completed request  
2. Submit feedback (e.g., 4-star rating, comment)  

**Expected Result:**  
Feedback is saved and associated with the request  

**Requirement ID:** FR-022  


## 📊 5.1 User Dashboard

---

### ✅ TC-033 – Display personalized user dashboard  
**Precondition:** User is logged in with pickup history  
**Steps:**  
1. Log in and navigate to `/dashboard`  

**Expected Result:**  
- Recent pickups section is visible  
- Upcoming scheduled pickups are listed  
- Environmental stats and achievement badges are shown  
- Quick action buttons (e.g., Schedule Pickup, View History) are displayed  

**Requirement ID:** FR-023  

---

### ✅ TC-034 – Show recent pickup requests  
**Steps:**  
1. Open dashboard  

**Expected Result:**  
Last 3–5 completed pickup requests appear under “Recent Activity”  

**Requirement ID:** FR-023  

---

### ✅ TC-035 – Display upcoming scheduled pickups  
**Precondition:** User has future scheduled pickups  
**Steps:**  
1. Open dashboard  

**Expected Result:**  
Pickup date/time, type, and status shown in “Upcoming Pickups”  

**Requirement ID:** FR-023  

---

### ✅ TC-036 – Show environmental impact stats  
**Steps:**  
1. View environmental section on dashboard  

**Expected Result:**  
Shows accurate metrics: Total waste diverted, CO₂ saved, Trees saved  

**Requirement ID:** FR-024  

---

### ✅ TC-037 – Environmental metrics calculation accuracy  
**Steps:**  
1. Compare metrics against backend or database calculations  

**Expected Result:**  
Displayed stats correctly match user’s actual pickup totals  

**Requirement ID:** FR-024  

---

### ✅ TC-038 – Display quick action buttons  
**Steps:**  
1. View dashboard buttons  

**Expected Result:**  
"Schedule Pickup", "Track Request", "Download Report", etc., are shown and clickable  

**Requirement ID:** FR-023  

---

## 📈 5.2 Analytics & Reports

---

### ✅ TC-039 – Display charts and graphs for user data  
**Steps:**  
1. Go to “Analytics” tab  

**Expected Result:**  
Charts show:  
- Waste type breakdown  
- Pickup frequency  
- CO₂ impact over time  

**Requirement ID:** FR-025  

---

### ✅ TC-040 – Community leaderboard shows impact rankings  
**Steps:**  
1. Open “Community” or “Leaderboard” tab  

**Expected Result:**  
- List of top users sorted by environmental metrics (e.g., waste diverted)  
- User’s own rank is highlighted  

**Requirement ID:** FR-026  

---

### ✅ TC-041 – Show monthly and yearly waste trends  
**Steps:**  
1. View analytics filters  
2. Select month/year filter  

**Expected Result:**  
- Graph updates to reflect selected timeframe  
- Trends show upward/downward waste activity  

**Requirement ID:** FR-027  

---

### ✅ TC-042 – Export user data to CSV  
**Steps:**  
1. Click "Export" on dashboard or profile  

**Expected Result:**  
Download starts for a `.csv` file with user's pickup history and impact stats  

**Requirement ID:** FR-028  

---

### ✅ TC-043 – Validate exported CSV content  
**Steps:**  
1. Open exported CSV  

**Expected Result:**  
Data includes:  
- Pickup dates  
- Waste types  
- Quantity  
- Impact values  

**Requirement ID:** FR-028  

---

## 🏅 5.3 Gamification

---

### 🏆 TC-044 – Award badge for first pickup  
**Precondition:** User schedules first pickup  
**Steps:**  
1. Complete first pickup  
2. Open dashboard  

**Expected Result:**  
"First Pickup" badge is awarded and displayed  

**Requirement ID:** FR-029  

---

### 🏆 TC-045 – Award badge for 10 completed pickups  
**Precondition:** User completes 10 pickups  
**Steps:**  
1. Open dashboard  

**Expected Result:**  
"10 Pickups Completed" badge is visible  

**Requirement ID:** FR-029  

---

### 🏆 TC-046 – Award badge for perfect recycling score  
**Precondition:** User has multiple pickups marked as “perfect recycling”  
**Steps:**  
1. Review badges on dashboard  

**Expected Result:**  
"Perfect Recycler" badge is awarded  

**Requirement ID:** FR-029  

---

### 🏆 TC-047 – Award badge for community contribution  
**Precondition:** User engages with community features (e.g., referrals, posts)  
**Steps:**  
1. Use community features  
2. Return to dashboard  

**Expected Result:**  
"Community Contributor" badge is shown  

**Requirement ID:** FR-029  

---

### 🏆 TC-048 – Track and display user points and levels  
**Steps:**  
1. View profile or dashboard gamification section  

**Expected Result:**  
- Total points and level are displayed  
- Activity log shows point history  

**Requirement ID:** FR-030  

---

### 🏆 TC-049 – Level up when threshold reached  
**Precondition:** User reaches level-up point threshold  
**Steps:**  
1. Complete an action that pushes points past the threshold  

**Expected Result:**  
- User levels up  
- Notification or animation shown  

**Requirement ID:** FR-030  


## 📝 6.1 Blog System

---

### ✅ TC-050 – Display list of blog articles  
**Precondition:** At least one blog post exists  
**Steps:**  
1. Navigate to the “Blog” page  

**Expected Result:**  
Blog posts are displayed with titles, preview text, and links  

**Requirement ID:** General  

---

### ✅ TC-051 – Read a full blog article  
**Steps:**  
1. Click on a blog post from the list  

**Expected Result:**  
Full content of the blog article is displayed  

**Requirement ID:** General  

---

### ✅ TC-052 – Like or bookmark a blog post (if applicable)  
**Steps:**  
1. Open a blog post  
2. Click "Like" or "Bookmark" (if implemented)  

**Expected Result:**  
Action is recorded and UI updates accordingly  

**Requirement ID:** Users should be able to interact with blog content  

---

### ✅ TC-053 – Admin can create, edit, and delete blog posts  
**Precondition:** Admin user logged in  
**Steps:**  
1. Navigate to blog admin panel  
2. Create a post with title, body, tags  
3. Edit it  
4. Delete it  

**Expected Result:**  
CRUD operations complete successfully  

**Requirement ID:** Users/admins should manage blog posts  

---

### ✅ TC-054 – Blog supports categories and tags  
**Steps:**  
1. View blog post details or filter list by category/tag  

**Expected Result:**  
Posts are grouped or filterable by categories or tags  

**Requirement ID:** Blog may support categories or tags  

---

## 🌱 6.2 Awareness Section

---

### ✅ TC-055 – Eco tips rotate every 5 seconds  
**Steps:**  
1. Go to Awareness section  
2. Observe tip content  

**Expected Result:**  
A new eco tip appears every 5 seconds without page refresh  

**Requirement ID:** FR-036  

---

### ✅ TC-056 – View environmental quizzes  
**Steps:**  
1. Click on "Take Quiz" in Awareness section  

**Expected Result:**  
Quiz page loads with question and answer options  

**Requirement ID:** FR-037  

---

### ✅ TC-057 – Submit quiz and view score  
**Steps:**  
1. Answer all quiz questions  
2. Submit the quiz  

**Expected Result:**  
Final score is shown along with correct answers and explanations  

**Requirement ID:** FR-038  

---

### ✅ TC-058 – Track quiz score in user history  
**Precondition:** User is logged in and has taken quizzes  
**Steps:**  
1. Go to profile or quiz history  

**Expected Result:**  
Previous quiz attempts and scores are displayed  

**Requirement ID:** FR-038  

---

### ✅ TC-059 – Display infographics with environmental statistics  
**Steps:**  
1. Open the Awareness section  

**Expected Result:**  
Charts/graphics showing recycling rates, CO₂ impact, etc., are displayed  

**Requirement ID:** FR-039  

---

### ✅ TC-060 – Action buttons in Awareness section work  
**Steps:**  
1. Click buttons like “Learn More”, “Join Campaign”, or “Schedule Pickup”  

**Expected Result:**  
Navigates to the correct feature or section  

**Requirement ID:** FR-040  

---

## 👥 6.3 Community Feed

---

### ✅ TC-061 – User creates a community post  
**Precondition:** User is logged in  
**Steps:**  
1. Go to Community section  
2. Click “New Post”  
3. Enter text and submit  

**Expected Result:**  
Post is displayed at the top of the feed  

**Requirement ID:** FR-041  

---

### ✅ TC-062 – User likes and comments on post  
**Steps:**  
1. Open a community post  
2. Click “Like” and leave a comment  

**Expected Result:**  
Like counter increases, comment appears under post  

**Requirement ID:** FR-042  

---

### ✅ TC-063 – Posts display in chronological order  
**Steps:**  
1. View community feed  

**Expected Result:**  
Newest posts appear first  

**Requirement ID:** FR-043  

---

### ✅ TC-064 – User shares eco tips or experiences  
**Steps:**  
1. Create a post with eco tip or experience story  

**Expected Result:**  
Post is added to feed and visible to community  

**Requirement ID:** FR-044  


## 👥 7.1 User Profiles

---

### ✅ TC-065 – View user profile  
**Precondition:** User is logged in  
**Steps:**  
1. Navigate to `/profile`  

**Expected Result:**  
Profile page loads with name, bio, photo, statistics, and edit button  

**Requirement ID:** FR-045  

---

### ✅ TC-066 – Edit user profile information  
**Steps:**  
1. Click "Edit Profile"  
2. Modify name, phone, or bio  
3. Save changes  

**Expected Result:**  
Changes are saved and reflected immediately  

**Requirement ID:** FR-045  

---

### ✅ TC-067 – Upload or change profile picture  
**Steps:**  
1. Click on profile picture  
2. Upload new image  
3. Save  

**Expected Result:**  
Profile image updates successfully  

**Requirement ID:** FR-047  

---

### ✅ TC-068 – Display user activity history  
**Precondition:** User has scheduled pickups, taken quizzes, or made posts  
**Steps:**  
1. View the "Activity" tab on profile  

**Expected Result:**  
List of past actions like pickups, posts, quiz results shown chronologically  

**Requirement ID:** FR-046  

---

### ✅ TC-069 – Display user achievements and badges  
**Steps:**  
1. Open profile page  
2. Scroll to “Achievements” section  

**Expected Result:**  
Badge icons and milestone titles are visible  

**Requirement ID:** FR-046  

---

### ✅ TC-070 – Display environmental impact stats  
**Steps:**  
1. Visit the profile dashboard or statistics tab  

**Expected Result:**  
Stats such as total waste recycled, CO₂ saved, trees saved are displayed  

**Requirement ID:** FR-048  

---

## 🔗 7.2 Social Features

---

### ✅ TC-071 – Follow another user  
**Precondition:** Multiple users exist  
**Steps:**  
1. Visit another user's profile  
2. Click "Follow"  

**Expected Result:**  
Followed user is added to the following list, and button changes to “Unfollow”  

**Requirement ID:** FR-049  

---

### ✅ TC-072 – View news feed of followed users  
**Steps:**  
1. Navigate to “News Feed” section  

**Expected Result:**  
Shows activity of followed users (e.g., new posts, achievements, events joined)  

**Requirement ID:** FR-050  

---

### ✅ TC-073 – Share achievement to community feed  
**Precondition:** User unlocks a badge or milestone  
**Steps:**  
1. View achievement popup  
2. Click “Share to Community”  

**Expected Result:**  
A post appears in the community feed with badge and user comment (if any)  

**Requirement ID:** FR-051  

---

### ✅ TC-074 – Participate in community challenges  
**Precondition:** A challenge is active (e.g., “Recycle 10 kg in July”)  
**Steps:**  
1. Navigate to “Challenges”  
2. Join a challenge  
3. Complete qualifying action (e.g., schedule pickup)  

**Expected Result:**  
Participation is recorded  
Progress bar or badge updates accordingly  

**Requirement ID:** FR-052  

---

### ✅ TC-075 – Join and view upcoming community events  
**Steps:**  
1. Navigate to “Events”  
2. Click “Join” on an event  

**Expected Result:**  
Event is added to user’s dashboard  
Reminders or countdown timer visible  

**Requirement ID:** FR-052  

## 🗂️ 8.1 Request Management

---

### ✅ TC-076 – View all pickup requests  
**Precondition:** Admin is logged in  
**Steps:**  
1. Navigate to “Admin > Pickup Requests”  

**Expected Result:**  
All user pickup requests are listed with status, date, type  

**Requirement ID:** FR-053  

---

### ✅ TC-077 – Approve a pickup request  
**Precondition:** A request is in "Pending" status  
**Steps:**  
1. Click “Approve” button on a pending request  

**Expected Result:**  
Request status changes to "Confirmed"  

**Requirement ID:** FR-054  

---

### ✅ TC-078 – Reject a pickup request  
**Steps:**  
1. Click “Reject” on a pending request  

**Expected Result:**  
Status changes to "Rejected", with optional rejection note  

**Requirement ID:** FR-054  

---

### ✅ TC-079 – Modify a pickup request  
**Steps:**  
1. Edit waste type, date, or instructions  
2. Save changes  

**Expected Result:**  
Request updates successfully and new values appear in the list  

**Requirement ID:** FR-054  

---

### ✅ TC-080 – Assign pickup date and time  
**Steps:**  
1. Select a request  
2. Set a new pickup date and time  

**Expected Result:**  
Assigned time is reflected on the request and visible to the user  

**Requirement ID:** FR-055  

---

### ✅ TC-081 – Filter and search pickup requests  
**Steps:**  
1. Use filters like date range, status, user email  

**Expected Result:**  
Only matching requests are shown  

**Requirement ID:** FR-056  

---

## 👤 8.2 User Management

---

### ✅ TC-082 – View all registered users  
**Steps:**  
1. Go to “Admin > Users”  

**Expected Result:**  
List of all users with names, emails, roles, and status  

**Requirement ID:** FR-057  

---

### ✅ TC-083 – Change a user’s role  
**Steps:**  
1. Select user  
2. Click “Change Role” and select “Admin” or “User”  

**Expected Result:**  
Role is updated and permission changes take effect  

**Requirement ID:** FR-058  

---

### ✅ TC-084 – Suspend a user account  
**Steps:**  
1. Select user  
2. Click “Suspend”  

**Expected Result:**  
User cannot log in or access system until reactivated  

**Requirement ID:** FR-059  

---

### ✅ TC-085 – Delete a user account  
**Steps:**  
1. Select user  
2. Click “Delete” and confirm  

**Expected Result:**  
User account is removed and cannot be recovered  

**Requirement ID:** FR-059  

---

### ✅ TC-086 – View user activity report  
**Steps:**  
1. Go to a user’s detail view  
2. Open “Activity Report”  

**Expected Result:**  
Shows log of pickups, posts, quizzes, etc.  

**Requirement ID:** FR-060  

---

## 📣 8.3 Content Moderation

---

### ✅ TC-087 – View all community posts and comments  
**Steps:**  
1. Go to “Admin > Community Content”  

**Expected Result:**  
All posts and comments are listed with user info and timestamps  

**Requirement ID:** FR-061  

---

### ✅ TC-088 – Delete inappropriate post or comment  
**Steps:**  
1. Select a flagged post  
2. Click “Delete”  

**Expected Result:**  
Post is removed from public view  

**Requirement ID:** FR-062  

---

### ✅ TC-089 – View content flagged by users  
**Steps:**  
1. Go to “Flagged Content” section  

**Expected Result:**  
All flagged posts with reason and flag count are shown  

**Requirement ID:** FR-063  

---

### ✅ TC-090 – Create and publish announcement  
**Steps:**  
1. Navigate to “Announcements”  
2. Enter message and publish  

**Expected Result:**  
Announcement is shown to all users on dashboard or community feed  

**Requirement ID:** FR-064  



## 🔔 9. Notification System

---

### ✅ TC-091 – Display notification bell with unread count  
**Precondition:** User has at least one unread notification  
**Steps:**  
1. Login as user  
2. Look at the top navigation bar  

**Expected Result:**  
Notification bell icon displays total unread count (e.g., 🔔 3)  

**Requirement ID:** FR-065  

---

### ✅ TC-092 – Show notification for pickup confirmation  
**Precondition:** User schedules a pickup  
**Steps:**  
1. Schedule a new pickup  
2. Wait for system to process confirmation  

**Expected Result:**  
A notification appears with the message like "Pickup confirmed for July 25, 10 AM"  

**Requirement ID:** FR-066  

---

### ✅ TC-093 – Show notification for new blog post  
**Precondition:** Admin publishes a new blog post  
**Steps:**  
1. Login as user  
2. Check notification center  

**Expected Result:**  
Notification appears: "New blog post: '10 Ways to Reduce Plastic Waste'"  

**Requirement ID:** FR-066  

---

### ✅ TC-094 – Show notification for community interaction (likes/comments)  
**Precondition:** Another user likes or comments on your post  
**Steps:**  
1. Create a community post  
2. Another user likes/comments on it  

**Expected Result:**  
Notification says: "Alex liked your post" or "Sami commented: Great tip!"  

**Requirement ID:** FR-066  

---

### ✅ TC-095 – Show notification for achievement unlocked  
**Precondition:** User completes a milestone (e.g., 10 pickups)  
**Steps:**  
1. Trigger an achievement by completing the requirement  

**Expected Result:**  
Notification appears: "🎉 You unlocked the ‘10 Pickups Completed’ badge!"  

**Requirement ID:** FR-066  

---

### ✅ TC-096 – Mark notifications as read  
**Precondition:** User has at least one unread notification  
**Steps:**  
1. Open notification dropdown or panel  
2. Click “Mark as read” on one or all notifications  

**Expected Result:**  
Notification icon count decreases or resets to 0; read state persists on refresh  

**Requirement ID:** FR-067  

---

### ✅ TC-097 – View notification history  
**Steps:**  
1. Click on notification bell  
2. Click “View All” or navigate to `/notifications`  

**Expected Result:**  
List of all past notifications is displayed, including read/unread status and timestamps  

**Requirement ID:** FR-068  

---

## 🧩 GitHub Projects Suggestions  
To integrate into GitHub Projects (Kanban):  
- **Columns:** To Do, In Progress, Passed, Failed  
- **Labels:**  
  - `feature:notifications`  
  - `type:test-case`  
  - `priority:medium`  
  - `ui:dashboard`


# 📱 10. User Interface Test Cases

These test cases are designed for integration into QA workflows, GitHub Projects, or test management tools.

---

## ✅ Test Case Format

| TC ID   | Title                                       | Precondition                             | Test Steps                                                                                 | Expected Result                                                                                  | FR ID     |
|---------|---------------------------------------------|------------------------------------------|--------------------------------------------------------------------------------------------|--------------------------------------------------------------------------------------------------|-----------|

---

## 📱 10.1 Responsive Design

### ✅ TC-098 – Display UI correctly on desktop (1920x1080+)
**Precondition:** User accesses the app on a desktop  
**Steps:**  
1. Open app on a device with 1920x1080 resolution  
**Expected Result:**  
Layout renders correctly with no UI overlap or broken components  
**FR:** FR-069  

---

### ✅ TC-099 – Display UI correctly on tablets (768px to 1024px)
**Steps:**  
1. Resize browser or use tablet emulator  
2. Navigate through multiple pages  
**Expected Result:**  
UI elements adjust gracefully (responsive grids, readable text, no clipping)  
**FR:** FR-069  

---

### ✅ TC-100 – Display UI correctly on mobile devices (320px to 767px)
**Steps:**  
1. Access app using a mobile browser (e.g., Chrome DevTools emulator or real device)  
**Expected Result:**  
Menu collapses into mobile nav, elements stack vertically, text is readable  
**FR:** FR-069  

---

### ✅ TC-101 – Functional parity across screen sizes
**Steps:**  
1. Perform common actions (e.g., login, schedule pickup, view dashboard) on all screen sizes  
**Expected Result:**  
No feature is missing or broken due to screen size  
**FR:** FR-070  

---

## ♿ 10.2 Accessibility

### ✅ TC-102 – UI meets WCAG 2.1 AA contrast and readability
**Steps:**  
1. Inspect UI using tools (axe, Lighthouse)  
2. Check contrast ratios, font sizes, spacing  
**Expected Result:**  
All critical elements pass WCAG 2.1 AA criteria  
**FR:** FR-071  

---

### ✅ TC-103 – Navigate UI using only keyboard
**Steps:**  
1. Use Tab, Enter, Space, and Arrow keys  
2. Attempt to activate all links, buttons, and inputs  
**Expected Result:**  
All interactive elements are reachable and operable via keyboard  
**FR:** FR-072  

---

### ✅ TC-104 – Verify alt text is present for all images
**Steps:**  
1. Inspect all content images in the UI  
2. Check for `alt` attribute in the DOM  
**Expected Result:**  
All non-decorative images include meaningful `alt` text  
**FR:** FR-073  

---

### ✅ TC-105 – Verify screen reader compatibility
**Precondition:** Screen reader software is active (e.g., NVDA, VoiceOver)  
**Steps:**  
1. Navigate through key screens using the screen reader  
2. Observe if labels, landmarks, and headings are properly read  
**Expected Result:**  
Screen reader reads UI logically and clearly  
**FR:** FR-074  

---

## 🧭 10.3 Navigation

### ✅ TC-106 – Display of primary navigation menu
**Steps:**  
1. Access any page  
2. Look for top or side navigation menu  
**Expected Result:**  
Menu is consistently placed and shows key sections (Dashboard, Community, etc.)  
**FR:** FR-075  

---

### ✅ TC-107 – Show breadcrumbs on deep navigation paths
**Steps:**  
1. Go to a nested page (e.g., Dashboard > Analytics > CO₂ Savings)  
**Expected Result:**  
Breadcrumbs are visible (e.g., "Home / Dashboard / Analytics")  
**FR:** FR-076  

---

### ✅ TC-108 – Verify search functionality presence
**Steps:**  
1. Navigate to searchable section (e.g., blog, community feed)  
2. Use search input to query a keyword  
**Expected Result:**  
Relevant results are displayed; no crash or missing feature  
**FR:** FR-077  

---

## 🧩 GitHub Projects (Kanban) Integration

Each test case can be entered as a GitHub Issue or Project Task with the following:

**Labels:**
- `type:test-case`
- `feature:ui`
- `feature:accessibility`
- `feature:responsive`
- `priority:medium`

**Columns:**
- To Do
- In Progress
- Passed
- Failed

**Assignees:**
- QA
- Frontend Dev
- Accessibility Lead





# 🔒 11. Data Management Test Cases

Well-structured and QA-ready test cases for validating data storage, validation, and security. Suitable for GitHub Projects, Issues, or test management tools like TestRail or Zephyr.

---

## ✅ Test Case Format

| TC ID   | Title                             | Precondition                                       | Test Steps                                                                                      | Expected Result                                                                                              | FR ID    |
|---------|-----------------------------------|----------------------------------------------------|--------------------------------------------------------------------------------------------------|----------------------------------------------------------------------------------------------------------------|----------|

---

## 🔒 11.1 Data Persistence

### ✅ TC-109 – Store user data in localStorage  
**Precondition:** User logs in or submits profile data  
**Steps:**  
1. Log in as a user  
2. Open DevTools → Application → localStorage  
**Expected Result:**  
localStorage contains keys for user session, profile, preferences, etc.  
**FR:** FR-078  

---

### ✅ TC-110 – Maintain data across browser sessions  
**Precondition:** User has previously logged in and data is stored  
**Steps:**  
1. Close browser completely  
2. Reopen browser and navigate to app  
**Expected Result:**  
User session or user-specific data persists; user is still logged in or sees their previous state  
**FR:** FR-079  

---

### ✅ TC-111 – Handle localStorage limit gracefully  
**Precondition:** localStorage usage is near browser limits (~5MB)  
**Steps:**  
1. Simulate or fill localStorage with large data  
2. Perform an action that writes to localStorage (e.g., save settings)  
**Expected Result:**  
System gracefully warns user or logs error; no crash or data corruption occurs  
**FR:** FR-080  

---

## ✅ 11.2 Data Validation

### ✅ TC-112 – Validate user input on form submit  
**Precondition:** User accesses a form (e.g., registration, pickup request)  
**Steps:**  
1. Leave required fields blank or enter invalid data  
2. Click submit  
**Expected Result:**  
Form shows appropriate error messages and does not submit  
**FR:** FR-081  

---

### ✅ TC-113 – Prevent SQL Injection attacks  
**Steps:**  
1. Enter SQL strings like `' OR '1'='1` or `DROP TABLE` into input fields  
2. Submit the form  
**Expected Result:**  
Inputs are rejected or sanitized; no data leakage, SQL behavior, or error logs triggered  
**FR:** FR-082  

---

### ✅ TC-114 – Prevent Cross-Site Scripting (XSS)  
**Steps:**  
1. Input `<script>alert("Hacked")</script>` into a comment or bio field  
2. Submit and view it in the app  
**Expected Result:**  
Script is rendered harmless or escaped as text (not executed)  
**FR:** FR-082  

---

### ✅ TC-115 – Sanitize user-generated content  
**Steps:**  
1. Enter special characters or markup like `<b>`, `<img src=...>` into content fields  
2. Submit and view content on another page or profile  
**Expected Result:**  
Dangerous or disallowed HTML is stripped, escaped, or safely rendered  
**FR:** FR-083  

---

## 🧩 GitHub Projects Integration

**Recommended Columns:**  
- To Do  
- In Progress  
- Passed  
- Failed  

**Suggested Labels:**  
- `type:test-case`  
- `feature:data-management`  
- `priority:high` (especially for FR-082, FR-083)  
- `security`  
- `validation`  
- `localstorage`  

**Assignees:** QA Engineer, Security Analyst, Frontend Dev  


# 🚀 12. Performance & Compatibility Test Cases

Detailed and QA-ready test cases for system responsiveness and cross-browser support. Suitable for use in GitHub Projects, test management tools, or Excel/Sheets.

---

## ✅ Test Case Format

| TC ID  | Title                                   | Precondition                                              | Test Steps                                                                                           | Expected Result                                                                                 | FR ID     |
|--------|-----------------------------------------|------------------------------------------------------------|--------------------------------------------------------------------------------------------------------|--------------------------------------------------------------------------------------------------|-----------|

---

## 🚀 12.1 Response Time

### ✅ TC-116 – Page loads within 3 seconds on standard connection  
**Precondition:** User has stable internet (~10 Mbps); browser cache is cleared  
**Steps:**  
1. Open homepage and key feature pages (e.g., Dashboard, Pickup Scheduling)  
2. Use browser DevTools → Performance tab or Lighthouse  
**Expected Result:**  
Full page loads in ≤ 3 seconds  
**FR:** FR-084  

---

### ✅ TC-117 – UI responds to interactions within 1 second  
**Precondition:** User is logged in  
**Steps:**  
1. Click buttons, open modals, toggle menus, submit short forms  
2. Use performance profiler to measure interaction delay  
**Expected Result:**  
Feedback is visible (e.g., animation, state change) within ≤ 1 second  
**FR:** FR-085  

---

### 🧪 Recommended Tools:
- Chrome DevTools → Performance tab  
- Lighthouse (Performance audit)  
- WebPageTest  
- GTMetrix  
- Real-user testing on mid-range devices  

---

## 🧭 12.2 Browser Compatibility

### ✅ TC-118 – Application works on Google Chrome (latest 2 versions)  
**Precondition:** Install Chrome latest and previous version  
**Steps:**  
1. Access all major pages  
2. Perform key actions (login, submit form, schedule pickup)  
**Expected Result:**  
No visual bugs, layout issues, or JS errors  
**FR:** FR-086  

---

### ✅ TC-119 – Application works on Mozilla Firefox (latest 2 versions)  
**Steps:**  
1. Repeat functional and visual testing on Firefox latest and previous  
**Expected Result:**  
All features work without compatibility issues  
**FR:** FR-086  

---

### ✅ TC-120 – Application works on Safari (latest 2 versions)  
**Steps:**  
1. Use Safari on macOS (and iOS optionally)  
2. Check UI rendering, buttons, forms, and navigation  
**Expected Result:**  
Same functionality and visual consistency as on Chrome/Firefox  
**FR:** FR-086  

---

### ✅ TC-121 – Application works on Microsoft Edge (latest 2 versions)  
**Steps:**  
1. Perform smoke test across the app in Edge  
**Expected Result:**  
App behaves identically to Chrome (same engine) with no visual or runtime issues  
**FR:** FR-086  

---

## 🧩 GitHub Projects Integration

**Suggested Labels:**  
- `type:test-case`  
- `feature:performance`  
- `feature:compatibility`  
- `priority:high`  

**Milestones:**  
- `MVP → Cross-browser support`  
- `Beta → Performance tuning`  

**Kanban Columns:**  
- To Do  
- Testing  
- Passed  
- Failed  



# 📋 13. Error Handling & Form Validation Test Cases

Detailed, QA-ready test cases formatted for GitHub Projects, Jira, TestRail, Zephyr, or spreadsheet-based tracking.

---

## ✅ Test Case Format

| TC ID   | Title                                   | Precondition                                                  | Test Steps                                                                                              | Expected Result                                                                                         | FR ID    |
|---------|-----------------------------------------|---------------------------------------------------------------|-----------------------------------------------------------------------------------------------------------|----------------------------------------------------------------------------------------------------------|----------|

---

## 📋 13.1 User-Friendly Errors

### ✅ TC-122 – Display clear, actionable error messages  
**Precondition:** User submits a form with invalid inputs (e.g., empty required field or wrong format)  
**Steps:**  
1. Navigate to the form (e.g., Registration or Pickup Request)  
2. Submit the form with missing or invalid fields (e.g., incorrect email format)  
**Expected Result:**  
Error messages appear (e.g., "Please enter a valid email address") with field-specific highlights  
**FR:** FR-087  

---

### ✅ TC-123 – Provide guidance for common issues  
**Precondition:** Simulate a common user error (e.g., incorrect login credentials)  
**Steps:**  
1. Enter incorrect password 3 times on login  
**Expected Result:**  
Message such as “Forgot your password? Click here to reset” appears with a link to help  
**FR:** FR-088  

---

### ✅ TC-124 – Handle network errors gracefully  
**Precondition:** Disconnect from the internet during an API call  
**Steps:**  
1. Disable network via DevTools or OS  
2. Try to submit a form or load dashboard  
**Expected Result:**  
User sees an appropriate error message (e.g., “Network error: please check your connection”) and the system does not crash  
**FR:** FR-089  

---

## 📝 13.2 Form Validation

### ✅ TC-125 – Real-time validation on form fields  
**Precondition:** Form has at least one required field  
**Steps:**  
1. Begin typing an invalid email, e.g., `user@`  
2. Move to the next field without correcting  
**Expected Result:**  
Error appears immediately without submitting the form, e.g., "Invalid email format"  
**FR:** FR-090  

---

### ✅ TC-126 – Prevent submission with invalid data  
**Precondition:** A required form is filled incorrectly  
**Steps:**  
1. Leave one required field blank  
2. Click “Submit”  
**Expected Result:**  
Form does not submit, and relevant errors are shown  
**FR:** FR-091  

---

### ✅ TC-127 – Highlight validation errors clearly  
**Precondition:** Form with multiple validation rules  
**Steps:**  
1. Enter invalid data in multiple fields  
2. Click “Submit”  
**Expected Result:**  
Errors are visually marked (e.g., red border, tooltips, or under-text) near each affected field  
**FR:** FR-092  

---

## 🧩 GitHub Projects Integration

**Suggested Columns:**  
- To Do  
- In Progress  
- Testing  
- Passed  
- Failed  

**Suggested Labels:**  
- `type:test-case`  
- `feature:error-handling`  
- `priority:high` (for FR-089, FR-091)  
- `ui:forms`, `ux:messages`  

---

## 🔧 Optional Automation Tools

- **Form validation:** Cypress, Playwright  
- **Error message detection:** Selenium assertions  
- **Network simulation:** Chrome DevTools → Network → Offline  



# ✅ Test Case Format

| TC ID   | Title                                      | Precondition                              | Test Steps                                                                                     | Expected Result                                                                                          | Related FR / Rule |
|---------|--------------------------------------------|-------------------------------------------|----------------------------------------------------------------------------------------------|-----------------------------------------------------------------------------------------------------------|-------------------|

---

## 🎯 14.1 Pickup Scheduling Rules

### TC-128 – Allow scheduling pickups up to 30 days in advance
- **Precondition:** User is logged in  
- **Steps:**  
  1. Open Pickup Scheduler  
  2. Attempt to select a date 31 days from today  
- **Expected Result:** System should not allow selection beyond 30 days  
- **Rule:** BR-14.1.1

---

### TC-129 – Disallow scheduling within less than 24 hours
- **Precondition:** User is logged in  
- **Steps:**  
  1. Open Pickup Scheduler  
  2. Try scheduling for the same day or within next 23 hours  
- **Expected Result:** System shows validation error: “Pickup must be scheduled at least 24 hours in advance”  
- **Rule:** BR-14.1.2

---

### TC-130 – Prevent more than 3 pickups per user per week
- **Precondition:** User has already scheduled 3 pickups this week  
- **Steps:**  
  1. Try to schedule a 4th pickup within the same calendar week  
- **Expected Result:** Error: “Maximum 3 pickups allowed per week”  
- **Rule:** BR-14.1.3

---

### TC-131 – Require approval for hazardous waste
- **Precondition:** User selects "Hazardous" waste type  
- **Steps:**  
  1. Fill in pickup form with hazardous waste  
  2. Submit request  
- **Expected Result:** Request enters "Pending Approval" state; user notified of special handling  
- **Rule:** BR-14.1.4

---

## 👥 14.2 User Management Rules

### TC-132 – Email addresses must be unique
- **Precondition:** Existing user email already registered  
- **Steps:**  
  1. Try registering with same email  
- **Expected Result:** Error: “Email already in use”  
- **Rule:** BR-14.2.1

---

### TC-133 – Passwords must meet security requirements
- **Steps:**  
  1. Try registering with weak password (e.g., 12345678)  
- **Expected Result:** Error: “Password must contain at least one uppercase letter, one number, and one special character”  
- **Rule:** BR-14.2.2

---

### TC-134 – Archive inactive accounts after 6 months
- **Precondition:** User hasn’t logged in for 6+ months  
- **Steps:**  
  1. System runs scheduled job  
- **Expected Result:** Account is marked inactive and archived (not deleted)  
- **Rule:** BR-14.2.3

---

### TC-135 – Prevent deletion of admin accounts
- **Precondition:** Logged in as Admin  
- **Steps:**  
  1. Try to delete an admin account from user management panel  
- **Expected Result:** Action denied, message: “Admin accounts cannot be deleted”  
- **Rule:** BR-14.2.4

---

## 📝 14.3 Content Rules

### TC-136 – Block offensive community posts
- **Steps:**  
  1. Attempt to post inappropriate content (test with known flagged words or profanity)  
- **Expected Result:** Post is blocked or flagged for moderation  
- **Rule:** BR-14.3.1

---

### TC-137 – Blog comments require moderation
- **Steps:**  
  1. Submit comment on blog  
  2. Log in as admin/moderator  
- **Expected Result:** Comment is not public until approved  
- **Rule:** BR-14.3.2

---

### TC-138 – Users can report inappropriate content
- **Steps:**  
  1. View a community post  
  2. Click “Report”  
- **Expected Result:** Post is flagged, notification sent to moderators  
- **Rule:** BR-14.3.3

---

### TC-139 – Archive content older than 1 year
- **Precondition:** Community post or blog post is 12+ months old  
- **Steps:**  
  1. Wait for scheduled cleanup job  
- **Expected Result:** Content is moved to "Archived" state and not shown in main feeds  
- **Rule:** BR-14.3.4

---

## 🧩 GitHub Projects Integration

Each test case can be created as a GitHub Issue with:

- **Labels:** `test-case`, `business-rules`, `content`, `scheduling`, `user-management`  
- **Milestone:** `"Business Logic Testing"`  
- **Kanban Columns:** `Backlog`, `In Testing`, `Tested`, `Failed`, `Rework`



# ✅ Test Case Format

| TC ID  | Title                              | Precondition                                                                  | Test Steps                                                                                                   | Expected Result                                                                                      | Related FR |
|--------|------------------------------------|--------------------------------------------------------------------------------|--------------------------------------------------------------------------------------------------------------|-------------------------------------------------------------------------------------------------------|-------------|

## 📞 15.1 Help System

### TC-140 – Display contextual help/tooltips
- **Precondition:** User is logged in and on a form/page with help icons/tooltips enabled  
- **Steps:**  
  1. Hover over or click a help icon (e.g., ❓ or ℹ️) near an input field or button  
- **Expected Result:** Tooltip appears with relevant information or guidance  
- **Related FR:** FR-093

---

### TC-141 – Display FAQ section
- **Precondition:** User has access to the help/support section  
- **Steps:**  
  1. Navigate to Help → FAQ  
- **Expected Result:** FAQ section loads with common questions and answers  
- **Related FR:** FR-094

---

### TC-142 – Display contact information for support
- **Steps:**  
  1. Navigate to Help or Contact Support section  
- **Expected Result:** Email, phone number, or contact form is clearly visible  
- **Related FR:** FR-095

---

## 🛠️ 15.2 System Monitoring

### TC-143 – Log user activity for debugging
- **Precondition:** Admin or developer has access to logs  
- **Steps:**  
  1. Perform typical user actions (e.g., login, schedule pickup, cancel request)  
  2. Check activity log output (via console, server log, or monitoring tool)  
- **Expected Result:** Each user action is logged with timestamp, user ID, and activity type  
- **Related FR:** FR-096

---

### TC-144 – Log and report system errors
- **Precondition:** Trigger an error (e.g., force a 500 internal server error)  
- **Steps:**  
  1. Simulate a failure (e.g., API request to an invalid endpoint)  
  2. Check backend/server log or error monitoring tool  
- **Expected Result:** Error is logged with details: error code, stack trace, user session ID  
- **Related FR:** FR-097

---

## 🧩 GitHub Projects Integration

Each test case can be created as a GitHub Issue with:

- **Labels:** `test-case`, `support`, `monitoring`, `type:manual`  
- **Milestone:** `"Support & Logging Validation"`  
- **Kanban Columns:** `To Do`, `In Testing`, `Verified`, `Re-test`, `Blocked`

---

## 🔧 Optional Automation Suggestions

- **Tooltips and FAQs:** Can be verified with Cypress UI tests  
- **Logging:** Validate with log monitoring tools (e.g., LogRocket, Datadog, or console logs for dev)



