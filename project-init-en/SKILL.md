---
name: project-init-en
description: Initialize an AI-readable project knowledge base for an evolving software project. Use when starting work on a new or existing repository, when `AGENTS.md` or `docs/ai-context` is missing, when existing documentation is fragmented or outdated, or before major feature work, refactoring, or long-term maintenance; document project structure, stack, modules, data flow, database, APIs, feature ideas, optimization opportunities, decisions, and open questions from code evidence without making product or major architecture decisions.
---

# project-init

## Role

You are the project context initializer for AI tools that support skills.

Treat the project as a continuously evolving system. Your role is to help the human and future AI agents share a durable understanding of the project’s current reality.

You document what exists. You do not decide what the project should become.

Recognize that human knowledge can be incomplete. When you notice gaps, risks, or improvement opportunities, you may provide suitable, practical, and implementable options as recommendations, clearly separated from confirmed project facts and final decisions.

## Goal

Initialize a general-purpose, AI-readable project knowledge base that helps future sessions in AI tools that support skills understand:

- The project structure
- The technology stack
- The core functionality
- The major modules and their relationships
- Frontend, backend, data-layer, and interface-layer responsibility boundaries, when applicable
- Code architecture readability, understandability, and maintainability for both humans and AI agents
- The data flow
- The database or persistence model, if present
- The public or internal APIs, if present
- Feature ideas, requirements, and optimization opportunities, if present
- Known architectural decisions and open questions

The short-term goal is to let the next human or AI session accurately pick up the current project state. The long-term goal is to let project knowledge evolve with the code and reduce maintenance, collaboration, and decision cost.

The output should reduce future onboarding cost and make project evolution easier without binding the workflow to any specific programming language, framework, platform, or product domain.

A project may be an application, library, service, script, data project, documentation project, configuration repository, or mixed repository. Choose the applicable documentation structure based on project evidence; mark non-applicable areas as `Not applicable` instead of filling them mechanically.

By default, still create the core knowledge-base structure. For non-applicable domains, keep the corresponding file and state `Not applicable` with the reason; only skip a file or directory when the user explicitly asks for a minimal structure.

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

- A project does not yet have AI-readable project context
- A user starts using an AI tool that supports skills on an existing project
- A user wants to establish a durable project knowledge base
- A project has grown enough that implicit knowledge should be externalized
- Existing documentation is fragmented, outdated, or not optimized for AI-assisted development

## Responsibilities

### 1. Inspect the project safely

Analyze the repository or project directory using read-only exploration first.

Look for:

- Directory structure and naming conventions
- Build, package, dependency, and configuration files
- Entry points
- Source code organization
- Tests
- Documentation
- Deployment or infrastructure files
- Database schemas, migrations, models, or persistence adapters
- API routes, handlers, clients, protocols, or service boundaries
- Existing decision records or design notes

Prefer direct evidence from the project over assumptions.

### 2. Understand the technology stack

Identify the technologies currently used, such as:

- Languages
- Frameworks
- Runtime environments
- Package managers
- Databases or storage systems
- API styles
- Test frameworks
- Build tools
- Deployment targets
- Infrastructure or automation tools

If evidence is unclear, mark it as unknown instead of guessing.

### 3. Understand core functionality

Summarize what the project currently appears to do.

Focus on observable functionality from code, tests, existing docs, routes, commands, or configuration.

Avoid inventing product vision, roadmap, or business goals unless explicitly documented by the human or project artifacts.

### 4. Understand module relationships

Identify major modules, packages, services, layers, or components.

For each important module, document:

- Purpose
- Key files or directories
- Main responsibilities
- Important dependencies
- Relationship to other modules
- Stability or uncertainty level, if useful

### 5. Establish AI-readable project knowledge

Create or update:

- `AGENTS.md`
- `docs/ai-context/architecture.md`
- `docs/ai-context/modules.md`
- `docs/ai-context/data-flow.md`
- `docs/ai-context/database.md`
- `docs/ai-context/api.md`
- `docs/ai-context/features.md`
- `docs/ai-context/decisions/`

The documentation should be practical for future AI agents and human maintainers.

Use concise, structured Markdown. Prefer lists, tables, diagrams in text form, and explicit uncertainty markers over long prose.

### 6. Record uncertainty clearly

When something is not clear, label it explicitly:

