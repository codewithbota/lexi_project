# Pre-defense 1 submission

- **Repository:** https://github.com/codewithbota/lexi
- **Tag:** `pre-defense-1`
- **Date:** 24 October 2026
- **YouTrack:** https://botanw.youtrack.cloud/projects/LEX

## Completed work
- Project proposal, scope, target users; literature review; comparison of existing applications (`docs/01_research/`)
- Technology comparison (framework, backend, database, AI) with weighted scores
- Requirements: 36 functional (20 Must, 11 Should, 5 Could) and 13 non-functional, with priorities and acceptance criteria
- Diagrams: system context, use cases, components, ER, data flow level 0, 1 and 2, architecture (PNG)
- AI calibration test: 14 runs and decisions about models and limits (`docs/02_technical_design/calibration/`)
- Mockups of the key scenarios (16 screens, PDF) and a clickable Figma prototype
- Verification and evaluation plan: 12 metrics, baseline, 35 test cases, failure handling
- Repository, YouTrack project with 74 tasks, milestones, risks, dependencies

## Known limitations
- No application code yet; the repository shows analysis, design and planning.
- User interviews: in progress. The notes and the verified findings will be added to `docs/01_research/interviews-summary.md`; until then the priorities of the requirements are assumptions.
- The limits (characters, file size, pages, items per lesson and per day) are initial values from the calibration; we will check them on the prototype.
- The test of the backup model Gemini 3.8 Flash used batches of 10-50 items; it is slow and has only 20 requests per day.
- Kazakh AI quality is measured on a small sample (10 items per run); a larger check is planned.
- The mockups are static screens and a Figma prototype, not an implementation.
- Editable draw.io files are kept for diagrams 1-3; the other diagrams are PNG only.

## Outstanding tasks
See YouTrack. The next steps are implementation (risky parts first).
