# Week 15 — Activity Logs and Cross-Module Integration

**Dates:** 13 April – 17 April 2026
**Location:** 75Way Technologies, Mohali
**Project:** Manage Business

---

## Tasks Done

- Shifted focus for the week from owned modules to contributing across the Activity Logs module, which was primarily owned by another team member but required several integration touch-points with the Access Control and Subscription modules built earlier.
- Reviewed the existing Activity Logs collection and the helper utility used by other modules to record audit entries, and understood the standard log shape consisting of actor, action key, target resource, project context, and timestamp.
- Added structured Activity Log entries from the Subscription module for every lifecycle event of a subscription, including creation, scope update, expiry adjustment, and revocation, with the structured access scope recorded in the log payload for full traceability.
- Extended the Activity Logs viewer screen with two new filter dropdowns for filtering by Subscription-related actions and for filtering by the granter project, both of which were natural extensions of the existing filter interface.
- Worked with the developer who owned the Activity Logs module to agree on a stable set of action key constants used across the platform, and consolidated all the duplicated string literals into a single shared constants file imported by every module that recorded logs.
- Picked up a small ticket on the Authentication module to record login and signup events into the Activity Logs collection consistently, since the existing implementation only recorded one of the two events.
- Contributed code review comments on three pull requests raised by other team members during the week, including suggestions for tighter validation, clearer error messages, and one case where a new endpoint had not been wired through the Access Control helper.
- Spent two days on end-to-end integration testing across the User Management, Access Control, Subscription, and Activity Logs modules, walking through realistic administrator workflows to confirm that data flowed correctly between modules and that audit entries were created at every expected step.
- Found and fixed two small bugs during integration testing, one where a soft-deleted user remained visible in the autocomplete on the subscription create flow, and another where revoking a subscription did not invalidate the cached permission state for the affected user.
- Helped the team prepare a short demo for the client at the end of the week showing the complete delegation flow, the admin role management screen, and the activity logs view filtered by recent subscription changes.
- Joined the demo call along with the project lead and the senior developer, presented the Subscription module work, walked the client through the delegation API and the safeguards built into it, and answered the client's questions on extensibility.
- Captured the client's feedback from the demo and added the requested follow-up items to the team's backlog for the final sprint, which included a richer audit log filter and an export-to-CSV option for the activity log screen.

---

## Technologies Used

- Next.js (App Router) with API route handlers
- React 18 with functional components and hooks
- MongoDB via the Mongoose ODM
- Activity Logs collection with shared action key constants
- Custom Access Control helper module (`lib/access.js`)
- Tailwind CSS for the admin UI
- Postman for endpoint verification
- Git feature branches and GitHub pull requests
- Browser-based screen sharing for the client demo

---

## Learnings

- Realised that contributing across a module owned by someone else is a different exercise from owning a module, because the priority shifts to respecting existing conventions rather than imposing new ones.
- Understood the practical importance of consolidating duplicated string literals into a single constants file, because every duplicated literal in a logging system eventually leads to a subtle inconsistency that is painful to debug across collections of audit entries.
- Picked up the value of explicit end-to-end integration testing as a planned activity at the end of a development cycle, because individual modules can each pass their own checks while still failing to cooperate correctly at the boundary points.
- Learned that the second category of bugs found during integration testing is almost always around cache invalidation across modules, which mirrors the well-known observation that cache invalidation is one of the hardest problems in software.
- Got first-hand experience of how meaningful a code review comment becomes when it is grounded in an architectural principle (such as the rule that all routes must use the Access Control helper) rather than a stylistic preference.
- Realised that participating in a client demo is a fundamentally different experience from the development cycle, because the client's questions reveal which features they consider valuable and which assumptions they had made differently from the team.
- Observed that the most useful preparation for a client demo is not the polish of the slides but the team's ability to handle unexpected questions confidently, which depends entirely on the team's depth of familiarity with the code.
