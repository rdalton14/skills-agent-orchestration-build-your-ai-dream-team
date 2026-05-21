# Mona's Project Pulse  Implementation Plan

This document is a complete, actionable implementation plan for building "Mona's Project Pulse" dashboard in this repository. It is intended for the Orchestrator to divide work between the Designer and Coder agents and to run in a learning Codespace environment. The plan is organized into phases with step-by-step work items, file responsibilities, dependencies, validation criteria, and open questions/risks.

--------------------------------------------------------------------------------
1) Summary
--------------------------------------------------------------------------------

Mona's Project Pulse is a lightweight, static-dashboard that presents project status, health metrics, and timelines for easy progress monitoring. The goal is a small, self-contained web app in the repo's app/ folder composed of index.html, styles, and a sample JSON data file. The Designer will deliver responsive UI mockups, palette, and interaction rules; the Coder will implement HTML/CSS/JS, load sample data, add charts/visualizations (lightweight CDN charting), and configure deterministic VS Code preview (.vscode/launch.json). The outcomes must be easily runnable in the Codespace (open app/index.html from the workspace app directory) and validated with explicit checks.

--------------------------------------------------------------------------------
2) Phases and ordered implementation steps
--------------------------------------------------------------------------------

Phase 0  Preparation (Setup)
- Step 0.1: Project orientation & constraints
  - Objective: Ensure both agents understand repository rules, file-scoped ownership, no secret commits, and the required VS Code preview behavior.
  - Files: docs/agent-team.md (read-only)
  - Responsible: Orchestrator (review) / Planner (already done)
  - Effort: S

Phase 1  Layout & Data Design (Designer leads; Coder prepares skeleton)
- Step 1.1: Designer  UI concept & information architecture
  - Objective: Produce low-fidelity mockup(s) showing layout elements: header, summary KPI cards, timeline/gantt or roadmap, project list table, filters/search, per-project detail panel, and responsive behavior for mobile/tablet/desktop.
  - Files to produce/modify: docs/assets/mockup-sketch.png (or docs/design-guide.md)
  - Responsible: Designer
  - Effort: M
- Step 1.2: Designer  Visual design tokens and accessibility spec
  - Objective: Provide palette (primary/secondary/neutral), font choices (web-safe), spacing scale, and contrast guidance (WCAG AA).
  - Files: docs/design-guide.md
  - Responsible: Designer
  - Effort: S
- Step 1.3: Coder  data schema & sample JSON
  - Objective: Design a simple, stable data schema for project entries and create a representative sample dataset.
  - Files to create: app/project-data.json
  - Responsible: Coder
  - Effort: S

Phase 2  Static skeleton & styles (Coder & Designer collaboration)
- Step 2.1: Coder  index.html skeleton & app structure
  - Objective: Create the base HTML with semantic structure and placeholders for components (cards, charts, table, filters). Include links to styles.css and placeholder script files (if any). Keep markup accessible (landmarks, aria labels).
  - Files to create: app/index.html, app/scripts.js (stub)
  - Responsible: Coder
  - Effort: M
- Step 2.2: Designer  provide CSS spec and asset handover
  - Objective: Deliver exact color tokens, spacing, and component states (hover/focus/active) to be implemented in CSS.
  - Files: docs/design-guide.md (update)
  - Responsible: Designer
  - Effort: S
- Step 2.3: Coder  styles implementation
  - Objective: Implement app/styles.css to match the design guide; include responsive breakpoints and accessible typography. Create utility classes (grid/flex) as needed.
  - Files to modify/create: app/styles.css
  - Responsible: Coder
  - Effort: M

Phase 3  Data binding and visuals
- Step 3.1: Coder  load JSON and render UI
  - Objective: Implement JS logic to fetch app/project-data.json, populate KPI cards, project list, and detail preview. Implement empty/error states.
  - Files: app/scripts.js (implement)
  - Responsible: Coder
  - Effort: M
- Step 3.2: Coder  add lightweight charts
  - Objective: Integrate a small CDN chart library (e.g., Chart.js or PicoCharts) to show at least one chart (project health over time, distribution by status). Use CDN script tags to avoid heavy dependency installs.
  - Files: app/index.html (script tags), app/scripts.js (chart initialization)
  - Responsible: Coder
  - Effort: M
- Step 3.3: Designer  review visuals & micro-interactions
  - Objective: Validate the charts and UI states, tweak styles if necessary.
  - Files: docs/design-guide.md (notes)
  - Responsible: Designer
  - Effort: S

