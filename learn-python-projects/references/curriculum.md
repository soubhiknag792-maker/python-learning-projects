# Adaptive Python Curriculum

Use this reference to place a learner, choose the next concept, and select a project increment. The phases are a dependency map, not a rigid calendar. Skip demonstrated knowledge and revisit weak concepts in later work.

## Placement

For a new learner, establish four facts before choosing a phase:

1. Whether a learner-controlled Python interpreter and editor are usable.
2. Prior programming and Python experience.
3. What the learner can explain about values, control flow, functions, and collections.
4. What the learner can produce in a short code-reading or code-writing task.

Do not turn placement into a long exam. Ask at most a few questions at once, use one short practical task, and let “I don't know” place the learner without penalty. An absolute beginner starts at Phase 0. A learner with experience enters at the earliest phase whose completion evidence they cannot yet demonstrate.

## Curriculum map

### Phase 0: Environment and programming model

- Concepts: interpreter versus source file, expressions and statements, syntax errors versus runtime errors, terminal basics, editor workflow, comments, and using `help()`.
- Build: hello program and an interactive unit converter.
- Evidence: run a file with the intended interpreter, change it, interpret a traceback location, and describe input-process-output.

### Phase 1: Values, decisions, and repetition

- Concepts: variables, naming, numeric and text types, Boolean logic, comparison and arithmetic operators, conversion, formatted strings, `if`/`elif`/`else`, `while`, `for`, `range`, `break`, and `continue`.
- Build: configurable quiz or number game with validation and scoring.
- Evidence: predict branches and loop iterations, choose an appropriate loop, and handle invalid user input without copying a finished solution.

### Phase 2: Functions and decomposition

- Concepts: definitions and calls, parameters, positional and keyword arguments, default values, return values, local/global scope, pure versus effectful functions, docstrings, basic recursion, and reading signatures.
- Build: refactor the quiz into tested functions, then create a small calculator or text utility.
- Evidence: split a requirement into cohesive functions, pass data explicitly, return useful values, and explain a simple call stack.

### Phase 3: Collections and data modelling

- Concepts: strings, lists, tuples, dictionaries, sets, mutability, copying/aliasing, slicing, unpacking, membership, comprehensions, sorting keys, nested data, and iteration patterns.
- Build: expense tracker with summaries, categories, search, and in-memory reports.
- Evidence: select a suitable collection, transform data clearly, avoid accidental mutation, and combine `enumerate`, `zip`, or comprehensions appropriately.

### Phase 4: Persistence, errors, and program structure

- Concepts: `pathlib`, text/binary distinctions, context managers, CSV/JSON, exceptions, validation, custom exceptions where useful, modules, imports, packages, `__name__`, and command-line arguments.
- Build: persistent contact manager and safe file organiser with dry-run mode.
- Evidence: preserve data across runs, recover from expected failures, keep I/O at boundaries, and organize code into importable modules.

### Phase 5: Objects and expressive models

- Concepts: classes and instances, attributes, methods, constructors, dataclasses, invariants, composition, limited inheritance, properties, class/static methods, protocols/abstract interfaces, equality, representation, and selected special methods.
- Build: library, inventory, or reservation domain model with persistence.
- Evidence: justify class versus function/data choices, keep invariants inside the model, prefer composition by default, and test object behavior.

### Phase 6: Quality and maintainability

- Concepts: tracebacks, debugger workflow, assertions, logging, type hints, documentation, unit tests, fixtures, boundaries, refactoring, style, dependency isolation, and basic profiling.
- Build: harden an earlier project with tests, structured logging, types, and a documented CLI.
- Evidence: reproduce a defect with a test, make the smallest correction, distinguish behavior from implementation detail, and explain a refactor.

Teach testing from early phases in small amounts; this phase makes it systematic rather than introducing it for the first time.

### Phase 7: Advanced core patterns

- Concepts: iterables, iterators, generators, lazy evaluation, decorators, closures, context managers, regular expressions, dates/time zones, enums, functional helpers, and safe resource handling.
- Build: streaming log analyser and reusable processing pipeline.
- Evidence: explain when laziness matters, write a generator, apply a decorator without hiding behavior, and handle resources deterministically.

### Phase 8: Data interfaces and automation

