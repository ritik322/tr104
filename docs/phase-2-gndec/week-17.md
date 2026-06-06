# Week 17 — GNDEC Onboarding and Training Letter Plugin Kick-off

**Dates:** 27 April – 1 May 2026
**Location:** GNDEC Training and Placement Cell, Ludhiana
**Project:** Training Letter Management Plugin

---

## Tasks Done

- Began the second part of the six-month industrial training at the Training and Placement Cell of Guru Nanak Dev Engineering College, Ludhiana, after the conclusion of the four-month internship at 75Way Technologies, Mohali, the previous week.
- Reported to the Training and Placement Cell on the first day, met the TnP coordinator, and discussed the scope of the on-campus training work covering two distinct deliverables: a Moodle plugin for digitising the training letter workflow and a full-stack web portal for managing campus placements.
- Spent the first two days understanding the existing manual workflows at the cell in depth, including the paper-based training letter application process, the physical handover of forms between departments and the cell, and the long turnaround times that the existing process had been suffering from.
- Documented the existing training letter workflow in a short specification note, capturing the journey of a typical application from student submission through department review, cell reference number issuance, physical signature, and confirmation letter return.
- Identified the four user roles involved in the workflow (Student, Teacher, Manager, Site Admin) and the distinct responsibilities of each, which would later map directly onto the role-resolution layer of the plugin.
- Studied the architecture of Moodle local plugins through the official Moodle developer documentation, focusing on the standard directory layout, the role of `version.php` and `lib.php`, the database schema definition through `db/install.xml`, and the convention of namespacing functions and tables with a plugin-specific prefix.
- Set up a local Moodle development environment on the assigned workstation, including a local Apache and MySQL stack, a fresh Moodle installation matching the version running on the GNDEC instance, and Visual Studio Code with the PHP Intelephense extension for autocomplete and navigation.
- Scaffolded the plugin skeleton at `local/training_letter` with the minimum required files (`version.php`, `lib.php`, `db/install.xml`, language strings) and confirmed that Moodle recognised the plugin and registered it without errors during the install step.
- Designed the database schema for the plugin on paper after the workflow study, defining the six tables required (`local_tl_requests`, `local_tl_dept_teachers`, `local_tl_managers`, `local_tl_courses`, `local_tl_depts`, `local_tl_batches`) along with their fields, foreign keys, and the dual-status fields on the request table.
- Translated the schema into the `db/install.xml` file following Moodle's XMLDB standard, ran the plugin install step, and verified through the local Moodle's database browser that all six tables had been created with the expected structure.
- Implemented the central role resolution function `local_training_letter_get_type()` in `lib.php`, which evaluated the current user's role by checking Moodle's native administrator capability, the `local_tl_managers` table, and the `local_tl_dept_teachers` table in order.
- Drafted a short development plan for the two-week plugin sprint covering the four role-specific dashboards, the dual-approval state machine, the reference number generation logic, and the file security gatekeeper for confirmation letters.

---

## Technologies Used

- Moodle LMS (matching the version of the GNDEC instance)
- PHP 8 with the Intelephense extension in Visual Studio Code
- MySQL via Moodle's internal connection
- Moodle's XMLDB standard for schema definition
- Apache and MySQL stack for the local development environment
- Markdown for the workflow specification and development plan
- Git and GitHub for version control of the plugin source

---

## Learnings

- Realised that the most valuable activity in the first few days at a new site is to study the existing manual workflow carefully, because every design decision in the plugin would later be judged against how well it served the existing process rather than how technically elegant it was.
- Understood the practical importance of Moodle's local plugin architecture as a stable extension point that does not require modifications to Moodle core, which is essential for long-term maintainability of the GNDEC instance across Moodle upgrades.
- Picked up the convention of prefixing every table with `local_tl_` and every public function with `local_training_letter_`, which is not merely a style choice but a hard requirement for avoiding namespace collisions with other Moodle plugins.
- Learned that designing a database schema on paper before writing the XMLDB definition is significantly more efficient, because the act of sketching forces all the foreign keys and constraint relationships to be reasoned about before they are translated into XML.
- Got first-hand experience of how Moodle's documentation, although denser than that of newer frameworks, is comprehensive enough that almost any architectural question can be answered without resorting to source code reading.
- Realised that the role resolution function is the most important single function in the plugin, because every dashboard, every endpoint, and every UI affordance is gated by what it returns, which raises the importance of getting it right early.
- Observed that the transition from a JavaScript-and-MongoDB stack to a PHP-and-MySQL stack felt natural after the wide range of stacks covered during the training phase at 75Way, which validated the breadth of the earlier curriculum in a very direct way.