Phase 4  Interactivity & UX polish
- Step 4.1: Coder  filters, search, and responsive behaviors
  - Objective: Implement client-side filtering, search, sorting, and responsive menu collapse behavior. Ensure keyboard accessibility.
  - Files: app/scripts.js, app/index.html, app/styles.css
  - Responsible: Coder
  - Effort: L
- Step 4.2: Designer  accessibility audit & final sign-off
  - Objective: Run quick accessibility/passive checks (color contrast, keyboard flow) and sign off or provide adjustments.
  - Files: docs/design-guide.md (audit notes)
  - Responsible: Designer
  - Effort: S

Phase 5  VS Code preview & runnable support
- Step 5.1: Coder  deterministic .vscode/launch.json
  - Objective: Add .vscode/launch.json that sets cwd to ${workspaceFolder}/app and opens index.html for preview. Ensure it's deterministic for Codespace preview (no reliance on system-specific paths).
  - Files to create/modify: .vscode/launch.json
  - Responsible: Coder
  - Effort: S
- Step 5.2: Coder  app-level README and run instructions
  - Objective: Add app/README.md with quick run steps (open index.html from the workspace, or Run/Debug preview). Include test checklist.
  - Files: app/README.md
  - Responsible: Coder
  - Effort: S

Phase 6  Validation, tests, wrap-up
- Step 6.1: Designer & Coder  integrated QA pass
  - Objective: Together run the validation checklist below, fix issues and edge cases, create small commits with clear messages.
  - Files: all app files
  - Responsible: Designer & Coder
  - Effort: M
- Step 6.2: Orchestrator  finalize and merge
  - Objective: Merge branch to main (or the exercise branch), close tasks, and document next steps.
  - Files: docs/ (update if necessary)
  - Responsible: Orchestrator
  - Effort: S

--------------------------------------------------------------------------------
3) File assignments (explicit)
--------------------------------------------------------------------------------

Required explicit file assignments:
- app/index.html  Responsible: Coder
- app/styles.css  Responsible: Coder
- app/project-data.json  Responsible: Coder
- .vscode/launch.json  Responsible: Coder

Other files to create and file owners:
- app/scripts.js  Coder (JS logic for data load & interactivity)
- app/README.md  Coder (run instructions & test checklist)
- docs/design-guide.md  Designer (colors, spacing, fonts, interaction spec)
- docs/assets/mockup-sketch.png (or .svg)  Designer (low-fidelity mockups)
- docs/accessibility-audit.md  Designer (short audit)
- (Optional) app/components/ (if splitting markup into partials)  Coder

Notes on file scope: Designer should only modify docs/ and provide design artifacts and guidance; Coder must not overwrite design docs. All changes should be committed in small, descriptive commits.

--------------------------------------------------------------------------------
4) Designer responsibilities (explicit checklist)
--------------------------------------------------------------------------------

Deliverables:
- Low-fidelity mockups (mobile/tablet/desktop) showing:
  - Header with title and user area
  - KPI summary cards (e.g., Total projects, On track, At risk, Overdue)
  - Project timeline/mini Gantt or progress sparkline
  - Project list (table or cards) with status badges
  - Project detail pane (on select)
  - Filter/search controls
- Design guide (docs/design-guide.md) with:
  - Color palette (HEX), primary/secondary/neutral, success/warning/error colors
  - Typography choices (font-family, sizes)
  - Spacing scale and grid (breakpoints: mobile  61600px, tablet 601 900px, desktop  901px)
  - Component states: hover/focus/disabled
  - Accessibility notes: contrast ratios, keyboard focus order, aria roles
- Accessibility audit notes (docs/accessibility-audit.md)  quick checks & required fixes

Validation criteria:
- Mockups align with available screen widths and show how UI reflows
- Colors meet WCAG AA for normal text and UI elements
- Components include clear focus states and accessible labels
- Provide explicit DOM or CSS selectors to be used for styling (helps Coder testing)

Designer acceptance tests:
- Provide screenshots or SVGs in docs/assets and a short checklist confirming each deliverable exists.
- Confirm at least one instance of each component state (hover/focus/error) in mockups or description.

--------------------------------------------------------------------------------
5) Coder responsibilities (explicit checklist)
--------------------------------------------------------------------------------

