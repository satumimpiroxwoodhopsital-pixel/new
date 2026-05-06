# Twhole Studio — Technical Requirements (v1)

## 1. Tech Stack

| Layer | Technology | Version |
|-------|-------------|---------|
| Framework | Next.js (App Router) | 16.2.4 |
| Language | TypeScript | 5.x |
| UI Library | React | 19 |
| Styling | Tailwind CSS | v4 |
| Theme | `@theme inline` (Tailwind v4) | — |
| State (Auth) | React Context API | — |
| Mock DB | In-memory arrays + localStorage | — |
| Build Tool | Turbopack | — |
| Font | Inter (Google Fonts) | — |
| Images | Next.js Image + picsum.photos | — |
| Notifications | Internal messaging + optional WhatsApp | — |

---

## 2. Project Structure

```
src/
├── app/
│   ├── layout.tsx              # Root layout → AuthProviderWrapper
│   ├── page.tsx                # Landing page (public)
│   ├── login/page.tsx          # Login page
│   ├── register/page.tsx       # Class registration (public)
│   ├── gallery/page.tsx         # Photo/video gallery (public)
│   ├── dashboard/
│   │   ├── layout.tsx          # Admin dashboard layout (sidebar + header)
│   │   ├── page.tsx            # Dashboard overview
│   │   ├── students/page.tsx   # Students management
│   │   ├── class-management/page.tsx  # Course CRUD
│   │   ├── registration-requests/page.tsx  # Registration approvals
│   │   ├── invoices/page.tsx   # Invoice management
│   │   ├── lesson-management/page.tsx  # Lesson modules CRUD
│   │   ├── bookings/page.tsx   # Bookings management
│   │   ├── users/page.tsx      # User management
│   │   ├── roles/page.tsx      # Role management
│   │   ├── cms/page.tsx        # CMS (sections, banners, gallery, mentors, news, theme)
│   │   ├── finance/page.tsx    # Finance page
│   │   ├── messages/page.tsx   # Messages + batch messaging
│   │   ├── attendance/page.tsx  # Attendance overview
│   │   ├── certificates/page.tsx  # Certificate management
│   │   ├── announcements/page.tsx  # Studio announcements
│   │   ├── mentor-management/page.tsx  # Mentor availability, reviews, leave, time tracking
│   │   ├── packages/page.tsx   # Package/subscription management
│   │   ├── studio-settings/page.tsx  # Closure dates, policies
│   │   └── settings/page.tsx   # Admin profile + password
│   ├── mentor/
│   │   ├── layout.tsx          # Mentor dashboard layout
│   │   ├── page.tsx            # Mentor overview
│   │   ├── my-students/page.tsx  # Assigned students
│   │   ├── attendance/page.tsx  # Mark attendance
│   │   ├── lesson-notes/page.tsx  # Private lesson notes
│   │   ├── grading/page.tsx    # Grade student recordings
│   │   ├── schedule/page.tsx   # Mentor schedule
│   │   ├── time-tracking/page.tsx  # Log teaching hours
│   │   ├── leave/page.tsx      # Request leave
│   │   ├── messages/page.tsx   # Messages
│   │   ├── performance/page.tsx  # Performance review
│   │   ├── availability/page.tsx  # Set available slots
│   │   └── profile/page.tsx   # Mentor profile + password
│   ├── student/
│   │   ├── layout.tsx           # Student dashboard layout (sidebar + header)
│   │   ├── page.tsx             # Student overview
│   │   ├── courses/page.tsx     # My courses + lessons
│   │   ├── schedule/page.tsx    # Schedule
│   │   ├── reschedule/page.tsx  # Reschedule requests
│   │   ├── practice/page.tsx    # Practice log
│   │   ├── certificates/page.tsx  # Certificates
│   │   ├── progress-reports/page.tsx  # Progress reports PDF
│   │   ├── goals/page.tsx       # Goals & milestones
│   │   ├── attendance/page.tsx  # Personal attendance
│   │   ├── messages/page.tsx    # Messages
│   │   └── profile/page.tsx     # Student profile + password
│   ├── parent/
│   │   ├── layout.tsx           # Parent dashboard layout
│   │   ├── page.tsx             # Parent overview
│   │   ├── children/page.tsx    # Children overview
│   │   ├── payments/page.tsx    # Payment history
│   │   ├── attendance/page.tsx  # Children attendance
│   │   ├── messages/page.tsx    # Messages + conference booking
│   │   ├── conference/page.tsx  # Parent-teacher conference booking
│   │   └── profile/page.tsx     # Parent profile
│   └── api/
│       └── (mock API handlers for future migration)
├── components/
│   ├── Header.tsx              # Sticky header (auth-aware, language switcher)
│   ├── Footer.tsx              # Site footer
│   ├── BannerSection.tsx       # Auto-rotate banners (5s)
│   ├── GallerySection.tsx      # Gallery grid + Lightbox
│   ├── MentorSection.tsx       # Mentor carousel (6s)
│   ├── TestimonialsSection.tsx  # Testimonials carousel (5s)
│   ├── NewsSection.tsx         # News list + ArticleModal
│   ├── CourseCatalog.tsx       # Public course catalog
│   ├── RegistrationForm.tsx    # Class registration form
│   ├── Lightbox.tsx            # Reusable image lightbox
│   ├── PracticeLogForm.tsx     # Practice logging form
│   ├── AttendanceMarker.tsx    # Attendance marking
│   ├── CertificateView.tsx     # Certificate display/download
│   ├── ProgressReportPDF.tsx   # PDF report generation
│   ├── BatchMessageComposer.tsx  # Bulk messaging
│   ├── PaymentPlanSelector.tsx  # Installment selection
│   ├── DiscountApplier.tsx     # Coupon/discount application
│   ├── GoalsTracker.tsx        # Visual goals & milestones
│   ├── PhotoGallery.tsx        # Recital/event gallery
│   ├── AnnouncementsBoard.tsx  # Announcements display
│   ├── ClassStatusDashboard.tsx  # Live class status
│   ├── StudentPortfolio.tsx    # Portfolio display
│   ├── ConferenceBooking.tsx    # Parent-teacher conference slots
│   ├── PolicyAcknowledgment.tsx  # Studio policy agreement
│   ├── EmergencyContactForm.tsx  # Emergency contact info
│   ├── ExternalCalendarExport.tsx  # Google/Outlook/iCal export
│   ├── QuizTaker.tsx           # Music theory quizzes
│   ├── LessonMaterialDownload.tsx  # PDF/sheet music download
│   └── WhatsAppNotifier.tsx    # WhatsApp notification button
├── lib/
│   ├── db.ts                   # Mock DB types + data + helpers
│   ├── auth.tsx                # AuthContext (login, logout, permissions, update)
│   ├── registration.ts          # Registration workflow helpers
│   ├── attendance.ts            # Attendance tracking helpers
│   ├── practice.ts             # Practice log helpers
│   ├── payments.ts             # Invoice/payment helpers
│   ├── certificates.ts          # Certificate generation
│   ├── reports.ts              # Progress report PDF generation
│   ├── messaging.ts            # Batch messaging helpers
│   ├── gallery.ts              # Photo/video gallery helpers
│   ├── packages.ts             # Package/subscription helpers
│   ├── announcements.ts        # Announcements helpers
│   ├── quiz.ts                 # Quiz system helpers
│   ├── goals.ts                # Goals & milestones helpers
│   ├── mentor.ts               # Mentor management helpers
│   ├── discounts.ts            # Discount/coupon helpers
│   ├── export.ts               # Calendar export helpers
│   └── whatsapp.ts             # WhatsApp notification helpers
└── app/
    ├── globals.css             # Pastel theme + animations
    └── AuthProviderWrapper.tsx # AuthProvider wrapper
```

