# Week 22 — Final Testing, Production Deployment, and Training Wrap-up

**Dates:** 1 June – 5 June 2026
**Location:** GNDEC Training and Placement Cell, Ludhiana
**Project:** Training and Placement Portal

---

## Tasks Done

- Entered the final week of the on-campus training at GNDEC with the goal of conducting full end-to-end regression testing, deploying the Portal to production, handing over the project to the TnP coordinator, and completing the personal exit formalities at the cell.
- Performed two full days of end-to-end regression testing across all three roles (Administrator, Recruiter, Student), walking through the complete placement lifecycle with seeded data including company creation, drive creation, student verification, application submission, round movement, Excel export, and recruiter-side workflows.
- Identified and fixed several small bugs surfaced during the integration testing, including a soft-deleted student remaining visible in the applicant autocomplete, a stale permission state after a profile unlock, and an inconsistent date format on one of the Excel export columns.
- Reviewed the codebase one final time to remove leftover debug logs, console statements, and commented-out experimental code, and confirmed that the production environment configuration was free of any local development overrides.
- Generated a final Prisma migration capturing the latest schema state, validated that the migration applied cleanly against a fresh database, and confirmed that all foreign keys and unique constraints were enforced as intended.
- Provisioned the production infrastructure by setting up a managed PostgreSQL instance on Neon with automatic backups enabled and a production project on Vercel with the appropriate environment variables configured through the dashboard.
- Deployed the application to production on Vercel, ran the initial Prisma migration on the production database, and seeded the initial set of administrator credentials and reference data such as branch lists and academic year defaults.
- Performed a smoke test on the production deployment, walking through registration, profile verification, drive creation, application submission, and Excel export end to end, and confirmed that the production behaviour matched the staging environment in every respect.
- Walked through the deployed production application with the TnP coordinator on the last working day, demonstrated the complete workflow for all three roles, handed over the administrator credentials and the codebase access, and discussed the items remaining on the future enhancement backlog (email notifications, analytics dashboard, multi-recruiter per company, bulk resume download).
- Prepared a short operational handover document covering routine tasks the TnP cell would need to perform on the live portal, including how to verify a profile, how to create a drive, how to move applicants between rounds, and how to export shortlists.
- Completed the personal exit formalities at the cell, collected the training completion documentation, and marked the formal conclusion of the five-month industrial training period spanning the ~3.5-month internship at 75Way Technologies, Mohali and the ~7-week on-campus training at the GNDEC Training and Placement Cell.

---

## Technologies Used

- Next.js 16 with the App Router (production build)
- React 18 with Server and Client Components
- PostgreSQL via the Prisma ORM (production hosted on Neon)
- Vercel for production deployment of the Next.js application
- Neon for managed PostgreSQL hosting with automatic backups
- Postman for production smoke testing
- Markdown for the operational handover document
- Git and GitHub for the final commit and release tag

---

## Learnings

- Realised that two full days of structured end-to-end regression testing surfaced bugs that no amount of module-level testing had caught, validating the principle that integration is its own activity and not a free side-effect of unit-level correctness.
- Understood the practical importance of removing leftover debug logs and commented-out code before a production deployment, because those traces of in-progress development reflect poorly on the maintainability of the codebase and can leak unintended internal information.
- Picked up the discipline of running a smoke test on the production environment immediately after deployment, because configuration differences between staging and production are exactly the kind of issue that only surfaces on live infrastructure with real environment variables.
- Learned that an operational handover document is far more valuable to the end user than a technical README, because the coordinator does not need to know how the code works internally but does need to know how to perform routine administrative tasks confidently.
- Got first-hand experience of how walking through the production deployment with the TnP coordinator on the last day was the right way to close the project, because it transferred not just the access credentials but also the confidence that the system was operational and ready for the upcoming placement season.
- Realised that the future enhancement backlog discussed at handover served as a natural bridge between the work delivered during the training period and the work that the cell or a future contributor could pick up later, making the project feel like a foundation rather than an ending.
- Reflected at the end of the five months that the breadth of the multi-stack training at 75Way, the depth of the Manage Business platform ownership, and the on-campus delivery of two production systems at GNDEC together formed a more complete industrial training experience than any single project alone could have delivered.
