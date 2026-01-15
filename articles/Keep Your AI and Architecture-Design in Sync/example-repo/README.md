# OpenSpec Integration Example

This directory demonstrates how **OpenSpec** integrates with the **architecture-as-code** approach from the previous
article.

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
├── openspec/                         # Specifications (this article)
│   ├── main-spec.md                  # Aggregated system specifications
│   ├── change-specs/
│   │   ├── loyalty-points.md         # Active change specification
│   │   └── archived/
│   │       └── user-registration.md  # Completed change specs
│   └── business-rules/
│       └── order-validation.md       # Domain rules & constraints
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

- **Why design decisions were made** (specifications document intent)
- **What business rules apply** (validation logic, constraints)
- **How changes are managed** (change specifications, evolution tracking)

## AI Agent Usage Pattern

### Planning Mode: Strong AI (Claude Opus)

```
"Create a new change specification for: Add customer loyalty points system"

"Review this change specification and ask questions about edge cases"

"Archive change specification loyalty-points and update main-spec.md"
```

### Execution Mode: Regular AI (GitHub Copilot)

```typescript
// Reference: /openspec/change-specs/loyalty-points.md section 2.1
// Follow guidelines in AGENTS.md
// Implement LoyaltyPoints entity following business rules

class LoyaltyPoints {
    // AI generates code that follows the specification and AGENTS.md guidelines...
}
```

**💡 Tip:** Always reference both the specification AND AGENTS.md in your prompts for consistent, architecture-aligned
code generation.

## OpenSpec Workflow Example

1. **Initial Spec (Step 0):** Document existing system behavior in `main-spec.md`
2. **Foundation Review (Step 1):** Ensure baseline specification is accurate
3. **Change Spec (Step 2):** Create `change-specs/loyalty-points.md` for new feature
4. **Review (Step 3):** Use Claude Opus to refine and ask clarifying questions
5. **Execute (Step 4):** Use GitHub Copilot to implement tasks one at a time
6. **Archive (Step 5):** Move completed spec to `archived/` and update main spec
7. **Iterate (Step 6):** Create next change specification

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
3. **Document one existing feature** as your baseline specification
4. **Try the workflow** with your next feature:
    - Use strong AI for change specification creation
    - Review and refine before implementation
    - Use regular AI for code generation with spec and AGENTS.md references
    - Archive completed change specs

5. **Build the habit:** Specifications and guidelines before implementation

This approach keeps your AI agents "on rails" by providing the complete "internal view" of your system's structure,
behavior, AND coding standards.

---

**Related:
** [Keep Your Architecture Diagrams in Code, Not in Tools](../Keep%20Your%20Architecture%20Diagrams%20in%20Code,%20Not%20in%20Tools/article.md)
