# Week 9 — Manage Business Project Kick-off

**Dates:** 2 March – 6 March 2026
**Location:** 75Way Technologies, Mohali
**Project:** Manage Business

---

## Tasks Done

- Began the project phase of the internship after the successful completion of the eight-week training programme, joining the three-member team assigned to the Manage Business platform under the supervision of the project lead.
- Attended the project kick-off meeting on the first day, where the project lead introduced the client, the business problem, and the long-term vision of building a centralized authentication and access management layer that would be integrated into multiple internal products of the client organisation.
- Received a high-level walkthrough of the existing codebase, which had been started earlier by the previous team and would be inherited and extended further by the new three-member team during this internship cycle.
- Studied the proposed module breakdown of the platform consisting of five major modules: Authentication, User Management, Access Control, Activity Logs, and Subscription Management, and learned the rough scope of each.
- Cloned the existing repository from GitHub, set up the local development environment with Node.js, npm, and the required environment variables, and verified that the development server started cleanly on the local machine.
- Connected the local environment to a development MongoDB Atlas cluster shared by the team, and confirmed that the application could read from and write to the database successfully through the existing API endpoints.
- Studied the project's directory structure built around the Next.js App Router, including the convention-based routing under the `app/` directory, the placement of API route handlers in `app/api/`, and the shared utilities under a top-level `lib/` folder.
- Reviewed the existing authentication implementation built on a custom NextAuth.js setup with a JWT-based session strategy, including the credentials provider, session callbacks, and token rotation logic.
- Reviewed the existing Mongoose models defined for the User and related collections, and understood the relationships between users, projects, roles, and permissions as represented in the document schema.
- Participated in the first sprint planning meeting of the cycle, where the team broke down the upcoming sprint's work into smaller tasks and the project lead assigned the initial set of tickets to each team member based on the modules they would own.
- Was assigned primary ownership of the Subscription Management module and the Access Management module after the planning discussion, with smaller contributions expected across the Authentication, User Management, and Activity Logs modules as needed.
- Familiarised the GitHub pull request workflow used by the team, including the branching strategy, the pull request template, the review requirements, and the convention that no commit goes to the `main` branch directly.

---

## Technologies Used

- Next.js (App Router)
- React 18
- MongoDB (development cluster on MongoDB Atlas)
- Mongoose ODM
- Custom NextAuth.js setup with JWT strategy
- Tailwind CSS
- Node.js and npm
- Visual Studio Code with ESLint and Prettier extensions
- Git and GitHub with pull request-based code review workflow
- Postman for API exploration

---

## Learnings

- Realised that joining an existing codebase is a fundamentally different exercise from starting a project from scratch, because the first task is not to write code but to read enough of it to understand the conventions, abstractions, and trade-offs already in place.
- Understood the difference between the older Pages Router and the newer App Router in Next.js, and observed why the team had chosen the App Router for this project despite the slight learning curve compared to the more familiar older model.
- Picked up the practical value of a custom NextAuth.js setup over an off-the-shelf configuration, because the team had specific requirements around session shape, JWT contents, and cross-product session sharing that the default setup could not satisfy.
- Learned that document databases like MongoDB encourage modelling decisions that would be unusual in a relational database, particularly around denormalisation and embedding of related data inside parent documents for read performance.
- Got first-hand experience of how an Agile team operates in practice, including the rhythm of sprint planning, the granularity of tickets, and the importance of clear acceptance criteria for each piece of work.
- Realised that being assigned ownership of two specific modules early in the project meant that responsibility for design decisions on those modules would also rest primarily on the assigned developer, which raised the stakes of every design choice.
- Observed that the team's strict pull request workflow, while occasionally slower than direct commits, was clearly designed to share knowledge across team members and catch design issues before they spread through the codebase.