---

## 3. Data Models

### User
```typescript
type User = {
  id: number;
  name: string;
  email: string;
  password: string;       // excluded from client state
  role: "Super Admin" | "Admin" | "Finance" | "Content Editor" | "Mentor" | "Student" | "Parent";
  phone?: string;
  status: "active" | "pending" | "expired";
  avatar: string;          // single char or initials
  language: "id" | "en";  // preferred language
  createdAt: string;       // ISO date
};
```

### Student
```typescript
type Student = {
  id: number;
  userId: number;          // links to User
  parentId?: number;        // links to Parent (if minor)
  course: string;           // e.g. "Violin - Beginner"
  mentor: string;
  mentorId: number;         // links to Mentor User
  sessionsDone: number;
  totalSessions: number;
  packageId: number;        // links to Package
  sessionsRemaining: number;
  status: "active" | "pending" | "expired";
  since: string;
  packageExpiry: string;
  emergencyContact?: EmergencyContact;
  policyAcknowledged: boolean;
  policyDate?: string;
  enrollmentStatus: "none" | "pending" | "approved" | "rejected";
};
```

### Parent
```typescript
type Parent = {
  id: number;
  userId: number;          // links to User
  linkedStudentIds: number[];  // links to Student records
  phone: string;
  emergencyContact?: EmergencyContact;
};
```

