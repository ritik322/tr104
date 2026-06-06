# Week 12 — Access Control Module

**Dates:** 23 March – 27 March 2026
**Location:** 75Way Technologies, Mohali
**Project:** Manage Business

---

## Tasks Done

- Began the sprint as the primary owner of the Access Control module, which was responsible for defining roles, permissions, and the enforcement layer that gated every protected API route on the platform.
- Designed the schema for the Role and Permission collections in MongoDB, with each role holding a list of permission keys and each permission representing a single discrete capability such as `user.create`, `user.delete`, or `project.read`.
- Discussed the schema with the project lead and one of the senior developers, and adjusted the design based on their feedback to store permissions as string keys rather than ObjectId references, since the keys themselves were stable identifiers and string-based checks were faster than additional database lookups.
- Implemented the Mongoose models for Role and Permission, including unique constraints on role names and permission keys, and seeded the development database with the initial set of permissions and a small set of default roles such as Administrator, Manager, and Viewer.
- Built the CRUD API endpoints for managing roles, including listing all roles, creating a new role with a chosen permission set, editing the permissions of an existing role, and soft-deleting a role that was no longer needed.
- Wrote a centralised permission helper utility at `lib/access.js` that exported a single function for checking whether the currently authenticated user held a given permission, based on the user's assigned role and the role's permission list.
- Refactored several existing API routes across the User Management and Authentication modules to use the new permission helper, replacing hard-coded role checks with explicit calls like `hasPermission(session, 'user.create')`.
- Built the admin-facing UI for managing roles, including a list of existing roles, a detail view showing the assigned permissions grouped by module, and a multi-select interface for adjusting the permission set when editing a role.
- Built the user-role assignment screen that allowed an administrator to assign a role to any existing user, and ensured that the change was reflected in the user's next session without requiring a full re-login.
- Added a small audit hook that appended an entry to the Activity Logs collection every time a role was created, edited, or deleted, providing a basic audit trail for sensitive permission changes.
- Wrote a short design note inside the module folder describing the role-based access model, the rationale for using string-based permission keys, and the convention that every new protected route must call the permission helper rather than implementing its own role check.
- Raised two pull requests covering the schema and helper utility in the first one and the admin UI plus audit hook in the second one, and got both merged after a thorough review by the project lead.

---

## Technologies Used

- Next.js (App Router) with API route handlers
- React 18 with functional components and hooks
- MongoDB via the Mongoose ODM
- Custom permission helper module (`lib/access.js`)
- Tailwind CSS for the admin UI
- Custom reusable table, modal, and multi-select components
- Postman for endpoint verification
- Git feature branches and GitHub pull requests

---

## Learnings

- Realised that designing an access control schema is a deceptively difficult exercise, because every modelling decision constrains how the system can be extended later when new modules and new permissions are added.
- Understood the practical reasons for preferring string-based permission keys over ObjectId references, including faster runtime checks, easier debugging in logs, and stable identifiers that survive database migrations.
- Picked up the value of a single centralised permission helper as a non-negotiable design principle, because permission logic scattered across routes inevitably drifts out of sync and becomes a source of subtle authorisation bugs.
- Learned that refactoring existing routes to use a new helper is just as important as building the helper itself, because the benefit is only realised when the entire codebase consistently calls the same gateway.
- Got first-hand experience of how access control changes need their own audit trail, because the most sensitive operations on the platform are exactly the ones that grant or revoke the ability to perform other sensitive operations.
- Realised that owning a module from the schema upwards means every downstream caller of that module is affected by design decisions made during the schema stage, which raises the importance of consulting senior developers early.
- Observed that writing a design note alongside the code is far more useful than writing it after the fact, because the rationale behind the chosen design is most clearly remembered while the decisions are still fresh.
