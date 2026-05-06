@ -1,136 +0,0 @@
## Problem Statement
Twhole Studio (music course business) has no dedicated website to promote its services, showcase its learning environment, and allow potential students to book courses. The owner needs a clean, easy-to-update one-page site with a pastel color theme, and the ability to edit all homepage content without technical help, built with minimal "caveman-style" (no bloat, straightforward) code.

## Solution
Build a one-page music course website for Twhole Studio with:
- Pastel color theme, clean design
- Required homepage sections: services banner, photo gallery, mentor bio, testimonials, course booking, address
- Integrated CMS to edit all homepage content (text, images, reorder sections, toggle visibility)
- Minimal, caveman-style codebase (no unnecessary abstractions, low bloat, simple dependencies)

## User Stories
1. As a site visitor, I want to see a banner highlighting Twhole Studio's music course services, so that I immediately understand what the studio offers.
2. As a site visitor, I want to view a photo gallery of the studio and classes, so that I can see the learning environment.
3. As a site visitor, I want to read about the mentor's background and qualifications, so that I can trust the quality of instruction.
4. As a site visitor, I want to read testimonials from past students, so that I can gauge the effectiveness of the courses.
5. As a site visitor, I want to fill out a course booking form, so that I can enroll in a music course.
6. As a site visitor, I want to see the studio's address and contact info, so that I can visit or get in touch.
7. As a site administrator (studio owner), I want to edit the banner content (headline, subtext, services list) via CMS, so that I can update promotions or service offerings without code changes.
8. As a site administrator, I want to add, remove, and reorder photos in the gallery via CMS, so that I can keep the gallery up to date with recent classes.
9. As a site administrator, I want to edit the mentor's bio, photo, and qualifications via CMS, so that I can update my profile as my experience grows.
10. As a site administrator, I want to add, remove, and edit testimonials via CMS, so that I can showcase new student feedback.
11. As a site administrator, I want to edit the course booking form fields and available courses via CMS, so that I can adjust offerings based on demand.
12. As a site administrator, I want to edit the studio address, contact info, and map embed via CMS, so that I can update location details if needed.
13. As a site visitor, I want the site to use a pastel color theme, so that it feels calm and inviting for music learners.
14. As a site visitor, I want the site to be clean and uncluttered, so that I can easily find the information I need.
15. As a site administrator, I want the CMS to be simple and intuitive, so that I don't need technical training to use it.
16. As a site visitor, I want the site to be responsive on mobile and desktop, so that I can access it from any device.
17. As a site administrator, I want all homepage content to be editable via CMS, so that I never have to modify code to update the site.
18. As a developer, I want the codebase to be minimal and caveman-style (no unnecessary abstractions, straightforward, low bloat), so that it's easy to maintain.
19. As a site visitor, I want to submit the course booking form and receive a confirmation, so that I know my enrollment was successful.
20. As a site administrator, I want to receive notifications when a course booking is submitted, so that I can follow up with the student.
21. As a site administrator, I want to reorder homepage sections via CMS, so that I can prioritize content based on marketing needs.
22. As a site visitor, I want to navigate smoothly between sections on the one-page site, so that I can quickly find what I'm looking for.
23. As a site administrator, I want to upload images for the gallery and mentor section via CMS, so that I don't have to use external tools.
24. As a site visitor, I want to see high-quality images in the gallery, so that the studio looks professional.
25. As a site administrator, I want to preview content changes in CMS before publishing, so that I can avoid mistakes on the live site.
26. As a site visitor, I want to receive instructions for manual payment after submitting a course booking, so that I know how to complete payment via bank transfer or other manual method.
27. As a site administrator, I want to view pending bookings and manually confirm payments, so that I can verify payment before enrolling students.
28. As a site administrator, I want to send payment confirmation notifications to students, so that they are informed their enrollment is confirmed.
29. As a super administrator, I want to create and manage user roles (e.g., admin, finance, content editor), so that I can control who has access to what features.
30. As a super administrator, I want to assign roles to users and modify their permissions, so that team members only access what they need.
31. As a finance staff (with finance role), I want to view revenue analytics (total bookings, payments received, pending payments), so that I can track the studio's financial performance.
32. As a finance staff, I want to filter financial data by date range and course type, so that I can generate specific financial reports.
33. As a content editor (with CMS role), I want to edit homepage content but not access booking or financial data, so that my permissions are limited to my responsibilities.
34. As a site administrator, I want to see a dashboard with key metrics (total students, active courses, monthly revenue), so that I can quickly assess the business at a glance.
35. As a super administrator, I want to view audit logs of who changed what content and when, so that I can track changes and maintain accountability.
36. As a finance staff, I want to export financial data (bookings, payments) to CSV or Excel, so that I can use it for accounting or tax purposes.
37. As a student (with student role), I want to log in and view the course schedule, so that I know when my classes are scheduled.
38. As a student, I want to submit a reschedule request (propose new date/time) for my course, so that I can adjust my schedule when needed.
39. As a student, I want to see the status of my reschedule requests (pending, accepted by admin, countered with new time, confirmed), so that I know where my request stands.
40. As a student, I want to accept or decline an admin-counter reschedule proposal, so that I can agree to or reject the alternative time offered.
41. As a student, I want to be notified when the admin responds to my reschedule request (accepts or proposes a new time), so that I can take action promptly.
42. As an administrator, I want to view all reschedule requests from students, so that I can process them in a timely manner.
43. As an administrator, I want to accept a student's reschedule request, so that the new schedule is confirmed for both parties.
44. As an administrator, I want to counter-offer a different date/time when a student's reschedule request is not suitable, so that we can negotiate a mutually acceptable time.
45. As an administrator, I want to see the back-and-forth history of reschedule negotiations with a student, so that I have full context of the discussion.
46. As an administrator, I want to be notified when a student accepts or declines my counter-offer, so that I know the current status.
47. As a student, I want the reschedule process to continue until both I and the administrator have accepted the same schedule, so that we both agree on the final time.
48. As an administrator, I want the reschedule process to continue until both I and the student have accepted the same schedule, so that we both agree on the final time.
49. As an administrator, I want to create a news article with title, content, featured image, publish date, and status (draft/published), so that I can share studio updates with visitors.
50. As an administrator, I want to view a list of all news articles (filter by draft/published), so that I can manage existing content.
51. As an administrator, I want to update an existing news article's title, content, image, or status, so that I can keep information current.
52. As an administrator, I want to delete a news article, so that I can remove outdated or incorrect content.
53. As an administrator, I want to set a news article as published or draft, so that I can control when it appears to visitors.
54. As an administrator, I want to upload a featured image for news articles via CMS, so that articles are visually engaging.
55. As an administrator, I want to reorder news articles on the homepage via CMS, so that I can prioritize important updates.
56. As a site visitor, I want to see published news articles on the homepage, so that I can stay updated on Twhole Studio activities.
57. As an administrator, I want to control the visibility and display order of the news section on the homepage via CMS, so that I can manage its prominence.
58. As a user (any role), I want to click my profile avatar/name to open a dropdown menu with options (edit profile, logout), so that I can access these actions quickly.
59. As a user (any role), I want to edit my own profile information (full name, phone number, email, password), so that I can keep my details up to date.
60. As a visitor, I want to be redirected to login when I try to book a course, so that my booking is tied to my account.
61. As a system, I want to require authentication before allowing course booking, so that all bookings are linked to a user account.
62. As a system, I want to automatically approve a student when their booking payment is confirmed, so that they gain access to student features (schedule viewing, reschedule) without manual intervention.
63. As a student, I want to be automatically approved after my payment is confirmed, so that I can immediately access my course schedule and reschedule features.
64. As a system, I want to send payment reminders to students before their course/package validity period expires, so that they can renew on time.
65. As a system, I want to send payment reminders to administrators about students with upcoming expiring packages, so that they can follow up.
66. As a system, I want to update a student's status (e.g., 'active' → 'expired') when their purchased course/package validity period ends, so that their access is managed correctly.
67. As an administrator, I want to manually confirm a student's status update (e.g., after reviewing their renewal payment), so that I have control over status changes.
68. As an administrator, I want to view a list of students with expired or soon-to-expire packages, so that I can prioritize follow-ups.
69. As a student, I want to receive reminders about my course/package expiration, so that I don't lose access unexpectedly.