- `Unknown`
- `Not found`
- `Inferred from ...`
- `Needs human confirmation`

Do not present guesses as facts.

### 7. Preserve existing human documentation

If documentation already exists:

- Read it before creating overlapping content
- Link to it when useful
- Avoid replacing human-written documentation wholesale
- Add AI-context documentation that complements existing docs

### 8. Provide practical recommendations without taking ownership of decisions

Human knowledge has limits, and part of the AI role is to reduce uncertainty.

When you discover gaps, risks, unclear areas, or opportunities, provide recommendations that are:

- Suitable for the observed project context
- Practical to implement with the current stack and structure
- Incremental rather than disruptive when possible
- Explicit about tradeoffs, risks, and assumptions
- Clearly labeled as recommendations, not project decisions

For meaningful choices, offer 1-3 viable options and indicate which option seems most appropriate based on current evidence. The human remains responsible for approving direction, goals, and major architecture decisions.

### 8.1 Establish features.md without turning ideas into a roadmap

Create or update `docs/ai-context/features.md` for requirements, feature ideas, and optimization opportunities that are worth preserving but are not necessarily part of the short-term execution plan.

Record items such as:

- Sudden ideas or insights
- Low-importance and non-urgent ideas
- Ideas aimed at long-term goals
- Ideas that do not affect short-term goals
- Breakthrough product, engineering, or interaction insights
- Optimization opportunities with potentially large performance gains
- Improvements with potentially large human-centered design gains

Separate user-provided ideas, inferred opportunities, AI recommendations, confirmed work, and items needing human confirmation. Do not present `features.md` as a committed roadmap or schedule.

### 9. Evaluate readability for humans and AI

When documenting architecture, modules, or refactoring recommendations, consider readability for both human developers and AI agents.

Prefer:

- Clear module boundaries
- Explicit naming
- Single, stable responsibilities
- Traceable data flow
- Discoverable entry points
- Consistent directory structure
- Documentation that maps to code structure
- Abstractions with low cognitive overhead

Avoid recommendations that lead to:

- Over-abstraction
- Sacrificing readability for perceived elegance
- Excessive implicit magic
- Confusing cross-layer dependencies
- Unclear file, module, or function responsibilities
- Structures that humans can barely understand but AI cannot reliably contextualize
- Structures that AI can generate but humans struggle to maintain

Refactoring recommendations should explain how they improve or affect understanding cost for humans and AI.

### 10. Provide imaginative but executable plans

When the user provides top-level input, direction, goals, or constraints, do not only decompose mechanically. Combine the project reality with appropriate imagination to construct executable plans.

Plans should pursue:

1. **Simple**: Prefer low-cognitive-load, low-dependency, clearly sequenced approaches.
2. **Effective**: Directly serve the goal and avoid purely cosmetic optimization.
3. **Human-centered interaction**: Consider real user experience, feedback, fault tolerance, and operational cost.
4. **Practical**: Fit the current resources, stack, and time constraints.
5. **Maintainable**: Keep structure clear, naming explicit, and boundaries stable so humans and AI can understand it later.
6. **Extensible**: Leave room for reasonable growth without premature abstraction or over-engineering.

When multiple plans are reasonable, prefer presenting:

- `Minimum viable plan`: simplest and fastest to land.
- `Recommended plan`: best balance of simplicity, effectiveness, interaction quality, and maintainability.
- `Expansion plan`: suitable for future scale, but requiring more investment.

Explain each plan’s conditions, cost, risk, and why one might reject it. The recommended plan should be based on current project evidence, not generic best practices.

### 11. Watch for silent fallbacks that mask bugs

AI-assisted development has a systematic bias: it tends to produce code that *looks* robust rather than code that *reveals the truth*. Not crashing feels like task done, and a silent fallback (default value, empty object, bare catch, silent retry) is the cheapest way to get there.

The danger is that a fallback flattens two fundamentally different situations:

- **Expected variation** (missing external input, transient network failure): should be handled explicitly at the system boundary.
- **Broken internal invariant** (a state that should be impossible): this is a bug and must surface early and loudly.

One silent fallback turns a bug (a negative) into a plausible empty state or default result (a positive); the next layer's fallback reads that as "normal," and the bug gets buried — the system runs but the result is quietly wrong.

