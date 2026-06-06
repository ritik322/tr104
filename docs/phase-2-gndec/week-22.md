# Week 22 — Final Build, Deployment, and Training Wrap-up

**Dates:** 1 June – 5 June 2026
**Location:** GNDEC Training and Placement Cell, Ludhiana
**Project:** Training and Placement Portal

---

## Tasks Done

- Entered the final week of the six-month industrial training period with the goal of completing the remaining Portal modules, deploying the application to production, and wrapping up the on-campus training cleanly with the TnP coordinator.
- Built the Student-side Drive Browsing module with two tabs (Opportunities and My Applications) on the student dashboard, where the Opportunities tab displayed only drives whose branches list included the student's branch and whose passout year matched the student's passout year, performed entirely through a server-side filter on the drive list query.
- Implemented the drive detail page for the student side, including the full description, the eligibility summary, the deadline, and an Apply button whose state was evaluated in real time across five values (Profile Pending, Cannot Apply, Apply Now, Applied, Closed) based on the student's profile verification, the drive's lifecycle status, the deadline, and the existing application record.
- Built the application submission endpoint with the full server-side eligibility algorithm enforcing every business rule independently of the client UI, including authentication check, profile verification check, drive status check, deadline check, branch check, passout year check, CGPA threshold, backlog threshold, and the duplicate-application check (complemented by the composite primary key on the Application table as a second defence at the database level).
- Built the Applicant Tracking module on the drive detail page for the Administrator and Recruiter, with a paginated applicant list, per-applicant round dropdown for single-applicant movement, and a bulk-selection interface with checkboxes that allowed the movement of multiple applicants to the same target round in a single API call.
- Implemented the Excel Export module using ExcelJS for server-side spreadsheet generation, with a round filter dropdown on the export action that produced an inclusive filter (selecting Round 2 included all applicants currently in Round 2, Round 3, and beyond up to Selected) and a dynamic file name in the format `Company_Drive_Round_Date.xlsx`.
- Built the Recruiter module with a company-scoped dashboard that showed only the drives of the recruiter's own company, enforced at both the route level and the database query level so that a recruiter could not view or act on any other company's drives even through tampered requests.
- Restricted the Recruiter's available actions to drive lifecycle status changes, custom round CRUD within their own drives, and applicant round movement (single and bulk), while explicitly disallowing drive creation, drive deletion, student verification, and student unlock at the API layer.
- Built the read-only student detail side panel on the Recruiter pages, reusing the same side-panel component from the Administrator screens but with all action buttons hidden, so that recruiters could view applicant profiles without any ability to modify them.
- Performed two full days of end-to-end regression testing across all three roles, walking through the complete placement lifecycle with seeded data (company creation, drive creation, student verification, application submission, round movement, export, recruiter view), and fixed several small bugs surfaced during the testing.
- Deployed the application to production using Vercel for the Next.js serverless hosting and Neon for the managed PostgreSQL database, configured all environment variables and production secrets through the Vercel dashboard, and ran the initial Prisma migration on the production database.
- Walked through the deployed production application with the TnP coordinator on the last working day, demonstrated the complete workflow for all three roles, handed over the administrator credentials and the codebase access, and discussed the items remaining on the future enhancement backlog (email notifications, analytics dashboard, multi-recruiter per company, bulk resume download).
- Completed the personal exit formalities at the cell, collected the training completion documentation, and marked the formal conclusion of the six-month industrial training period spanning the four-month internship at 75Way Technologies, Mohali and the six weeks at the GNDEC Training and Placement Cell.

---

## Technologies Used

- Next.js 16 with the App Router (page routes and API route handlers)
- React 18 with Server and Client Components
- PostgreSQL via the Prisma ORM (production hosted on Neon)
- Custom permission helper module (`lib/driveAccess.js`) with company-scoped recruiter checks
- ExcelJS for server-side spreadsheet generation
- Material UI for forms, tables, dropdowns, and the side-panel component
- Tailwind CSS for layout, spacing, and responsive behaviour
- Vercel for production deployment of the Next.js application
- Neon for managed PostgreSQL hosting with automatic backups
- Postman for endpoint verification through the regression testing days
- Git and GitHub for version control through the final commit

---

## Learnings

- Realised that the apply-to-drive eligibility algorithm was the single most consequential piece of business logic in the entire Portal, because it was the gate through which every application had to pass and any bug in it would either allow ineligible applications or block eligible ones, both of which would severely undermine trust in the system.
- Understood the practical value of the early-exit pattern in the eligibility algorithm, where the first failed check returned an error immediately, because it produced fast and predictable feedback for the student and avoided unnecessary downstream database queries on requests that were going to fail anyway.
- Picked up the deep value of the dual-layer duplicate-application protection (application-layer check plus database-level composite primary key), because no single layer alone would have been sufficient against concurrent submissions, and the database layer is the only place where the uniqueness invariant truly holds.
- Learned that the inclusive round-based export filter matched the operational mental model of the TnP coordinator perfectly, because the coordinator naturally thought of a Round 2 export as "all applicants who reached at least Round 2", which is exactly what the inclusive semantics produced.
- Got first-hand experience of how strict company-scoping at the database query level for recruiters is dramatically safer than scoping at the route level alone, because the database-level scope survives any future route refactor or accidental endpoint exposure.
- Realised that two full days of structured end-to-end regression testing surfaced bugs that no amount of module-level testing had caught, validating the principle that integration is its own activity and not a free side-effect of unit-level correctness.
- Observed that walking through the production deployment with the TnP coordinator on the last day was the right way to close the project, because it transferred not just the access credentials but also the confidence that the system was operational and ready for the upcoming placement season.
- Reflected at the end of the six months that the breadth of the multi-stack training at 75Way, the depth of the Manage Business platform ownership, and the on-campus delivery of two production systems at GNDEC together formed a more complete industrial training experience than any single project alone could have delivered.
