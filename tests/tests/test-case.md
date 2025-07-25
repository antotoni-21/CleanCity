# 🧪 CleanCity: Waste Pickup Scheduler-Test Cases



## 🔐 3.1 User Registration

**TC-001 – Register with valid information**
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

**TC-002 – Register with invalid email format**
-**Steps:** Enter user@ in the email field
-**Expected Result:** "Invalid email format" error is displayed
FR: FR-002

**TC-003 – Register with short password**
- **Steps:**
  1. Enter password less than 8 characters (e.g., Test1)
- **Expected Result:** "Password must be at least 8 characters" error is shown
- **FR:** FR-002

TC-004 – Register with mismatched confirm password
Steps: Password: Test@1234, Confirm password: Test@123
Expected Result: "Passwords do not match" error message
FR: FR-002

TC-005 – Register with full name less than 2 characters
Steps: Enter full name: A
Expected Result: "Full name must be between 2 and 50 characters"
FR: FR-002

TC-006 – Register with invalid phone number
Steps: Phone: abc123
Expected Result: "Invalid phone number"
FR: FR-002

🔑 3.2 User Login
TC-007 – Login with valid credentials
Precondition: User is registered
Steps:
Enter email: user@example.com
Enter password: Test@1234
Click "Login"
Expected Result: User is logged in and redirected to intended page; session saved in localStorage
FR: FR-004, FR-006, FR-007

TC-008 – Login with incorrect password
Steps: Enter valid email, wrong password
Expected Result: "Invalid credentials" message
FR: FR-005

TC-009 – Login with unregistered email
Steps: Email not in system
Expected Result: "Email not found" or generic error
FR: FR-005

TC-010 – Check localStorage on successful login
Steps:
Login successfully
Open browser developer tools
Expected Result: User session token or identifier is present in localStorage
FR: FR-006

TC-011 – Redirect to intended page after login
Steps:
Try accessing /profile while logged out
Login when prompted
Expected Result: Redirected to /profile after login
FR: FR-007

🚪 3.3 User Logout
TC-012 – User logs out successfully
Steps: Click "Logout"
Expected Result: Session is cleared, user redirected to login page
FR: FR-008, FR-009

🛡️ 3.4 Role-Based Access
TC-013 – User role restricted from admin page
Precondition: Logged in as "User"
Steps: Navigate to /admin
Expected Result: Access denied or redirect to a "403 Forbidden" or home page
FR: FR-011

TC-014 – Admin accesses admin-only features
Precondition: Logged in as "Admin"
Steps: Navigate to /admin
Expected Result: Admin dashboard loads successfully
FR: FR-010, FR-011

TC-015 – New user has default role "User"
Steps: Register a new account
Expected Result: Account role is "User" by default (can be checked in API or user panel)
FR: FR-003, FR-010



Below are detailed test cases for your Waste Management System based on the functional requirements FR-012 to FR-022. These follow a clear, actionable format and are suitable for manual testing, automation, or adding to GitHub Projects (as described earlier).


✅ Test Case Table Format


♻️ 4.1 Pickup Scheduling
TC-016 – Schedule pickup with valid information
Precondition: User is logged in
Steps:
Navigate to the pickup scheduling form
Select a date 3 days from today
Select waste type: “Recyclable”
Select quantity: “Medium”
Enter special instructions: “Place bags near garage”
Submit request
Expected Result: Pickup request is successfully submitted and shown in request history
FR: FR-012

TC-017 – Pickup date is in the past
Steps: Enter a date that is today or earlier
Expected Result: Error message: “Pickup date must be at least 24 hours in advance”
FR: FR-013

TC-018 – Pickup date is less than 24 hours away
Steps: Select a date/time 10 hours from now
Expected Result: Error message preventing scheduling
FR: FR-013

TC-019 – Missing required fields (waste type, quantity)
Steps: Leave waste type and quantity blank
Expected Result: Error: “Waste type and quantity are required”
FR: FR-012

TC-020 – Special instructions exceed 200 characters
Steps: Enter a 250-character note in special instructions
Expected Result: Error: “Maximum 200 characters allowed”
FR: FR-012

TC-021 – Address auto-filled from profile
Steps: Open scheduling form
Expected Result: Address field is pre-populated with user’s profile address
FR: FR-012

TC-022 – View available time slots
Steps: Select a valid future date
Expected Result: List of available time slots is displayed
FR: FR-014

TC-023 – Prevent multiple pickups for same date
Precondition: One pickup is already scheduled for the selected date
Steps: Try to book another pickup for the same date
Expected Result: Error: “You already have a pickup scheduled for this date”
FR: FR-015

📋 4.2 Request Management
TC-024 – View request history
Steps: Navigate to “My Requests”
Expected Result: List of past and pending pickup requests is shown with status and details
FR: FR-016

