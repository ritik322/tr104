# Week 20 — Student Profile and Administrator Student Management

**Dates:** 18 May – 22 May 2026
**Location:** GNDEC Training and Placement Cell, Ludhiana
**Project:** Training and Placement Portal

---

## Tasks Done

- Continued the Training and Placement Portal build with the goal of completing the Student Profile module and the Administrator-facing Student Management module by the end of the week, since every downstream module (drives, applications, exports) depended on a working profile and verification flow.
- Designed the Student Profile screen as a tabbed interface containing three sections (Personal, Academic, Professional), with each section grouping the fields that logically belonged together and a single shared submit button at the bottom of the form.
- Implemented the profile creation flow for newly registered students, with server-side validation on every field including format checks on the CRN and URN, length checks on the phone number, range checks on the CGPA, and non-negative checks on the active backlog count.
- Built the profile update flow that allowed students to edit their own profile through the same tabbed form, with the server-side handler distinguishing between the initial create and the subsequent update through the presence of an existing Student record linked to the User.
- Implemented the verification-based profile lock mechanism on the server side, where the personal and academic fields became read-only at the API layer once the `isVerified` flag was set to true, while the professional fields (skills, resume link, summary, other links) remained editable at all times regardless of the verification status.
- Designed the lock enforcement as a strict server-side check rather than a client-side restriction, meaning that even a request crafted directly through Postman or a tampered client would be rejected if it attempted to modify a locked field on a verified profile.
- Built the Administrator Student Management screen as a paginated table with multi-criteria filtering on branch, passout year, and verification status, along with a free-text search on student name and CRN, reusing the table pagination pattern from the User Management work at 75Way.
- Implemented the side-panel detail view that opened on row selection and displayed the complete student profile across the same three tabs as the student-facing form, with inline editing supported for unlocked fields and Verify and Unlock action buttons gated by the Administrator role.
- Built the single-click verification action that set the `isVerified` flag to true on the selected student record, and the corresponding unlock action that reverted the flag to false, with both operations recorded with a timestamp for audit reconstruction.
- Implemented the bulk unlock operation by passout year, which allowed the Administrator to set the `isVerified` flag to false on all students of a chosen passout year in a single transaction, designed specifically to support the start-of-session re-verification cycle.
- Wrote a centralised permission helper at `lib/driveAccess.js` (extended later to cover drive operations) with an initial function for checking whether the current session belonged to an Administrator, replicating the centralisation pattern that had worked well on the Manage Business platform.
- Tested the entire profile and verification flow with a small set of seed students inserted into the development database, walking through profile creation, verification, lock enforcement on personal fields, unlock, and bulk unlock to confirm correct behaviour at every step.

---

## Technologies Used

- Next.js 16 with the App Router (page routes and API route handlers)
- React 18 with Server and Client Components
- PostgreSQL via the Prisma ORM
- Prisma migrations for any schema adjustments made during the week
- Custom permission helper module (`lib/driveAccess.js`)
- Material UI for the tabbed form and the side-panel detail view
- Tailwind CSS for spacing, alignment, and responsive behaviour
- Postman for endpoint verification
- Git and GitHub for version control

---

## Learnings

- Realised that the most important property of the profile lock mechanism is that it cannot be bypassed by the client, because a verified student profile is the foundation that every recruiter shortlist will later be built on, and any client-only restriction would defeat the purpose entirely.
- Understood the practical importance of keeping a small set of professional fields (skills, resume link, summary) editable even on a verified profile, because these are exactly the fields that students legitimately need to update between drives without going through a full re-verification cycle.
- Picked up the value of the side-panel detail view pattern over a separate detail page, because the side panel preserves the main page context (the list of students with active filters and pagination) while still showing the full detail of the selected record.
- Learned that bulk operations like the bulk unlock by passout year need to be designed with clear scoping rather than as a generic mass update, because tying the operation explicitly to a passout year makes the consequences predictable and reviewable.
- Got first-hand experience of how the centralised permission helper pattern, which had proven its value on the Manage Business platform, translated cleanly to the TnP Portal, validating that the same design principle applies regardless of the framework or stack.
- Realised that seeding a small set of fixture students into the development database early in the module work is a small investment that pays back many times over, because every subsequent UI iteration can be tested against realistic data rather than empty states.
- Observed that the tabbed form pattern is far more user-friendly for a multi-section profile than a single long scrolling form, because it reduces visual overload and lets the user focus on one section at a time without losing the unsaved data in the others.