### Course
```typescript
type Course = {
  id: number;
  name: string;            // e.g. "Piano Mastery - Beginner"
  instrument: string;      // "Piano" | "Guitar" | "Violin"
  level: string;            // custom: "Beginner", "Intermediate", "Advanced", etc.
  mentorId: number;
  mentorName: string;
  schedule: string;         // e.g. "Mon/Wed 14:00-15:00"
  price: number;
  capacity: number;
  enrolledCount: number;
  description: string;
  status: "active" | "cancelled" | "full";
};
```

### Lesson
```typescript
type Lesson = {
  id: number;
  courseId: number;
  moduleNumber: number;
  title: string;
  content: string;          // lesson description
  videoUrl?: string;        // lesson video/audio URL
  materials: LessonMaterial[];  // PDF sheets, tabs, etc.
  order: number;             // sequence within course
  quizId?: number;           // optional quiz
  duration: number;          // in minutes
};
```

### LessonMaterial
```typescript
type LessonMaterial = {
  id: number;
  lessonId: number;
  name: string;             // e.g. "C Major Scale Sheet"
  type: "pdf" | "tab" | "chord_chart" | "audio";
  url: string;               // download URL
};
```

### Registration
```typescript
type Registration = {
  id: number;
  studentId: number;
  courseId: number;
  instrument: string;
  requestedLevel: string;    // custom level text
  preferredSchedule?: string;
  packageId: number;
  status: "pending" | "approved" | "rejected";
  requestDate: string;
  responseDate?: string;
  adminNotes?: string;
  invoiceId?: number;
};
```

### Invoice
```typescript
type Invoice = {
  id: number;
  registrationId: number;
  studentId: number;
  amount: number;
  discountCode?: string;     // applied discount
  discountedAmount: number;
  paymentPlan: "full" | "2x" | "3x";
  installmentsPaid: number;
  status: "pending" | "paid" | "overdue";
  issuedDate: string;
  paidDate?: string;
  manualConfirmation: boolean;  // no payment gateway
};
```

### Payment
```typescript
type Payment = {
  id: number;
  invoiceId: number;
  amount: number;
  date: string;
  method: "cash" | "transfer" | "other";
  status: "confirmed" | "pending";
  confirmedBy?: number;  // admin user ID
};
```

### Attendance
```typescript
type Attendance = {
  id: number;
  studentId: number;
  courseId: number;
  lessonId: number;
  classDate: string;
  status: "present" | "absent" | "late" | "excused";
  markedBy: number;      // mentor user ID
  notes?: string;
};
```

### PracticeLog
```typescript
type PracticeLog = {
  id: number;
  studentId: number;
  date: string;
  duration: number;        // in minutes
  pieces: string[];         // pieces practiced
  notes?: string;
  goalId?: number;          // linked goal if any
};
```

### Certificate
```typescript
type Certificate = {
  id: number;
  studentId: number;
  courseId: number;
  issuedDate: string;
  certificateUrl: string;    // view/download URL
  mentorSignature: string;
  status: "active" | "revoked";
};
```

### QuizResult
```typescript
type QuizResult = {
  id: number;
  studentId: number;
  lessonId: number;
  score: number;            // 0-100
  date: string;
  passed: boolean;
};
```

