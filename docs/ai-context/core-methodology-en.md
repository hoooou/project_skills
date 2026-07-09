# Core Methodology for Project Knowledge Management

> Integrating Mao Zedong's Theory of Contradictions, Elon Musk's First Principles, and Steve Jobs' Minimalism

## I. Theoretical Foundation

### 1.1 Identifying Principal Contradictions (Mao Zedong)

**Core Ideas**:
- Complex systems contain principal and secondary contradictions
- The principal contradiction determines the direction of development
- Solving the principal contradiction can drive resolution of secondary contradictions
- At different stages, the principal contradiction transforms

**Applied to Project Knowledge Management**:
- Identify the current core problem (missing docs vs outdated docs vs architectural chaos)
- Distinguish symptoms from root causes (code hard to understand is a symptom; unclear responsibilities are the cause)
- Find leverage points: solving one problem can resolve multiple others
- Dynamic adjustment: principal contradictions change at different project stages

### 1.2 First Principles Thinking (Elon Musk)

**Core Ideas**:
- Return to the most fundamental truths and assumptions
- Don't rely on analogies, conventions, or existing solutions
- Re-derive from fundamentals
- Question everything that's "taken for granted"

**Applied to Project Knowledge Management**:
- What's the fundamental purpose of project knowledge? → Reduce understanding cost, improve collaboration efficiency
- Why do we need documentation? → Context that code cannot self-explain
- What knowledge must be preserved? → Decision context, constraints, trade-offs
- Why does traditional documentation fail? → Separated from code, cannot evolve in sync

### 1.3 Minimalism (Steve Jobs)

**Core Ideas**:
- Less is more, eliminate complexity
- Focus on essence, remove everything unnecessary
- Pursue extreme experience and aesthetics
- User experience first (applies to both humans and AI)
- Every element must have a reason to exist

**Applied to Project Knowledge Management**:
- More documentation is not better, only keep what's necessary
- Every sentence, every file must have clear value
- Prioritize readability and maintainability over "completeness"
- Form follows function, don't document for documentation's sake

---

## II. Core Method: Three-Layer Progressive Analysis

### 2.1 Layer 1: First Principles Analysis (Find the Root Goal)

**Question Sequence**:

1. **What is the project's fundamental goal?**
   - Not "complete features", but "solve what problem"
   - Not "write code", but "create what value"

2. **What is the fundamental purpose of project knowledge?**
   - Enable future humans and AI to quickly understand the project
   - Reduce collaboration, maintenance, and decision-making costs
   - Preserve critical context, avoid repeating mistakes

3. **What knowledge is essential?**
   - What code cannot self-explain: decision context, constraints, trade-offs
   - Easy to forget: why not do something, why choose A over B
   - Cross-time necessary: what new members need 6 months later to take over

4. **What knowledge is redundant?**
   - Can be directly derived from code
   - Will quickly become outdated and not worth syncing
   - Only useful for current tasks, temporary information

**Output**: Clear boundaries and core value proposition for project knowledge

### 2.2 Layer 2: Principal Contradiction Analysis (Find the Core Problem)

**Contradiction Identification Framework**:

#### A. Identify All Contradictions

List all current project problems:
- Missing documentation
- Outdated documentation
- Architectural chaos
- Unclear module responsibilities
- Accumulated technical debt
- Inconsistent naming
- Insufficient testing
- ...

#### B. Determine Principal vs Secondary Contradictions

Use the "Four-Quadrant Method":

| Dimension | Principal Contradiction Characteristics | Secondary Contradiction Characteristics |
|-----------|----------------------------------------|----------------------------------------|
| **Impact Scope** | Systemic, global | Local, module-level |
| **Blocking Relationship** | Blocks other work progress | Doesn't block other work |
| **Risk Accumulation** | Compound deterioration (exponential growth) | One-time, doesn't worsen |
| **Solution Leverage** | Solving it drives multiple other solutions | Only solves itself |

**Judgment Method**:

```
If you could only solve one problem, which would improve the project state most?
→ That's the principal contradiction
```

#### C. Common Patterns of Principal Contradictions

**Pattern 1: Knowledge Gap**
- **Manifestation**: AI or new members frequently misjudge project state
- **Essence**: Critical context is missing or misleading
- **Impact**: All subsequent work is built on wrong assumptions
- **Priority**: Extremely high

