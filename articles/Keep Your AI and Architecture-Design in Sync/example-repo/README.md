# OpenSpec Integration Example

This directory demonstrates how **OpenSpec** integrates with the **architecture-as-code** approach from the previous
article.

## Terminology

This example uses two AI categories:

| Term           | Description                                                                    | Examples                                 | Use For                                                     |
|:---------------|:-------------------------------------------------------------------------------|:-----------------------------------------|:------------------------------------------------------------|
| **Strong AI**  | Premium, frontier-class models with advanced reasoning and high-level strategy | Claude 4.5 Opus, Gemini Ultra            | Spec creation, architectural planning, requirement analysis |
| **Regular AI** | High-performance coding assistants, cost-effective for implementation          | Claude 4.5 Sonnet, GPT-5.2, Gemini 3 Pro | Code implementation, task execution, archiving              |

When we say "AI agent", we mean an **agentic AI** that can execute multi-step tasks, read/write files, and run commands
autonomously.

## Directory Structure

```
example-repo/
├── AGENTS.md                         # AI agent guidelines and instructions
├── docs/                             # Architecture diagrams (from previous article)
│   └── architecture/
│       ├── domain/
│       │   ├── customer.md           # Entity diagrams & relationships
│       │   ├── order.md              # State machines & ER diagrams  
│       │   └── payment.md            # Class diagrams & workflows
│       └── flows/
│           ├── create-order.md       # Sequence diagrams
│           └── payment-processing.md
├── openspec/                         # Specifications (OpenSpec structure)
│   ├── specs/                        # Source of truth specifications
│   │   ├── order/
│   │   │   └── spec.md               # Order domain specification
│   │   ├── customer/
│   │   │   └── spec.md               # Customer domain specification
│   │   └── payment/
│   │       └── spec.md               # Payment domain specification
│   └── changes/                      # Active and archived change proposals
│       ├── loyalty-points/           # Active change proposal
│       │   ├── proposal.md           # What and why
│       │   ├── tasks.md              # Implementation checklist
│       │   └── specs/
│       │       └── customer/
│       │           └── spec.md       # Spec delta for this change
│       └── archived/
│           └── user-registration/    # Completed change proposal
│               ├── proposal.md
│               └── tasks.md
└── src/
    └── ...                           # Application code
```

## How They Work Together

### AGENTS.md provides GUIDELINES

- **How to write code** (style, conventions, patterns)
- **What to avoid** (common pitfalls, anti-patterns)
- **Quality standards** (testing, documentation requirements)

### /docs provides STRUCTURE

- **What entities exist** (class diagrams, ER schemas)
- **How they relate** (entity relationships, sequence flows)
- **System boundaries** (context diagrams, component views)

### /openspec provides BEHAVIOR

- **/openspec/specs/** - Source of truth specifications with business rules
- **/openspec/changes/** - Change proposals with tasks and spec deltas
- **Why design decisions were made** (specifications document intent)
- **How changes are managed** (proposals track evolution)

## AI Agent Usage Pattern

### Planning Mode: Strong AI

```
"Create a new change proposal for: Add customer loyalty points system"

"Review this change proposal and ask questions about edge cases"

"Archive the loyalty-points change and update the specs"
```

### Execution Mode: Regular AI

```typescript
// Reference: /openspec/changes/loyalty-points/specs/customer/spec.md
// Follow guidelines in AGENTS.md
// Implement LoyaltyPoints entity following business rules

class LoyaltyPoints {
    // AI generates code that follows the specification and AGENTS.md guidelines...
}
```

**💡 Tip:** Always reference both the specification AND AGENTS.md in your prompts for consistent, architecture-aligned
code generation.

## OpenSpec Workflow Example

1. **Create Initial Specs (Step 1):** Document existing system behavior in `/openspec/specs/`
2. **Foundation Review (Step 2):** Ensure baseline specs are accurate
3. **Create Change Proposal (Step 3):** Create `/openspec/changes/loyalty-points/` with proposal.md and tasks.md
4. **Review (Step 4):** Use strong AI to refine and ask clarifying questions
5. **Execute (Step 5):** Use regular AI to implement tasks one at a time
6. **Archive (Step 6):** Move completed change to `changes/archived/` and merge spec deltas
7. **Iterate:** Create next change proposal

## Key Benefits

### For AI Agents

- **Complete context:** Structure (/docs), behavior (/openspec), and guidelines (AGENTS.md)
- **Clear boundaries:** Specifications prevent architectural violations
- **Consistent patterns:** AGENTS.md ensures consistent code style across AI sessions

### For Developers

- **Brownfield friendly:** Works with existing codebases (not just greenfield)
- **Chat-based:** Simple prompts, no complex templates
- **Version controlled:** Specifications and guidelines evolve with code in same repository
- **Predictable AI:** AGENTS.md creates consistent AI behavior across team members

### For Architecture

- **Integrity maintained:** AI agents understand design intent
- **Evolution tracked:** Change specifications document system growth
- **Knowledge preserved:** Decisions and reasoning captured in specifications
- **Standards enforced:** AGENTS.md ensures code quality and consistency

## Getting Started

1. **Create `/openspec` folder** alongside existing `/docs`
2. **Create `AGENTS.md` file** in repository root with AI guidelines
3. **Document one existing feature** as your baseline specs in `/openspec/specs/`
4. **Try the workflow** with your next feature:
    - Use strong AI for change proposal creation
    - Review and refine before implementation
    - Use regular AI for code generation with spec and AGENTS.md references
    - Archive completed change specs

5. **Build the habit:** Specifications and guidelines before implementation

This approach keeps your AI agents "on rails" by providing the complete "internal view" of your system's structure,
behavior, AND coding standards.

---

**Related:
** [Keep Your Architecture Diagrams in Code, Not in Tools](../Keep%20Your%20Architecture%20Diagrams%20in%20Code,%20Not%20in%20Tools/article.md)
