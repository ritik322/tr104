# Week 16 — Final Sprint, Handover, and Internship Wrap-up

**Dates:** 20 April – 24 April 2026
**Location:** 75Way Technologies, Mohali
**Project:** Manage Business

---

## Tasks Done

- Entered the final week of the four-month internship at 75Way Technologies with the goal of completing the follow-up items from the previous week's client demo, freezing the codebase for handover, and finishing the personal exit formalities.
- Picked up the two backlog items raised by the client during the demo, namely a richer filter on the Activity Logs viewer and an export-to-CSV option for the activity log screen, both of which were scoped tightly to fit within the final sprint.
- Implemented the richer filter on the Activity Logs viewer, adding date-range filtering, multi-select filtering on the action key, and a free-text search across the target resource field, all wired through the same shared filter component used elsewhere in the platform.
- Built the export-to-CSV option using a small server-side helper that streamed the matching rows directly to the response without holding the entire result set in memory, which kept the export responsive even on larger date ranges.
- Wrote a short module-level README for the Subscription module summarising the schema, the endpoint surface, the inter-project delegation flow, and the safeguards built into the design, intended as the primary reference for whoever maintained the module after handover.
- Updated the in-repo design notes for the Access Control module with the integration points added during the Subscription and Activity Logs work, so that the documentation remained consistent with the current state of the codebase.
- Walked through the Subscription and Access Control modules in detail with the project lead during a recorded handover session, covering the schema decisions, the helper utility, the delegation flow, and the known limitations that had been left for future iterations.
- Walked through the same modules with the other two team members in a separate informal session, focusing on the day-to-day operations of the code (where to find what, which conventions to follow) so that they could continue iterating on the module after the internship ended.
- Completed a final round of manual regression testing across the platform, walking through the major administrator workflows one last time to confirm that no regressions had been introduced by the final sprint's changes.
- Raised the final pull request of the internship covering the activity log filter and CSV export, got it reviewed and merged by the project lead, and confirmed that the staging deployment reflected the changes correctly.
- Completed the personal exit formalities including the return of the workstation, the deactivation of the company accounts, the collection of the internship completion certificate, and the closing conversation with the HR team.
- Attended the team's farewell lunch on the last day with the project lead, the senior developer, and the two co-interns, marking the end of the four-month industrial internship at 75Way Technologies, Mohali.

---

## Technologies Used

- Next.js (App Router) with API route handlers
- React 18 with functional components and hooks
- MongoDB via the Mongoose ODM
- Custom server-side CSV streaming helper
- Tailwind CSS for the admin UI
- Markdown for module READMEs and design notes
- Postman for endpoint verification
- Git feature branches and GitHub pull requests
- Staging deployment for final verification

---

## Learnings

- Realised that the final week of an internship is best treated as a separate phase of work focused on closure rather than new feature development, because the value of a smooth handover often exceeds the value of one more shipped feature.
- Understood the practical importance of writing module-level READMEs at the end of an ownership cycle, because the developer leaving the module is the one with the clearest mental model of its design and is therefore the best person to capture that knowledge in writing.
- Picked up the technique of streaming responses for export endpoints rather than building the full payload in memory, because the difference is invisible at small data sizes but becomes the deciding factor between a working and a broken export at larger sizes.
- Learned that a recorded handover session combined with an informal walkthrough with peers is a more effective knowledge transfer than either alone, because the recorded session captures the formal design and the informal walkthrough surfaces the day-to-day tacit knowledge.
- Got first-hand experience of how an internship concludes when the work has been carried out genuinely, namely with a clear sense of the modules owned, the contributions made, and the gaps that remained for the next iteration.
- Realised that the relationships built with the project lead, the senior developer, and the co-interns over four months are themselves a valuable outcome of the internship, independent of the code shipped.
- Observed that the multi-stack training in the first two months, although it occasionally felt disconnected from the final project work, ended up being directly useful because the breadth of exposure shaped how design decisions were considered during the project phase.
