# Keep your AI and Architecture/Design in sync

**Follow-up to "Keep Your Architecture Diagrams in Code, Not in Tools"**

## The Core Problem

When developers use AI agents ad-hoc without specifications, the AI lacks the "internal view" of the system's architecture and design intent. This leads to:

- Code that compiles but violates architectural patterns
- Inconsistent implementation across features 
- AI suggestions that ignore existing design decisions
- Loss of architectural integrity over time

## The Solution: Spec-Driven Development (SDD)

By providing AI agents with specifications alongside architecture diagrams, we create a feedback loop:

**spec ↔ code** synchronization

The specifications give AI agents the "internal view" they need to generate code that respects your architecture and design decisions.

## OpenSpec Methodology

I use **OpenSpec** (https://github.com/Fission-AI/OpenSpec) because:

- **Focus on Software Development** (not API documentation like OpenAPI)
- **Easy to get started** with simple chat-based process
- **Works for brownfield projects** (most developers work on existing systems)
- **Lightweight process** that doesn't require formal templates

### OpenSpec vs Alternatives

**OpenSpec vs OpenAPI:**
- OpenAPI = REST API specification format
- OpenSpec = Software development methodology with specifications

**Alternatives to consider:**
- [GitHub Spec-Kit](https://github.com/github/spec-kit)
- [BMAD (Build More, Architect Dreams)](https://github.com/bmad-code-org/BMAD-METHOD)  
- [Kiro (by Amazon/AWS)](https://kiro.dev/)

I chose OpenSpec for its brownfield-friendly approach and simple chat-based workflow.

## OpenSpec Process (6 Steps)

**0. Create initial spec** (brownfield or greenfield)
**1. Review it** - make sure everything in spec is correct (your foundation!)
**2. Create new Change Spec**
**3. Review change spec** - important! Make changes before implementation
**4. Execute one task at a time**
**5. Archive the spec when done** - delta is used to update main spec (important!)
**6. Create new task** → back to step 2

### AI Agent Roles in the Process

**Planning Mode (Steps 0-3):** Use strong AI agents like **Claude Opus** level
- Create specifications
- Ask clarifying questions
- Review and refine change specs

**Execution Mode (Step 4):** Use "normal" AI agents like **GitHub Copilot**
- Implement individual tasks
- Generate code following the specification
- Use Plan mode for task breakdown

## Key Concepts

- **Specifications vs Change Specifications:** Main specs are "aggregated mass", change specs are deltas
- **/openspec folder convention:** Follow OpenSpec methodology (not /docs)
- **Chat-based workflow:** Simple prompts like "Create a new change specification for: xxxx"
- **Coexistence with /docs:** Specifications complement architecture diagrams

## Article Structure

This article will:

1. Build directly on the architecture-as-code foundation
2. Show how specs provide the "internal view" for AI agents
3. Demonstrate practical OpenSpec workflow with chat prompts
4. Extend the architecture-as-code-example repository with /openspec
5. Show when to use which AI agent type in the process
6. Demonstrate spec ↔ code synchronization keeping AI "aligned"

## Example: Brownfield Enhancement

Use the existing e-commerce domain from architecture-as-code-example to show:
- Adding customer loyalty points feature
- Creating change specification with chat prompts
- Using strong AI for planning, regular AI for execution
- Integrating /openspec with existing /docs architecture
