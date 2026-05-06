# Twhole Studio — Design Guidance (v1)

## 1. Design Philosophy

Twhole Studio uses a **pastel, soft, and approachable** visual language. The design should feel welcoming, creative, and calm — reflecting a music studio environment. No harsh colors, no sharp edges, no aggressive contrasts.

**Core principles:**
- Pastel everywhere (backgrounds, avatars, hover states)
- Rounded corners (default: `rounded-lg`, `rounded-xl`, `rounded-full`)
- Soft shadows (`shadow-lg` for modals, `border-border` for subtle separation)
- Minimal but clear (plenty of whitespace, no clutter)

---

## 2. Color Palette

Defined in `src/app/globals.css` via `@theme inline`:

| Token | Hex | Usage |
|-------|-----|---------|
| `--color-background` | `#FFFFFF` | Page backgrounds |
| `--color-pastel-pink` | `#FFE5E5` | Pink accents, error backgrounds |
| `--color-pastel-blue` | `#E5F0FF` | Blue accents, hover states, info backgrounds |
| `--color-pastel-green` | `#E5FFE5` | Green accents, student avatars, success states |
| `--color-pastel-yellow` | `#FFFDE5` | Yellow accents, warning states |
| `--color-pastel-purple` | `#F3E5FF` | Purple accents |
| `--color-accent-primary` | `#B8C0FF` | Primary actions, avatars, active states |
| `--color-accent-secondary` | `#FFD6E0` | Secondary actions, hover variant |
| `--color-text-primary` | `#333333` | Headings, body text |
| `--color-text-secondary` | `#666666` | Muted text, labels, descriptions |
| `--color-text-light` | `#999999` | Placeholder text, metadata |

