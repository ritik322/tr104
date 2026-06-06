# Week 21 — Company, Drive, and Round Management

**Dates:** 25 May – 29 May 2026
**Location:** GNDEC Training and Placement Cell, Ludhiana
**Project:** Training and Placement Portal

---

## Tasks Done

- Continued the Portal build by shifting focus from student-side work to the Administrator-facing Company, Drive, and Round Management modules, which together form the supply side of the placement process.
- Built the Company Management module with a paginated company list, search by name, and a create-company form that captured the company name, the recruiter email, and an initial password for the recruiter account.
- Implemented the company creation flow as a single Prisma transaction that created both the Company record and the linked recruiter User record atomically, ensuring that a failure on either side rolled back the other and avoided orphan records.
- Built the company edit flow that allowed the Administrator to update the company details, and the soft-delete flow that set a `deletedAt` timestamp on the Company record with a safety check that prevented deletion of any company that had at least one linked drive.
- Built the Drive Management module with a paginated drive list grouped by lifecycle status (open, in progress, completed), and a create-drive form that captured the drive title, description, eligible branches as a multi-select, passout year, optional minimum CGPA, optional maximum backlog count, and the application deadline.
- Implemented the create-drive flow with a key behaviour built in from the start: on successful drive creation, the server automatically inserted two system rounds into the Round table for the new drive, namely Round 0 (Applied) and Round 999 (Selected), wrapped in the same Prisma transaction as the drive insertion.
- Built the drive edit flow that allowed the Administrator to update the eligibility criteria, the deadline, and the lifecycle status, with the status field exposed as a dropdown limited to the three allowed values.
- Built the Round Management module within the drive detail page, supporting the creation of custom rounds with round numbers between 1 and 998 and free-text round names such as "Aptitude Test", "Technical Interview", and "HR Round", arranged in the UI in chronological order based on round number.
- Implemented strict server-side protection on the system rounds (Round 0 and Round 999), so that any attempt to edit or delete a round with `roundNumber = 0` or `roundNumber = 999` was rejected at the API layer with a clear error message, regardless of the user's role.
- Extended the centralised permission helper at `lib/driveAccess.js` with role-aware checks for the drive, round, and company endpoints, replacing inline role checks across the API routes with explicit calls to the helper.
- Built the read-side optimisations on the drive list query, including indexed lookups on `companyId` and `passoutYear`, selective field fetching to reduce the response payload, and an eager-load of the linked company name to avoid an additional round trip from the frontend.
- Tested the full Company-Drive-Round lifecycle end to end with a set of seeded data, including the creation of a company, the creation of a drive under that company, the auto-creation of the two system rounds, the addition of three custom rounds, the lifecycle status transitions, and the attempted deletion of a system round (correctly rejected).

---

## Technologies Used

- Next.js 16 with the App Router (page routes and API route handlers)
- React 18 with Server and Client Components
- PostgreSQL via the Prisma ORM
- Prisma transactions for the atomic Company-and-User and Drive-and-system-rounds creation flows
- Custom permission helper module (`lib/driveAccess.js`)
- Material UI for the forms, multi-select inputs, and modal dialogs
- Tailwind CSS for layout and responsive behaviour
- Postman for endpoint verification
- Git and GitHub for version control

---

## Learnings

- Realised that wrapping the Company-and-User creation in a single Prisma transaction was not a premature optimisation but a correctness requirement, because a failure between the two inserts in a non-transactional flow would have left an unusable orphan record on one side or the other.
- Understood the practical importance of auto-creating the two system rounds at drive creation time, because every downstream feature (applications going to Round 0, the export filter starting from the round dropdown, the round-based pagination on applicants) assumed their existence and would have to handle a missing-system-round case otherwise.
- Picked up the value of representing the system rounds through reserved numeric values (0 and 999) rather than a separate boolean flag or table, because the reserved-number approach kept the Round table schema uniform and made the system-round protection check a simple numeric comparison.
- Learned that strict server-side rejection of edits and deletes on system rounds, with a clear error message, is significantly more reliable than relying on the client to hide the affected buttons, because any tampered or alternative client could otherwise reach the underlying endpoints unimpeded.
- Got first-hand experience of how the centralised permission helper continued to pay back as more modules were added, because each new endpoint required only a single call to the helper rather than its own role-checking logic, which materially reduced the surface area for authorisation bugs.
- Realised that the safety check preventing deletion of companies with linked drives is exactly the kind of small constraint that prevents large operational accidents, because the alternative (cascading deletion of the linked drives) would silently destroy historical placement records.
- Observed that the soft-delete pattern continued to feel right as it was applied to companies, because preserving deleted records (rather than hard deleting them) ensured that audit logs and historical drive references would never resolve to a missing parent.