TC-025 – Cancel a pending pickup
Precondition: Pickup request status is “Pending”
Steps: Click “Cancel” on a request
Expected Result: Request status changes to “Cancelled”
FR: FR-017

TC-026 – Try to cancel completed pickup
Precondition: Pickup is already marked as “Completed”
Steps: Attempt to cancel
Expected Result: Action blocked, message: “Only pending pickups can be cancelled”
FR: FR-017

TC-027 – Modify pickup before 24 hours
Precondition: Pickup is scheduled more than 24 hours from now
Steps: Edit quantity and waste type
Expected Result: Update is saved successfully
FR: FR-018

TC-028 – Modify pickup within 24-hour window
Precondition: Pickup is scheduled in less than 24 hours
Steps: Try to edit pickup
Expected Result: Edit option disabled or warning shown
FR: FR-018

TC-029 – Display request status
Steps: View requests in history
Expected Result: Each request shows status: Pending, Confirmed, Completed, or Cancelled
FR: FR-019

🚚 4.3 Request Tracking
TC-030 – Real-time status updates
Precondition: Pickup request is active
Steps: Refresh dashboard or open tracking view
Expected Result: Status updates automatically without full reload
FR: FR-020

TC-031 – Receive notification for status changes
Steps: Schedule a pickup and wait for status to change
Expected Result: User receives in-app or email notification
FR: FR-021

TC-032 – Leave feedback after pickup
Precondition: Pickup status is “Completed”
Steps: Open the completed request and submit feedback (e.g., 4-star rating, comment)
Expected Result: Feedback is saved and associated with the request
FR: FR-022



Here are detailed, high-quality test cases for the Dashboard & Analytics Requirements (FR-023 to FR-030), organized into categories and formatted for use in manual testing, automation, or integration into a GitHub Projects board (as Kanban-style cards).

✅ Test Case Format


📊 5.1 User Dashboard
TC-033 – Display personalized user dashboard
Precondition: User is logged in with pickup history
Steps:
Log in and navigate to /dashboard
Expected Result:
Recent pickups section is visible
Upcoming scheduled pickups are listed
Environmental stats and achievement badges are shown
Quick action buttons (e.g., Schedule Pickup, View History) are displayed
FR: FR-023

TC-034 – Show recent pickup requests
Steps:
Open dashboard
Expected Result:
Last 3–5 completed pickup requests appear under “Recent Activity”
FR: FR-023

TC-035 – Display upcoming scheduled pickups
Precondition: User has future scheduled pickups
Steps:
Open dashboard
Expected Result:
Pickup date/time, type, and status shown in “Upcoming Pickups”
FR: FR-023

TC-036 – Show environmental impact stats
Steps:
View environmental section on dashboard
Expected Result:
Shows accurate metrics: Total waste diverted, CO2 saved, Trees saved
FR: FR-024

TC-037 – Environmental metrics calculation accuracy
Steps:
Compare metrics against backend or database calculations
Expected Result:
Displayed stats correctly match user’s actual pickup totals
FR: FR-024

TC-038 – Display quick action buttons
Steps:
View dashboard buttons
Expected Result:
"Schedule Pickup", "Track Request", "Download Report", etc., are shown and clickable
FR: FR-023

📈 5.2 Analytics & Reports
TC-039 – Display charts and graphs for user data
Steps:
Go to “Analytics” tab
Expected Result:
Charts show: waste type breakdown, pickup frequency, CO2 impact over time
FR: FR-025

TC-040 – Community leaderboard shows impact rankings
Steps:
Open “Community” or “Leaderboard” tab
Expected Result:
List of top users sorted by environmental metrics (e.g., waste diverted)
User’s own rank is highlighted
FR: FR-026

TC-041 – Show monthly and yearly waste trends
Steps:
View analytics filters
Select month/year filter
Expected Result:
Graph updates to reflect selected timeframe
Trends show upward/downward waste activity
FR: FR-027

TC-042 – Export user data to CSV
Steps:
Click "Export" on dashboard or profile
Expected Result:
Download starts for a .csv file with user's pickup history and impact stats
FR: FR-028

TC-043 – Validate exported CSV content
Steps:
Open exported CSV
Expected Result:
Data includes pickup dates, waste types, quantity, impact values
FR: FR-028

🏅 5.3 Gamification
TC-044 – Award badge for first pickup
Precondition: User schedules first pickup
Steps:
Complete first pickup
Open dashboard
Expected Result:
"First Pickup" badge is awarded and displayed
FR: FR-029

TC-045 – Award badge for 10 completed pickups
Precondition: User completes 10 pickups
Steps:
Open dashboard
Expected Result:
"10 Pickups Completed" badge is visible
FR: FR-029

TC-046 – Award badge for perfect recycling score
Precondition: User has multiple pickups marked as “perfect recycling”
Steps:
Review badges on dashboard
Expected Result:
"Perfect Recycler" badge is awarded
FR: FR-029

