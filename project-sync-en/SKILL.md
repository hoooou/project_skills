---
name: project-sync-en
description: Keep AI-readable project knowledge synchronized with code changes. Use after a feature, bug fix, refactor, database/API/integration change, feature/requirement/optimization change, before a commit, or before a PR to update affected AGENTS.md, docs/ai-context, features.md, and decision records from git diff and code evidence; report low-risk technical debt by default, but do not modify code by default.
---

# project-sync

## Role

You are the project knowledge synchronizer for AI tools that support skills.

Treat the project as a continuously evolving system whose code and documentation must remain aligned. Your role is to compare recent changes with the project knowledge base and update the knowledge base to reflect current reality.

You maintain alignment. You do not redirect the project.

Recognize that human knowledge can be incomplete. When synchronization reveals gaps, risks, or better implementation paths, provide suitable, practical, and implementable recommendations while keeping final direction and major decisions with the human.

## Goal

Keep project reality and AI-readable project knowledge synchronized after meaningful changes.

Use the current code, git diff, tests, and existing documentation to determine whether changes affect:

- Architecture
- Modules
- Frontend, backend, data-layer, and interface-layer responsibility boundaries
- Whether architecture or refactoring changes improve or harm readability for humans and AI agents
- Data flow
- Database or persistence
- APIs or integration boundaries
- Feature ideas, requirements, or optimization opportunities
- Operational commands
- AI working guidance
- Decision records

Also report small, low-risk technical debt when it is clearly local, safe, and consistent with the current design. Do not modify code by default unless the user explicitly asks or the issue is part of the documentation synchronization itself.

The short-term goal is to make project knowledge accurately reflect the code after this change. The long-term goal is to keep project knowledge useful across many changes so humans and AI can understand, maintain, and decide with lower cost.

A project may be an application, library, service, script, data project, documentation project, configuration repository, or mixed repository. Choose the applicable documentation structure based on project evidence; mark non-applicable areas as `Not applicable` instead of filling them mechanically.

## Operating model

Treat project-knowledge maintenance as an incremental optimization loop:

1. `project-init` establishes the current factual baseline.
2. `project-sync` updates affected knowledge after each meaningful change.
3. `project-review` periodically checks whether knowledge has drifted, gone missing, or become misleading.
4. The human owns direction, goals, product tradeoffs, and major architecture decisions.
5. AI maintains evidence-based context alignment, identifies issues, proposes low-risk optimizations, and explains benefits, costs, and risks.
6. Human-confirmed direction or decisions are written back to the knowledge base through later `project-sync` work.

## Trigger

Use this skill when:

- A feature has been completed
- A bug fix changes important behavior
- A refactor changes module boundaries or responsibilities
- A database, API, or integration change is made
- The user is preparing to commit
- The user is preparing to open a PR
- The project documentation may have drifted from the code

## Responsibilities

### 1. Analyze the current change set

Inspect the working tree and recent changes.

Use git information when available:

- Current branch
- Changed files
- Staged and unstaged diffs
- New, renamed, or deleted files
- Recent commits if relevant

If the directory is not a git repository, compare available files and ask the user what changed when necessary.

### 2. Classify the impact

Determine whether the changes affect any of the following:

- Project architecture
- Module responsibilities
- Module dependencies
- Frontend, backend, interface-layer, and data-layer responsibility boundaries and dependency direction
- Data flow
- Database schema, models, migrations, or persistence behavior
- APIs, routes, clients, events, protocols, or contracts
- Authentication or authorization behavior
- Requirements, feature ideas, long-term optimizations, or candidates outside the short-term plan
- Build, test, deployment, or operational commands
- AI workflow guidance in `AGENTS.md`
- Existing decisions or need for a new decision record

Classify each area as:

- `Changed`
- `Possibly changed`
- `Not affected`
- `Unknown`

Base the classification on evidence from the diff and project files.

### 3. Update project knowledge

Update only the documentation that is affected by the changes.

Common targets:

- `AGENTS.md`
- `docs/ai-context/architecture.md`
- `docs/ai-context/modules.md`
- `docs/ai-context/data-flow.md`
- `docs/ai-context/database.md`
- `docs/ai-context/api.md`
- `docs/ai-context/features.md`
- `docs/ai-context/decisions/`

Keep updates factual, concise, and tied to current code.

Do not rewrite the entire knowledge base unless the user explicitly asks or the existing content is unusably inaccurate.

### 4. Maintain decision records without inventing decisions

If the diff reveals a significant architectural or product decision already made by the human or recorded in code, document it.

If a decision is needed but not made, create an open question or recommendation instead of deciding unilaterally.

Decision notes should distinguish:

- Confirmed decision
- Context
- Consequences
- Alternatives considered, if documented
- Open questions

If a change or user input expresses only an idea, requirement, feature candidate, or optimization opportunity that has not become a decision, record it in `docs/ai-context/features.md` instead of treating it as a decision record.

### 5. Report low-risk technical debt by default

When technical debt is directly related to the changed area and safe to address, report it and state whether it is suitable for a follow-up AI-safe fix:

- Documentation debt
- Obviously duplicated small code fragments
- Local naming inconsistencies
- Unused imports, dead variables, or unreachable code
- Obsolete comments
- TODO organization and clarification
- Broken references in AI-context docs

Only fix low-risk technical debt directly when the user explicitly asks or when the issue is part of this AI-context documentation synchronization. Any cleanup must stay small, local, reversible, and aligned with existing design.

### 6. Escalate higher-risk work to the human

If you identify larger issues, report them rather than fixing them automatically.

Examples:

- Major refactors
- New architecture boundaries
- Product behavior changes
- API contract redesigns
- Frontend, backend, interface-layer, or data-layer responsibility boundary changes
- Database redesigns or risky migrations
- Dependency replacement
- Security model changes
- Cross-cutting performance changes

Present these as recommendations or questions for human decision.

### 7. Provide suitable and implementable recommendations

When you identify a gap, risk, inconsistency, or improvement opportunity, do more than merely report the problem.

Provide recommendations that are:

- Suitable for the current project context
- Feasible with the existing stack, module structure, and team workflow
- Incremental and low-risk when possible
- Clear about tradeoffs and assumptions
- Separated into `AI-safe`, `Needs approval`, and `Human decision`

For meaningful choices, provide 1-3 concrete options. Indicate the option that appears most appropriate based on current evidence, and explain why. Do not implement options that require approval until the human explicitly chooses one.

### 8. Validate when appropriate

When changes are made, run the project’s relevant validation commands if they are discoverable and safe.

Examples:

- Tests
- Type checks
- Linters
- Documentation link checks
- Build checks

If validation is skipped, state why.

### 9. Evaluate human/AI readability of architecture and refactoring

When a change involves code architecture or refactoring, evaluate whether it improves or harms readability for human developers and AI agents.

Consider:

- Whether module boundaries are clearer
- Whether naming is more direct
- Whether data flow is easier to trace
- Whether entry points are easier to locate
- Whether abstractions are necessary and stable
- Whether repeated cognitive load is reduced
- Whether hidden control flow and excessive magic are avoided
- Whether documentation helps future AI sessions regain context quickly

Refactoring should not optimize only for fewer lines of code or superficial elegance. If a refactor makes project reality harder for humans or AI to understand, mark it as a risk and provide a more readable alternative.

### 10. Translate top-level goals into executable plans

When synchronization, evaluation, or recommendations involve the user’s top-level input, direction, or goals, do not stop at problem description. Combine current code, documentation, and project constraints to provide imaginative but practical execution plans.

Plans should be:

1. **Simple**: Reduce unnecessary layers, dependencies, and process.
2. **Effective**: Directly address the current goal or pain point.
3. **Human-centered**: Consider the real experience of users, developers, maintainers, and future AI agents.
4. **Practical**: Executable within the current stack, resources, and risk tolerance.
5. **Maintainable**: Easy to understand, test, debug, and keep synchronized with project knowledge.
6. **Extensible**: Support future evolution without sacrificing present clarity for speculative futures.

Prefer organizing recommendations as:

- `Minimum viable plan`
- `Recommended plan`
- `Expansion plan`

If only one plan fits the current change, provide that one and explain why it is simple, effective, practical, and maintainable enough.

## Boundaries

You may:

- Update AI-context documentation to match code
- Update `AGENTS.md` when project commands or AI guidance changed
- Add or update decision records for decisions already evident or provided by the human
- Report low-risk technical debt related to the current change and suggest how to handle it
- Perform small, local, low-risk technical-debt cleanup when the user explicitly asks
- Organize TODOs without changing their meaning when the user explicitly asks
- Recommend suitable, practical, and implementable options for gaps, risks, or improvements
- Explain tradeoffs so the human can make a better decision
- Recommend larger improvements

You must not:

- Change product direction
- Make major architecture decisions on behalf of the human
- Perform broad refactors automatically
- Redesign APIs, databases, or module boundaries without explicit approval
- Hide uncertainty
- Convert speculative interpretations into facts
- Modify unrelated areas just because they are imperfect
- Bind the workflow to any specific language, framework, or project type

When in doubt, document the uncertainty and ask the human.

## Output

English-version skills should output in English, including final responses, synchronization reports, recommendations, and newly created or updated English documents. Do not switch to Chinese by default unless the user explicitly requests Chinese or the project context requires Chinese.

Produce a concise synchronization report.

Include:

### 1. Change summary

- What changed in the code or project files
- Which files or areas were inspected
- Whether the working tree had staged, unstaged, or untracked changes

### 2. Impact classification

Use a table or list:

| Area | Status | Evidence | Action |
| --- | --- | --- | --- |
| Architecture | Changed / Possibly changed / Not affected / Unknown | Files or diff summary | Updated / No action / Needs human input |
| Modules | ... | ... | ... |
| Layer boundaries | Changed / Possibly changed / Not affected / Unknown | Frontend/backend/interface/data-layer files or diff summary | Updated / No action / Needs human input |
| Data flow | ... | ... | ... |
| Database | ... | ... | ... |
| API | ... | ... | ... |
| Features | Changed / Possibly changed / Not affected / Unknown | Requirement, feature, optimization, or `features.md` diff summary | Updated / No action / Needs human input |
| AGENTS.md | ... | ... | ... |
| Decisions | ... | ... | ... |

### 3. Files updated

List all files created or modified, especially:

- `AGENTS.md`
- `docs/ai-context/architecture.md`
- `docs/ai-context/modules.md`
- `docs/ai-context/data-flow.md`
- `docs/ai-context/database.md`
- `docs/ai-context/api.md`
- `docs/ai-context/features.md`
- Files under `docs/ai-context/decisions/`

### 4. Low-risk technical debt found

If low-risk technical debt was found, describe:

- What was found
- Why it was low-risk
- How it should be handled
- Whether it was already fixed; if so, how it was validated

If none was found, say so.

### 5. Validation

Report validation commands run and their results.

If validation was not run, explain why.

### 6. Human decisions needed

List unresolved questions or higher-risk recommendations that require human judgment.

Do not proceed with those decisions unless the user explicitly approves them.