### Goal
```typescript
type Goal = {
  id: number;
  studentId: number;
  description: string;      // e.g. "Master C major scale"
  target: number;            // target value (hours, pieces, etc.)
  current: number;           // current progress
  unit: "hours" | "pieces" | "sessions";
  deadline?: string;
  status: "active" | "completed";
};
```

### Package
```typescript
type Package = {
  id: number;
  name: string;             // e.g. "8 Sessions Pack"
  sessions: number;
  price: number;
  description: string;
  status: "active" | "inactive";
};
```

### Announcement
```typescript
type Announcement = {
  id: number;
  title: string;
  content: string;
  date: string;
  targetAudience: ("all" | "students" | "mentors" | "parents")[];
  isPublic: boolean;        // shows on public site too
  type: "info" | "warning" | "closure" | "achievement";
};
```

### Photo
```typescript
type Photo = {
  id: number;
  title: string;
  url: string;
  category: "recital" | "class" | "event" | "portfolio";
  eventDate?: string;
  taggedStudentIds: number[];
  isPublic: boolean;
};
```

### Discount
```typescript
type Discount = {
  id: number;
  code: string;             // e.g. "EARLYBIRD20"
  type: "percentage" | "fixed";
  value: number;             // 20 for 20% or 50000 for Rp50000
  validUntil: string;
  usageCount: number;
  maxUsage: number;
  applicableTo: ("course" | "package")[];
};
```

### MentorAvailability
```typescript
type MentorAvailability = {
  id: number;
  mentorId: number;
  date: string;
  startTime: string;
  endTime: string;
  status: "available" | "blocked" | "booked";
};
```

### MentorLeave
```typescript
type MentorLeave = {
  id: number;
  mentorId: number;
  startDate: string;
  endDate: string;
  reason: string;
  status: "pending" | "approved" | "rejected";
  substituteMentorId?: number;
};
```

### MentorTimeLog
```typescript
type MentorTimeLog = {
  id: number;
  mentorId: number;
  studentId: number;
  date: string;
  hours: number;
  notes?: string;
};
```

### MentorReview
```typescript
type MentorReview = {
  id: number;
  mentorId: number;
  reviewerId: number;       // admin user ID
  rating: number;            // 1-5
  comments: string;
  period: string;            // e.g. "Q1 2026"
  date: string;
};
```

### StudioClosure
```typescript
type StudioClosure = {
  id: number;
  date: string;
  reason: string;
  affectedClassIds: number[];
  makeupScheduled?: string;
};
```

### ConferenceBooking
```typescript
type ConferenceBooking = {
  id: number;
  parentId: number;
  mentorId: number;
  date: string;
  time: string;
  status: "pending" | "confirmed" | "cancelled";
  notes?: string;
};
```

### NewsArticle
```typescript
type NewsArticle = {
  id: number;
  title: string;
  date: string;
  seed: string;              // picsum.photos seed
  excerpt: string;
  content: string;
  status: "published" | "draft";
};
```

### Message
```typescript
type Message = {
  id: number;
  fromId: number;
  fromName: string;
  toId: number;
  lastMsg: string;
  time: string;              // relative time e.g. "2h ago"
  unread: number;
  avatar: string;
  groupIds?: number[];        // for batch messages
};
```

### EmergencyContact
```typescript
type EmergencyContact = {
  name: string;
  relationship: string;       // "Parent", "Guardian", "Sibling"
  phone: string;
  medicalNotes?: string;       // allergies, conditions
};
```

---

## 4. DB Helper Functions (`src/lib/db.ts`)

### User Helpers
| Function | Signature | Purpose |
|----------|-----------|---------|
| `getUserByEmail` | `(email: string) => User \| undefined` | Find user by email |
| `validateUser` | `(email, password) => Omit<User,"password"> \| null` | Login validation |
| `getUsersByRole` | `(role: string) => Omit<User,"password">[]` | List users by role |
| `getAllUsers` | `() => Omit<User,"password">[]` | All users (no passwords) |
| `updateUser` | `(id, data) => User \| null` | Update user fields |
| `verifyUserPassword` | `(id, password) => boolean` | Verify current password |

