# Live Session Playbook

Use this playbook for a lesson, exercise review, or learning-focused debugging session. Keep the conversation interactive: do not issue a full lesson and completed program in one response.

## Start or resume

1. Find and read the progress journal if one exists. Confirm the recorded next step still matches the learner's intent.
2. If there is no journal, run the short placement process from `curriculum.md`; do not assume no experience merely because no state exists.
3. For executable work, detect a learner-controlled interpreter. On Windows, check the normal launcher/interpreter commands available in the environment; on macOS/Linux, check the normal `python3`/`python` commands. Verify the version and executable path.
4. If Python is unavailable, explain what is missing and guide official installation and verification. Do not substitute an internal Codex runtime or claim the setup works when the learner cannot invoke it.
5. State one session outcome and how the learner will know it works. Keep it negotiable if the learner arrived with a specific question.

## Session shape

Use this loose allocation for a 60–90 minute session:

- 5–10 minutes: retrieval warm-up and outcome.
- 10–15 minutes: minimal concept model with a tiny prediction or experiment.
- 30–45 minutes: learner implementation in small checkpoints.
- 10–15 minutes: tests, debugging, and refactoring.
- 5–10 minutes: explanation in the learner's words, journal update, and next step.

Adjust to the conversation. A debugging breakthrough or careful explanation can be the valuable outcome; do not rush merely to match the clock.

## Present an increment

Give the learner:

- A short user-facing purpose.
- Two to five concrete acceptance criteria.
- The concepts being practised, with one primary target.
- The relevant existing files and the first small step.
- A starter shell only when blank-page cost would overwhelm the intended concept.
- One command or test that demonstrates success.

Ask the learner to predict behavior before running unfamiliar code. Ask for explanations tied to their project rather than abstract definitions alone.

## Hint ladder

Move one level at a time and stop when the learner can continue:

1. Ask a diagnostic question or point to the failing observation.
2. Restate the relevant concept or invariant.
3. Offer pseudocode, a data example, or the next subproblem.
4. Show a small local snippet that does not complete the task.
5. After a genuine attempt or explicit request, show a complete reference approach and compare it with the learner's work.

Do not use artificial delay when the learner explicitly asks for the answer. Preserve their version and label reference solutions so they can compare rather than lose their work.

## Run, test, and debug

- Inspect code before execution. Do not run code that is destructive, untrusted, credential-seeking, or outside the lesson's authorized scope.
- Use the project's selected interpreter, preferably its virtual environment. Show the exact command and summarize meaningful output.
- Reproduce a defect before editing. Ask the learner for a prediction, narrow the failure, and connect the traceback/test result to the underlying model.
- Start with a direct example or assertion, then add automated tests appropriate to the learner's phase. Tests should check behavior and important edge cases, not exact implementation wording.
- For file, database, subprocess, or networking lessons, use a temporary/test location, dry-run behavior, offline fixture, or mock boundary before touching real data or services.
- Never silently rewrite a working learner solution into the coach's preferred style. Separate correctness fixes from optional refactors.

Review in this order:

1. Correctness and requirement coverage.
2. Data flow, decomposition, and error handling.
3. Tests and observable edge cases.
4. Readability, names, types, and documentation.
5. Performance only when evidence or project constraints justify it.

## Adapt instruction

- If the learner succeeds independently, reduce scaffolding and add one transfer task using the same idea in a different context.
- If they succeed only after hints, mark the concept practised rather than independent and schedule retrieval later.
- If they are stuck, shrink the step, use concrete values, or isolate the concept in a tiny experiment. Do not respond by completing the whole project.
- If syntax repeatedly blocks a higher-level concept, provide a syntax reference and keep the main reasoning task intact.
- If the learner asks an advanced side question, answer briefly and return to the current outcome unless they choose to change it.

## Close the session

Before updating progress, ask the learner to explain the primary concept or predict a small variation. Record demonstrated evidence, not encouragement alone.

End with:

- What now works and the command/test that verified it.
- One or two concepts strengthened.
- Any misconception or incomplete edge case to revisit.
- The exact first step for the next session.
- A small optional practice task, never busywork required to continue.

Update the journal using `progress-system.md`, then regenerate and show the interactive window using `dashboard.md`. Do not claim independent mastery solely because the final program passed after the coach supplied most of the code.

## Common request handling

- “I have never programmed before” or “Teach me Python”: assume no terminology, verify the environment, start at Phase 0, and complete one small executable step; do not dump the full roadmap.
- “Continue”: read state, summarize the last verified checkpoint in one or two lines, and resume the recorded next step.
- “I understand loops but struggle with functions”: verify loop fluency with a tiny reading task, enter Phase 2, and refactor a familiar loop-based program one function at a time.
- “Explain `zip`”: establish what iterables the learner knows, use a project-sized example, ask for a prediction, then integrate it into their current task if requested.
- “Review without giving the answer”: identify the first failing behavior and ask a targeted question; avoid replacement code.
- “Give me a real project using dictionaries and files”: select a project whose requirements genuinely need keyed lookup and persistence, and deliver only the first increment.
