<div align="center">

# 🏫 PBES SchoolPortal

### Full-Featured School Management System

**🧪 Live Demo → [pbes-demo.vercel.app](https://pbes-demo.vercel.app)**

[![Next.js](https://img.shields.io/badge/Next.js_16-black?style=for-the-badge&logo=next.js)](https://nextjs.org)
[![TypeScript](https://img.shields.io/badge/TypeScript-3178C6?style=for-the-badge&logo=typescript&logoColor=white)](https://www.typescriptlang.org)
[![PostgreSQL](https://img.shields.io/badge/PostgreSQL-4169E1?style=for-the-badge&logo=postgresql&logoColor=white)](https://www.postgresql.org)
[![Supabase](https://img.shields.io/badge/Supabase-3ECF8E?style=for-the-badge&logo=supabase&logoColor=white)](https://supabase.com)
[![Tailwind CSS](https://img.shields.io/badge/Tailwind_CSS_4-06B6D4?style=for-the-badge&logo=tailwindcss&logoColor=white)](https://tailwindcss.com)

> 💼 **THIS APP IS FOR SALE OR RENT!** A complete, production-ready School Management System template with all features fully implemented.  
> Built for **Pantalan Bago Elementary School** (DepEd Division of Bataan). Perfect for public schools, private schools, or education startups. [Contact me ↓](#-app-for-salerental)

> ⚠️ **Demo Notice:** The live demo uses entirely fictional, sample-generated data. No real student, teacher, or school records are used. All names, grades, and enrollment entries are for demonstration purposes only.

</div>

---

## 📸 What Is PBES SchoolPortal?

A **fully-featured School Management System** built from scratch with enterprise-grade architecture for Philippine elementary schools. Every feature is production-ready: multi-role portals (Admin / Teacher / Student / Parent), OTP-verified online enrollment, attendance tracking, quarterly gradebook, real-time push notifications, and a full audit trail.

## 🧪 Demo Account Credentials

| Role | Email | Password |
|------|-------|----------|
| **Admin** | admin@pbes.demo | Demo@1234 |
| **Teacher** | teacher@pbes.demo | Demo@1234 |
| **Student** | student@pbes.demo | Demo@1234 |
| **Parent** | parent@pbes.demo | Demo@1234 |

**Live Demo (Sample Data Only) → [pbes-demo.vercel.app](https://pbes-demo.vercel.app)**

> 🔒 No real student, teacher, or school data is used in the demo. All records are fictional and generated solely for demonstration purposes.

---

## ✨ Feature Highlights

### 🎓 Core School Features
| Feature | Details |
|---|---|
| **Online Enrollment** | OTP-verified public enrollment form — students apply, admin reviews & approves |
| **Attendance Tracking** | Daily & subject-based attendance, SF2 report export, chronic absentee flagging |
| **Quarterly Gradebook** | Teachers enter/edit grades per subject per student; students & parents view live |
| **Assignments** | Teachers create assignments with file attachments; students submit with file uploads |
| **School Announcements** | School-wide or section-scoped; image uploads, expiry dates, role targeting |
| **Events Calendar** | Create and manage school events with categories, images, and homepage visibility |
| **Document Requests** | Configurable enrollment schedules with start/end dates per school year |
| **Audit Log** | Immutable log of all admin & teacher actions — actor, timestamp, metadata |

### 🔐 Auth & Security
| Feature | Details |
|---|---|
| **Invite-Based Accounts** | Admin invites teachers; approved students receive invite emails via Resend |
| **OTP Enrollment** | Public enrollment form verified by email OTP before submission |
| **Parent Linking** | Students send parent-invite links; parents link to multiple children |
| **Rate Limiting** | Upstash Redis (production) + in-memory fallback (dev) on all sensitive endpoints |
| **Content Security Policy** | Nonce-based CSP headers generated per-request — blocks XSS at the edge |
| **IDOR Protection** | File proxy enforces ownership; students & parents only access their own files |
| **Zod Validation** | Strict schema validation on every API route input |
| **Row Level Security** | Supabase RLS enforces data access at the PostgreSQL level |

### 🛡️ Admin Portal
- Full user management — create/edit/delete Admin, Teacher, Student, and Parent accounts
- Sections & Classes management per school year
- Enrollment schedule configuration with approval workflow
- School-wide attendance overview with SF2 compliance reports
- School settings — school year config, attendance mode, teacher permission flags
- Immutable audit log — every sensitive action recorded with actor identity & metadata

### 📚 Teacher Portal
- Advisory section overview — today's attendance status & class schedule at a glance
- Daily & subject attendance marking with edit capability and export
- Quarterly grade entry per subject per student
- Assignment creation with file attachments scoped to their classes
- Section-scoped announcements

### 🔔 Notifications & Communication
- **Web Push (VAPID)** via `web-push` library — new assignments, graded submissions, announcements
- In-app notification bell with unread count and click routing
- Service worker (`sw.js`) for background push handling
- **6 transactional email templates** via Resend — invites, OTP, enrollment approval, password reset
- Vercel Cron at 02:00 UTC for expired announcement cleanup

### 🌐 Public Landing Page
- School announcements & upcoming events visible without login
- OTP-verified online enrollment portal
- Dark / Light theme toggle (system-aware via `next-themes`)

---

## 🧱 Tech Stack

| Layer | Technology |
|---|---|
| **Framework** | Next.js 16 (App Router, Server Actions) |
| **Language** | TypeScript 5 (strict) |
| **Database / Auth** | PostgreSQL via Supabase + Row Level Security + Supabase Auth |
| **UI** | React 19 + Tailwind CSS 4 + Lucide Icons |
| **Email** | Resend (6 templates) |
| **Rate Limiting** | Upstash Redis (`@upstash/ratelimit`) |
| **Push Notifications** | web-push (VAPID) |
| **Validation** | Zod 4 |
| **Theme** | next-themes (light / dark / system) |
| **Image Cropping** | react-easy-crop |
| **Fonts** | Geist Sans / Geist Mono |
| **Deployment** | Vercel (with Cron jobs) |

---

## 🏗️ Architecture Highlights

- **Static landing page** (`○`) — pre-rendered at build time, school announcements & events served without auth
- **Edge-compatible middleware** — session refresh + nonce-based CSP at the edge; no heavy DB calls in middleware
- **Server Actions** for mutations — no client-side `fetch()` for forms
- **Role-scoped queries** — every query scoped to `userId` and `role`; prevents IDOR across all 4 portals
- **Plan-aware permission flags** — teacher permissions (create classes, manage students) toggled by admin per school settings
- **0 raw SQL** — 100% Supabase client + RLS throughout all API routes
- **Invite-only teacher & parent access** — no self-signup; all accounts created via secure email invite flow
- **Vercel Cron** — automatic daily cleanup of expired announcements at 02:00 UTC

---

## 📦 Project Scale

| Metric | Count |
|---|---|
| API route groups | **29** |
| Pages | **45+** |
| Supabase tables | **20+** |
| Email templates | **6** |
| User roles | **4** (Admin, Teacher, Student, Parent) |
| Lines of code | **~18,000** |

---

## 💼 App For Sale/Rental

### 🏪 Purchase Options

This complete school management application is available for:

#### 💰 **Outright Purchase**
- Full ownership of all source code
- Complete documentation and setup guide
- White-label ready (rebrand for any school)
- All features included (no restrictions)
- Perfect for: Schools, LGUs, EdTech startups, agencies

#### 📅 **Monthly Rental/License**
- Use the codebase for your school or business
- Regular updates and bug fixes
- Technical support included
- Lower upfront cost
- Perfect for: Testing the platform, pilot school rollout

### ✨ What You Get

- ✅ **Complete codebase** — All 18,000+ lines of production code
- ✅ **4 full portals** — Admin, Teacher, Student, Parent dashboards
- ✅ **29 API route groups** — Role-guarded, rate-limited, fully validated
- ✅ **45+ pages** — Public landing, auth, enrollment, all dashboards
- ✅ **Supabase integration** — PostgreSQL + RLS + Auth fully wired
- ✅ **Invite-based authentication** — Secure onboarding for all roles
- ✅ **OTP enrollment** — Students apply online, admin approves
- ✅ **Attendance system** — Daily & subject-based, SF2 export-ready
- ✅ **Gradebook** — Quarterly grades with live student/parent visibility
- ✅ **Push notifications** — Web Push VAPID (background-capable)
- ✅ **Email system** — 6 transactional templates (Resend)
- ✅ **Audit log** — Immutable admin/teacher action history
- ✅ **Security hardened** — CSP, rate limiting, Zod, RLS, IDOR protection
- ✅ **Deployment ready** — Vercel config, cron job, environment template

### 🎯 Perfect For

- 🏫 **Public Schools** — Digitize enrollment, attendance & grades in one platform
- 🏛️ **LGUs & DepEd Divisions** — Roll out across multiple schools
- 🚀 **EdTech Startups** — Launch your school SaaS without building from scratch
- 🏢 **Agencies** — White-label for school clients

### 📬 Contact for Pricing

| | |
|---|---|
| **GitHub** | [@ldsalud](https://github.com/ldsalud/) |
| **Email** | Contact via GitHub profile |
| **Live Demo** | [pbes-demo.vercel.app](https://pbes-demo.vercel.app) |

> 💡 **Want to see more?** I'm happy to:
> - Do a live walkthrough of all four role portals
> - Share private repo access for code review
> - Discuss customization for your school's specific needs
> - Explain the architecture and Supabase RLS setup in detail

---

<div align="center">

**Live Demo → [pbes-demo.vercel.app](https://pbes-demo.vercel.app)**

💼 **This app is available for purchase or rental.**

</div>