### Student Helpers
| Function | Signature | Purpose |
|----------|-----------|---------|
| `getStudentByUserId` | `(userId: number) => Student \| undefined` | Student profile from user |
| `getAllStudents` | `() => Student[]` | All students |
| `getStudentsByMentorId` | `(mentorId: number) => Student[]` | Mentor's assigned students |
| `getStudentsByParentId` | `(parentId: number) => Student[]` | Parent's linked students |
| `updateStudent` | `(id, data) => Student \| null` | Update student fields |

### Course & Lesson Helpers
| Function | Signature | Purpose |
|----------|-----------|---------|
| `getAllCourses` | `() => Course[]` | All courses |
| `getCourseById` | `(id: number) => Course \| undefined` | Single course |
| `getCoursesByInstrument` | `(instrument: string) => Course[]` | Filter by instrument |
| `getLessonsByCourseId` | `(courseId: number) => Lesson[]` | Lessons for a course |
| `getLessonById` | `(id: number) => Lesson \| undefined` | Single lesson |
| `markLessonComplete` | `(lessonId: number, studentId: number) => void` | Mark complete |

### Registration & Invoice Helpers
| Function | Signature | Purpose |
|----------|-----------|---------|
| `getAllRegistrations` | `() => Registration[]` | All registrations |
| `getRegistrationsByStudentId` | `(studentId: number) => Registration[]` | Student's registrations |
| `createRegistration` | `(data: Partial<Registration>) => Registration` | Submit registration request |
| `updateRegistrationStatus` | `(id, status, notes?) => void` | Approve/reject |
| `getInvoiceById` | `(id: number) => Invoice \| undefined` | Single invoice |
| `createInvoice` | `(registrationId: number) => Invoice` | Generate invoice after approval |
| `confirmPayment` | `(invoiceId: number) => void` | Manual payment confirmation |
| `applyDiscount` | `(invoiceId: number, code: string) => boolean` | Apply discount code |

### Attendance & Practice Helpers
| Function | Signature | Purpose |
|----------|-----------|---------|
| `markAttendance` | `(studentId, lessonId, status) => void` | Mentor marks attendance |
| `getAttendanceByStudentId` | `(studentId: number) => Attendance[]` | Student's attendance |
| `getAttendanceRate` | `(studentId: number) => number` | Calculate attendance % |
| `addPracticeLog` | `(studentId, data) => PracticeLog` | Log practice session |
| `getPracticeLogsByStudentId` | `(studentId: number) => PracticeLog[]` | Student's practice history |
| `getPracticeStats` | `(studentId: number) => {totalHours, streak, pieces}` | Practice statistics |

### Certificate & Report Helpers
| Function | Signature | Purpose |
|----------|-----------|---------|
| `generateCertificate` | `(studentId, courseId) => Certificate` | Auto-generate on completion |
| `getCertificatesByStudentId` | `(studentId: number) => Certificate[]` | Student's certificates |
| `generateProgressReport` | `(studentId: number) => ProgressReport` | Monthly PDF report |
| `revokeCertificate` | `(certId: number) => void` | Admin revoke certificate |

### Payment & Package Helpers
| Function | Signature | Purpose |
|----------|-----------|---------|
| `getAllPayments` | `() => Payment[]` | All payments |
| `getPaymentsByStudentId` | `(studentId: number) => Payment[]` | Student's payments |
| `createPayment` | `(invoiceId, data) => Payment` | Record payment |
| `getAllPackages` | `() => Package[]` | All packages |
| `getPackageById` | `(id: number) => Package \| undefined` | Single package |
| `updatePackage` | `(id, data) => Package \| null` | Update package |

### Mentor Helpers
| Function | Signature | Purpose |
|----------|-----------|---------|
| `getMentorAvailability` | `(mentorId: number) => MentorAvailability[]` | Mentor's availability |
| `setMentorAvailability` | `(mentorId, slots) => void` | Set available slots |
| `createMentorLeave` | `(mentorId, data) => MentorLeave` | Request leave |
| `getTimeLogsByMentorId` | `(mentorId: number) => MentorTimeLog[]` | Mentor's time logs |
| `createTimeLog` | `(mentorId, data) => MentorTimeLog` | Log teaching hours |
| `getMentorReviews` | `(mentorId: number) => MentorReview[]` | Mentor's reviews |
| `addMentorReview` | `(mentorId, data) => MentorReview` | Admin adds review |