**Pattern 2: Blurred Responsibility Boundaries**
- **Manifestation**: Modules interdependent, changing one affects many
- **Essence**: Architectural design problem, not code quality problem
- **Impact**: High cost and risk for every change
- **Priority**: High

**Pattern 3: Knowledge Drift**
- **Manifestation**: Documentation and code gradually become inconsistent
- **Essence**: Lack of synchronization mechanism
- **Impact**: Compound deterioration, harder the later you address it
- **Priority**: Medium-high

**Pattern 4: Technical Debt Accumulation**
- **Manifestation**: Code hard to read, duplicated, confusing names
- **Essence**: Usually a secondary contradiction, unless already blocking core work
- **Impact**: Linear growth, manageable
- **Priority**: Medium-low (unless it has become the principal contradiction)

#### D. Transformation of Contradictions

**Important Principle**: Principal contradictions transform across project stages

| Project Stage | Typical Principal Contradiction | Why |
|---------------|--------------------------------|-----|
| **Startup** | Unclear direction, undefined architecture | No baseline, cannot collaborate |
| **Rapid Iteration** | Knowledge sync can't keep up with code changes | Change speed > documentation speed |
| **Stable Phase** | Knowledge drift, technical debt accumulation | Maintenance willingness declines |
| **Refactoring** | Old and new architecture coexist, unclear boundaries | Chaos during transition |

**Output**: Identify the principal contradiction at current stage, clarify priority issues to solve

### 2.3 Layer 3: Minimalist Filtering (Eliminate Complexity)

**Filtering Principles**:

1. **Every document must answer**:
   - What problem does this document solve?
   - What consequences if this document doesn't exist?
   - Who will read it, in what scenario?
   - If you can't answer clearly, delete or merge

2. **Every sentence must answer**:
   - What information does this sentence convey?
   - What loss if readers don't know this sentence?
   - If it's just for "looking complete", delete

3. **Every section must answer**:
   - What's the core value of this section?
   - Can it be merged with other sections?
   - If it can be merged, merge it

4. **Signal-to-Noise Ratio Principle**:
   - Signal: Facts, decisions, constraints that must be known
   - Noise: Optional descriptions, repeated content, obvious things
   - Goal: Signal-to-noise ratio > 80%

**Jobs-style Questioning**:

```
Designer: We should add project history introduction to README
Jobs: Why?
Designer: To let people understand project background
Jobs: Who needs to understand? When do they need it?
Designer: When new members join
Jobs: What do new members need most when joining? History or how to get started quickly?
Designer: How to get started
Jobs: Then only write how to get started. History is not important.
```

**Output**: Streamlined knowledge system, each part with clear reason to exist

---

## III. Practical Operations: 5-Step Workflow

### Step 1: Zero-Based Thinking (First Principles)

**Ask Yourself**:
- If this project started today, how would I organize knowledge?
- If I could only keep 3 documents, which 3?
- If I could only write 100 sentences to describe this project, what would I write?

**Output**: Minimum necessary set of knowledge system

### Step 2: Contradiction Analysis (Principal Contradiction)

**List Problem Checklist**:
```
[ ] Missing documentation
[ ] Outdated documentation
[ ] Architectural chaos
[ ] Unclear module responsibilities
[ ] ...
```

**Four-Quadrant Classification**:
```
High Impact + High Leverage → Principal contradiction, handle immediately
High Impact + Low Leverage → Important but requires significant investment
Low Impact + High Leverage → Cost-effective, prioritize
Low Impact + Low Leverage → Ignore or postpone
```

**Identify Principal Contradiction**:
- What currently most hinders project progress?
- Solving which problem can lead to solving other problems?

**Output**: Problem list with clear priorities

### Step 3: Minimalist Design (Jobs)

**Question Every Proposed Document/Section**:
1. Reason to exist?
2. Target audience?
3. Reading scenario?
4. Consequences if it doesn't exist?
5. Can it be merged elsewhere?

**Reduction Rules**:
- Can be derived from code → Delete
- Obvious → Delete
- Duplicated → Merge
- Will quickly become outdated and not worth maintaining → Delete
- Only useful for current task → Don't write into long-term knowledge

**Output**: Minimized knowledge system design

### Step 4: Focused Execution (Concentrate Forces to Solve Principal Contradiction)