## Implementation Decisions
- **Stack (caveman-style, minimal within chosen tools)**:
  - Frontend: Next.js (App Router, React) with minimal components, no unnecessary state management or abstractions
  - Backend: Supabase (PostgreSQL database, Auth for admin access, Storage for images, no custom backend server needed)
  - Styling: Tailwind CSS with custom pastel color palette (or CSS variables) for clean, responsive design
- **Modules to build**:
  - Next.js Frontend: Single page with all required sections, smooth scroll navigation, responsive layout, pastel theme
  - Supabase Database Schema: Tables for `profiles` (extended with is_approved BOOLEAN DEFAULT FALSE), `roles`, `banner_content`, `gallery_items`, `mentor_profile`, `testimonials`, `courses`, `bookings`, `address_info`, `section_settings`, `audit_logs`, `course_schedules`, `reschedule_requests`, `reschedule_messages`, `news`, `packages` (name, description, price, validity_days), `student_packages` (student_id, package_id, purchase_date, expiry_date, status: active/expired/pending_confirmation)
  - Supabase Storage: Bucket for gallery images, mentor photo, other uploads
  - Profile Module: Profile dropdown menu (click avatar/name) for all authenticated users, edit own profile (full_name, phone, email, password), API endpoint for own profile CRUD
  - CMS Admin Interface: Next.js protected routes (Supabase Auth) for admin to CRUD all content, reorder sections, toggle visibility, manage booking payments (manual confirmation)
  - Role Management Module: Super admin interface to create/edit roles, assign permissions (CMS access, finance access, booking management), assign roles to users
  - Role-Based Access Control (RBAC): Middleware or server-side checks to enforce permissions per route/action based on user role
  - Finance Analytics Module: Dashboard with revenue metrics (total bookings, payments received, pending), date range and course-type filters, data export (CSV/Excel)
  - Audit Log Module: Track content changes, booking updates, and payment confirmations with user, action, timestamp
  - News Module: `news` table (title, content, featured_image_url, status draft/published, publish_date, display_order), CMS CRUD for administrators, public API for published articles, News section added to homepage (order/visibility controlled via `section_settings`)
  - Student Role & Dashboard: Student login (Supabase Auth), role-based access to view `course_schedules` (their own classes), submit reschedule requests
  - Reschedule Workflow Module:
    - Student submits reschedule request with proposed new date/time → status: `pending`
    - Admin views request, can: Accept (status → `confirmed`, both parties agreed) or Counter-offer new time (status → `countered`, saves to `reschedule_messages`)
    - Student views counter-offer, can: Accept (status → `confirmed`) or Decline (status → `pending`, can submit new request)
    - Process repeats until both accept the same schedule → status: `confirmed`, `course_schedules` updated
    - Full negotiation history stored in `reschedule_messages` for transparency
  - Notification Module: Students notified on admin response (accept/counter), admins notified on student submit/accept/decline
  - Booking Flow: **Requires authentication** (redirect to login if not logged in), Next.js Server Actions or API routes for form submission, store bookings with `pending_payment` status, admin manually updates to `confirmed`
  - Email Notifications: Supabase Edge Functions or simple SMTP for admin notifications on new bookings, student notifications on payment confirmation, reschedule-related notifications, and approval confirmation
  - **Automated Student Approval**: When booking payment_status is updated to `confirmed`, system automatically sets `profiles.is_approved = TRUE` and ensures student role is assigned, granting access to student features (schedule viewing, reschedule)
  - **Packages Module**: `packages` table (name, description, price, validity_days), `student_packages` table (student_id, package_id, purchase_date, expiry_date, status: active/expired/pending_confirmation)
  - **Payment Reminder Module**: Supabase Cron or Edge Functions to send reminders to students (before expiry) and administrators (students with expiring packages), using Email Notifications
  - **Student Status Update**: System automatically updates `student_packages.status` to `expired` when `expiry_date` passes, requires manual confirmation from admin to reactivate (set to `active` after renewal payment is verified)