### Misc Helpers
| Function | Signature | Purpose |
|----------|-----------|---------|
| `getAllAnnouncements` | `() => Announcement[]` | All announcements |
| `getAllPhotos` | `() => Photo[]` | Gallery photos |
| `getAllDiscounts` | `() => Discount[]` | All discount codes |
| `validateDiscount` | `(code: string) => Discount \| null` | Check if code valid |
| `getAllStudioClosures` | `() => StudioClosure[]` | All closure dates |
| `getConferenceBookings` | `(parentId?: number) => ConferenceBooking[]` | Conference bookings |
| `createQuizResult` | `(studentId, lessonId, score) => QuizResult` | Record quiz score |
| `createGoal` | `(studentId, data) => Goal` | Set learning goal |
| `updateGoalProgress` | `(goalId, current) => void` | Update goal progress |
| `getAllMessages` | `() => Message[]` | All messages (enhanced) |
| `sendBatchMessage` | `(fromId, group, content) => void` | Send to group |

---

## 5. Auth System (`src/lib/auth.tsx`)

### AuthContextType
```typescript
type AuthContextType = {
  user: Omit<User, "password"> | null;
  login: (email: string, password: string) => boolean;
  logout: () => void;
  hasPermission: (route: string) => boolean;
  updateUser: (data: Partial<UpdatableUserFields>) => void;
  verifyPassword: (password: string) => boolean;
  switchLanguage: (lang: "id" | "en") => void;
};
```

### Permission Map
```typescript
const rolePermissions: Record<string, string[]> = {
  "Super Admin": ["all"],
  "Admin": ["dashboard", "students", "class-management", "registration-requests", "invoices", "lesson-management", "bookings", "users", "roles", "cms", "finance", "messages", "attendance", "certificates", "announcements", "mentor-management", "packages", "studio-settings", "settings"],
  "Finance": ["dashboard", "finance", "invoices", "users"],
  "Content Editor": ["dashboard", "cms"],
  "Mentor": ["mentor", "mentor/my-students", "mentor/attendance", "mentor/lesson-notes", "mentor/grading", "mentor/schedule", "mentor/time-tracking", "mentor/leave", "mentor/messages", "mentor/performance", "mentor/availability", "mentor/profile"],
  "Student": ["student", "student/courses", "student/schedule", "student/reschedule", "student/practice", "student/certificates", "student/progress-reports", "student/goals", "student/attendance", "student/messages", "student/profile"],
  "Parent": ["parent", "parent/children", "parent/payments", "parent/attendance", "parent/messages", "parent/conference", "parent/profile"],
};
```

### Auth Flow
1. User submits login form → `AuthContext.login(email, password)`
2. `validateUser()` checks mock DB → returns user without password
3. User stored in `useState` + `localStorage` as `"tw_user"`
4. **Redirect logic**: If `enrollmentStatus === "none"` → `/register`; if approved → role-based dashboard
5. `useAuth()` returns current user + methods
6. Layouts check `user` → redirect to `/login` if null
7. `hasPermission(route)` checks rolePermissions for nav/route access
8. `logout()` clears state + localStorage → redirects to `/login`

---

## 6. Protected Routes

| Route | Redirect if unauthenticated |
|-------|---------------------------|
| `/dashboard/*` | `/login` |
| `/mentor/*` | `/login` |
| `/student/*` | `/login` |
| `/parent/*` | `/login` |
| `/register` | Accessible to all (auth-aware: pre-fills if logged in) |
| `/login` | Accessible to all (auto-redirect if already logged in) |

---

## 7. Component Patterns

### "use client" Directive
All interactive components must use `"use client"` at top of file.

### Lightbox/Modal Pattern
- Rendered conditionally: `{show && <Modal onClose={() => setShow(false)} />}`
- Escape key + click-outside to close
- Keyboard nav for image lightboxes (ArrowLeft, ArrowRight)

