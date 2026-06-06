# Week 13 — Subscription Module Foundations

**Dates:** 30 March – 3 April 2026
**Location:** 75Way Technologies, Mohali
**Project:** Manage Business

---

## Tasks Done

- Began the largest deliverable of the project as the primary owner of the Subscription Management module, which would allow external client products integrated with Manage Business to grant scoped access to their users through the central platform.
- Spent the first day with the project lead and the client point of contact gathering detailed requirements for the module, including the expected user stories around inter-project access delegation, the granularity of access scopes, and the lifecycle of a subscription record.
- Documented the requirements in a short specification note inside the module folder, including the supported subscription types, the entities involved (granter project, grantee user, scope, expiry), and the boundary conditions that needed to be handled.
- Designed the Mongoose schema for the Subscription collection after reviewing the requirements, with fields covering the granter project, the grantee user, the access scope, the expiry timestamp, the lifecycle status, and audit timestamps for creation, update, and revocation.
- Reviewed the schema design with the project lead and incorporated several refinements, including the addition of a composite uniqueness constraint to prevent duplicate active subscriptions for the same project-user-scope combination.
- Implemented the Mongoose model with the agreed schema, including indexed fields on the granter project and grantee user for fast lookups, and a TTL-style expiry filter applied at query time rather than relying on a background job.
- Built the basic CRUD API endpoints for the module, including creating a new subscription, listing subscriptions filtered by granter project or grantee user, retrieving a single subscription by ID, updating the scope or expiry of an existing subscription, and revoking an active subscription.
- Implemented the access scope as a structured object rather than a flat string, with fields for the permission keys granted, the resource identifiers the access applied to, and an optional list of denied keys for fine-grained overrides.
- Integrated the new Subscription module with the Access Control helper from Week 12, so that the permission check could optionally consider both the user's role-based permissions and any active subscriptions granting additional capabilities.
- Wrote a handful of focused manual test cases in Postman covering the most important scenarios, including creating a subscription, attempting to create a duplicate one (which should fail), revoking a subscription, and querying expired subscriptions.
- Raised the first pull request for the module containing the schema, model, and CRUD endpoints, along with the design note as supporting documentation, and got it reviewed and merged by the end of the week.
- Drafted a rough plan for the following sprint covering the admin-facing UI for the Subscription module, the inter-project access delegation flow, and the integration with the Activity Logs module.

---

## Technologies Used

- Next.js (App Router) with API route handlers
- MongoDB via the Mongoose ODM
- Composite uniqueness constraints and indexed lookups
- Custom Access Control helper module (`lib/access.js`)
- Postman for endpoint verification
- Markdown for the in-repo specification and design notes
- Git feature branches and GitHub pull requests

---

## Learnings

- Realised that the most important hour of a new module's lifecycle is the requirements conversation with the client and the project lead, because every line of code written afterwards is shaped by the choices made in that conversation.
- Understood the practical value of writing a short specification note before any schema work, because the act of writing forces unspoken assumptions to surface in a form that can be reviewed by others.
- Picked up the importance of composite uniqueness constraints at the database level rather than at the application layer, because database-level enforcement is the only guarantee that survives concurrent requests and bypassed application checks.
- Learned that representing complex domain concepts like access scope as structured objects rather than flat strings pays off significantly later, because the structure can be extended without breaking the existing serialisation format.
- Got first-hand experience of how a well-designed permission helper from one module becomes a foundation that other modules build on, since the Subscription module was able to extend the existing checks rather than reinvent them.
- Realised that filtering expired records at query time is often a simpler and more reliable choice than relying on background jobs to clean up the collection, particularly when the volume of expired records is small.
- Observed that drafting a rough plan for the next sprint at the end of the current sprint is a habit worth keeping, because it keeps the next set of work clearly in mind during the weekend break and avoids a cold start on Monday.
