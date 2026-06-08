# GNDEC TnP Cell, Ludhiana

**Duration:** 20 April 2026 – 5 June 2026 (~7 weeks)
**Location:** Training and Placement Cell, Guru Nanak Dev Engineering College, Ludhiana
**Development Model:** Iterative and Incremental

---

## Structure

The final seven weeks of the training period were spent on campus at the GNDEC Training and Placement Cell, delivering two distinct software systems that directly address long-standing manual workflows of the cell.

### Training Letter Management Plugin (Weeks 16–17)

The first two weeks at GNDEC were dedicated to the development and deployment of the **Training Letter Management Plugin** (`local_training_letter`), a custom Moodle local plugin that digitizes the industrial training letter application, approval, and verification workflow.

The plugin replaces a previously paper-based process that involved physical handover of application forms between students, departments, and the TnP cell. It is built directly into the existing GNDEC Moodle Learning Management System and integrates with Moodle's native authentication, File API, and form rendering systems.

The plugin supports four user roles (Student, Teacher, Manager, Site Admin) and implements a dual-approval state machine governing both the initial training request and the subsequent confirmation letter lifecycle. Reference numbers are auto-generated in the format `GNDEC/[YEAR]/[ID]` upon teacher approval, and file access is gated through a strict security gatekeeper function.

**Technology Stack:** PHP 8, MySQL via Moodle's `$DB` abstraction layer, Moodle XMLDB schema definition, Moodle Form API, Moodle File API, HTML and CSS Grid for responsive layouts.

### Training and Placement Portal (Weeks 18–22)

The remaining five weeks were dedicated to the **Training and Placement Portal**, the primary deliverable of the on-campus phase. The portal is a full-stack web application that replaces the existing manual, Google Forms-based placement workflow with a single integrated, role-based, database-driven platform.

The portal serves three distinct user roles (Administrator, Recruiter, Student) each with a dedicated dashboard and role-scoped permissions enforced at the server level. Key functionality includes verification-based profile locking, eligibility-based automatic drive filtering, system-managed and custom rounds, round-by-round applicant tracking with bulk operations, and one-click Excel export of shortlists with round-based inclusive filtering.

Development followed an iterative and incremental model, with each functional area (authentication, profile, drives, rounds, applications, export, recruiter module) built, tested, and refined as an independent vertical slice before integration into the larger system.

**Technology Stack:** Next.js 16 (App Router), React 18 with Server and Client Components, PostgreSQL, Prisma ORM, NextAuth.js with JWT-based session strategy, bcrypt (10 salt rounds), Material UI, Tailwind CSS, ExcelJS for server-side spreadsheet generation, Vercel for deployment, Neon for managed PostgreSQL hosting.

---

## Weekly Index

### Training Letter Management Plugin

| Week | Dates | Focus |
|------|-------|-------|
| Week 16 | 20 Apr – 24 Apr 2026 | GNDEC onboarding and Training Letter Plugin kick-off |
| Week 17 | 27 Apr – 1 May 2026 | Plugin completion and deployment |

### Training and Placement Portal

| Week | Dates | Focus |
|------|-------|-------|
| Week 18 | 4 May – 8 May 2026 | TnP Portal kick-off and schema design |
| Week 19 | 11 May – 15 May 2026 | Student profile and Administrator Student Management |
| Week 20 | 18 May – 22 May 2026 | Company, Drive, and Round Management |
| Week 21 | 25 May – 29 May 2026 | Applicant tracking, Excel export, and Recruiter module |
| Week 22 | 1 Jun – 5 Jun 2026 | Final testing, production deployment, and training wrap-up |

Individual week pages will be added to the left navigation as they are filled in.