### Auto-Rotate Pattern
```typescript
useEffect(() => {
  const t = setInterval(() => {
    setVisible(false);
    setTimeout(() => { setIdx(i => (i + 1) % items.length); setVisible(true); }, 500);
  }, INTERVAL_MS);
  return () => clearInterval(t);
}, []);
```

### Role-Based Nav Filtering
```typescript
const nav = allNav.filter((n) => user && (user.role === "Super Admin" || n.roles.includes(user.role)));
```

### Registration Flow Pattern
```typescript
// Request → Approve → Invoice → Payment → Schedule
const handleRegistration = async (data) => {
  const reg = createRegistration(data);       // Step 1: Submit request
  // Admin reviews → updateRegistrationStatus(reg.id, "approved")
  // → createInvoice(reg.id)                     // Step 2: Invoice generated
  // → confirmPayment(invoice.id)                // Step 3: Manual payment
  // → assignSchedule(reg.studentId, reg.courseId) // Step 4: Schedule assigned
};
```

### Practice Log Pattern
```typescript
// Quick-add form with auto-update
const handleAddPractice = (data) => {
  addPracticeLog(studentId, data);
  updateGoalProgress(goalId, data.duration);  // auto-update linked goals
  // streak calculation happens in getPracticeStats
};
```

### Attendance Marking Pattern
```typescript
// One-click mark with bulk options
const markAllPresent = (studentIds, lessonId, date) => {
  studentIds.forEach(id => markAttendance(id, lessonId, "present"));
};
```

---

## 8. Styling Conventions