Deliverables:
- app/index.html  accessible markup with semantic elements and placeholders for components
- app/styles.css  matching the design guide, responsive and accessible
- app/scripts.js  fetch project-data.json, render cards, table, detail pane, chart initialization, and implement filters/search/sort
- app/project-data.json  representative sample dataset with at least 8 projects covering statuses (on-track, at-risk, delayed), date ranges, owners, and metrics used in KPIs
- .vscode/launch.json  deterministic file for preview: must set cwd to ${workspaceFolder}/app and open index.html
- app/README.md  run instructions and validation checklist

Runnable-app support (.vscode/launch.json requirements):
- cwd must be ${workspaceFolder}/app
- Launch or preview must open index.html (a simple HTML preview target)
- The configuration must be deterministic (no local absolute paths)

Validation & tests the Coder must pass:
- Index loads directly via the VS Code preview launch configuration and shows no console errors
- app/project-data.json loads (fetch) successfully and UI populates
- Charts render and reflect sample data
- Filters/search operate without page reload
- Empty-state and error-state handling (simulate missing or malformed JSON)
- Responsive breakpoints sanity-checked
- Keyboard navigation: tab through interactive elements in logical order
- No inline secrets; no external installations required (CDN usage acceptable)

Deliverable commit strategy:
- Multiple small commits (setup, HTML skeleton, CSS base, JSON data, JS rendering, charts, polish)
- Each commit message should be of the form: feat(app): add KPI cards skeleton or fix(app): improve responsive CSS

--------------------------------------------------------------------------------
6) Dependencies
--------------------------------------------------------------------------------

Step dependencies (high-level):
- Phase 1 Designer mockups (Step 1.1) should be available before final CSS styling (Step 2.3). However, Coder can create a minimal skeleton (Step 2.1) beforehand.
- app/project-data.json (Step 1.3) should exist before steps that bind data to UI (Steps 3.1, 3.2).
- .vscode/launch.json (Step 5.1) should be present before final runnable verification in Phase 6.
- Accessibility audit (Designer Step 4.2) should come after main interactions and responsive adjustments are implemented.