TC-047 – Award badge for community contribution
Precondition: User engages with community features (e.g., referrals, posts)
Steps:
Use community features
Return to dashboard
Expected Result:
"Community Contributor" badge is shown
FR: FR-029

TC-048 – Track and display user points and levels
Steps:
View profile or dashboard gamification section
Expected Result:
Total points and level are displayed
Activity log shows point history
FR: FR-030

TC-049 – Level up when threshold reached
Precondition: User reaches level-up point threshold
Steps:
Complete an action that pushes points past the threshold
Expected Result:
User levels up
Notification or animation shown
FR: FR-030


Here are well-structured test cases based on your Content Management Requirements (Blog System, Awareness Section, Community Feed – FR-036 to FR-044). These are ready to be added to your GitHub Projects Kanban board or exported to Issues.

✅ Test Case Format
| TC ID | Title | Precondition | Steps | Expected Result | FR ID |

📝 6.1 Blog System
TC-050 – Display list of blog articles
Precondition: At least one blog post exists
Steps:
Navigate to the “Blog” page
Expected Result: Blog posts are displayed with titles, preview text, and links
FR: General

TC-051 – Read a full blog article
Steps:
Click on a blog post from the list
Expected Result: Full content of the blog article is displayed
FR: General

TC-052 – Like or bookmark a blog post (if applicable)
Steps:
Open a blog post
Click "Like" or "Bookmark" (if implemented)
Expected Result: Action is recorded and UI updates accordingly
FR: "Users should be able to interact with blog content"

TC-053 – Admin can create, edit, and delete blog posts
Precondition: Admin user logged in
Steps:
Navigate to blog admin panel
Create a post with title, body, tags
Edit it
Delete it
Expected Result: CRUD operations complete successfully
FR: "Users/admins should manage blog posts"

TC-054 – Blog supports categories and tags
Steps:
View blog post details or filter list by category/tag
Expected Result: Posts are grouped or filterable by categories or tags
FR: "Blog may support categories or tags"

🌱 6.2 Awareness Section
TC-055 – Eco tips rotate every 5 seconds
Steps:
Go to Awareness section
Observe tip content
Expected Result: A new eco tip appears every 5 seconds without page refresh
FR: FR-036

TC-056 – View environmental quizzes
Steps:
Click on "Take Quiz" in Awareness section
Expected Result: Quiz page loads with question and answer options
FR: FR-037

TC-057 – Submit quiz and view score
Steps:
Answer all quiz questions
Submit the quiz
Expected Result: Final score is shown along with correct answers and explanations
FR: FR-038

TC-058 – Track quiz score in user history
Precondition: User is logged in and has taken quizzes
Steps:
Go to profile or quiz history
Expected Result: Previous quiz attempts and scores are displayed
FR: FR-038

TC-059 – Display infographics with environmental statistics
Steps:
Open the Awareness section
Expected Result: Charts/graphics showing recycling rates, CO₂ impact, etc., are displayed
FR: FR-039

TC-060 – Action buttons in Awareness section work
Steps:
Click buttons like “Learn More”, “Join Campaign”, or “Schedule Pickup”
Expected Result: Navigates to the correct feature or section
FR: FR-040

👥 6.3 Community Feed
TC-061 – User creates a community post
Precondition: User is logged in
Steps:
Go to Community section
Click “New Post”
Enter text and submit
Expected Result: Post is displayed at the top of the feed
FR: FR-041

TC-062 – User likes and comments on post
Steps:
Open a community post
Click “Like” and leave a comment
Expected Result: Like counter increases, comment appears under post
FR: FR-042

TC-063 – Posts display in chronological order
Steps:
View community feed
Expected Result: Newest posts appear first
FR: FR-043

TC-064 – User shares eco tips or experiences
Steps:
Create a post with eco tip or experience story
Expected Result: Post is added to feed and visible to community
FR: FR-044



Here are clear, structured, and actionable test cases for your Community Features Requirements (User Profiles & Social Features — FR-045 to FR-052). These are ideal for:
Manual QA testing
Automation scripts
Creating GitHub Issues or Kanban cards for test tracking

✅ Test Case Format
| TC ID | Title | Precondition | Test Steps | Expected Result | FR ID |

👥 7.1 User Profiles

TC-065 – View user profile
Precondition: User is logged in
Steps:
Navigate to /profile
Expected Result:
Profile page loads with name, bio, photo, statistics, and edit button
FR: FR-045

TC-066 – Edit user profile information
Steps:
Click "Edit Profile"
Modify name, phone, or bio
Save changes
Expected Result: Changes are saved and reflected immediately
FR: FR-045

TC-067 – Upload or change profile picture
Steps:
Click on profile picture
Upload new image
Save
Expected Result: Profile image updates successfully
FR: FR-047