- Concepts: HTTP and API structure, offline fixtures, serialization, SQLite, transactions, subprocess boundaries, configuration, secrets hygiene, and repeatable automation.
- Build: API client that works against saved fixtures, followed by a SQLite task manager or personal data tool.
- Evidence: separate transport from parsing, parameterize SQL, handle partial failures, keep secrets out of source, and provide an offline test path.

### Phase 9: Concurrency foundations

- Concepts: concurrency versus parallelism, blocking work, threads, processes, futures, asynchronous functions, tasks, cancellation, timeouts, shared-state risks, and measurement before optimization.
- Build: bounded batch processor or status monitor using offline/local workloads.
- Evidence: choose a model based on the workload, bound concurrency, handle task errors and cancellation, and compare behavior with a sequential baseline.

### Phase 10: Capstone

Offer a choice of automation, data/CLI, API-backed, or small backend-oriented application. Require a written brief, milestones, persistence, validation, error handling, modular design, tests, user documentation, and a retrospective. Keep the first version small enough to finish, then add stretch goals.

## Built-in function coverage

Teach built-ins by problem and category; do not deliver a memorization dump. Record direct use or explanation in the mastery journal.

- Numeric and representation: `abs`, `round`, `pow`, `divmod`, `bin`, `oct`, `hex`, `chr`, `ord`, `format`, `repr`, and `ascii`.
- Constructors and core types: `bool`, `int`, `float`, `complex`, `str`, `bytes`, `bytearray`, `memoryview`, `list`, `tuple`, `dict`, `set`, `frozenset`, `range`, `slice`, and `object`.
- Aggregation and ordering: `len`, `sum`, `min`, `max`, `sorted`, `reversed`, `all`, and `any`.
- Iteration: `iter`, `next`, `enumerate`, `zip`, `map`, and `filter`. Prefer comprehensions when they are clearer; teach lazy behavior rather than declaring one style universally superior.
- Inspection and discovery: `type`, `isinstance`, `issubclass`, `callable`, `dir`, `help`, `id`, `hash`, `getattr`, `setattr`, `delattr`, `hasattr`, `vars`, `globals`, and `locals`.
- I/O and debugging: `print`, `input`, `open`, and `breakpoint`.
- Object model: `super`, `property`, `classmethod`, and `staticmethod`.
- Dynamic execution: explain `compile`, `eval`, `exec`, and `__import__` late, with their risks and uncommon direct-use cases. Never use untrusted input with dynamic execution.

Also teach common constants and exception families when they arise. “Covered” means the learner can decide when to use the feature and can verify unfamiliar behavior with documentation or a small experiment.

## Standard-library map

Select modules when a project needs them:

- Paths and system boundaries: `pathlib`, `os`, `sys`, `shutil`, `tempfile`, `subprocess`, `argparse`, and `venv`.
- Data and modelling: `json`, `csv`, `sqlite3`, `dataclasses`, `typing`, `enum`, `collections`, `copy`, and `pprint`.
- Algorithms and numbers: `math`, `statistics`, `decimal`, `fractions`, `random`, `secrets`, `itertools`, `functools`, and `operator`.
- Text and time: `re`, `string`, `textwrap`, `datetime`, `time`, and `zoneinfo`.
- Reliability: `logging`, `traceback`, `unittest`, `doctest`, `contextlib`, and `abc`.
- Networking and concurrency: `urllib`, `http`, `threading`, `multiprocessing`, `concurrent.futures`, `queue`, and `asyncio`.

Introduce third-party tools only after the corresponding standard concept: typically `pytest` for a more expressive test workflow, `requests` or `httpx` for HTTP ergonomics, and optionally `rich` for a polished CLI. Create a virtual environment and record direct dependencies before installing anything, and obtain authorization for installation or network access.

## Project selection rules

- Each 60–90 minute session should finish one visible, executable increment rather than an entire ambitious application.
- Reuse two or three older concepts in each new increment and make one concept the main learning target.
- Provide acceptance criteria that can be observed by running the program or tests.
- Default to offline, deterministic inputs. Use saved JSON responses before a live API and seeded/local data before external services.
- Scale difficulty by changing scaffolding, not by withholding requirements: beginners receive file/function shells and examples; experienced learners receive interfaces, tests, and constraints.
- If a learner repeatedly needs the same hint, schedule a smaller retrieval exercise before advancing.
