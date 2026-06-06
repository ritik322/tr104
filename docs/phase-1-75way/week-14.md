# Week 14 — Subscription UI and Inter-Project Access Delegation

**Dates:** 6 April – 10 April 2026
**Location:** 75Way Technologies, Mohali
**Project:** Manage Business

---

## Tasks Done

- Continued ownership of the Subscription module with the goal of completing the admin-facing user interface and implementing the inter-project access delegation flow, which was the headline feature requested by the client for this module.
- Built the admin-facing Subscription dashboard with a paginated table showing all active subscriptions across the platform, with filters for granter project, grantee user, and lifecycle status, reusing the table and pagination components from the User Management module.
- Added a detail side panel that opened on row selection and displayed the complete subscription record, including the structured access scope, the audit timestamps, and a revoke action gated by the appropriate permission key from the Access Control module.
- Built the create-subscription form as a multi-step modal, with the first step selecting the granter project, the second step selecting the grantee user through a searchable autocomplete, and the third step configuring the access scope through a permission picker grouped by module.
- Implemented client-side and server-side validation throughout the create flow, including the rule that the granter project must be one the current administrator had access to, the expiry timestamp must be in the future, and the scope must include at least one permission key.
- Implemented the inter-project access delegation API endpoint, which allowed a user authenticated on one integrated client product to grant scoped access to another user through the Manage Business platform without requiring administrator intervention.
- Designed the delegation flow to be initiated through a server-to-server call from the originating product, with the originating product's API key authenticating the request and the granted scope strictly limited to the permissions the granter held within their own role.
- Added safeguards to the delegation flow including a maximum expiry duration of ninety days, a hard cap on the number of active delegations per granter, and a server-side check that prevented escalation of privileges beyond what the granter held themselves.
- Extended the Access Control helper from Week 12 to consider active subscriptions and delegations alongside role-based permissions when evaluating a permission check, ensuring that all paths of permission grant flowed through the same evaluation logic.
- Tested the complete end-to-end delegation flow using two separate test client products configured in the development environment, confirming that a delegated user could access exactly the granted resources and nothing more.
- Wrote integration documentation for the delegation API targeted at developers of the client's other internal products, including the request shape, the authentication mechanism, the scope structure, and the error response conventions.
- Raised three pull requests during the week covering the admin UI, the delegation endpoint, and the documentation update, all of which were merged after addressing review feedback from the project lead.

---

## Technologies Used

- Next.js (App Router) with API route handlers
- React 18 with functional components and hooks
- MongoDB via the Mongoose ODM
- Custom Access Control helper module (`lib/access.js`)
- Tailwind CSS for the admin UI
- Custom reusable table, modal, side panel, and autocomplete components
- API key authentication for server-to-server delegation calls
- Postman for endpoint verification with multiple environments
- Markdown for the integration documentation
- Git feature branches and GitHub pull requests

---

## Learnings

- Realised that building a multi-step modal for a complex create flow is significantly more user-friendly than a single long form, because each step focuses the administrator's attention on one decision at a time.
- Understood the practical importance of the privilege-escalation safeguard, because a delegation flow without it would allow a low-privilege user to grant another user permissions they themselves did not possess, which would be a serious security flaw.
- Picked up the value of designing every permission grant path to flow through the same evaluation logic, because the entire benefit of the Access Control helper is lost the moment any module starts bypassing it.
- Learned that server-to-server authentication using API keys is the right choice for product-to-platform calls, because the API keys can be rotated independently of user sessions and the call is not tied to any particular logged-in user.
- Got first-hand experience of why integration documentation written by the developer who built the API is far more useful than documentation written by anyone else, because only the developer knows which edge cases the API actually handles and which it does not.
- Realised that testing inter-project flows requires multiple test environments configured in parallel, and that the small investment of setting them up paid off many times over during the verification phase.
- Observed that even features explicitly requested by the client benefit from being introduced with clear safeguards, because the client's stated requirements rarely include the constraints needed to prevent misuse.
