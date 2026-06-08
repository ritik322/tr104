# Week 18 — TnP Portal Kick-off and Schema Design

**Dates:** 4 May – 8 May 2026
**Location:** GNDEC Training and Placement Cell, Ludhiana
**Project:** Training and Placement Portal

---

## Tasks Done

- Transitioned from the Training Letter Plugin work to the second and primary deliverable of the on-campus phase, namely the Training and Placement Portal, which would replace the existing manual Google Forms-based placement workflow at the cell.
- Spent the first day with the TnP coordinator gathering detailed requirements for the portal, capturing the complete lifecycle of a typical placement drive from announcement, through student application, round-by-round candidate tracking, to shortlist generation and selection.
- Documented the three user roles that the portal would serve (Administrator, Recruiter, Student) along with the operations available to each, and identified the specific pain points in the existing manual workflow that the portal needed to address explicitly.
- Confirmed the technology stack with the coordinator and the senior faculty supervisor, settling on Next.js 16 with the App Router as the full-stack framework, PostgreSQL as the relational database, Prisma as the type-safe ORM, NextAuth.js for authentication with a JWT-based session strategy, bcrypt for password hashing, and a combination of Material UI and Tailwind CSS for the user interface.
- Set up the Next.js project on the assigned workstation using the latest stable version, configured the App Router directory structure, installed and initialised Prisma, and connected it to a local PostgreSQL instance for development.
- Designed the relational schema on paper before any code, sketching out seven primary tables: User, Student, Company, Drive, Round, Application, and Post, along with their fields, primary keys, unique constraints, foreign keys, and the relationships between them.
- Made several deliberate schema decisions during the design exercise, including the composite primary key on the Application table to prevent duplicate applications at the database level, the array column for branches on the Drive table to support multi-branch eligibility, and the soft-delete pattern using `deletedAt` timestamps on the User, Student, and Company tables.
- Translated the schema into the Prisma schema file using the Prisma Schema Definition Language, took advantage of Prisma's enum support for the User role discriminator, and ran the initial Prisma migration to create the corresponding tables in the development database.
- Configured NextAuth.js with the credentials provider and a custom `authorize` callback that validated submitted credentials against the User table using bcrypt for password comparison, and implemented the `jwt` and `session` callbacks to embed the role and identity in the session token.
- Built the unified login screen as a single page accessible to all three user roles, with the server-side redirect after login routing the user to the appropriate dashboard (`/admin`, `/recruiter`, or `/student`) based on the role in their session.
- Implemented the student registration flow, including server-side validation of the email and password fields, automatic creation of the corresponding User record with the `student` role, and a redirect to the profile creation screen on successful signup.
- Set up the initial layout structure for each of the three role-based dashboards, with role-specific sidebar navigation defined and the layout-level redirect logic in place to prevent cross-role access at the page level.

---

## Technologies Used

- Next.js 16 with the App Router
- React 18 with Server and Client Components
- PostgreSQL (local instance for development)
- Prisma ORM with the Prisma Schema Definition Language
- NextAuth.js with credentials provider and JWT session strategy
- bcrypt with 10 salt rounds for password hashing
- Material UI and Tailwind CSS for the user interface
- Visual Studio Code with the Prisma, ESLint, Prettier, and Tailwind CSS IntelliSense extensions
- Git and GitHub for version control
- Postman for endpoint verification

---

## Learnings

- Realised that the requirements conversation with the TnP coordinator was the single most important input into the portal's design, because the coordinator's deep familiarity with the existing process surfaced operational details that would not have been visible from outside.
- Understood the practical value of designing the relational schema on paper before writing any Prisma code, because the act of sketching exposed several constraint relationships (such as the composite primary key on Application) that would have been missed in a code-first approach.
- Picked up the importance of choosing the soft-delete pattern early in the project rather than retrofitting it later, because every related query and every audit log would otherwise need to be revisited to handle the new pattern correctly.
- Learned that Prisma's enum support combined with its auto-generated TypeScript types provides genuine compile-time safety for role-based logic, which directly translated into fewer category-of-bugs from misspelled role identifiers later in the codebase.
- Got first-hand experience of how NextAuth.js's custom `authorize` callback is the right place to enforce authentication-specific business rules, because every login attempt across the entire portal flows through it exactly once.
- Realised that role-based redirection at the layout level is a cleaner pattern than checking roles inside individual pages, because the layout is the natural choke point that all pages within a role's section share.
- Observed that the experience of working on the custom NextAuth.js setup for the Manage Business platform at 75Way translated directly into the configuration of NextAuth.js for the TnP Portal, validating the cross-project value of the earlier ownership work.
