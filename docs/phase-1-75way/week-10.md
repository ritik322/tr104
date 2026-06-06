# Week 10 — Authentication Module Deep Dive

**Dates:** 9 March – 13 March 2026
**Location:** 75Way Technologies, Mohali
**Project:** Manage Business

---

## Tasks Done

- Began the first full sprint of the project phase with the Authentication module as the primary focus area for the week, since every other module on the platform depends on a correctly working authentication layer.
- Read through the existing NextAuth.js configuration in detail, including the credentials provider definition, the `authorize` callback that validates submitted credentials against the User collection, and the `jwt` and `session` callbacks that shape the contents of the issued token and the exposed session object.
- Studied the existing signup flow, which creates a new user document in MongoDB after hashing the submitted password with bcrypt and validating that the email is not already registered.
- Reviewed the existing login flow end to end, tracing the request from the client form, through the NextAuth credentials provider, to the JWT token issued by the server and stored in an HTTP-only cookie.
- Identified a few areas in the existing authentication code where validation could be tightened, including missing length checks on the password field at the API layer and inconsistent error messages between the signup and login endpoints.
- Picked up a small ticket to add stronger server-side validation on the signup endpoint, including minimum password length, allowed character set, and a clearer error response format aligned with the team's conventions.
- Implemented the validation changes, wrote a few manual test cases through Postman to confirm all error and success scenarios, and committed the work on a feature branch following the team's branching convention.
- Raised a pull request for the validation changes with a clear description of the problem, the chosen approach, and the manual test scenarios that had been verified.
- Addressed review comments from two team members on the pull request, including a suggestion to extract the password validation rules into a shared utility function so that the same rules could later be reused on a password reset endpoint.
- Got the pull request approved and merged into the `main` branch by the end of the week, completing the first contribution to the project.
- Set up a personal local script that seeded the development MongoDB database with a small set of fixture users for faster manual testing during development, which removed the need to repeatedly sign up new users through the UI.
- Attended the mid-sprint check-in meeting where the team shared progress on their respective tickets and the project lead clarified upcoming work on the User Management and Access Control modules.

---

## Technologies Used

- Next.js (App Router) and its built-in API route handlers
- Custom NextAuth.js setup with credentials provider and JWT strategy
- MongoDB via the Mongoose ODM
- bcrypt for password hashing
- Postman for API endpoint testing
- Git feature branches and GitHub pull requests
- Visual Studio Code with ESLint and Prettier
- Chrome DevTools (Application tab for inspecting cookies)

---

## Learnings

- Realised that the most valuable skill in the first week of touching authentication code is not writing new code but reading the existing code carefully enough to understand exactly how the JWT, the session cookie, and the database records relate to each other.
- Understood the practical importance of HTTP-only cookies as a defence against XSS-based session theft, and why the team had standardised on this storage strategy over local storage despite the slightly more complex client-side code.
- Learned that input validation at the API layer is not a substitute for client-side validation but a non-negotiable additional layer, because client-side checks can always be bypassed by anyone who can send a raw HTTP request.
- Picked up the team's coding convention that error responses should always have a consistent JSON shape with a stable set of keys, since this makes it much easier for the frontend to handle errors uniformly across the application.
- Got first-hand experience of how a pull request review can improve code quality through the suggestion to extract the password validation logic into a shared utility, which is a refactoring decision that would not have occurred to a developer working in isolation.
- Realised that seeding the database with fixture data for development is a simple investment that pays off many times over during a sprint, because it eliminates the slow path of clicking through the UI for every test cycle.
- Observed that even though the contribution this week was small, going through the entire feature branch, pull request, review, and merge cycle was an important rehearsal for the larger contributions planned for the coming weeks.
