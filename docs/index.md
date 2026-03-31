# CodeZero System Features - Product Requirements Document

## Document Overview

This PRD outlines all system features for the CodeZero platform, organized by user role (Student, Teacher, Admin, Public). Each feature is detailed with user stories, acceptance criteria, and implementation remarks.

**Technical conventions (for implementation):**

- **Rich text:** Long-form or descriptive text fields (e.g. course description, teacher bio/qualifications, project description, submission feedback, promotional text, learning objectives, syllabus) **use a rich text editor** so users can format content (bold, headings, lists, links). Store sanitized HTML in the existing `TEXT` columns. See `.cursor/rules/tech-stack.mdc` and `frontend.mdc` for the shared TipTap-based `RichTextEditor` and sanitization rules.

---

## Table of Contents

1. [Student Portal](#student-portal)
2. [Teacher Portal](#teacher-portal)
3. [Admin Dashboard](#admin-dashboard)
4. [Public Site](#public-site)
5. [Cross-Functional Features](#cross-functional-features)

---

## STUDENT PORTAL

### Dashboard

#### Overview

**Section:** Dashboard > Overview

##### 1. View Profile & Stats

- **Feature:** Profile and progress summary display
- **User Story:** As a Student, I want to view my profile and progress summary, so that I can see my status instantly.
- **Acceptance Criteria:**
  - Display student name, avatar, and basic information
  - Show current progress metrics (e.g., completed lessons, active courses)
  - Display overall learning stats on first load
- **Implementation Notes:** Quick snapshot of student's current standing

##### 2. Classes Leaderboard

- **Feature:** Class-specific leaderboard rankings
- **User Story:** As a Student, I want to see the leaderboard rankings specifically for my class, so that I can compare my progress with my classmates.
- **Acceptance Criteria:**
  - Display ranked list of classmates by performance metric
  - Show current student's rank and position
  - Include student name, score/points, and achievement badges
  - Filter or sort by different metrics if applicable
- **Implementation Notes:** Gamification element to encourage engagement

##### 3. Current Lessons

- **Feature:** Live lesson access with join functionality
- **User Story:** As a Student, I want to see a list of my lessons happening now with a "Join" link, so that I can enter the class immediately.
- **Acceptance Criteria:**
  - Display lessons currently in progress
  - Show lesson name, teacher name, and start time
  - Include prominent "Join" button/link for each active lesson
  - Auto-refresh or real-time update of lesson status
- **Implementation Notes:** Critical for seamless class entry; should be the first action visible

##### 4. Notification Feed

- **Feature:** Real-time notification center
- **User Story:** As a Student, I want to see notifications for recent grades or teacher messages, so that I don't miss updates.
- **Acceptance Criteria:**
  - Display notifications for: grades posted, feedback received, teacher messages, assignment reminders
  - Show timestamp and notification sender
  - Allow marking notifications as read/unread
  - Provide notification history or archive
  - Badge/indicator showing unread count
- **Implementation Notes:** Reduce email overload; keep students informed via in-app notifications

---

### My Classes

#### Class List

**Section:** My Classes > Class List

##### 5. Class List with Payment Verification

- **Feature:** Scheduled classes with payment status badge
- **User Story:** As a Student, I want to see a list of my scheduled classes with time and date. I want to see a "Payment Verified" badge on my class card, so that I know my booking is confirmed and safe.
- **Acceptance Criteria:**
  - Display all enrolled classes in a card or list view
  - Show: class name, schedule (day/time), teacher name
  - Display "Payment Verified" badge for paid classes
  - Show "Pending" or "Trial" status for unpaid/trial classes
  - Sort by upcoming date/time
  - Click to view class details or schedule information
- **Implementation Notes:** Trust and transparency; payment verification is crucial for students

#### Schedule

**Section:** My Classes > Schedule

##### 6. Join Class & Upload Activity

- **Feature:** Class participation and post-class activity submission
- **User Story:** As a Student, I want to join valid lessons and upload my activity/video after class, so that I can complete the session.
- **Acceptance Criteria:**
  - Clickable "Join" button links to lesson meeting
  - After class ends, provide upload form for activity/project files
  - Support video uploads (recorded during or after class)
  - Allow multiple file types (PDF, document, video, image)
  - Show submission confirmation and receipt
  - Display upload deadline if applicable
- **Implementation Notes:**
  - After class completion, students upload activity/project during learning session
  - Students upload/submit via link provided
  - Teacher will upload video after class finishes (recorded by teacher)
  - Track submission timestamps for grading

##### 7. Auto-Attendance

- **Feature:** Automatic attendance marking upon class join
- **User Story:** As a Student, I want my status to automatically change to "Present" the moment I click the "Join Class" button, so that I get credit for attending without needing to manually sign in.
- **Acceptance Criteria:**
  - Attendance status updates immediately to "Present" on "Join" button click
  - Record timestamp of attendance
  - No manual sign-in form required
  - Show attendance confirmation message
  - Display attendance history in student profile/dashboard
- **Implementation Notes:** Streamline class entry; remove friction from attendance process

---

### Projects

#### My Projects

**Section:** Projects > My Projects

##### 8. Project List & Submit

- **Feature:** View and submit projects/assignments
- **User Story:** As a Student, I want to view new projects from the teacher and submit my work via link, so that I can complete the assignment.
- **Acceptance Criteria:**
  - Display list of active projects assigned by teacher
  - Show project title, description, and due date
  - Include "Submit" button or link for each project
  - Provide submission form or file upload interface
  - Display project status (Not Started, In Progress, Submitted, Graded)
  - Allow resubmission before deadline if allowed
- **Implementation Notes:**
  - Teacher creates new projects/assignments in Classes > [class] > Assignments (see Teacher Classes > Assignments)
  - Students view projects and submit work via provided link
  - Maintain project history; teacher grades in Submission Inbox (#22)

##### 9. View Feedback

- **Feature:** Grade and feedback review
- **User Story:** As a Student, I want to view the teacher's grade and feedback on my past submissions, so that I can improve.
- **Acceptance Criteria:**
  - Display list of graded projects/submissions
  - Show grade/score prominently
  - Display teacher's written feedback and comments
  - Include grading rubric or evaluation criteria if available
  - Show grading date
  - Allow student to download feedback document
- **Implementation Notes:** Learning reinforcement; essential for student improvement

---

### Progress

#### Reports

**Section:** Progress > Reports

##### 10. Assessment & Progress Tracking

- **Feature:** Course progress and module assessments
- **User Story:** As a Student, I want to view my course progress and take module assessments, so that I can track my learning.
- **Acceptance Criteria:**
  - Display overall course progress percentage
  - Show breakdown by module or unit
  - Display completed vs. remaining lessons
  - Provide access to take module/monthly assessments
  - Show assessment scores and results
  - Display learning timeline or milestone markers
- **Implementation Notes:**
  - Assessment conducted for 1 module or 1 month on student project and in-class activities
  - Comprehensive tracking of student achievement

##### 11. Future Evaluation

- **Feature:** Course recommendations and evaluation guidance
- **User Story:** As a Student, I want to view evaluations for future class recommendations, so that I know what to study next.
- **Acceptance Criteria:**
  - Display evaluation results from completed courses
  - Suggest recommended next courses based on performance
  - Show skill level progression
  - Provide learning path recommendations
  - Display prerequisites for advanced courses
- **Implementation Notes:** Help students plan their learning journey; project progress and evaluation for future courses

---

## TEACHER PORTAL

### Dashboard

#### Overview

**Section:** Dashboard > Overview

##### 12. View Profile & Stats

- **Feature:** Teacher profile creation and management
- **User Story:** As a Teacher, I want to upload my photo and write a short bio, so that prospective students and parents can view my qualifications on the public Course Details page.
- **Acceptance Criteria:**
  - Allow photo/avatar upload (drag & drop or browse)
  - Provide text editor for bio/qualifications
  - Display preview of public profile
  - Save and publish profile updates
  - Show profile completion percentage
- **Implementation Notes:** Public-facing profile enhances credibility and student enrollment

##### 13. Stats & Announcements

- **Feature:** Dashboard widget with teaching workload overview
- **User Story:** As a Teacher, I want to view my total courses, total students, assignment statuses, upcoming classes, and recent announcements on one screen, so that I can manage my teaching workload effectively.
- **Acceptance Criteria:**
  - Display KPI widgets: Total Active Courses, Total Enrolled Students
  - Show assignment submission status (pending review, graded, etc.)
  - Display next 3-5 upcoming classes with time/room info
  - Show recent announcements or platform updates
  - Widget selection/customization (can select which to display)
  - One-click navigation to detailed sections
- **Implementation Notes:** Comprehensive workload overview; customizable widgets

---

### Courses

#### My Courses

**Section:** Courses > My Courses

##### 14. Create/Edit Course

- **Feature:** Course content creation and management
- **User Story:** As a Teacher, I want to create a new course or edit details, so that I can build content.
- **Acceptance Criteria:**
  - Form to input: course title, description, category, level, duration
  - Ability to structure course into modules/units
  - Add learning objectives and syllabus
  - Upload course materials (curriculum documents)
  - Save as draft or publish
  - Edit existing courses and versions
- **Implementation Notes:** Core feature for teacher content creation

##### 15. Submit for Approval

- **Feature:** Course submission workflow for admin approval
- **User Story:** As a Teacher, I want a button to submit my finalized course to Admin, so that it can be approved.
- **Acceptance Criteria:**
  - Display "Submit for Approval" button on completed course
  - Show submission checklist (required fields validation)
  - Record submission timestamp and version
  - Provide feedback notification when course is approved/rejected
  - Allow resubmission after edits
- **Implementation Notes:**
  - Upload course content, activities, and recorded videos
  - Quality control mechanism for platform consistency

---

### Classes

#### Schedule

**Section:** Classes > Schedule

##### 16. Set Class Link

- **Feature:** Online meeting link and schedule management
- **User Story:** As a Teacher, I want to add/update the online meeting link and time for a specific class slot, so that students can join.
- **Acceptance Criteria:**
  - Form to input meeting link (Google Meet, Zoom, etc.)
  - Set or adjust class time and duration
  - Save and publish link to students
  - Edit link before class starts
  - Display link in teacher view and student view
  - Once a meeting link is set, the teacher sees a **"Join meeting"** button that opens the link in a new tab, in both the schedule page (per session row) and the dashboard **"Upcoming classes"** widget — mirrors the student Join experience for parity
  - In **"Upcoming classes"**: when session is **IN_PROGRESS**, show **"Join meeting"** (like student); when **SCHEDULED**, show **"Start class"** button that links to the schedule page so the teacher can update the session status and enable students to join
- **Implementation Notes:** Flexible for different meeting platforms

##### 17. Update Session Video URL

- **Feature:** Post-class video recording management
- **User Story:** As a Teacher, I want to update the video url link after the session via google meet completed for students that haven't joined can view the video later.
- **Acceptance Criteria:**
  - Provide field to add/update video link after class
  - Link is accessible to students who missed the live session — students see a **"Watch recording"** button on completed sessions when teacher has set a video URL
  - Display video availability status
  - Allow video to be recorded during class (via Google Meet integration)
  - Show video upload/link deadline
  - Notify students of video availability
- **Additional behaviour (session management):**
  1. **Sessions from schedule:** Sessions are created from the class schedule. For now, creation is triggered by the teacher (e.g. when opening the schedule page or via a "Generate sessions" action), so the teacher controls when sessions appear.
  2. **Create and manage in advance:** Teachers can create sessions in advance and set the meeting (student) link in advance; video URLs are added after class. This keeps sessions manageable and allows students to see the join link before class.
  3. **Editable session date/time:** When creating a session, default start date, end date, start time, and end time are inherited from the class schedule, but the teacher can edit any of these per session.
  4. **Session status control:** Teacher can set an upcoming or current session to **IN_PROGRESS** (e.g. "Start class") or back to **SCHEDULED** (e.g. "Revert to scheduled"), so the live session can be enabled or disabled without changing the schedule.
- **Implementation Notes:** Important for asynchronous learning; students can catch up on missed classes

#### Resources

**Section:** Classes > Resources

##### 18. Upload Material

- **Feature:** Learning resource management and distribution
- **User Story:** As a Teacher, I want to upload slides, homework, and videos to a specific class instance, so that students can access them.
- **Acceptance Criteria:**
  - File upload interface for slides (PPT, PDF, images)
  - Upload homework assignments and instructions
  - Upload/link videos (course recordings, tutorials)
  - Organize materials by module or date
  - Set visibility/release date for materials — students see a **Materials** section on the class detail page with released resources (respecting release dates)
  - Download management and version control
  - File preview/preview capability
- **Implementation Notes:**
  - Upload course materials, activities, and recorded videos
  - Multiple file type support for diverse learning resources

#### Assignments

**Section:** Classes > Assignments (projects for student submission and grading)

- **Feature:** Create and manage assignments (projects) per class
- **User Story:** As a Teacher, I want to create assignments for a class and optionally set a due date and rubric, so that students see them in their Projects menu and can submit work for grading.
- **Acceptance Criteria:**
  - From class detail, access an Assignments list for that class
  - Create assignment: title, description (optional), due date (optional), rubric (optional), allow resubmission (optional)
  - List assignments for the class with due date and submission counts
  - Edit or archive assignments (archived assignments no longer appear for new submission; students keep read-only view)
  - Assignments appear in the student Projects menu for enrolled students; students submit via link (see PRD #8)
- **Implementation Notes:**
  - Separate from Class materials (#18): materials = upload files for download; assignments = tasks students submit and teacher grades (#22)
  - Teacher creates assignments per class; grading is done in Submission Inbox (#22)

#### Students

**Section:** Classes > Students

##### 19. Student Directory

- **Feature:** Class roster management and student filtering
- **User Story:** As a Teacher, I want to filter students by class and view their profiles, so that I can know who is in my class.
- **Acceptance Criteria:**
  - Display list of all students in selected class
  - Show student names, enrollment status, payment status
  - Filter or search by name, enrollment date, status
  - Click to view student profile and performance
  - Display student contact information
- **Implementation Notes:** Class management and student recognition

##### 20. Message Student

- **Feature:** Private direct messaging with students
- **User Story:** As a Teacher, I want to click a "Message" button on a student's profile, so that I can communicate privately.
- **Acceptance Criteria:**
  - "Message" button on each student profile
  - Open messaging interface/compose screen
  - Show message history with selected student
  - Send and receive messages
  - Notification for new messages
- **Implementation Notes:** Improve communication; personal touch for student support

#### Attendance

**Section:** Classes > Attendance

##### 21. Attendance Review

- **Feature:** Attendance verification and manual correction
- **User Story:** As a Teacher, I want to verify the automated attendance records (marked when students joined) and manually correct any errors, so that the class records are accurate.
- **Acceptance Criteria:**
  - Display auto-marked attendance records for selected class/date
  - Show list of students with Present/Absent status
  - Allow manual editing of attendance status
  - Add notes or reasons for absent students
  - View attendance history for the class
  - Export attendance report
- **Implementation Notes:** Override auto-attendance if issues occur; maintain accurate records

---

### Grading

#### Assessment

**Section:** Grading > Assessment

##### 22. Submission Inbox

- **Feature:** Student submission review and grading workspace
- **User Story:** As a Teacher, I want to view a list of student project submissions, so that I can begin grading.
- **Acceptance Criteria:**
  - Display all pending student submissions in chronological or custom order
  - Show: student name, assignment name, submission date, file preview
  - Filter by assignment, student, or submission date
  - Click to open submission for detailed review
  - Mark submission as graded/reviewed
  - Provide feedback form for each submission (grade 0–100, written feedback)
- **Implementation Notes:**
  - Assignments are created per class (Classes > Assignments); submissions appear here for grading
  - View student project submissions; provide feedback to each student; streamline grading workflow
  - Students see grade and feedback on their project detail page (#8, #9)

##### 23. Monitoring Matrix

- **Feature:** Class-wide performance overview
- **User Story:** As a Teacher, I want to view a matrix of the whole class's progress, so that I can spot struggling students.
- **Acceptance Criteria:**
  - Display matrix/grid: rows = students, columns = assignments/assessments
  - Show grade/score in each cell
  - Color-coding for performance levels (green = good, red = struggling)
  - Click on cell to view detailed student work
  - Identify at-risk or struggling students
  - Filter by assignment or performance threshold
  - Export or print matrix report
- **Implementation Notes:** Identify struggling students quickly; data-driven teaching

---

## ADMIN DASHBOARD

### Dashboard

#### Overview

**Section:** Dashboard > Overview

##### 24. KPI Widgets

- **Feature:** System health monitoring dashboard
- **User Story:** As an Admin, I want to view Total Users, Total Courses, and Active Users, so that I can monitor system health.
- **Acceptance Criteria:**
  - Widget 1: Total Users (Student, Teacher, Admin counts)
  - Widget 2: Total Courses (active, pending approval, archived)
  - Widget 3: Active Users (logged in today, this week)
  - Widget 4: Revenue/Payment Status (if applicable)
  - Real-time or hourly data updates
  - Click-through to detailed reports
  - Customizable time range filters
- **Implementation Notes:** Executive overview of platform performance

---

### Users

#### User List

**Section:** Users > User List

##### 25. User Management

- **Feature:** Full user CRUD operations
- **User Story:** As an Admin, I want to view all users and use "Create/Edit/Delete" actions, so that I manage access.
- **Acceptance Criteria:**
  - Display list of all users (Students, Teachers, Admins)
  - Show: username, email, role, registration date, status (active/inactive)
  - Create new user form (name, email, role, password)
  - Edit user information and role
  - Update user profile
  - Deactivate or delete user accounts
  - Search/filter by name, email, role
  - Bulk actions (bulk activate, deactivate, delete)
  - View user activity/login history
  - View user profile
- **Implementation Notes:** Central user management; enable/disable access as needed

#### Leads & Trials

**Section:** Users > Leads & Trials

##### 26. Trial Request Inbox

- **Feature:** Centralized trial request management
- **User Story:** As an Admin, I want to view a centralized list of all "Free Trial" requests coming from Telegram, so that I can follow up and convert them into enrolled students without searching through chat logs.
- **Acceptance Criteria:**
  - Display all trial requests in a dedicated inbox
  - Show: requester name, email, contact info (Telegram), request date
  - Mark request as "Reviewed", "Contacted", "Converted", or "Rejected"
  - Click to send follow-up message or email template
  - Track conversion status
  - Set reminders for follow-up
  - Export lead list for CRM integration
- **Implementation Notes:**
  - Requests come from Telegram registration
  - Eliminates need to search through chat logs
  - Improves lead conversion tracking

---

### Courses

#### Course Registry

**Section:** Courses > Course Registry

##### 27. Search Courses

- **Feature:** Course discovery and search
- **User Story:** As an Admin, I want to search courses by Teacher Name, so that I can find specific content.
- **Acceptance Criteria:**
  - Search field for course title and teacher name
  - Filter by category, level, status (active, pending, archived)
  - Display results with: course name, teacher, category, enrollment count
  - Click to view course details
  - View course syllabus and materials
- **Implementation Notes:** Quick course lookup; monitor course inventory

#### Approvals

**Section:** Courses > Approvals

##### 28. Approval Queue

- **Feature:** Teacher course approval workflow
- **User Story:** As an Admin, I want to view courses submitted by teachers and click "Approve" or "Edit," so that quality is maintained.
- **Acceptance Criteria:**
  - Display queue of pending course submissions
  - Show: course title, teacher name, submission date, preview
  - "Approve" button to publish course
  - "Edit" button to request changes or edit course
  - Add approval notes or feedback
  - Send approval/rejection notification to teacher
  - Track approval history and timestamps
- **Implementation Notes:** Quality assurance gate; ensure platform standards

---

### Classes

#### Class Management

**Section:** Classes > Class Management

##### 29. Create/Edit Class

- **Feature:** Class instance creation and setup
- **User Story:** As an Admin, I want to create a class instance (e.g., "Junior Code A") and assign a category, so that the schedule is built.
- **Acceptance Criteria:**
  - Form to input: class name, course link, category, level
  - Select schedule template or create custom schedule
  - Set capacity/max students
  - Assign time slots (day, time, duration)
  - Publish class for enrollment
  - Save as draft before publishing
  - Edit the class
- **Implementation Notes:** Build the class catalog

##### 30. Assign Teacher

- **Feature:** Teacher-to-class assignment
- **User Story:** As an Admin, I want to assign a specific teacher to a class instance, so that the class has an instructor.
- **Acceptance Criteria:**
  - Dropdown or search to select teacher from database
  - Display teacher profile and qualifications preview
  - Assign/reassign teachers to class
  - Confirm assignment and send notification to teacher
  - Show class assignment to teacher in their dashboard
  - Allow unassigning if needed
- **Implementation Notes:** Link instructors to classes

##### 31. Manage Enrollment

- **Feature:** Student enrollment and status management
- **User Story:** As an Admin, I want to add students to a class and update their status, so that records are accurate.
- **Acceptance Criteria:**
  - Add individual students to class by name/email search
  - Download Bulk import template
  - Bulk import students (CSV file)
  - Update enrollment status: Active, Waitlist, Inactive, Dropped
  - Update payment status: Paid, Pending, Trial
  - Set enrollment date and trial expiry
  - Remove students from class
  - View enrollment history
- **Implementation Notes:** Student roster management; payment tracking

#### Class Directory

**Section:** Classes > Class Directory

##### 32. Master Class List & Filters

- **Feature:** Comprehensive class inventory with filtering
- **User Story:** As an Admin, I want to view a master list of all classes and filter by Teacher, Day, or Status, so that I can quickly locate specific sessions without searching one by one.
- **Acceptance Criteria:**
  - Display table/list of all class instances
  - Columns: Class Name, Teacher, Schedule (Day/Time), Students (e.g., 10/12 Paid), Status
  - Filter by: Teacher name, Day of week, Status (Active, Pending, Archived)
  - Search by class name or keyword
  - Sort by any column
  - Click row to view class details
  - Show capacity utilization (10/12 students)
  - Multi-select for bulk actions
- **Implementation Notes:** Central view of entire class schedule; operational management

#### Class Detail

**Section:** Classes > Class Detail

##### 33. Roster & Payment Status Management

- **Feature:** Detailed class roster with payment verification
- **User Story:** As an Admin, I want to click on a class to see the full student roster with their Payment Status (Paid/Pending/Trial) and be able to manually toggle it, so that I can verify who is allowed to be in the room.
- **Acceptance Criteria:**
  - Display full roster for selected class
  - Columns: Student Name, Email, Phone, Status (Paid/Pending/Trial)
  - Click toggle to change payment status
  - Confirm status changes with notification
  - View payment history/transaction details
  - Identify and flag unpaid students
  - Remove students from class if needed
  - Print or export roster
- **Implementation Notes:** Access control and payment verification; trust/safety critical

---

### Project/Assignment

#### Global Project View

**Section:** Project/Assignment > Global Project View

##### 34. View All Projects & Assignments

- **Feature:** Platform-wide project monitoring
- **User Story:** As an Admin, I want to view every project and assignment created by all teachers, so that I can monitor the quality and consistency of the curriculum across the platform.
- **Acceptance Criteria:**
  - Display all projects/assignments from all teachers
  - Show: project title, teacher name, course, creation date, status
  - Filter by teacher, course, or date range
  - Search by project name or keywords
  - View project description, rubric, and expected submissions
  - Click to preview project details
  - Archive or remove projects if needed
  - Track submission counts per project
- **Implementation Notes:** Quality assurance and curriculum consistency monitoring

---

### Performance

#### Quality Assessment

**Section:** Performance > Quality Assessment

##### 35. Assess Teachers' and Students' Performance

- **Feature:** Comprehensive performance analytics
- **User Story:** As an Admin, I want to review the performance metrics of both teachers and students, so that I can identify high-performers and those needing additional support.
- **Acceptance Criteria:**
  - Teacher metrics: Course completion rate, student satisfaction (if surveyed), assignment submission rates, average grade distribution
  - Student metrics: Course progress %, average scores, attendance rate, assignment completion rate, engagement level
  - Sortable leaderboards (top teachers, top students)
  - Identify low performers requiring support/intervention
  - Filter by course, time period, or cohort
  - Drill-down to individual performance details
  - Generate performance comparison reports
  - Create alerts/flags for at-risk students or underperforming teachers
- **Implementation Notes:** Data-driven platform improvement and targeted support

---

### Content

#### Public Content

**Section:** Content > Public Content

##### 36. Ad Manager

- **Feature:** Marketing content and promotions management
- **User Story:** As an Admin, I want to post content for advertisements and new class promotions, so that the public site is updated.
- **Acceptance Criteria:**
  - Create/edit promotional banners and slides
  - Upload promotional images and videos
  - Write promotional text/descriptions
  - Schedule promotion visibility dates
  - Display promotions on public landing page
  - Track promotion clicks/impressions (if analytics available)
  - Featured class section management
  - Remove expired promotions
- **Implementation Notes:** Drive enrollment through marketing content

---

### Reports

#### Analytics

**Section:** Reports > Analytics

##### 37. Activity Tracker

- **Feature:** System-wide activity auditing and logging
- **User Story:** As an Admin, I want to view logs of teacher and student activities, so that I can audit usage.
- **Acceptance Criteria:**
  - Display chronological log of activities: login, course access, content upload, grading
  - Filter by user, activity type, date range
  - Show: user name, activity, timestamp, affected resource
  - Search for specific activities or users
  - Export activity logs for compliance/audit
  - Track attendance and session duration
  - Identify suspicious activity
- **Implementation Notes:** Audit trail for compliance and platform monitoring

##### 38. Download Reports

- **Feature:** Report generation and export
- **User Story:** As an Admin, I want to click "Generate Report" for student progress or teacher performance, so that I have offline records.
- **Acceptance Criteria:**
  - Report templates: Student Progress Report, Teacher Performance Report, Course Analytics
  - Select filters (date range, course, cohort, etc.)
  - Generate report in PDF or Excel format
  - Include charts, graphs, and summary tables
  - Download or email report
  - Schedule recurring reports (if needed)
  - Archive historical reports
- **Implementation Notes:** Business intelligence and record-keeping

---

### Settings

#### System Config

**Section:** Settings > System Config

##### 39. General Settings

- **Feature:** Platform configuration and system parameters
- **User Story:** As an Admin, I want to set the System Name, Maintenance Mode, and Default Locale, so that the platform is configured correctly.
- **Acceptance Criteria:**
  - System Name: update platform branding/display name
  - Maintenance Mode: enable/disable with display message (for planned downtime)
  - Default Locale: set language and timezone defaults
  - Email settings: SMTP configuration for notifications
  - Payment settings: currency, payment methods (if applicable)
  - File upload settings: file size limits, allowed formats
  - Integration settings: Telegram bot, Google Meet API credentials
  - Save and test configurations
  - Audit log of configuration changes
- **Implementation Notes:** Core platform administration; affects all users

---

## PUBLIC SITE

### Home

#### Landing Page

**Section:** Home > Landing Page

##### 40. Promotions

- **Feature:** Class promotions and featured content
- **User Story:** As a Visitor, I want to see upcoming class promotions, so that I am encouraged to explore.
- **Acceptance Criteria:**
  - Display promotional banners/carousel on landing page
  - Show featured courses or special offers
  - Include promotional images, titles, and brief descriptions
  - Click through to course details or registration
  - Rotate promotions or update regularly
- **Implementation Notes:** Increase discoverability and enrollment

#### Header/Navigation

**Section:** Home > Header/Nav

##### 41. Login / SSO

- **Feature:** User authentication and role-based access
- **User Story:** As a Visitor, I want to log in using Telegram (if I am a Student) or Email/Password (if I am a Teacher/Admin), so that I can access the correct dashboard.
- **Acceptance Criteria:**
  - Telegram login button for students
    - Register/login via Telegram
    - Telegram profile/ID verification
    - Option to link email address to Telegram account later
  - Email/Password login for teachers and admins
  - Forgot password recovery flow
  - Dashboard redirect based on user role
  - Session management (login/logout)
  - Remember me option
- **Implementation Notes:**
  - Students: Register via Telegram (can link Email later)
  - Admins/Teachers: Email & Password only
  - Telegram login acts as phone number verification (cost savings - no SMS OTP needed)
  - Seamless experience across roles

---

### Courses

#### Catalog

**Section:** Courses > Catalog

##### 42. Filter & Search

- **Feature:** Course discovery with filtering options
- **User Story:** As a Visitor, I want to filter courses by category, age, or skill level, so that I find relevant classes.
- **Acceptance Criteria:**
  - Search box for course title and keywords
  - Filter options: Category dropdown, Age group, Skill level (Beginner/Intermediate/Advanced)
  - Display filtered course results as cards or list
  - Show: course title, teacher name, price (if any), student count, rating
  - Sort by name, popularity, newest, price
  - Click to view course details
  - Show number of matching results
- **Implementation Notes:** Help visitors find relevant courses quickly

#### Course Details

**Section:** Courses > Course Details

##### 43. View Syllabus

- **Feature:** Course curriculum and instructor information
- **User Story:** As a Visitor, I want to read the curriculum and teacher profile, so that I understand what is being taught.
- **Acceptance Criteria:**
  - Display course title, description, and overview
  - Show teacher profile: name, photo, bio, qualifications
  - Course syllabus: modules, topics, learning objectives
  - Course duration, schedule, and price
  - Student enrollment count and reviews/ratings
  - Prerequisites if any
  - Share course link
- **Implementation Notes:** Build trust through transparency

##### 44. Watch Sample

- **Feature:** Sample lesson video preview
- **User Story:** As a Visitor, I want to click "Play" on a sample video/trial lesson, so that I can see the teaching style.
- **Acceptance Criteria:**
  - Display embedded video player for sample lesson
  - Show video title, duration, and description
  - Video playback controls and fullscreen option
  - Display class name and teacher for sample video
  - Option to download transcript or notes (if available)
  - Call-to-action button after video: "Book a Trial" or "Enroll Now"
- **Implementation Notes:** Preview teaching quality; reduce enrollment hesitation

---

### Join

#### Registration

**Section:** Join > Registration

##### 45. Book Class

- **Feature:** Student registration and class booking
- **User Story:** As a Visitor, I want to register/login with Telegram to verify my identity before booking a class, so that I don't need to pay for SMS OTP.
- **Acceptance Criteria:**
  - Telegram login/registration on registration form
  - Select desired course and class instance
  - Confirm booking (date, time, price)
  - Payment handled separately/externally by admin
  - Send booking confirmation email
  - Add class to student calendar
  - Receive class details and join link via email/notification
- **Implementation Notes:**
  - Telegram login acts as phone verification (cost saving - no SMS OTP)
  - Payment done externally from admin dashboard directly with students
  - Streamlined registration process

##### 46. Request Trial

- **Feature:** Free trial request submission
- **User Story:** As a Visitor, I want to request a trial by clicking "Start with Telegram", so that my request is instantly verified and sent to the Admin.
- **Acceptance Criteria:**
  - "Request Trial" button on course page
  - Trigger Telegram login for verification
  - Send trial request to admin inbox instantly
  - Send confirmation to user: "Request Received"
  - Admin receives Telegram bot alert for new trial request
  - Track trial request status (Pending, Approved, Completed)
  - Show request step tracking above each step
- **Implementation Notes:**
  - Replaces SMS OTP verification
  - Telegram bot notifies admin of new trial requests instantly
  - Faster qualification process

---

### Support

#### Help

**Section:** Support > Help

##### 47. Contact Form

- **Feature:** Customer support inquiry form
- **User Story:** As a Visitor, I want to use a contact form or chat, so that I can ask for support.
- **Acceptance Criteria:**
  - Contact form with fields: name, email, subject, message
  - Dropdown for inquiry type (billing, technical, other)
  - Form validation (required fields, email format)
  - Submission confirmation message
  - Support ticket creation and tracking number
  - Email copy of inquiry to visitor
  - After user fill the contact form and submit save to table and then send the message to telegram.
- **Implementation Notes:** Multiple support channels

##### 48. Direct Contact Info

- **Feature:** Visible contact information
- **User Story:** As a Visitor, I want to clearly see direct contact details (Email, Telegram, Phone) on the site, so that I can reach out for a trial manually.
- **Acceptance Criteria:**
  - Display contact section with:
    - Email address (clickable mailto link)
    - Telegram username/link
    - Phone number (clickable tel link)
  - Place in header, footer, and dedicated contact page
  - Include business hours if applicable
- **Implementation Notes:** Multiple contact options for user preference

#### Testimonials

**Section:** Support > Testimonials

##### 49. Review List

- **Feature:** Student success stories and social proof
- **User Story:** As a Visitor, I want to view a list of student success stories, so that I feel confident in the platform.
- **Acceptance Criteria:**
  - Display testimonials in carousel, grid, or list format
  - Show: student name, photo, course taken, quote/review, rating
  - Include success metrics (e.g., "Improved from 40% to 90%")
  - Testimonial date and verification badge (if authentic)
  - Filter by course or star rating
  - Pagination or scroll loading
- **Implementation Notes:** Build confidence and credibility; social proof

---

## CROSS-FUNCTIONAL FEATURES

### Notifications

- Real-time notifications for all user roles (in-app and optional email)
- Notification preferences and opt-out options
- Notification history and archive

### Messaging

- Direct messaging between students and teachers
- Notification bells for new messages

### File Management

- Upload, download, and preview capabilities across platform
- Supported formats: PDF, images, videos, documents
- File versioning and storage limits

### Search & Filtering

- Global search across courses, materials, and users
- Advanced filtering options throughout platform
- Search history and saved filters

### Reporting & Analytics

- User activity logs
- Course analytics and performance metrics
- Customizable reports
- Data export capabilities

### Web Analytics (Google Analytics 4)

- **Feature:** Website analytics and conversion tracking via Google Analytics 4 (GA4) for acquisition, conversion, and engagement insights.
- **User Story:** As a product or marketing owner, I want to understand how visitors find the site, which courses and promotions drive interest, and how trial and contact conversions perform, so that I can improve acquisition and engagement.
- **Acceptance Criteria:**
  - Page views tracked on every route (including client-side navigation) when GA Measurement ID is configured.
  - Public and conversion events tracked: course detail views, sample video view/play, promotion clicks, trial request started/completed, contact form submitted, login (by method: Telegram vs credentials).
  - Key engagement events tracked: student join class click, project submitted; teacher grade submitted.
  - No PII (no user id, email, name, or phone) sent in any event parameters.
  - Analytics script loads only when `NEXT_PUBLIC_GA_MEASUREMENT_ID` is set; otherwise no tracking.
- **Implementation Notes:**
  - **Setup:** One GA4 property; Measurement ID (e.g. `G-XXXXXXXXXX`) in env var `NEXT_PUBLIC_GA_MEASUREMENT_ID`. gtag script injected in root layout with `send_page_view: false`; SPA page_view sent from `AnalyticsProvider` on pathname/search change.
  - **Events (custom):** `view_course` (course_slug, course_category, course_level), `view_sample_video` (video_source), `promotion_click` (promotion_id, promotion_type, destination), `trial_request_started` (source, course_slug), `trial_request_completed` (source, course_slug), `generate_lead` (lead_type: contact_form, inquiry_type), `login` (method: password | telegram), `join_class_click` (session_id), `project_submitted` (project_id), `grade_submitted` (submission_id). Mark `trial_request_completed` and `generate_lead` as conversions in GA4 if desired.
  - **Components:** `app/layout.tsx` (script injection), `components/providers/AnalyticsProvider.tsx` (page_view), `CourseViewTracker`, `SampleVideoPlayer`, `PromotionCarousel`/`PromotionCard`, course detail trial CTA, `TrialCompletedTracker`, `ContactForm`, `LoginForm`, `SessionRow`, `ProjectSubmitForm`, `GradeSubmissionForm`.
  - **Privacy:** No PII in events; detailed audit remains in Activity Tracker (#37) and reports. Add consent banner and gtag consent mode when required (e.g. EU).

### Mobile Responsiveness

- All features accessible on mobile/tablet
- Responsive design for iOS and Android devices
- Mobile-optimized navigation

---

## IMPLEMENTATION PRIORITIES

### Phase 1: Core Features (MVP)

- Student Dashboard & Class Join
- Teacher Class Management & Grading
- Admin User & Course Management
- Public Course Browsing & Registration
- Telegram Authentication

### Phase 2: Engagement

- Notifications & Messaging
- Student Progress Tracking
- Project Submissions & Feedback
- Teacher Attendance & Analytics

### Phase 3: Advanced

- Payment Integration (if external)
- Advanced Reporting & Analytics
- Content Management
- Performance Assessments

---

## TECHNICAL NOTES

### Authentication & Authorization

- Role-based access control (RBAC): Student, Teacher, Admin, Public
- Telegram OAuth integration for students
- Email/password authentication for teachers and admins
- Session management and security

### Data Models

- Users (Students, Teachers, Admins)
- Courses and Modules
- Classes/Sessions
- Assignments/Projects
- Submissions and Grades
- Attendance Records
- Notifications and Messages

### Integration Requirements

- Google Meet API for class links
- Telegram Bot API for notifications and authentication
- Email service for notifications
- File storage (cloud or local)

### Performance Considerations

- Real-time notifications with minimal latency
- Efficient search and filtering
- Scalability for growing user base
- Caching for frequently accessed data (see **Redis Cache** below)

### Redis Cache

Redis (Upstash in Phase 1; VPS: Redis via `CACHE_PROVIDER=redis`) is used for short-TTL caching of read-heavy, aggregate data to reduce database load and improve response times. All cache keys and TTLs are defined below; invalidation is applied when source data changes.

**Cache provider:** `lib/providers/cache/` — `ICacheProvider` (get, set, del, exists), `UpstashCacheProvider`, optional `RedisCacheProvider` for VPS. Export `cacheService`; swap via `CACHE_PROVIDER=upstash|redis`.

| Priority | Data                          | Service / location                                                     | Cache key                   | TTL   | Invalidation                                                                     |
| -------- | ----------------------------- | ---------------------------------------------------------------------- | --------------------------- | ----- | -------------------------------------------------------------------------------- |
| 1        | Admin dashboard KPIs (#24)    | `getAdminDashboardStats()` — `services/admin-dashboard.service.ts`     | `kpi:admin:stats`           | 60s   | TTL only                                                                         |
| 2        | Class leaderboard (#2)        | `getClassLeaderboard()` — `services/leaderboard.service.ts`            | `leaderboard:{classId}`     | 30s   | On grade posted or attendance updated for that class; Inngest `class-ended` step |
| 3        | Public settings (#39)         | `getPublicSettings()` — `services/settings.service.ts`                 | `settings:public`           | 5 min | When admin updates general settings                                              |
| 4        | Active promotions (#40, #36)  | `getActivePromotions()` — `services/promotion.service.ts`              | `promotions:active`         | 5 min | On create/update/delete promotion                                                |
| 5        | Teacher dashboard stats (#13) | `getTeacherDashboardStats()` — `services/teacher-dashboard.service.ts` | `kpi:teacher:{teacherId}`   | 60s   | TTL only                                                                         |
| 6        | Student profile stats (#1)    | `getStudentProfileWithStats()` — `services/user.service.ts`            | `profile:stats:{studentId}` | 60s   | On enrollment, submission, or attendance change for that student                 |

**Rules:**

- Never store PII in cache; store only aggregate counts, IDs, and non-sensitive metadata.
- Serialize complex values as JSON for `set`; parse on `get`.
- Invalidation: call `cacheService.del(key)` in the same code path that mutates the underlying data (e.g. after `gradeSubmission` → del `leaderboard:{classId}`; after `updateGeneralSettings` → del `settings:public`).
- Inngest `class-ended` must include a step that deletes `leaderboard:{classId}` for the affected class.

**Optional (later):** Catalog search result cache (`searchCatalog`) for popular filter combinations; rate limiting (login, contact form, upload) using the same Redis instance.

---

## APPENDIX: FEATURE SUMMARY BY ROLE

### Student Features (11 features)

1. View Profile & Stats
2. Classes Leaderboard
3. Current Lessons
4. Notification Feed
5. Class List with Payment Badge
6. Join Class & Upload Activity
7. Auto-Attendance
8. Project List & Submit
9. View Feedback
10. Assessment & Progress
11. Future Evaluation

### Teacher Features (11 features)

1. View Profile & Stats
2. Stats & Announcements
3. Create/Edit Course
4. Submit Course for Approval
5. Set Class Link
6. Update Session Video URL
7. Upload Material
8. Student Directory
9. Message Student
10. Attendance Review
11. Submission Inbox
12. Monitoring Matrix

### Admin Features (16 features)

1. KPI Widgets
2. User Management
3. Trial Request Inbox
4. Search Courses
5. Approval Queue
6. Create Class
7. Assign Teacher
8. Manage Enrollment
9. Master Class List & Filters
10. Roster & Payment Status
11. View All Projects/Assignments
12. Assess Performance
13. Ad Manager
14. Activity Tracker
15. Download Reports
16. General Settings

### Public Features (10 features)

1. Promotions
2. Login / SSO
3. Filter & Search Courses
4. View Syllabus
5. Watch Sample
6. Book Class
7. Request Trial
8. Contact Form
9. Direct Contact Info
10. Review List

**Total Features: 49**

---

## Inngest Implementation (Queue & Async Jobs)

This section tracks Inngest-based features for async processing, retries, and improved UX. Queue provider: Inngest (Phase 1); VPS alternative: BullMQ.

| Function          | Event              | PRD Feature            | Trigger Point                                         | Status  |
| ----------------- | ------------------ | ---------------------- | ----------------------------------------------------- | ------- |
| `generate-report` | `report/requested` | #38 Download Reports   | Admin requests report with delivery=email             | ✅ Done |
| `grade-posted`    | `grade/posted`     | #9 View Feedback       | Teacher grades submission in grading action           | ✅ Done |
| `course-approved` | `course/approved`  | #28 Approval Queue     | Admin approves course                                 | ✅ Done |
| `class-ended`     | `class/ended`      | #3 Current Lessons     | Cron `update-session-status` marks sessions COMPLETED | ✅ Done |
| `trial-requested` | `trial/requested`  | #26, #46 Trial Request | Student submits trial request (join flow)             | ✅ Done |
| `send-message`    | `message/send`     | #20 Message Student    | Action enqueues → serverless saves to DB (fast UI)    | ✅ Done |

### Planned (not yet implemented)

| Function              | Event                         | PRD Feature        | Notes                                                          |
| --------------------- | ----------------------------- | ------------------ | -------------------------------------------------------------- |
| `scan-upload`         | `file/uploaded`               | #6 Upload Activity | VirusTotal scan; requires upload tracking + VIRUSTOTAL_API_KEY |
| `attendance-exported` | `attendance/export-requested` | #21 Attendance     | CSV/PDF export; needs export trigger in admin UI               |

### Email templates (Inngest-related)

- `ReportEmail.tsx` — Report ready download link (#38)
- `CourseApprovedEmail.tsx` — Course approved notification to teacher (#28)
- `TrialConfirmationEmail.tsx` — Trial request received (#46)

---

**Document Version:** 1.0
**Last Updated:** 2025
**Status:** Production Ready

---
