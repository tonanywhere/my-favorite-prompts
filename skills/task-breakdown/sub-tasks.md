# Sub-Task Rules

A sub-task says **what** must be true when it is done, and where. **How** to make it true is the implementer's decision.

Each sub-task has:

- **Kind and outcome**: `Implementation`, `Test`, `Docs`, or the final `Verification`, followed by one sentence of observable outcome.
- **Where**: the files it touches, by path.
- **For an implementation**: any public name, signature, config key, or wire value another task or the outside world relies on, exactly as written in Interfaces. Nothing private. Its unit tests are part of it: list the test file, test names, and what each asserts, as input → expected result. Whether to write them first is the implementer's choice.
- **For a `Test` sub-task**: every test that is not a unit test (integration, end-to-end, smoke, live, mutation) gets its own `Test` sub-task, including manual ones. Name the file or procedure, the scenarios, and the observable result of each. The Verification sub-task runs it.

The last sub-task is always **Verification**, with every `_Verify:_ [command] → [expected output]` line for the task. No other sub-task carries a `_Verify:_` line.

**External data** sub-tasks also name the source URL, the file format, the field names, the expected volume, and any format quirks. For example: "download `t_kjv.csv` from [URL]; columns `b` (book), `c` (chapter), `v` (verse), `t` (text); join with `key_english.csv` for book names; about 31,102 rows."

**Blocked** sub-tasks depend on information nobody has yet. Mark them `⚠️ BLOCKED: <what must be known first>`.

A sub-task that contains code, a private function or variable name, a line-level edit, or a step-by-step recipe has crossed into implementation: cut it back to the outcome and the files.