External dependencies / repo constraints:
- Internet access is required for CDN-hosted chart libraries (if chosen). If offline, opt for no external chart libs or include minimal local vendor files (requires additional commit).
- No package.json or build tools expected  keep solution static (HTML/CSS/JS) to keep simple for learning environment.
- Must follow repository rule: Designer only edits docs/*, Coder edits app/* and .vscode/*.

--------------------------------------------------------------------------------
7) Parallel work decisions
--------------------------------------------------------------------------------

Work that can run in parallel:
- Designer Step 1.1 & 1.2 (mockups and tokens) can run in parallel with Coder Step 1.3 (sample JSON) and Coder Step 2.1 (HTML skeleton). Rationale: Mockups guide final styling but skeleton and sample data can be created without final CSS.
- Designer can update design-guide while Coder iterates on styles; small sync cycles will prevent misalignment.
- Coder 99s implementation of chart initialization (Step 3.2) can run in parallel with filter/search implementation (Step 4.1) once the data schema is fixedthese touch different JS modules or functions.

Work that must be sequential:
- Final CSS polish (Step 2.3) should happen after Designer provides tokens (Step 1.2).
- Data-binding and chart rendering (Phase 3) must wait for project-data.json (Step 1.3).
- Accessibility audit (Step 4.2) must happen after interactivity & responsive behavior (Step 4.1) is implemented.

Coordination points:
- Agree on JSON schema quickly (Coder and Designer), commit app/project-data.json before heavy JS work.
- Use small commits and branch naming convention to avoid merge conflicts (e.g., feature/pulse-design, feature/pulse-code).

--------------------------------------------------------------------------------
8) Validation expectations (per phase)
--------------------------------------------------------------------------------

Phase 0  Preparation validation:
- Check: docs/agent-team.md exists and agents know their scopes.
- Manual check: Orchestrator confirms both agents read docs.

Phase 1  Layout & Data Design validation:
- Designer:
  - Mockups present for three breakpoints (mobile/tablet/desktop).
  - Checklist: header, KPI cards, timeline, project list, filters, detail pane.
  - Confirm colors and typography in docs/design-guide.md.
- Coder:
  - app/project-data.json exists and follows agreed schema; must contain >=8 projects with varied statuses.
- Test: Orchestrator or Coder opens JSON in editor and verifies structure matches UI needs.

Phase 2  Static skeleton & styles validation:
- Testable checks:
  - Open app/index.html (via file preview)  page loads and skeleton structure visible.
  - app/styles.css is linked and basic styles apply (header, card outlines).
  - HTML contains landmarks (header, main, nav, footer) and aria labels for interactive controls.
- Manual check: Designer verifies layout matches mockup.

Phase 3  Data binding and visuals validation:
- Tests:
  - On load, KPI cards display numbers derived from project-data.json (e.g., Total projects = count of elements).
  - Project list shows rows equal to JSON length (or filtered count).
  - Charts show without JS console errors and correspond roughly to sample data.
  - Error state: rename project-data.json temporarily and verify UI shows a friendly data-load error message.
- Acceptance: No uncaught exceptions in console; UI reflects JSON.

Phase 4  Interactivity & UX polish validation:
- Tests:
  - Search: typing filters the project list in real-time.
  - Filters: selecting "At risk" shows only matching items.
  - Keyboard navigation: tab order flows header 60 filters 60 first card 60 table 60 details
  - Responsive: resize preview to mobile width and verify layout collapses sensibly (cards stack, table becomes list or scrolls).
  - Accessibility: main text has contrast > AA (check with a simple ratio tool), focus states visible.
- Acceptance: All interactions work without page reload and pass the quick accessibility checklist.

Phase 5  VS Code preview & runnable support validation:
- Tests:
  - Use the .vscode/launch.json configuration: open VS Code Run/Debug and launch preview; it should open index.html and the preview should load.
  - Confirm the cwd used by launch.json is ${workspaceFolder}/app (inspect file).
- Acceptance: A person can open task and see index.html load via the configured preview.

Phase 6  Validation & wrap-up:
- Final QA checklist executed and all high-priority defects fixed.
- Commit history includes small descriptive commits.
- Orchestrator signs off and merges.

--------------------------------------------------------------------------------
9) Open questions / risks
--------------------------------------------------------------------------------

Open questions for Orchestrator or user:
1. Data features: Which project metrics must appear in KPIs? (examples: percent on time, completed tasks, burn rate). If not specified, plan to implement a minimal default: total count, on-track count, at-risk count, overdue count.
2. Charting library preference: Is using a CDN-hosted Chart.js acceptable? Or must zero external libs be used? If offline environment is required, we must vendor a minimal script locally.
3. Live updates: Will project-data.json be static for the exercise or will there be an API endpoint in future? If API is desired later, a small adapter pattern in scripts.js will be recommended.
4. Branding/logo: Is there a Mona or project logo to include? Designer should be given assets or permission to use placeholder.
5. Accessibility requirements: Must WCAG AA be strictly achieved for all pages, or is a lightweight audit sufficient for this exercise?
6. Browser support: What minimum browser versions to support? Default: modern Chromium-based and recent Firefox.
7. Performance constraints: dataset sizedo we need virtual scrolling or pagination? Default: small sample (3 50 projects) so no advanced virtualization needed.

Risks:
- CDN failures (charts not loading)  mitigated by graceful fallback (static text or sparkline SVG).
- Schema changes mid-development  mitigate by finalizing project-data.json schema as the first Coder step and locking it for other tasks.
- Merge conflicts between Designer and Coder if both edit docs/design-guide.md  coordinate by Designer owning design-guide.md and Coder only referring to it.
- Accessibility omissions discovered late  reduce risk by doing a quick audit early (Designer Step 4.2).

--------------------------------------------------------------------------------
Appendix: Minimal project-data.json schema suggestion (for alignment)
--------------------------------------------------------------------------------

(For discussion  Coder to implement after agreeing with Designer)
- Array of project objects with:
  - id (string)
  - name (string)
  - owner (string)
  - status (enum: on-track, at-risk, delayed)
  - startDate (ISO date)
  - endDate (ISO date)
  - percentComplete (number 0100)
  - healthScore (0100)
  - tags (array)
  - lastUpdate (ISO date)
- Include 8 varied sample entries to exercise all UI paths.

--------------------------------------------------------------------------------
Concluding notes
--------------------------------------------------------------------------------

- Keep commits small and descriptive. Use branches feature/pulse-design and feature/pulse-code.
- Ensure Designer and Coder coordinate on the JSON schema, CSS token names, and the set of interactive controls.
- The Orchestrator should collect Designer mockups and Coder commits for periodic review checkpoints after Phase 1, Phase 3, and Phase 6.

If you would like, I can:
- Generate a recommended sample project-data.json content to start the Coder quickly (no code changes  just a JSON sample to paste).
- Produce a short checklist template for commits and review PR descriptions.
