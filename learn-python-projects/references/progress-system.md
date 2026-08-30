# Learner Progress System

Use a readable Markdown journal as the source of continuity. The journal supports teaching; it is not a grading transcript.

## Location and discovery

- Never place learner state inside the installed skill directory.
- In the current writable workspace, look for `python-learning-workspace/progress.md` before creating anything.
- If exactly one journal exists, resume it. If several plausible journals exist, ask which one to use. If none exists and the user wants to start a learning session, create `python-learning-workspace/` in the agreed workspace.
- Keep the generated interactive window at `python-learning-workspace/dashboard.html`. It mirrors the journal but never replaces it.
- Keep projects under `python-learning-workspace/projects/<number>-<short-name>/` with stable, zero-padded numbers such as `01-unit-converter`.
- Use one workspace-level `.venv` by default. A project may get its own environment only when dependency conflicts or isolation goals justify it.
- Do not modify or delete unrelated files. Do not add generated caches, environments, secrets, or local databases to version control.

## Journal format

Create `progress.md` with these sections and keep them concise:

```markdown
# Python Learning Progress

## Learner profile
- Started: YYYY-MM-DD
- Goal: Broad Python foundation
- Typical session: 60–90 minutes
- Platform: ...
- Interpreter: command, version, and resolved path; or "not installed"
- Current phase: ...

## Current project
- Project: number and name
- Purpose: ...
- Status: planned | active | paused | complete
- Last verified command: ...
- Last verified result: ...
- Next step: one concrete action

## Mastery
| Concept | State | Evidence | Last practised |
|---|---|---|---|
| ... | introduced/practised/independent/revisit | observable work | YYYY-MM-DD |

## Session log
### YYYY-MM-DD — short outcome
- Built or changed: ...
- Verification: ...
- Learner explanation: ...
- Hints needed: none or levels used
- Revisit: ...
- Next session: ...

## Project history
| Project | Concepts | Status | Verification |
|---|---|---|---|

## Recurring patterns
- Strengths: ...
- Misconceptions or habits to revisit: ...
```

Use only information relevant to instruction. Do not record sensitive personal data, credentials, unrelated conversation, or negative personality judgments.

## Mastery states

- `introduced`: the learner has seen and discussed the concept.
- `practised`: the learner used it with meaningful prompting or correction.
- `independent`: the learner selected, implemented, and explained it with little or no prompting, ideally in more than one context.
- `revisit`: current evidence shows a misconception, fragile recall, or repeated need for the same hint.

Move states based on evidence. Passing code may still be `practised` when the coach provided the design. A failed attempt can still demonstrate strong reasoning and should record the specific gap rather than reset unrelated mastery.

## Update rules

- Read the journal before proposing the next lesson.
- Append one session entry rather than rewriting history. Correct factual mistakes explicitly if necessary.
- Keep `Current project`, `Current phase`, and `Next step` synchronized with the newest session entry.
- Record the exact verification command and a short result. Do not claim a test passed if it was not run.
- Record which hint level was needed only to tune scaffolding, not to score the learner.
- Mark a project complete only when its agreed acceptance criteria pass or the learner intentionally closes a reduced scope.
- When an environment or authorization issue blocks execution, record the blocker and the next verification step without claiming lesson completion.
- After a meaningful journal update, regenerate `dashboard.html` from the same facts using `dashboard.md`. If dashboard generation fails, preserve the valid journal and report the dashboard as stale rather than changing learning state to match it.

## Project folder baseline

Choose only files the project needs. A typical project can contain:

```text
projects/03-expense-tracker/
|-- project.md        Brief, acceptance criteria, and milestones
|-- src/              Program modules when multiple files are justified
|-- tests/            Automated behavior checks
|-- fixtures/         Small offline data samples when needed
`-- requirements.txt Direct third-party dependencies, only when introduced
```

A one-file beginner exercise does not need this full structure. Avoid ceremony that distracts from the concept.

## Resume algorithm

1. Read the learner profile, current project, newest session entry, and all `revisit` rows.
2. Confirm the interpreter still works if the environment may have changed.
3. Re-run or inspect the last verified checkpoint when practical.
4. Start with a two- to five-minute retrieval prompt for one relevant concept.
5. Continue the recorded next step, incorporating at most one revisit target unless the learner chooses a review session.
6. If files disagree with the journal, treat executable files and test results as current reality and update the journal after explaining the discrepancy.
7. Refresh and open `dashboard.html` after the journal is current.
