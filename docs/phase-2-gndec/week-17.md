# Week 17 — Plugin Completion and Deployment

**Dates:** 27 April – 1 May 2026
**Location:** GNDEC Training and Placement Cell, Ludhiana
**Project:** Training Letter Management Plugin

---

## Tasks Done

- Continued the Training Letter Plugin work with the goal of completing all four role-specific dashboards, the dual-approval state machine, the reference number generation, and the file security gatekeeper, followed by deployment to the GNDEC Moodle instance by the end of the week.
- Built the Student Dashboard inside `request.php`, combining a Moodle Form API application form with a tracking table of the logged-in student's historical requests, including color-coded status badges for both the initial request status and the confirmation letter status.
- Built the Teacher Dashboard inside `approve.php` with department-scoped visibility enforced at the database query level, a responsive CSS Grid-based multi-parameter filter system, statistical counter cards summarising pending, approved, and rejected requests, and one-click quick-action buttons embedded in the table view for direct approval and rejection.
- Built the Manager Dashboard inside `manage.php` as a tabbed interface with a global request management tab and separate CRUD tabs for Courses, Departments, and Batches, including Moodle's autocomplete component for the many-to-many teacher-department assignment screen.
- Built the Site Admin Setup screen inside `admin.php`, restricted strictly to Moodle site administrators through Moodle's native capability check, using Moodle's AJAX user selector for adding and removing manager-role users from the `local_tl_managers` table.
- Implemented the reference number generation logic to fire on the initial request approval action, producing reference numbers in the format `GNDEC/[YEAR]/[ID]` where the year is the current calendar year and the ID is the auto-incremented primary key of the request record.
- Implemented the dual-approval state machine across both `status` (initial request) and `conf_status` (confirmation letter) fields on the request table, enforcing all valid transitions at the database update layer rather than only in the UI, and blocking invalid transitions such as uploading a confirmation letter before the initial request approval.
- Implemented the file security gatekeeper as the function `local_training_letter_pluginfile()`, which Moodle invokes for every file access request, with strict checks that the requesting user is either the owner of the uploaded confirmation letter or an authorised teacher mapped to the relevant department.
- Walked through all four dashboards end to end with the TnP coordinator, demonstrated each role's workflow with realistic test data seeded into the local database, and incorporated several small UX refinements based on the coordinator's feedback.
- Packaged the plugin into a distributable zip archive, deployed it to the GNDEC Moodle staging environment, and ran the install step under the Moodle site administrator account to confirm that the install process worked cleanly on the production-grade Moodle instance.
- Performed an end-to-end verification on the staging environment with three test accounts (a student, a teacher, and a manager), confirming that the role resolution worked correctly, the dashboards loaded as expected, and the dual-approval state machine behaved identically to the local environment.
- Deployed the plugin to the production GNDEC Moodle instance after the staging verification, ran the install step, and confirmed with the TnP coordinator that the plugin was now visible and usable by the intended user roles.

---

## Technologies Used

- Moodle LMS local plugin architecture
- PHP 8 with the Intelephense extension in Visual Studio Code
- MySQL via Moodle's `$DB` abstraction layer with prepared statements
- Moodle Form API (`moodleform`) for all submission forms
- Moodle File API with the custom `local_training_letter_pluginfile()` gatekeeper
- Moodle's AJAX user selector for the Site Admin setup screen
- Moodle's autocomplete component for the teacher-department assignment
- Moodle's `hideIf()` form logic for dynamic field reveals
- HTML and CSS Grid for responsive dashboard layouts
- Git and GitHub for version control of the plugin source

---

## Learnings

- Realised that completing all four role dashboards in a single sprint week was achievable only because the role resolution function and the schema had been built carefully in the previous week, which validated the principle of investing in foundations before features.
- Understood the practical importance of enforcing state machine transitions at the database update layer rather than only in the UI, because the UI layer can always be bypassed by anyone with direct access to the API, and the database is the only place where the invariant truly holds.
- Picked up the value of the file security gatekeeper as a non-negotiable layer in any file-upload feature, because without it the uploaded files would be served by Moodle to anyone who could guess or enumerate the file URLs.
- Learned that the auto-generation of reference numbers in a fixed format gives the cell a stable institutional identifier that can be quoted in official communication, which is one of the operational benefits of digitising the workflow that the coordinator valued highly.
- Got first-hand experience of how the cycle of local development, staging deployment, and production deployment surfaces environment-specific issues that are invisible during local-only testing, particularly around file paths, permissions, and Moodle version compatibility.
- Realised that walking through the dashboards with the actual end user (the TnP coordinator) revealed several small UX issues that would have been missed in self-review, because the end user thinks about the workflow in operational terms rather than technical ones.
- Observed that deploying a working version of the plugin to production within two weeks of the initial site visit demonstrated the practical value of Moodle's local plugin architecture, because the same scope on a custom-built platform would have taken significantly longer.
