# Interactive Learning Dashboard

Generate a self-contained browser window at `python-learning-workspace/dashboard.html` from the learner's current journal. Use `../assets/dashboard-template.html` as the base. The dashboard is a friendly view of verified learning state; `progress.md` remains authoritative.

## When to generate

- Create the dashboard when the learning workspace is first initialized, even if Python is not installed yet.
- Refresh it after a session closes, a project status changes, mastery evidence changes, or the recorded next step changes.
- Do not rewrite it for a narrow explanation that does not alter the journal.
- If an existing dashboard contains learner-authored visual customization, preserve it when practical or confirm before replacing it.

## Output contract

Copy the template to the learning workspace and replace the entire contents of the `learning-data` JSON script element with current serialized data matching this shape:

```json
{
  "generatedAt": "2026-08-30T19:30:00+05:30",
  "learner": {
    "goal": "Broad Python foundation",
    "phase": "Phase 2 · Functions and decomposition",
    "interpreter": "Python 3.12.5 · .venv\\Scripts\\python.exe"
  },
  "current": {
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
      "name": "02 · Quiz refactor",
      "status": "active",
      "concepts": ["functions", "testing"],
      "verification": "8 tests passed",
      "path": "projects/02-quiz-refactor/"
    }
  ],
  "sessions": [
    {
      "date": "2026-08-30",
      "outcome": "Added validation and a scoring loop.",
      "verification": "8 tests passed",
      "next": "Extract score_answer()."
    }
  ]
}
```

Use the curriculum reference to include all relevant phases, marking each `locked`, `available`, `current`, or `complete`. Use only journal-supported facts for mastery, projects, sessions, commands, and results. Empty arrays and empty strings are valid and must render as useful empty states.

Serialize data as JSON rather than interpolating it into markup or JavaScript. Escape `<`, `>`, `&`, U+2028, and U+2029 in JSON string values so learner text cannot terminate the script element. The template renders data with `textContent`; do not replace that with `innerHTML` for learner-controlled values.

## Interaction and design requirements

The generated page must remain a single portable HTML file and work from `file://` without a server. Preserve these template behaviors:

- Overview, Curriculum, Projects, and Sessions tabs with keyboard navigation.
- Overall curriculum progress and mastery counts.
- A mastery-state filter.
- Expandable curriculum phase cards.
- A copy-next-step action with a local-file-safe fallback.
- Light/dark theme choice stored only in browser `localStorage`.
- Responsive layout, visible focus states, semantic landmarks, reduced-motion support, and useful empty states.

Do not add analytics, remote fonts, CDNs, network requests, credentials, executable learner code, or third-party scripts. UI preferences in `localStorage` are allowed; progress changes are not. The page must never claim that clicking a control updates `progress.md`.

## Show and verify

After generation:

1. Confirm the file exists outside the skill directory.
2. Parse the embedded JSON and check that required top-level keys exist.
3. Check the inline JavaScript for syntax errors when a JavaScript runtime is available.
4. Open the local file in the available browser or HTML preview. If opening is unavailable, provide a clickable file link.
5. Verify tab switching, keyboard focus, theme toggle, mastery filter, phase expansion, and copy-next-step behavior.
6. Confirm there are no required network requests or console errors.

If visual or interaction verification fails, keep the journal untouched, correct only the generated dashboard, and rerun the checks.
