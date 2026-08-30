# Interactive Learning Dashboard

Generate a self-contained browser window at `python-learning-workspace/dashboard.html` from the learner's current journal. Use `../assets/dashboard-template.html` as the base. The dashboard combines a view of verified journal state with an explicitly local working copy for placement choices, checklists, scratch notes, and session drafts; `progress.md` remains authoritative.

## When to generate

- Create the dashboard when the learning workspace is first initialized, even if Python is not installed yet.
- Refresh it after a session closes, a project status changes, mastery evidence changes, or the recorded next step changes.
- Do not rewrite it for a narrow explanation that does not alter the journal.
- If an existing dashboard contains learner-authored visual customization, preserve it when practical or confirm before replacing it.

## Output contract

Copy the template to the learning workspace and replace the entire contents of the `learning-data` JSON script element with current serialized data matching this shape:

```json
{
  "version": 1,
  "generatedAt": "2026-08-30T19:30:00+05:30",
  "savedAt": "",
  "learner": {
    "goal": "Broad Python foundation",
    "phase": "Phase 2 · Functions and decomposition",
    "interpreter": "Python 3.12.5 · .venv\\Scripts\\python.exe",
    "experience": "beginner",
    "sessionLength": "60–90 minutes",
    "onboardingComplete": true
  },
  "current": {
    "projectId": "quiz",
    "project": "02 · Quiz refactor",
    "purpose": "Split a working quiz into focused functions.",
    "status": "active",
    "nextStep": "Extract score_answer() and run the current tests.",
    "lastCommand": "python -m unittest",
    "lastResult": "8 tests passed"
  },
  "mastery": [
    {
      "concept": "for loops",
      "state": "independent",
      "evidence": "Implemented quiz iteration without prompting.",
      "lastPractised": "2026-08-30"
    }
  ],
  "phases": [
    {
      "number": 2,
      "title": "Functions and decomposition",
      "status": "current",
      "topics": ["parameters", "return values", "scope"]
    }
  ],
  "projects": [
    {
      "id": "quiz",
      "phase": 1,
      "name": "02 · Quiz refactor",
      "status": "active",
      "concepts": ["functions", "testing"],
      "verification": "8 tests passed",
      "path": "projects/02-quiz-refactor/",
      "tasks": ["Extract score_answer()", "Run the current tests"],
      "completedTasks": ["Extract score_answer()"]
    }
  ],
  "sessions": [
    {
      "date": "2026-08-30",
      "outcome": "Added validation and a scoring loop.",
      "verification": "8 tests passed",
      "next": "Extract score_answer()."
    }
  ],
  "scratchpad": ""
}
```

Use the curriculum reference to include all relevant phases, marking each `locked`, `available`, `current`, or `complete`. Use only journal-supported facts for mastery, projects, sessions, commands, and results. Empty arrays and empty strings are valid and must render as useful empty states.

Serialize data as JSON rather than interpolating it into markup or JavaScript. Escape `<`, `>`, `&`, U+2028, and U+2029 in JSON string values so learner text cannot terminate the script element. The template renders data with `textContent`; do not replace that with `innerHTML` for learner-controlled values.

## Interaction and design requirements

The generated page must remain a single portable HTML file and work from `file://` without a server. Preserve these template behaviors:

- Overview, Practice, Curriculum, Projects, and Sessions tabs with keyboard navigation.
- Overall curriculum progress and mastery counts.
- A mastery-state filter.
- Expandable curriculum phase cards.
- A copy-next-step action with a local-file-safe fallback.
- An adaptive placement form, project task checklists, a local scratchpad, and session-note capture.
- Versioned browser `localStorage` autosave plus JSON import, export, and confirmed reset.
- Light/dark theme choice stored in browser `localStorage`.
- Responsive layout, visible focus states, semantic landmarks, reduced-motion support, and useful empty states.

Do not add analytics, remote fonts, CDNs, network requests, credentials, executable learner code, or third-party scripts. The page must never claim that clicking a control updates `progress.md` or verifies Python behavior.

The browser may store a non-authoritative working copy of checklist state, scratch notes, setup choices, and session drafts. Label these changes as local, keep verified mastery separate, and require coach review plus real command/test evidence before copying them into `progress.md`. A generated dashboard may merge exported browser JSON only after reviewing it against the learner's files and journal.

## Show and verify

After generation:

1. Confirm the file exists outside the skill directory.
2. Parse the embedded JSON and check that required top-level keys exist.
3. Check the inline JavaScript for syntax errors when a JavaScript runtime is available.
4. Open the local file in the available browser or HTML preview. If opening is unavailable, provide a clickable file link.
5. Verify tab switching, keyboard focus, theme toggle, placement, task persistence, scratchpad persistence, session capture, mastery filter, phase expansion, copy actions, JSON export/import, and confirmed reset.
6. Confirm there are no required network requests or console errors.

If visual or interaction verification fails, keep the journal untouched, correct only the generated dashboard, and rerun the checks.