- **One-page design**: Single Next.js page with all sections, content fetched from Supabase via client or server components
- **Pastel theme**: Define 4-6 pastel colors in Tailwind config or CSS variables, applied consistently across all sections
- **Manual payment confirmation**: No payment gateway integration; admin verifies manual transfers and updates booking status in CMS
- **Responsive design**: Mobile-first approach, test across common breakpoints (320px, 768px, 1024px+)
- **Caveman-style constraints**: No unnecessary Next.js features (e.g., avoid overusing server components, no complex state management), minimal code, no bloat

## Testing Decisions
- **Good test criteria**: Test external behavior (Supabase DB operations, form submission outcomes, content rendering, payment status updates, role access enforcement, analytics data accuracy, reschedule workflow completion) not implementation details
- **Modules to test**: Supabase DB CRUD operations (all content types including roles/permissions, schedules, reschedule requests, news articles, profile updates, packages, student_packages), Next.js Server Actions/API routes (booking submission [requires auth], CMS updates, reschedule submit/accept/counter, news CRUD, profile edit, package management), Booking flow (pending → confirmed payment status, automated student approval sets is_approved=TRUE), Frontend rendering (content states, responsive layout, news section rendering, profile menu), Role-Based Access Control (unauthorized access blocked per role, student can only see own schedules, news CRUD restricted to admin+, profile edit restricted to own profile), Finance Analytics (correct metric calculations, filter behavior, export functionality), Audit Log (entries created on tracked actions including news CRUD, profile updates), Reschedule Workflow (submit → admin accept, submit → admin counter → student accept, submit → admin counter → student decline → submit new → admin accept → confirmed, full negotiation history preserved), Notification system (student notified on admin response, admin notified on student actions, approval confirmation, payment reminders), News Module (create/update/delete articles, draft/published status, display order, public API returns only published), Profile Module (dropdown menu, edit own profile fields, auth required), Automated Student Approval (payment confirmed → is_approved=TRUE, student role assigned), Packages Module (create/update packages, assign to students, expiry date calculation), Payment Reminder (reminders sent before expiry to students and admins), Student Status Update (expired status set automatically, manual confirmation to reactivate)
- **Prior art**: None (greenfield project, no existing tests)

## Out of Scope
- Multi-page site functionality
- Automated payment gateways (only manual payment confirmation is in scope)
- Blog or additional pages beyond the homepage
- Complex third-party integrations (beyond basic email notifications for bookings)
- Heavy component libraries or UI frameworks (use minimal custom components)
- Accessibility compliance beyond basic responsive design (can be added later)

## Further Notes
- "Build it like a caveman" means minimal code within the Next.js/Supabase stack: no unnecessary abstractions, components, or state management
- All CMS content must be editable without any code changes
- Site must be fully responsive across all device sizes and use a pastel color palette
- Manual payment confirmation: no payment gateway integration, admin verifies transfers manually via CMS
- Issue tracker not set up (no git repo exists), so this PRD cannot be published to a project issue tracker yet. Run `git init` and set up a remote with issue tracking to publish.