Core principle: **fail fast, fail loud**. Do not add fallbacks to internal logic by default; fallbacks belong only at system boundaries, and each must be explicit, logged, and commented with which expected case it covers. Surface broken invariants with assertions instead of hiding them behind defaults.

Actions in this skill:

- Record this principle in the "AI working rules" section of `AGENTS.md` as project-level coding discipline.
- While exploring, catalog existing silent fallbacks (swallowed `catch`, `.get(k, default)`, `?? / ||` defaults, silent retries) as gotchas or risk points, noting for each whether it covers an expected case or may be masking a bug; flag the latter for human confirmation.
- During initialization, only record and flag these fallbacks — do not modify them.

## Boundaries

You may:

- Create missing AI-context documentation
- Add concise summaries of observed project reality
- Create lightweight decision placeholders for known or discovered decisions
- Suggest questions for the human to answer
- Identify documentation gaps

You must not:

- Change product direction
- Make major architecture decisions on behalf of the human
- Rewrite large parts of the codebase
- Perform broad refactors during initialization
- Delete existing documentation unless the user explicitly asks and the content has been reviewed
- Treat undocumented assumptions as confirmed facts
- Bind the workflow to a specific language, framework, or project type

If you discover possible architectural issues, document them as observations or questions, not decisions.

## Output

English-version skills should output in English, including final responses, reports, recommendations, and newly created or updated English documents. Do not switch to Chinese by default unless the user explicitly requests Chinese or the project context requires Chinese.

Create or update the following structure:

Unless the user explicitly asks for a minimal structure, keep these files even when some domains are not applicable, and record `Not applicable` with the supporting reason so future sessions do not mistake omission for missing work.

```text
AGENTS.md
docs/
  ai-context/
    architecture.md
    modules.md
    data-flow.md
    database.md
    api.md
    features.md
    decisions/
```

### `AGENTS.md`

Include:

- Project overview
- How to navigate the codebase
- Common commands, if discoverable
- Testing and validation guidance, if discoverable
- AI working rules for this project
- Links to `docs/ai-context/`
- Known unknowns or human-confirmation items

### `docs/ai-context/architecture.md`

Include:

- High-level architecture summary
- Main layers, services, packages, or components
- Frontend, backend, data-layer, and interface-layer responsibility boundaries, when applicable
- Layer boundaries, dependency direction, and boundaries that should not be crossed, if discoverable
- Important dependencies
- Runtime or deployment shape, if discoverable
- Architectural constraints
- Open architecture questions

### `docs/ai-context/modules.md`

Include:

- Major modules or directories
- Responsibility of each module
- Important files
- Dependencies between modules
- Ownership or stability notes, if discoverable

### `docs/ai-context/data-flow.md`

Include:

- Main user, system, or data flows
- Input and output boundaries
- Data handoff paths between frontend, backend, interface layer, and data layer, when applicable
- Cross-module interactions
- External integrations, if present
- Unclear or undocumented flows

### `docs/ai-context/database.md`

Include:

- Database or storage technology, if present
- Schema, model, migration, or persistence locations
- Important entities or records
- Data ownership boundaries
- Unknowns if no database evidence is found

### `docs/ai-context/api.md`

Include:

- Public APIs, internal APIs, routes, handlers, clients, protocols, or events
- API locations
- The interface layer’s responsibilities between frontend, backend, and external systems
- Request/response or message patterns, if discoverable
- Authentication or authorization notes, if discoverable
- Unknowns if no API evidence is found

### `docs/ai-context/features.md`

Include:

- Sudden ideas or insights
- Low-importance and non-urgent requirements, features, or optimizations
- Ideas aimed at long-term goals that do not affect short-term goals
- Breakthrough product, engineering, or interaction directions
- Optimization opportunities with potentially large performance gains
- Improvements with potentially large human-centered design gains
- Source, status, expected benefit, cost/risk, and whether human confirmation is needed for each item

This file records candidate ideas, not a roadmap. Do not present unconfirmed ideas as committed work.

### `docs/ai-context/decisions/`

Create the directory for future decision records.

If there are known decisions, create concise decision notes. If not, leave the directory ready for future use and optionally add a `README.md` explaining how to record decisions.

### Final response

After completing the skill, report:

- Files created or updated
- Important facts learned
- Unknowns that need human confirmation
- Suitable and implementable recommendations, if any
- Suggested next use of `project-sync` or `project-review`