**Principles**:
- Only solve one principal contradiction at a time
- Don't try to solve all problems simultaneously
- After solving the principal contradiction, re-evaluate (secondary contradictions may have resolved automatically or become principal)

**Execution Strategy**:
```
if principal_contradiction == "knowledge gap":
    → Execute project-init, establish baseline
    
elif principal_contradiction == "knowledge drift":
    → Execute project-sync, align docs and code
    
elif principal_contradiction == "blurred responsibility boundaries":
    → Clarify architecture first, then sync documentation
    → May need refactoring, but documentation cannot solve architectural problems
    
elif principal_contradiction == "technical debt accumulation":
    → First assess whether technical debt is symptom or cause
    → If symptom, find underlying architectural or process problems
```

**Output**: Precise action targeting principal contradiction

### Step 5: Dynamic Adjustment (Contradiction Transformation)

**After Each Problem Resolution**:
1. Re-evaluate: Has the principal contradiction been solved?
2. Identify new principal contradiction: Have secondary contradictions risen to principal?
3. Adjust strategy: What should be solved next?

**Output**: Continuously evolving knowledge management strategy

---

## IV. Application to Three Skills

### 4.1 project-init

**Enhancements After Integration**:

1. **First Principles Application**:
   - Don't try to describe the project "completely", only record what must be known
   - Before each document exists, ask: what if it doesn't exist?
   
2. **Principal Contradiction Identification**:
   - Principal contradiction during initialization is usually: no baseline, cannot collaborate
   - Secondary contradictions: code quality, technical debt
   - Strategy: Quickly establish baseline, don't obsess over perfection
   
3. **Minimalism**:
   - Default to creating minimum knowledge set
   - Every section must have clear value
   - Prioritize "usable" over "perfect"

**New Instructions**:
```
Before creating each document, must answer:
1. What principal contradiction does this document solve?
2. What are the consequences if this document doesn't exist?
3. If you can't answer clearly, consider whether this document is really needed
```

### 4.2 project-sync

**Enhancements After Integration**:

1. **First Principles Application**:
   - Fundamental purpose of sync: keep docs and code consistent
   - Only sync affected parts, don't "casually" change unrelated content
   
2. **Principal Contradiction Identification**:
   - Determine the principal impact of current changes
   - Distinguish: systemic changes vs local changes
   - Strategy: Systemic changes prioritize syncing architecture docs, local changes only update related module docs
   
3. **Minimalism**:
   - Delete outdated content during sync, not accumulate
   - Every sync is an opportunity for streamlining

**New Instructions**:
```
Before syncing, must identify:
1. What is the principal contradiction of current changes? (Architecture change? Module boundary adjustment? Local optimization?)
2. Which docs are affected by principal contradiction? (Prioritize sync)
3. Which docs are secondarily affected? (Can be postponed)
4. Can outdated or redundant content be deleted during sync?
```

### 4.3 project-review

**Enhancements After Integration**:

1. **First Principles Application**:
   - Fundamental purpose of review: discover core problems hindering project evolution
   - Don't list all problems, identify principal contradictions
   
2. **Principal Contradiction Identification**:
   - Use four-quadrant method to classify all findings
   - Clearly point out: what is the current project's principal contradiction
   - Provide: priority recommendations for solving principal contradiction
   
3. **Minimalism**:
   - Report itself should be streamlined: highlight key points, not cover everything
   - Recommendations should be specific, actionable, not vague

**New Instructions**:
```
Review report must include:
1. Principal Contradiction Identification: Core problems currently most hindering the project (1-3)
2. Secondary Problem List: Other findings (can be briefly listed)
3. Contradiction Analysis: Why are these principal contradictions? (Impact scope, blocking relationship, risk accumulation)
4. Solution Strategy: Which to solve first, why, expected effect
5. Minimalist Recommendation: If you could only do one thing, what should it be?
```

---

## V. Judgment Criteria and Examples

### 5.1 Good Knowledge Management (Follows Methodology)

**Example 1: Identifying Principal Contradiction**

❌ **Bad** (Enumerating all problems):
```
Found the following problems:
- README is outdated
- 3 functions have inconsistent naming
- Missing API documentation
- Database documentation missing
- 5 TODOs without owners
- ...(20 problems total)

Recommendation: Solve these problems one by one
```