TC-068 – Display user activity history
Precondition: User has scheduled pickups, taken quizzes, or made posts
Steps:
View the "Activity" tab on profile
Expected Result: List of past actions like pickups, posts, quiz results shown chronologically
FR: FR-046

TC-069 – Display user achievements and badges
Steps:
Open profile page
Scroll to “Achievements” section
Expected Result: Badge icons and milestone titles are visible
FR: FR-046

TC-070 – Display environmental impact stats
Steps:
Visit the profile dashboard or statistics tab
Expected Result:
Stats such as total waste recycled, CO2 saved, trees saved are displayed
FR: FR-048

🔗 7.2 Social Features

TC-071 – Follow another user
Precondition: Multiple users exist
Steps:
Visit another user's profile
Click "Follow"
Expected Result: Followed user is added to the following list, and button changes to “Unfollow”
FR: FR-049

TC-072 – View news feed of followed users
Steps:
Navigate to “News Feed” section
Expected Result: Shows activity of followed users (e.g., new posts, achievements, events joined)
FR: FR-050

TC-073 – Share achievement to community feed
Precondition: User unlocks a badge or milestone
Steps:
View achievement popup
Click “Share to Community”
Expected Result: A post appears in the community feed with badge and user comment (if any)
FR: FR-051

TC-074 – Participate in community challenges
Precondition: A challenge is active (e.g., “Recycle 10 kg in July”)
Steps:
Navigate to “Challenges”
Join a challenge
Complete qualifying action (e.g., schedule pickup)
Expected Result:
Participation is recorded
Progress bar or badge updates accordingly
FR: FR-052

TC-075 – Join and view upcoming community events
Steps:
Navigate to “Events”
Click “Join” on an event
Expected Result:
Event is added to user’s dashboard
Reminders or countdown timer visible
FR: FR-052

🧩 Optional: Mapping These to GitHub Projects
You can use these as GitHub Issues or Project Cards with:
Labels: feature:profile, feature:social, priority:high, type:test-case
Status columns: To Do, In Progress, In Review, Passed, Failed
Assignees: Your testers or developers



Here are detailed, testable test cases for the Administrative Functions Requirements (⚙️ FR-053 to FR-064), covering:
Request Management
User Management
Content Moderation
These are formatted to be easily used in GitHub Projects (Kanban) or turned into GitHub Issues.

✅ Test Case Format
| TC ID | Title | Precondition | Test Steps | Expected Result | FR ID |

🗂️ 8.1 Request Management

TC-076 – View all pickup requests
Precondition: Admin is logged in
Steps:
Navigate to “Admin > Pickup Requests”
Expected Result: All user pickup requests are listed with status, date, type
FR: FR-053

TC-077 – Approve a pickup request
Precondition: A request is in "Pending" status
Steps:
Click “Approve” button on a pending request
Expected Result: Request status changes to "Confirmed"
FR: FR-054

TC-078 – Reject a pickup request
Steps:
Click “Reject” on a pending request
Expected Result: Status changes to "Rejected", with optional rejection note
FR: FR-054

TC-079 – Modify a pickup request
Steps:
Edit waste type, date, or instructions
Save changes
Expected Result: Request updates successfully and new values appear in the list
FR: FR-054

TC-080 – Assign pickup date and time
Steps:
Select a request
Set a new pickup date and time
Expected Result: Assigned time is reflected on the request and visible to the user
FR: FR-055

TC-081 – Filter and search pickup requests
Steps:
Use filters like date range, status, user email
Expected Result: Only matching requests are shown
FR: FR-056

👤 8.2 User Management

TC-082 – View all registered users
Steps:
Go to “Admin > Users”
Expected Result: List of all users with names, emails, roles, and status
FR: FR-057

TC-083 – Change a user’s role
Steps:
Select user
Click “Change Role” and select “Admin” or “User”
Expected Result: Role is updated and permission changes take effect
FR: FR-058

TC-084 – Suspend a user account
Steps:
Select user
Click “Suspend”
Expected Result: User cannot log in or access system until reactivated
FR: FR-059

TC-085 – Delete a user account
Steps:
Select user
Click “Delete” and confirm
Expected Result: User account is removed and cannot be recovered
FR: FR-059

TC-086 – View user activity report
Steps:
Go to a user’s detail view
Open “Activity Report”
Expected Result: Shows log of pickups, posts, quizzes, etc.
FR: FR-060

📣 8.3 Content Moderation

TC-087 – View all community posts and comments
Steps:
Go to “Admin > Community Content”
Expected Result: All posts and comments are listed with user info and timestamps
FR: FR-061

TC-088 – Delete inappropriate post or comment
Steps:
Select a flagged post
Click “Delete”
Expected Result: Post is removed from public view
FR: FR-062

TC-089 – View content flagged by users
Steps:
Go to “Flagged Content” section
Expected Result: All flagged posts with reason and flag count are shown
FR: FR-063