- **No CSS modules** — use Tailwind utility classes directly in JSX
- **Theme tokens** via `@theme inline` in `globals.css`
- **Pastel palette**: pink, blue, green, yellow, purple — used for backgrounds, avatars, hover states
- **Accent**: `accent-primary` (#B8C0FF) for primary actions, avatars
- **Text**: `text-primary` (#333) for headings/body, `text-secondary` (#666) for muted text
- **Borders**: `border-border` for all borders
- **Transitions**: `transition-colors` for hover, `animate-fadeIn` for modals/lightboxes
- **No `@apply`** in CSS files

---

## 9. Image Handling

- **Next.js Image** component with `fill`, `sizes`, `className="object-cover"`
- **Source**: `picsum.photos/seed/{seed}/600/400` for placeholders
- **Lightbox**: full-size images in modal overlay
- **Avatars**: colored divs with initials/character (no image)
- **Gallery**: recital/event photos with tagging support

---

## 10. Build & Dev (Local Only)

**No Vercel or Supabase:** This project is built and run entirely locally. No cloud hosting, no Vercel deployment, no Supabase backend.

| Command | Purpose |
|---------|---------|
| `npm run dev` | Start local dev server (Turbopack, port 3000) |
| `npm run build` | Local production build (Turbopack) |
| `npm run start` | Start local production server |

### Local Development Only
- No Vercel deployment or hosting
- No Supabase database or authentication
- Mock DB (`src/lib/db.ts`) runs in-memory client-side
- Auth uses React Context + localStorage (no external services)
- All data persists only in browser localStorage
- WhatsApp notifications: opens WhatsApp Web with pre-filled message (no API integration)

### Known Issues
- **Port 3000 in use**: Kill process with `Stop-Process -Id (Get-NetTCPConnection -LocalPort 3000).OwningProcess -Force`
- **Build cache**: Delete `.next/` if old routes persist after file moves
- **Unicode escapes**: Use `Write` not `Edit` when replacing non-ASCII characters

---

## 11. TypeScript Strictness

- Target: `ES2017`
- Module: `esnext`
- Module Resolution: `bundler`
- Strict: `true`
- JSX: `preserve`
- No implicit any: enforced
- All DB helper return types explicitly annotated

---

## 12. Mock Data (Initial State)

| Entity | Records | Purpose |
|--------|---------|---------|
| Users | 14 | 7 roles × 2 each (demo accounts) |
| Students | 8 | Student dashboard data, linked to Users |
| Parents | 4 | Parent portal, 2+ children each |
| Courses | 9 | 3 instruments × 3 levels |
| Lessons | 27 | 3 lessons per course |
| Registrations | 8 | Pending + approved requests |
| Invoices | 8 | Pending + paid invoices |
| Payments | 15 | Payment history |
| Attendance | 60 | Attendance records |
| PracticeLogs | 20 | Practice sessions |
| Certificates | 2 | Completion certificates |
| QuizResults | 10 | Lesson quiz scores |
| Goals | 8 | Student learning goals |
| Packages | 5 | Subscription packages |
| Announcements | 6 | Studio announcements |
| Photos | 15 | Gallery items (recitals, events) |
| Discounts | 4 | Coupon codes |
| MentorAvailability | 40 | Mentor time slots |
| MentorLeave | 3 | Leave requests |
| MentorTimeLog | 20 | Teaching hours |
| MentorReview | 8 | Performance reviews |
| StudioClosures | 3 | Closure dates |
| ConferenceBookings | 5 | Parent-teacher conferences |
| Messages | 12 | Messaging system (enhanced) |
| NewsArticles | 3 | CMS news management |
| LessonMaterials | 27 | PDF sheets, tabs per lesson |

---

## 12. Responsive Design (All Devices)

**v1 is fully responsive** — works on phone (320px+), tablet (768px+), and desktop (1024px+).

### Breakpoints
| Breakpoint | Tailwind Prefix | Target Device |
|------------|------------------|---------------|
| `sm:` | 640px+ | Large phone (landscape) |
| `md:` | 768px+ | Tablet |
| `lg:` | 1024px+ | Small desktop / large tablet |
| `xl:` | 1280px+ | Desktop |
| `2xl:` | 1536px+ | Large desktop |

### Layout Patterns
| Component | Mobile (<768px) | Tablet (768px-1024px) | Desktop (1024px+) |
|-----------|-------------------|--------------------------|---------------------|
| Sidebar | Hidden, hamburger menu slides in | Collapsible, w-48 or overlay | Fixed w-60 (240px) |
| Main Content | Full width, p-4 | p-6, max-w-none | p-6, max-w-none |
| Cards Grid | grid-cols-1 | grid-cols-2 | grid-cols-3 |
| Tables | Horizontal scroll (overflow-x-auto) | Scroll or compact view | Full width |
| Header Nav | Hamburger menu, stacked links | Partial nav + hamburger | Full nav, right-aligned items |
| Course Catalog | 1 column, full width | 2 columns | 3 columns |
| Dashboard Stats | 1 col (stacked) | 2 cols | 3-4 cols |

### Component Rules
- **Sidebar**: `hidden md:block` for desktop; `fixed inset-0 z-50` + overlay for mobile toggle
- **Hamburger**: `md:hidden` button, opens/closes sidebar via state
- **Grids**: Always use responsive grid (`grid-cols-1 md:grid-cols-2 lg:grid-cols-3`)
- **Tables**: Wrap in `div className="overflow-x-auto"` on all screen sizes
- **Forms**: Full width inputs (`w-full`), stack vertically on mobile
- **Modals**: `max-w-[95vw] sm:max-w-lg` (nearly full width on mobile)
- **Text**: `text-sm md:text-base` (slightly smaller on mobile)
- **Padding**: `p-4 md:p-6` (less padding on mobile)
- **Gaps**: `gap-3 md:gap-4` (tighter on mobile)

### Mobile-Specific UX
- **Touch targets**: Minimum `h-10` (40px) for buttons, `p-3` for clickable items
- **No hover states on mobile**: Use `hover:bg-*` with care (touch devices ignore hover)
- **Viewport**: `<meta name="viewport" content="width=device-width, initial-scale=1">` in layout
- **Tap highlight**: `-webkit-tap-highlight-color: transparent` for clean taps

### Testing Checklist
- [ ] 320px (small phone) — sidebar hidden, hamburger works, no horizontal overflow
- [ ] 375px (iPhone) — all pages render, forms usable
- [ ] 768px (iPad) — tablet layout, sidebar collapsible
- [ ] 1024px (small desktop) — full sidebar visible
- [ ] 1920px (large desktop) — no stretched content, max-width respected