✅ **Good** (Identifying principal contradiction):
```
Principal Contradiction: Database schema changes frequently, but no documentation, causing frontend team to frequently misjudge data structures

Impact Analysis:
- Blocking relationship: Every frontend development requires repeated confirmation of fields
- Risk accumulation: Compound type, every change amplifies the problem
- Impact scope: Systemic, affects frontend-backend collaboration

Other Findings:
- README outdated (local problem, doesn't block)
- Inconsistent naming (secondary contradiction)

Recommendation: Prioritize establishing database.md and API contract documentation, postpone other problems
```

**Example 2: First Principles Thinking**

❌ **Bad** (Based on conventions):
```
Project lacks documentation, should create:
- README
- CONTRIBUTING
- CODE_OF_CONDUCT
- CHANGELOG
- API.md
- ARCHITECTURE.md
- ...
```

✅ **Good** (Starting from fundamental needs):
```
Fundamental purpose of project knowledge: Enable new members to start contributing code within 1 hour

Questions that must be answered:
1. What does this project do? → README (keep)
2. How to run and test? → README (keep)
3. How is code organized? → architecture.md (keep)
4. What are important decisions? → decisions/ (keep)

Not necessary:
- CODE_OF_CONDUCT: Small team, not needed
- CONTRIBUTING: Internal team project, face-to-face communication more effective
- CHANGELOG: git log is sufficient

Minimum knowledge set: README + architecture.md + decisions/
```

**Example 3: Minimalist Filtering**

❌ **Bad** (Redundant description):
```
## User Module

The User Module is responsible for managing users in the system. 
It handles user creation, user updates, user deletion, and user queries.
The module is located in src/modules/user/.
It uses the User model defined in src/models/user.ts.
It exposes a UserService class.
The UserService depends on the Database service.
```

✅ **Good** (Streamlined to essence):
```
## User Module

**Responsibility**: User CRUD
**Location**: src/modules/user/
**Dependencies**: Database service
**Public Interface**: UserService
```

### 5.2 Bad Knowledge Management (Violates Methodology)

**Anti-pattern 1: Equal Effort Distribution**
- Treat all problems equally
- Don't identify principal contradiction
- Try to solve all problems simultaneously

**Anti-pattern 2: Over-design**
- Create too many documents
- Add unnecessary sections for "completeness"
- Violate minimalism

**Anti-pattern 3: Surface Work**
- Only solve surface problems (change naming, adjust formatting)
- Ignore fundamental problems (architectural chaos, unclear responsibilities)
- Don't identify principal contradiction

**Anti-pattern 4: Inertial Thinking**
- "Other projects have CONTRIBUTING, we should have it too"
- "Documentation should include history, background, future plans..."
- Don't think from first principles

---

## VI. Self-Check Checklist

### For AI Agents

When executing project-init / project-sync / project-review, always ask yourself:

**First Principles Check**:
- [ ] Am I starting from fundamental needs, not conventions?
- [ ] Have I questioned every "should"?
- [ ] Do I know the reason for each document/section to exist?

**Principal Contradiction Check**:
- [ ] Have I identified the current principal contradiction?
- [ ] Have I distinguished principal from secondary problems?
- [ ] Have I provided recommendations with clear priorities?
- [ ] Am I focusing on high-leverage problems?

**Minimalism Check**:
- [ ] Have I deleted all redundant content?
- [ ] Does each document have a clear reason to exist?
- [ ] Does each sentence convey necessary information?
- [ ] Is the signal-to-noise ratio > 80%?

### For Users

After using these skills, should check:

**Effect Check**:
- [ ] Do documents help me understand the project faster?
- [ ] Can I quickly find the information I need?
- [ ] Are documents concise, without verbosity?
- [ ] Did AI identify the real core problems?

**Continuous Improvement**:
- [ ] Has the principal contradiction been solved?
- [ ] Have new principal contradictions emerged?
- [ ] Is the knowledge system evolving with the project?

---

## VII. Summary

### Core Formula

```
Good Project Knowledge Management = First Principles (Find Fundamentals) 
                                   + Theory of Contradictions (Grasp Key Points)
                                   + Minimalism (Eliminate Complexity)
```

### Three Iron Laws

1. **Always start from first principles**: Question every "should", return to fundamental needs
2. **Always identify principal contradictions**: Don't distribute effort equally, focus on high-leverage problems
3. **Always pursue minimalism**: Every element must have a reason to exist

### Ultimate Goal

> With minimum documentation, solve core problems, create maximum value