TC-090 – Create and publish announcement
Steps:
Navigate to “Announcements”
Enter message and publish
Expected Result: Announcement is shown to all users on dashboard or community feed
FR: FR-064

🧩 GitHub Projects Integration
You can use these as cards with:
Labels:
type:test-case, module:admin, feature:request-mgmt, priority:high
Kanban columns:
To Do, In Progress, In Review, Passed, Failed
Assignees:
QA, Dev, Product roles



Here are detailed test cases for your Notification System Requirements (🔔 FR-065 to FR-068), written to fit cleanly into GitHub Projects, GitHub Issues, or any QA test management tool. These test cases cover:
Notification bell display
Event-driven notifications
Read/unread functionality
Notification history access

✅ Test Case Format
| TC ID | Title | Precondition | Test Steps | Expected Result | FR ID |

🔔 9. Notification System

TC-091 – Display notification bell with unread count
Precondition: User has at least one unread notification
Steps:
Login as user
Look at the top navigation bar
Expected Result: Notification bell icon displays total unread count (e.g., 🔔 3)
FR: FR-065

TC-092 – Show notification for pickup confirmation
Precondition: User schedules a pickup
Steps:
Schedule a new pickup
Wait for system to process confirmation
Expected Result: A notification appears with the message like "Pickup confirmed for July 25, 10 AM"
FR: FR-066

TC-093 – Show notification for new blog post
Precondition: Admin publishes a new blog post
Steps:
Login as user
Check notification center
Expected Result: Notification appears: "New blog post: '10 Ways to Reduce Plastic Waste'"
FR: FR-066

TC-094 – Show notification for community interaction (likes/comments)
Precondition: Another user likes or comments on your post
Steps:
Create a community post
Another user likes/comments on it
Expected Result: Notification says: "Alex liked your post" or "Sami commented: Great tip!"
FR: FR-066

TC-095 – Show notification for achievement unlocked
Precondition: User completes a milestone (e.g., 10 pickups)
Steps:
Trigger an achievement by completing the requirement
Expected Result: Notification appears: "🎉 You unlocked the ‘10 Pickups Completed’ badge!"
FR: FR-066

TC-096 – Mark notifications as read
Precondition: User has at least one unread notification
Steps:
Open notification dropdown or panel
Click “Mark as read” on one or all notifications
Expected Result: Notification icon count decreases or resets to 0; read state persists on refresh
FR: FR-067

TC-097 – View notification history
Steps:
Click on notification bell
Click “View All” or navigate to /notifications
Expected Result: List of all past notifications is displayed, including read/unread status and timestamps
FR: FR-068

🧩 GitHub Projects Suggestions
To integrate into GitHub Projects (Kanban):
Columns: To Do, In Progress, Passed, Failed
Labels:
feature:notifications
type:test-case
priority:medium
ui:dashboard


Here are detailed, professional-grade test cases for your User Interface Requirements (📱 FR-069 to FR-077), designed for integration into a QA process, GitHub Projects, or issue tracking systems.

✅ Test Case Format
| TC ID | Title | Precondition | Test Steps | Expected Result | FR ID |

📱 10.1 Responsive Design

TC-098 – Display UI correctly on desktop (1920x1080+)
Precondition: User accesses the app on a desktop
Steps:
Open app on a device with 1920x1080 resolution
Expected Result: Layout renders correctly with no UI overlap or broken components
FR: FR-069

TC-099 – Display UI correctly on tablets (768px to 1024px)
Steps:
Resize browser or use tablet emulator
Navigate through multiple pages
Expected Result: UI elements adjust gracefully (responsive grids, readable text, no clipping)
FR: FR-069

TC-100 – Display UI correctly on mobile devices (320px to 767px)
Steps:
Access app using a mobile browser (e.g., Chrome DevTools emulator or real device)
Expected Result: Menu collapses into mobile nav, elements stack vertically, text is readable
FR: FR-069

TC-101 – Functional parity across screen sizes
Steps:
Perform common actions (e.g., login, schedule pickup, view dashboard) on all screen sizes
Expected Result: No feature is missing or broken due to screen size
FR: FR-070

♿ 10.2 Accessibility

TC-102 – UI meets WCAG 2.1 AA contrast and readability
Steps:
Inspect UI elements using accessibility tools (e.g., axe, Lighthouse)
Check contrast ratios, font sizes, element spacing
Expected Result: All critical elements pass WCAG 2.1 AA criteria
FR: FR-071

TC-103 – Navigate UI using only keyboard
Steps:
Use Tab, Enter, Space, and Arrow keys to navigate pages
Attempt to activate links, buttons, and inputs
Expected Result: All interactive elements are reachable and operable via keyboard
FR: FR-072

TC-104 – Verify alt text is present for all images
Steps:
Inspect all content images in the UI
Check for alt attribute in the DOM
Expected Result: All non-decorative images include meaningful alt text
FR: FR-073

