## Plan: Keep your AI and Architecture/Design in sync

**TL;DR:** Build on architecture-as-code foundation to show how spec-driven development creates the synchronization between AI agents and architectural intent. Using OpenSpec methodology with practical chat prompts, demonstrate how specifications provide the "internal view" that keeps AI agents aligned with design decisions.

### Article Structure

1. **Hook + Problem** (2-3 min read)
   - Reference the successful architecture-as-code article
   - New problem: AI agents work ad-hoc without architectural context
   - Personal angle: the "internal view" problem - AI needs specs, not just code
   - Pain point: code that compiles but violates architectural patterns

2. **The Sync Problem** (1-2 min)
   - Define spec ↔ code synchronization
   - Why ad-hoc AI usage breaks architectural integrity
   - How specifications provide the missing "internal view"
   - Connect to the architecture diagrams from previous article

3. **OpenSpec vs Alternatives** (2 min)
   - Clear distinction: OpenSpec ≠ OpenAPI (REST specs)
   - Compare with GitHub Spec-Kit, BMAD, Kiro
   - Why OpenSpec works for brownfield (most developers' reality)
   - Simple chat-based approach vs formal templates

4. **The OpenSpec Process** (3-4 min)
   - 6-step workflow with practical examples
   - Chat prompts: "Create a new change specification for: xxxx"
   - When to use Claude Opus vs GitHub Copilot
   - /openspec folder convention alongside /docs

5. **Practical Example** (4-5 min)
   - Extend architecture-as-code-example repository
   - Brownfield: Add customer loyalty points feature
   - Show actual change specification workflow
   - Demonstrate AI agent role differentiation

6. **Integration with Architecture-as-Code** (2-3 min)
   - How /openspec complements /docs architecture diagrams
   - Specs provide business logic, diagrams provide structure
   - Both give AI agents complete "internal view"
   - Version control and PR review workflow

7. **Getting Started** (2 min)
   - Start with existing codebase (brownfield approach)
   - Simple first steps with chat prompts
   - When to use which AI agent type
   - Link to updated example repository

### Key Messages

- **Architecture diagrams** (previous article) + **Specifications** (this article) = Complete AI alignment
- **Brownfield-friendly:** Most developers work on existing systems
- **Chat-based workflow:** No complex templates, just simple prompts
- **AI agent differentiation:** Strong AI for planning, regular AI for execution
- **Practical methodology:** OpenSpec provides the structure without overhead

### Article Tone

- Build directly on previous article's success
- Practical and actionable (like the first article)
- Show real examples and workflows
- Address brownfield reality (not just greenfield examples)
- Technical but accessible

### Validation Approach

- Extend the existing architecture-as-code-example repository
- Show real OpenSpec structure with /openspec folder
- Provide actual chat prompts used in practice  
- Demonstrate spec ↔ code sync with concrete example
- Make it immediately actionable for readers

### Success Metrics

- Readers can immediately start using OpenSpec workflow
- Clear understanding of when to use which AI agent type
- Practical integration with existing architecture-as-code approach
- Actionable next steps for their own projects
