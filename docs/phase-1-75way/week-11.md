# Week 11 — User Management Module

**Dates:** 16 March – 20 March 2026
**Location:** 75Way Technologies, Mohali
**Project:** Manage Business

---

## Tasks Done

- Shifted focus from the Authentication module to the User Management module for the second sprint of the project, with the goal of building out the administrator-facing CRUD interface for managing user accounts across the platform.
- Studied the existing User Mongoose model in detail, including its fields for identity, contact information, role references, and timestamps for creation, update, and soft deletion.
- Reviewed the existing list-users API endpoint and identified that it returned the entire user collection without pagination, which would not scale as the user base grew across integrated client products.
- Picked up the ticket to add server-side pagination to the list-users endpoint, including support for page size, page number, total count, and search by email or name through a case-insensitive regular expression match.
- Implemented the paginated query using Mongoose's `skip`, `limit`, and `countDocuments` methods, and confirmed through manual testing that the response shape included both the page of users and the total count required by the frontend pagination component.
- Built a new admin-facing user listing screen on the frontend using a reusable table component, with the pagination controls wired to the new server-side endpoint and a debounced search input that did not fire a request on every keystroke.
- Added the create-user flow on the admin side, including a modal form that accepted email, password, name, and an initial role assignment, with the same shared validation utility from Week 10 reused on the password field.
- Implemented the edit-user flow, which fetched the existing user record into the same modal form, hid the password field by default (unless the admin chose to reset it), and submitted only the changed fields through a partial update endpoint.
- Built the soft-delete flow for users by setting a `deletedAt` timestamp on the record rather than removing the document from the collection, which preserved historical references from audit logs and other related collections.
- Adjusted the list-users endpoint to filter out soft-deleted users by default, while exposing a query parameter that allowed an admin to view soft-deleted records for recovery purposes if needed.
- Wrote a short README section inside the User Management module folder describing the available endpoints, the expected request and response shapes, and the soft-delete convention so that other team members joining the module later would have a clear starting point.
- Raised three separate pull requests during the week for the pagination, the create and edit flows, and the soft-delete behaviour, and got all of them merged after addressing review comments.

---

## Technologies Used

- Next.js (App Router) with API route handlers
- React 18 with functional components and hooks
- MongoDB via the Mongoose ODM (`skip`, `limit`, `countDocuments`, `findByIdAndUpdate`)
- Tailwind CSS for styling
- Custom reusable table and modal components shared across the platform
- Lodash `debounce` for the search input
- Postman for endpoint verification
- Git feature branches and GitHub pull requests

---

## Learnings

- Realised that pagination is one of the most commonly missed details in early-stage CRUD endpoints, and that adding it after the fact is much harder once the frontend has been built against the unpaginated version.
- Understood the practical trade-offs between `skip` and `limit` pagination versus cursor-based pagination, and learned that the team had standardised on offset pagination for admin screens because the data volumes were small and the simplicity outweighed the performance benefits of cursors.
- Picked up the value of debounced search inputs as a small but high-impact frontend pattern, because it prevents a flood of requests to the server when an admin is typing a multi-character search query.
- Learned that soft delete is not just a defensive habit but a deliberate design choice that preserves the integrity of foreign references in other collections, particularly audit logs and activity records that should never lose context due to a deletion.
- Got first-hand experience of how splitting a feature into multiple focused pull requests is far more reviewable than a single large pull request, even when the work is closely related.
- Realised that writing a short module-level README during development is a low-cost investment, because the developer who wrote the code has the clearest mental model of it and is therefore the best person to document it.
- Observed that even small frontend conveniences like reusable table and modal components dramatically accelerate the build pace, because new screens compose existing primitives rather than reinventing layout and behaviour every time.