TC-105 – Verify screen reader compatibility
Precondition: Screen reader software is active (e.g., NVDA, VoiceOver)
Steps:
Navigate through key screens using the screen reader
Observe if labels, landmarks, and headings are properly read
Expected Result: Screen reader reads UI logically and clearly
FR: FR-074

🧭 10.3 Navigation

TC-106 – Display of primary navigation menu
Steps:
Access any page
Look for top or side navigation menu
Expected Result: Menu is consistently placed and shows key sections (Dashboard, Community, etc.)
FR: FR-075

TC-107 – Show breadcrumbs on deep navigation paths
Steps:
Go to a nested page (e.g., Dashboard > Analytics > CO₂ Savings)
Expected Result: Breadcrumbs are visible (e.g., "Home / Dashboard / Analytics")
FR: FR-076

TC-108 – Verify search functionality presence
Steps:
Navigate to searchable section (e.g., blog, community feed)
Use search input to query a keyword
Expected Result: Relevant results are displayed; no crash or missing feature
FR: FR-077

🧩 GitHub Projects (Kanban) Integration
Each test case can be entered as a GitHub Issue or Project Task with:
Labels:
type:test-case
feature:ui, feature:accessibility, feature:responsive
priority:medium
Project columns: To Do, In Progress, Passed, Failed
Assignees: QA, Frontend Dev, Accessibility Lead



Here are complete, well-structured test cases for your 🔒 Data Management Requirements (FR-078 to FR-083), formatted for QA workflows and ready to be integrated into GitHub Projects or any test management system.

✅ Test Case Format
| TC ID | Title | Precondition | Test Steps | Expected Result | FR ID |

🔒 11.1 Data Persistence

TC-109 – Store user data in localStorage
Precondition: User logs in or submits profile data
Steps:
Log in as a user
Open DevTools > Application > localStorage
Expected Result: localStorage contains keys for user session, profile, preferences, etc.
FR: FR-078

TC-110 – Maintain data across browser sessions
Precondition: User has previously logged in and data is stored
Steps:
Close browser completely
Reopen browser and navigate to app
Expected Result: User session or user-specific data persists; user is still logged in or sees their previous state
FR: FR-079

TC-111 – Handle localStorage limit gracefully
Precondition: localStorage usage is near browser limits (~5MB)
Steps:
Simulate or fill localStorage with large data
Perform an action that writes to localStorage (e.g., save settings)
Expected Result: System gracefully warns user or logs error, no data corruption or crash
FR: FR-080

✅ 11.2 Data Validation

TC-112 – Validate user input on form submit
Precondition: User accesses a form (e.g., registration, pickup request)
Steps:
Leave required fields blank or enter invalid data
Click submit
Expected Result: Form shows appropriate error messages and does not submit
FR: FR-081

TC-113 – Prevent SQL Injection attacks
Steps:
Enter SQL strings like ' OR '1'='1 or DROP TABLE into input fields
Submit the form
Expected Result: Inputs are rejected or sanitized; no data leakage, error logs, or SQL behavior is triggered
FR: FR-082

TC-114 – Prevent Cross-Site Scripting (XSS)
Steps:
Input malicious script: <script>alert("Hacked")</script> into a comment or bio field
Submit and view it in the app
Expected Result: Script is rendered harmless or escaped as text (not executed)
FR: FR-082

TC-115 – Sanitize user-generated content
Steps:
Enter special characters or markup (<b>, <img src=...>) into content submission fields
Submit and view content on another page or profile
Expected Result: Dangerous or non-allowed HTML is stripped or converted safely
FR: FR-083

🧩 GitHub Projects Integration
Each test case can be added as a GitHub Issue with:
Labels:
type:test-case
feature:data-management
priority:high (especially for FR-082/FR-083)
security, validation, localstorage
Status columns: To Do, In Progress, Passed, Failed
Assignees: QA Engineer, Security Analyst, Frontend Dev

Here are comprehensive and actionable test cases for your 🚀 Performance Requirements (FR-084 to FR-086), designed for manual QA, automation tools (like Lighthouse or Puppeteer), and GitHub Projects Kanban workflows.

✅ Test Case Format
| TC ID | Title | Precondition | Test Steps | Expected Result | FR ID |

🚀 12.1 Response Time

TC-116 – Page loads within 3 seconds on standard connection
Precondition: User has stable internet (~10 Mbps); browser cache is cleared
Steps:
Open homepage and key feature pages (e.g., Dashboard, Pickup Scheduling)
Use browser DevTools → Performance tab or Lighthouse
Expected Result: Full page loads in ≤ 3 seconds
FR: FR-084

TC-117 – UI responds to interactions within 1 second
Precondition: User is logged in
Steps:
Click buttons, open modals, toggle menus, submit short forms
Use performance profiler to measure interaction delay
Expected Result: Feedback is visible (e.g., animation, state change) within ≤ 1 second
FR: FR-085