### Semantic Aliases (use these in components)
- **Success**: `text-green-600` (not a theme token — use Tailwind default)
- **Error**: `text-error` (maps to pastel-pink/red)
- **Border**: `border-border` (subtle #e5e5e5)

---

## 3. Typography

| Level | Class | Size | Weight | Usage |
|-------|-------|------|--------|---------|
| Page Title | `text-2xl font-bold` | 24px | 700 | Page headers (e.g., "My Profile") |
| Section Title | `text-xl font-semibold` | 20px | 600 | Section headers within pages |
| Body Text | `text-sm` | 14px | 400 | Standard body, labels |
| Small Text | `text-xs` | 12px | 400 | Metadata, email, dates |
| Label | `text-sm font-medium` | 14px | 500 | Form labels |

**Font family:** Inter (via Google Fonts, variable: `--font-sans`)

---

## 4. Layout Patterns

### Public Pages (`/`)
- Max width: `max-w-7xl mx-auto`
- Section padding: `py-16 px-6` (generous vertical space)
- Background: `bg-background` (white)
- Alternating: some sections can use `bg-background-alt` (light gray) for visual separation

### Dashboard Layout (`/dashboard/*`, `/student/*`)
```
┌──────────┬──────────────────────────────┐
│          │  Header (h-16, border-b)    │
│          │  [messages] [avatar▼]        │
│ Sidebar  ├──────────────────────────────┤
│ (w-60)  │                              │
│          │  Main Content (p-6)          │
│ bg-white │  max-w-none (full width)     │
│ border-r │                              │
└──────────┴──────────────────────────────┘
```

- **Sidebar**: `w-60` (240px), `bg-white`, `border-r border-border`
- **Header**: `h-16`, `bg-white`, `border-b`, `justify-end` (right-aligned)
- **Main**: `p-6`, `flex-1`, `overflow-auto`

---

## 5. Component Styling

### Cards
```jsx
<div className="bg-white rounded-xl border border-border p-6">
  ...
</div>
```
- White background, rounded-xl, subtle border
- Padding: `p-6` (24px)
- Space between cards: `space-y-6` or `mt-6`

### Buttons
| Variant | Classes | Usage |
|----------|----------|---------|
| Primary | `px-5 py-2.5 bg-accent-primary text-text-primary font-medium rounded-lg hover:bg-accent-secondary transition-colors` | Save, Login, Submit |
| Danger | `text-error hover:bg-pastel-pink transition-colors` | Logout, delete actions |
| Link | `text-accent-primary hover:text-accent-secondary` | "Change Photo", navigation links |

### Form Inputs
```jsx
<input
  type="text"
  className="w-full px-4 py-2.5 border border-border rounded-lg text-text-primary focus:outline-none focus:border-accent-primary"
  // NEVER use focus:ring (not in design system)
/>
```
- No focus rings — use `focus:border-accent-primary` instead
- Height: `py-2.5` (40px)
- Border: `border-border` always

### Tables
```jsx
<table className="w-full text-sm">
  <thead>
    <tr className="border-b border-border text-text-secondary">
      <th className="text-left py-3 px-4">...</th>
    </tr>
  </thead>
  <tbody>
    <tr className="border-b border-border hover:bg-pastel-blue transition-colors">
      <td className="py-3 px-4">...</td>
    </tr>
  </tbody>
</table>
```
- Row hover: `hover:bg-pastel-blue`
- Badges: `{status}` → colored pill badges (see Badges below)

### Badges (Status Pills)
```jsx
<span className="px-2.5 py-0.5 rounded-full text-xs font-medium
  {status === 'active' ? 'bg-pastel-green text-green-700' :
   status === 'pending' ? 'bg-pastel-yellow text-yellow-700' :
   'bg-pastel-pink text-red-700'}">
  {status}
</span>
```

### Avatars
```jsx
{/* Colored circle with initial */}
<div className="w-9 h-9 rounded-full bg-pastel-green flex items-center justify-center text-sm font-medium shrink-0">
  {user.avatar || "U"}
</div>

{/* Larger profile avatar */}
<div className="w-20 h-20 rounded-full bg-pastel-green flex items-center justify-center text-2xl font-medium shrink-0">
  {user.avatar || "S"}
</div>
```
- Color by role/user: `pastel-green` (students), `accent-primary` (admin), `pastel-blue` (mentors)
- Always `rounded-full`, always `shrink-0`

---

## 6. Navigation Patterns

### Sidebar Nav (Active State)
```jsx
<Link
  href={n.href}
  className={`flex items-center gap-3 px-3 py-2.5 rounded-lg text-sm font-medium transition-colors ${
    pathname === n.href
      ? "bg-accent-primary/20 text-text-primary"  // active
      : "text-text-secondary hover:bg-pastel-blue"  // inactive
  }`}
>
  <span className="w-5 text-center">{n.icon}</span>
  {n.label}
</Link>
```
- Active: `bg-accent-primary/20` (light purple tint)
- Hover: `hover:bg-pastel-blue`
- Icons: emoji (◫, 👤, 📅, ✉, etc.)

### Header Nav (Public Site)
- Sticky: `sticky top-0 z-50 bg-white/90 backdrop-blur`
- Links: `text-text-secondary hover:text-accent-primary`
- Login button: `px-5 py-2 bg-accent-primary text-text-primary rounded-lg`

---

## 7. Modals & Lightboxes

### Lightbox (Full-screen image viewer)
```jsx
<div className="fixed inset-0 z-50 bg-black/80 flex items-center justify-center animate-fadeIn">
  <img src={...} className="max-h-[90vh] max-w-[90vw] object-contain" />
  {/* Close, prev, next buttons */}
</div>
```
- Backdrop: `bg-black/80`
- Entry: `animate-fadeIn` (opacity 0→1 in 0.3s)
- Keyboard: ArrowLeft, ArrowRight, Escape
- Content: `max-h-[90vh] max-w-[90vw] object-contain`

### Modal (Form/information dialog)
```jsx
<div className="fixed inset-0 z-50 bg-black/50 flex items-center justify-center p-4">
  <div className="bg-white rounded-2xl shadow-lg w-full max-w-lg p-6 animate-fadeIn">
    ...
  </div>
</div>
```
- Width: `max-w-lg` (512px) for forms, `max-w-2xl` (672px) for tables
- Padding: `p-6`
- Close: Escape key + click outside (`fixed inset-0` overlay)

### Dropdown Menu
```jsx
<div className="absolute right-0 top-12 w-44 bg-white rounded-lg border border-border shadow-lg py-1 z-50 animate-fadeIn">
  <button className="w-full text-left px-4 py-2.5 text-sm text-text-primary hover:bg-pastel-blue transition-colors">
    Edit Profile
  </button>
  <div className="my-1 border-t border-border" />
  <button className="w-full text-left px-4 py-2.5 text-sm text-error hover:bg-pastel-pink transition-colors">
    Logout
  </button>
</div>
```
- Width: `w-44` (176px)
- Items: full-width, left-aligned, hover states
- Divider: `border-t border-border` with `my-1` margin

---

## 8. Animations & Transitions

### Available Animations (globals.css)
```css
@keyframes fadeIn { from { opacity: 0; } to { opacity: 1; } }
.animate-fadeIn { animation: fadeIn 0.3s ease-out; }
```

### Auto-Rotate Pattern
- Banners: 5s interval, 500ms fade transition
- Mentors: 6s interval, fade + slide
- Testimonials: 5s interval, fade only
- Always clean up interval on unmount: `return () => clearInterval(t)`

### Hover Transitions
- Buttons: `transition-colors` (not `transition-all`)
- Nav items: `transition-colors`
- Never use `transition-transform` (not in design system)

---

## 9. Responsive Design (All Devices)

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

---

## 10. Image Guidelines

### Sources
- **Placeholders**: `https://picsum.photos/seed/{seed}/600/400`
- **Next.js Image**: always use `fill` + `sizes` + `className="object-cover"`
- **Lightbox**: full-size images (no `fill`, just `max-h-[90vh] max-w-[90vw]`)

### Aspect Ratios (by section)
| Section | Dimensions | Aspect |
|---------|-----------|--------|
| Banner | 600×400 (seed) | 3:2 |
| Gallery | 600×400 (seed) | 3:2 |
| Mentor photos | 600×400 (seed) | 3:2 |
| News hero | 600×400 (seed) | 3:2 |
| Avatars | 36×36 or 80×80 | 1:1 |

---

## 11. Icon Strategy

**Emoji-based icons** (no icon library):

| Context | Emoji | Meaning |
|---------|-------|---------|
| Dashboard | ◫ | Overview |
| Students | 👤 | Student management |
| Bookings | 📅 | Scheduling |
| Users | 👥 | User management |
| Roles | ⚙ | Role management |
| CMS | ✎ | Content management |
| Finance | 💰 | Financial data |
| Messages | ✉ | Messaging |
| Settings | ⚙ | Settings |
| Courses | 🎵 | Music courses |
| Reschedule | 🔄 | Rescheduling |
| Profile | 👤 | User profile |
| Unread badge | (dot) | `w-2 h-2 bg-error rounded-full` |

---

## 12. New Component Styling (v1 Features)

### Course Catalog
```jsx
<div className="grid grid-cols-1 md:grid-cols-3 gap-6">
  <div className="bg-white rounded-xl border border-border p-6 hover:shadow-lg transition-shadow">
    <div className="w-full h-40 bg-pastel-blue rounded-lg mb-4 flex items-center justify-center text-4xl">
      🎹
    </div>
    <h3 className="text-lg font-semibold text-text-primary">{course.name}</h3>
    <p className="text-sm text-text-secondary mt-1">{course.instrument} • {course.level}</p>
    <p className="text-sm text-text-secondary">{course.schedule}</p>
    <p className="text-lg font-bold text-text-primary mt-2">Rp{course.price.toLocaleString()}</p>
    <button className="mt-4 w-full px-5 py-2.5 bg-accent-primary text-text-primary font-medium rounded-lg hover:bg-accent-secondary transition-colors">
      Register
    </button>
  </div>
</div>
```

### Registration Form
```jsx
<form className="max-w-lg mx-auto bg-white rounded-2xl shadow-lg p-6">
  <h2 className="text-2xl font-bold text-text-primary mb-6">Register for a Class</h2>
  <div className="space-y-4">
    <div>
      <label className="text-sm font-medium text-text-primary">Instrument</label>
      <select className="w-full px-4 py-2.5 border border-border rounded-lg text-text-primary focus:outline-none focus:border-accent-primary">
        <option>Piano</option>
        <option>Guitar</option>
        <option>Violin</option>
      </select>
    </div>
    <div>
      <label className="text-sm font-medium text-text-primary">Level</label>
      <input type="text" placeholder="e.g. Beginner, Intermediate" className="w-full px-4 py-2.5 border border-border rounded-lg text-text-primary focus:outline-none focus:border-accent-primary" />
    </div>
    <div>
      <label className="text-sm font-medium text-text-primary">Package</label>
      <div className="space-y-2">
        {packages.map(p => (
          <div key={p.id} className="flex items-center justify-between p-3 border border-border rounded-lg hover:bg-pastel-blue cursor-pointer">
            <div>
              <p className="font-medium text-text-primary">{p.name}</p>
              <p className="text-sm text-text-secondary">{p.sessions} sessions</p>
            </div>
            <p className="font-bold text-text-primary">Rp{p.price.toLocaleString()}</p>
          </div>
        ))}
      </div>
    </div>
  </div>
</form>
```

### Practice Log
```jsx
<div className="bg-white rounded-xl border border-border p-6">
  <h3 className="text-xl font-semibold text-text-primary mb-4">Log Practice</h3>
  <div className="grid grid-cols-2 gap-4">
    <input type="date" className="px-4 py-2.5 border border-border rounded-lg" />
    <input type="number" placeholder="Duration (minutes)" className="px-4 py-2.5 border border-border rounded-lg" />
  </div>
  <textarea placeholder="Pieces practiced, notes..." className="w-full mt-4 px-4 py-2.5 border border-border rounded-lg h-24" />
  <button className="mt-4 px-5 py-2.5 bg-accent-primary text-text-primary font-medium rounded-lg">
    Save Practice Log
  </button>
  {/* Stats */}
  <div className="mt-6 grid grid-cols-3 gap-4">
    <div className="bg-pastel-green p-4 rounded-lg text-center">
      <p className="text-2xl font-bold text-green-700">{totalHours}h</p>
      <p className="text-sm text-text-secondary">Total Hours</p>
    </div>
    <div className="bg-pastel-blue p-4 rounded-lg text-center">
      <p className="text-2xl font-bold text-blue-700">{streak}</p>
      <p className="text-sm text-text-secondary">Day Streak</p>
    </div>
    <div className="bg-pastel-yellow p-4 rounded-lg text-center">
      <p className="text-2xl font-bold text-yellow-700">{pieces}</p>
      <p className="text-sm text-text-secondary">Pieces Learned</p>
    </div>
  </div>
</div>
```

### Attendance Marker
```jsx
<div className="bg-white rounded-xl border border-border p-6">
  <h3 className="text-xl font-semibold mb-4">Today's Attendance</h3>
  <table className="w-full text-sm">
    <thead>
      <tr className="border-b border-border text-text-secondary">
        <th className="text-left py-3 px-4">Student</th>
        <th className="text-center py-3 px-4">Status</th>
      </tr>
    </thead>
    <tbody>
      {students.map(s => (
        <tr key={s.id} className="border-b border-border">
          <td className="py-3 px-4">{s.name}</td>
          <td className="py-3 px-4 text-center">
            <div className="flex gap-2 justify-center">
              <button className="px-3 py-1 rounded-full text-xs bg-pastel-green text-green-700 hover:bg-green-200">Present</button>
              <button className="px-3 py-1 rounded-full text-xs bg-pastel-pink text-red-700 hover:bg-red-200">Absent</button>
              <button className="px-3 py-1 rounded-full text-xs bg-pastel-yellow text-yellow-700 hover:bg-yellow-200">Late</button>
            </div>
          </td>
        </tr>
      ))}
    </tbody>
  </table>
</div>
```

### Certificate Display
```jsx
<div className="bg-white rounded-2xl border border-border p-8 max-w-2xl mx-auto">
  <div className="text-center border-4 border-accent-primary p-8 rounded-xl">
    <div className="text-6xl mb-4">🎓</div>
    <h2 className="text-3xl font-bold text-text-primary">Certificate of Completion</h2>
    <p className="text-text-secondary mt-2">This certifies that</p>
    <p className="text-2xl font-semibold text-accent-primary mt-2">{studentName}</p>
    <p className="text-text-secondary mt-2">has successfully completed</p>
    <p className="text-xl font-medium text-text-primary mt-1">{courseName}</p>
    <div className="mt-6 flex items-center justify-center gap-8">
      <div className="text-center">
        <p className="text-sm text-text-secondary">Date</p>
        <p className="font-medium">{date}</p>
      </div>
      <div className="text-center">
        <p className="text-sm text-text-secondary">Mentor</p>
        <p className="font-medium">{mentorName}</p>
      </div>
    </div>
  </div>
  <button className="mt-6 w-full px-5 py-2.5 bg-accent-primary text-text-primary font-medium rounded-lg">
    Download PDF
  </button>
</div>
```

### Goals & Milestones
```jsx
<div className="bg-white rounded-xl border border-border p-6">
  <h3 className="text-xl font-semibold mb-4">Learning Goals</h3>
  <div className="space-y-4">
    {goals.map(g => (
      <div key={g.id} className="p-4 border border-border rounded-lg">
        <div className="flex justify-between items-center">
          <p className="font-medium text-text-primary">{g.description}</p>
          <span className={`px-2.5 py-0.5 rounded-full text-xs font-medium ${g.status === 'completed' ? 'bg-pastel-green text-green-700' : 'bg-pastel-yellow text-yellow-700'}`}>
            {g.status}
          </span>
        </div>
        <div className="mt-2 flex items-center gap-2">
          <div className="flex-1 bg-pastel-blue rounded-full h-2">
            <div className="bg-accent-primary h-2 rounded-full" style={{ width: `${(g.current / g.target) * 100}%` }} />
          </div>
          <span className="text-sm text-text-secondary">{g.current}/{g.target} {g.unit}</span>
        </div>
      </div>
    ))}
  </div>
</div>
```

### Photo/Video Gallery
```jsx
<div className="grid grid-cols-3 gap-4">
  {photos.map(p => (
    <div key={p.id} className="relative rounded-lg overflow-hidden cursor-pointer hover:shadow-lg transition-shadow" onClick={() => openLightbox(p)}>
      <img src={p.url} className="w-full h-48 object-cover" />
      <div className="absolute bottom-0 left-0 right-0 bg-black/50 text-white p-2">
        <p className="text-sm">{p.title}</p>
        <p className="text-xs opacity-75">{p.category}</p>
      </div>
      {p.taggedStudentIds.length > 0 && (
        <div className="absolute top-2 right-2 bg-accent-primary text-text-primary text-xs px-2 py-0.5 rounded-full">
          {p.taggedStudentIds.length} tagged
        </div>
      )}
    </div>
  ))}
</div>
```

### Announcements Board
```jsx
<div className="space-y-4">
  {announcements.map(a => (
    <div key={a.id} className={`p-4 rounded-xl border ${a.type === 'warning' ? 'bg-pastel-yellow border-yellow-300' : a.type === 'closure' ? 'bg-pastel-pink border-red-300' : 'bg-white border-border'}`}>
      <div className="flex items-center gap-2">
        <span className="text-lg">{a.type === 'closure' ? '🚫' : a.type === 'warning' ? '⚠️' : '📢'}</span>
        <h4 className="font-semibold text-text-primary">{a.title}</h4>
      </div>
      <p className="text-sm text-text-secondary mt-1">{a.content}</p>
      <p className="text-xs text-text-light mt-2">{a.date}</p>
    </div>
  ))}
</div>
```

### Batch Messaging
```jsx
<div className="bg-white rounded-2xl shadow-lg p-6 max-w-2xl">
  <h3 className="text-xl font-semibold mb-4">Send Batch Message</h3>
  <select className="w-full px-4 py-2.5 border border-border rounded-lg mb-4">
    <option>All Students</option>
    <option>Piano Students</option>
    <option>Beginners</option>
    <option>Specific Class</option>
  </select>
  <textarea className="w-full px-4 py-2.5 border border-border rounded-lg h-32" placeholder="Message content..." />
  <div className="mt-4 flex gap-2">
    <button className="px-5 py-2.5 bg-accent-primary text-text-primary font-medium rounded-lg">Send Message</button>
    <button className="px-5 py-2.5 border border-border text-text-primary rounded-lg">Send via WhatsApp</button>
  </div>
</div>
```

### Payment Plan & Discount
```jsx
<div className="bg-white rounded-xl border border-border p-6">
  <h3 className="text-xl font-semibold mb-4">Payment Options</h3>
  <div className="space-y-3">
    {['full', '2x', '3x'].map(plan => (
      <label key={plan} className="flex items-center gap-3 p-3 border border-border rounded-lg cursor-pointer hover:bg-pastel-blue">
        <input type="radio" name="plan" value={plan} />
        <span className="font-medium">{plan === 'full' ? 'Full Payment' : `${plan.replace('x', '')} Installments`}</span>
      </label>
    ))}
  </div>
  <div className="mt-4">
    <label className="text-sm font-medium">Discount Code</label>
    <div className="flex gap-2 mt-1">
      <input type="text" placeholder="Enter code" className="flex-1 px-4 py-2.5 border border-border rounded-lg" />
      <button className="px-5 py-2.5 bg-pastel-green text-green-700 font-medium rounded-lg">Apply</button>
    </div>
  </div>
</div>
```

### Quiz System
```jsx
<div className="bg-white rounded-xl border border-border p-6 max-w-2xl">
  <h3 className="text-xl font-semibold mb-2">{lesson.title} - Quiz</h3>
  <div className="space-y-4">
    {questions.map((q, i) => (
      <div key={i} className="p-4 bg-pastel-blue rounded-lg">
        <p className="font-medium text-text-primary">{i + 1}. {q.question}</p>
        <div className="mt-2 space-y-2">
          {q.options.map((opt, j) => (
            <label key={j} className="flex items-center gap-2">
              <input type="radio" name={`q${i}`} value={j} />
              <span>{opt}</span>
            </label>
          ))}
        </div>
      </div>
    ))}
  </div>
  <button className="mt-6 px-5 py-2.5 bg-accent-primary text-text-primary font-medium rounded-lg">
    Submit Quiz
  </button>
</div>
```

---

## 13. Do's and Don'ts

### Do's
- Use Tailwind utility classes directly in JSX
- Use `@theme inline` tokens for colors
- Use `border-border` for all borders
- Use `hover:bg-pastel-*` for hover states
- Use `animate-fadeIn` for modals/lightboxes
- Use `rounded-lg` or `rounded-xl` for containers
- Use `rounded-full` for avatars and badges
- Clean up intervals/timeouts in `useEffect` returns

### Don'ts
- Don't use `focus:ring` (not in design system)
- Don't use `@apply` in CSS files
- Don't use hard-coded colors (use theme tokens)
- Don't use sharp corners (`rounded-none`)
- Don't use aggressive colors (red, bright blue, neon)
- Don't nest modals (lightbox inside modal)
- Don't forget `use client` directive on interactive components
- Don't use `any` type — annotate explicitly
