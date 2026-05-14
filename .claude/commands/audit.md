Your goal is to report on vulnerable dependencies — **without** modifying them.

**Important:** Do NOT run `npm audit fix`, `npm update`, or otherwise mutate `package.json` / `package-lock.json`. CLAUDE.md pins these deps deliberately — `audit fix` is known to break the app. Report findings only; let the user decide what to upgrade.

Do the following:

1. Run `npm audit --json` and parse the output.
2. Summarize vulnerabilities grouped by severity (critical → high → moderate → low). For each: package name, installed version, vulnerable range, advisory title, and whether the package is a direct dependency in `package.json` or transitive.
3. For critical/high direct dependencies, look at the relevant import sites with Grep (e.g. for `bcrypt`, search `from "bcrypt"`) and note whether the vulnerable code path is actually reachable in this project. Be concise — one line per finding.
4. Output a prioritized list of recommended manual upgrades (package + suggested version), but stop there. Do not edit any files.