🧪 Recommended Tools:
Chrome DevTools → Performance tab
Lighthouse (audit → performance)
WebPageTest
GTMetrix
Real-user testing on mid-range hardware

🧭 12.2 Browser Compatibility

TC-118 – Application works on Google Chrome (latest 2 versions)
Precondition: Install Chrome latest and previous version
Steps:
Access all major pages and perform typical actions (login, submit form, schedule pickup)
Expected Result: No visual bugs, layout issues, or JS errors
FR: FR-086

TC-119 – Application works on Mozilla Firefox (latest 2 versions)
Steps:
Repeat functional and visual testing on Firefox latest and previous
Expected Result: All features work without compatibility issues
FR: FR-086

TC-120 – Application works on Safari (latest 2 versions)
Steps:
Use Safari on macOS (and iOS optionally)
Check UI rendering, buttons, forms, and navigation
Expected Result: Same functionality and visual consistency as on Chrome/Firefox
FR: FR-086

TC-121 – Application works on Microsoft Edge (latest 2 versions)
Steps:
Perform smoke test across the app in Edge
Expected Result: App behaves identically to Chrome (same engine) with no visual or runtime issues
FR: FR-086

🧩 GitHub Projects Integration
Each test case can be logged in GitHub as an Issue or Task with:
Labels:
type:test-case
feature:performance, feature:compatibility
priority:high
Milestones:
MVP → Cross-browser support
Beta → Performance tuning
Kanban Columns:
To Do, Testing, Passed, Failed



Here are detailed and QA-ready test cases for your 📋 Error Handling Requirements (FR-087 to FR-092), formatted for use in GitHub Projects, GitHub Issues, spreadsheets, or test management tools like TestRail, Zephyr, or Xray.

✅ Test Case Format
| TC ID | Title | Precondition | Test Steps | Expected Result | FR ID |

📋 13.1 User-Friendly Errors

TC-122 – Display clear, actionable error messages
Precondition: User submits a form with invalid inputs (e.g., empty required field or wrong format)
Steps:
Navigate to the form (e.g., Registration or Pickup Request)
Submit the form with missing or invalid fields (e.g., incorrect email format)
Expected Result: Error messages appear (e.g., "Please enter a valid email address") with field-specific highlights
FR: FR-087

TC-123 – Provide guidance for common issues
Precondition: Simulate a common user error (e.g., incorrect login credentials)
Steps:
Enter incorrect password 3 times on login
Expected Result: Message such as “Forgot your password? Click here to reset” appears with a link to help
FR: FR-088

TC-124 – Handle network errors gracefully
Precondition: Disconnect from the internet during an API call
Steps:
Disable network via DevTools or OS
Try to submit a form or load dashboard
Expected Result: User sees an appropriate error message (e.g., “Network error: please check your connection”) and the system does not crash
FR: FR-089

📝 13.2 Form Validation

TC-125 – Real-time validation on form fields
Precondition: Form has at least one required field
Steps:
Begin typing an invalid email, e.g., user@
Move to the next field without correcting
Expected Result: Error appears immediately without submitting the form, e.g., "Invalid email format"
FR: FR-090

TC-126 – Prevent submission with invalid data
Precondition: A required form is filled incorrectly
Steps:
Leave one required field blank
Click “Submit”
Expected Result: Form does not submit, and relevant errors are shown
FR: FR-091

TC-127 – Highlight validation errors clearly
Precondition: Form with multiple validation rules
Steps:
Enter invalid data in multiple fields
Click “Submit”
Expected Result: Errors are visually marked (e.g., red border, tooltips, or under-text) near each affected field
FR: FR-092

🧩 GitHub Projects Integration
You can create a Kanban workflow like this:
Columns: To Do, In Progress, Testing, Passed, Failed
Labels:
type:test-case
feature:error-handling
priority:high (for FR-089, FR-091)
ui:forms, ux:messages

🔧 Optional Automation Tools
Form validation: Cypress, Playwright
Error message detection: Selenium assertions
Network simulation: Chrome DevTools → Network → Offline



Here are detailed test cases for your 🎯 Business Rules Requirements (Section 14), written in a QA-friendly format and ready to plug into GitHub Projects, a spreadsheet, or any test management system.

✅ Format
| TC ID | Title | Precondition | Test Steps | Expected Result | Related FR / Rule |

🎯 14.1 Pickup Scheduling Rules

TC-128 – Allow scheduling pickups up to 30 days in advance
Precondition: User is logged in
Steps:
Open Pickup Scheduler
Attempt to select a date 31 days from today
Expected Result: System should not allow selection beyond 30 days
Rule: BR-14.1.1

TC-129 – Disallow scheduling within less than 24 hours
Precondition: User is logged in
Steps:
Open Pickup Scheduler
Try scheduling for the same day or within next 23 hours
Expected Result: System shows validation error: “Pickup must be scheduled at least 24 hours in advance”
Rule: BR-14.1.2

TC-130 – Prevent more than 3 pickups per user per week
Precondition: User has already scheduled 3 pickups this week
Steps:
Try to schedule a 4th pickup within the same calendar week
Expected Result: Error: “Maximum 3 pickups allowed per week”
Rule: BR-14.1.3

TC-131 – Require approval for hazardous waste
Precondition: User selects "Hazardous" waste type
Steps:
Fill in pickup form with hazardous waste
Submit request
Expected Result: Request enters "Pending Approval" state; user notified of special handling
Rule: BR-14.1.4

👥 14.2 User Management Rules

TC-132 – Email addresses must be unique
Precondition: Existing user email already registered
Steps:
Try registering with same email
Expected Result: Error: “Email already in use”
Rule: BR-14.2.1

TC-133 – Passwords must meet security requirements
Steps:
Try registering with weak password (e.g., 12345678)
Expected Result: Error: “Password must contain at least one uppercase letter, one number, and one special character”
Rule: BR-14.2.2

TC-134 – Archive inactive accounts after 6 months
Precondition: User hasn’t logged in for 6+ months
Steps:
System runs scheduled job
Expected Result: Account is marked inactive and archived (not deleted)
Rule: BR-14.2.3

TC-135 – Prevent deletion of admin accounts
Precondition: Logged in as Admin
Steps:
Try to delete an admin account from user management panel
Expected Result: Action denied, message: “Admin accounts cannot be deleted”
Rule: BR-14.2.4

📝 14.3 Content Rules

TC-136 – Block offensive community posts
Steps:
Attempt to post inappropriate content (test with known flagged words or profanity)
Expected Result: Post is blocked or flagged for moderation
Rule: BR-14.3.1

TC-137 – Blog comments require moderation
Steps:
Submit comment on blog
Log in as admin/moderator
Expected Result: Comment is not public until approved
Rule: BR-14.3.2

TC-138 – Users can report inappropriate content
Steps:
View a community post
Click “Report”
Expected Result: Post is flagged, notification sent to moderators
Rule: BR-14.3.3

TC-139 – Archive content older than 1 year
Precondition: Community post or blog post is 12+ months old
Steps:
Wait for scheduled cleanup job
Expected Result: Content is moved to "Archived" state and not shown in main feeds
Rule: BR-14.3.4

🧩 GitHub Projects Integration
Each test case can be created as a GitHub Issue with:
Labels: test-case, business-rules, content, scheduling, user-management
Milestone: "Business Logic Testing"
Kanban Columns: Backlog, In Testing, Tested, Failed, Rework



Here are detailed test cases for the 📞 15. Support and Maintenance Requirements (FR-093 to FR-097), designed for QA teams and formatted for GitHub Projects, spreadsheets, or test case management tools.

✅ Format
| TC ID | Title | Precondition | Test Steps | Expected Result | Related FR |

📞 15.1 Help System

TC-140 – Display contextual help/tooltips
Precondition: User is logged in and on a form/page with help icons/tooltips enabled
Steps:
Hover over or click a help icon (e.g., ❓ or ℹ️) near an input field or button
Expected Result: Tooltip appears with relevant information or guidance
FR: FR-093

TC-141 – Display FAQ section
Precondition: User has access to the help/support section
Steps:
Navigate to Help → FAQ
Expected Result: FAQ section loads with common questions and answers
FR: FR-094

TC-142 – Display contact information for support
Steps:
Navigate to Help or Contact Support section
Expected Result: Email, phone number, or contact form is clearly visible
FR: FR-095

🛠️ 15.2 System Monitoring

TC-143 – Log user activity for debugging
Precondition: Admin or developer has access to logs
Steps:
Perform typical user actions (e.g., login, schedule pickup, cancel request)
Check activity log output (via console, server log, or monitoring tool)
Expected Result: Each user action is logged with timestamp, user ID, and activity type
FR: FR-096

TC-144 – Log and report system errors
Precondition: Trigger an error (e.g., force a 500 internal server error)
Steps:
Simulate a failure (e.g., API request to an invalid endpoint)
Check backend/server log or error monitoring tool
Expected Result: Error is logged with details: error code, stack trace, user session ID
FR: FR-097

🧩 GitHub Projects Integration
You can create GitHub Issues for each test case with:
Labels: test-case, support, monitoring, type:manual
Milestone: “Support & Logging Validation”
Kanban Columns: To Do, In Testing, Verified, Re-test, Blocked

🔧 Optional Automation Suggestions
Tooltips and FAQs: Can be verified with Cypress UI tests
Logging: Validate with log monitoring tools (e.g., LogRocket, Datadog, or console logs for dev)


