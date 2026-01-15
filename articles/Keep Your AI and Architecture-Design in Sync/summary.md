# Article Summary: Keep your AI and Architecture/Design in sync

## Key Concepts Implemented

### 1. The "Internal View" Problem
- AI agents working ad-hoc lack context about architectural decisions
- Specifications provide the missing behavioral context that complements structural diagrams
- **spec ↔ code synchronization** keeps AI agents aligned with design intent

### 2. OpenSpec Methodology Integration
- **6-step process:** Initial spec → Review → Change spec → Review → Execute → Archive → Iterate
- **Chat-based workflow:** Simple prompts instead of formal templates
- **Brownfield-friendly:** Works with existing codebases (realistic for most developers)

### 3. AI Agent Role Differentiation
- **Strong AI (Claude Opus):** Planning, specification creation, requirement clarification
- **Regular AI (GitHub Copilot):** Task execution, code generation following specifications
- **Clear separation:** Planning vs execution phases use different AI capabilities

### 4. Folder Structure Integration
- **/openspec** (specifications) complements **/docs** (architecture diagrams)  
- **AGENTS.md** (AI guidelines) in repository root provides coding standards
- Specifications provide behavior, diagrams provide structure, AGENTS.md provides conventions
- Both give AI agents complete "internal view" of the system

## Practical Examples Created

### 0. AGENTS.md Example
- **AGENTS.md:** Complete AI guidelines template with code style, architecture patterns, testing requirements
- Shows how to establish predictable AI behavior across team members
- Demonstrates integration with /openspec specifications
- Provides practical "do this, not that" examples for AI agents

### 1. Complete Change Specification
- **loyalty-points.md:** Realistic brownfield enhancement to e-commerce system
- Shows business rules, edge cases, data model changes, and implementation tasks
- Demonstrates specification quality needed for AI agent alignment

### 2. Business Rules Documentation
- **order-validation.md:** Detailed validation logic and constraints
- Includes pseudocode examples for AI implementation guidance
- Shows how to structure business logic for AI consumption

### 3. Archived Change Specification
- **user-registration.md:** Example of completed change spec with lessons learned
- Demonstrates the archive process and delta integration
- Shows real-world AI agent usage results

### 4. Main System Specification
- **main-spec.md:** Aggregated baseline showing system evolution
- Integration with existing architecture documentation
- Clear change log and version tracking

## Chat Prompts Demonstrated

### Planning Phase (Claude Opus)
```
"Create a new change specification for: Add customer loyalty points system"
"Review this change specification and ask questions about edge cases"
"What business rules should we consider for refunds and account deletions?"
```

### Execution Phase (GitHub Copilot)
```typescript
// Reference: /openspec/change-specs/loyalty-points.md section 2.1
// Implement LoyaltyPoints entity following business rules
```

### Archive Phase
```
"Archive change specification loyalty-points and update main-spec.md with implemented changes"
```

## Integration with Previous Article

### Building on Architecture-as-Code Foundation
- Previous article established **/docs** with Mermaid diagrams
- This article adds **/openspec** with behavioral specifications
- This article adds **AGENTS.md** with AI coding guidelines
- Combined approach gives AI agents complete system understanding

### Enhanced AI Collaboration
- Architecture diagrams show "what exists" and "how it relates"
- Specifications show "why decisions were made" and "what rules apply"
- AGENTS.md shows "how to write code" and "what standards to follow"
- AI agents can now generate code that respects structure, behavior, AND team conventions

## Success Metrics for Readers

After implementing this approach, developers should achieve:

1. **AI-generated code that respects architectural patterns**
2. **Consistent implementation across features and team members**
3. **Preserved architectural integrity as system evolves**
4. **Reduced manual code review for architectural compliance**
5. **Better AI agent suggestions that understand business context**
6. **Predictable AI behavior through AGENTS.md guidelines**

## Next Steps for Implementation

### Phase 1: Setup
- Create `/openspec` folder alongside existing `/docs`
- Document one existing feature as baseline specification
- Establish the chat-based workflow with preferred AI agents

### Phase 2: Practice
- Use methodology for next feature development
- Build habit of specifications before implementation
- Refine prompts and AI agent usage patterns

### Phase 3: Scale
- Apply to larger features and system changes
- Create team standards for specification quality
- Integrate with PR review process

## Article Positioning

This article successfully:
- **Builds naturally** on the previous architecture-as-code success
- **Addresses real brownfield scenarios** (not just greenfield examples)  
- **Shows practical AI agent usage** with concrete prompts and examples
- **Provides immediate value** with actionable methodology
- **Maintains technical quality** while staying accessible

The combination creates a comprehensive approach for AI-assisted development that maintains architectural integrity while leveraging AI capabilities effectively.

## Repository Integration

The example repository structure demonstrates:
- How `/openspec` and `/docs` coexist and complement each other
- How `AGENTS.md` provides predictable AI guidelines in the repository root
- Real-world change specification quality and detail
- Practical business rules documentation for AI consumption
- Complete workflow from planning through archiving
- AI hygiene practices for consistent code generation

This provides readers with immediately usable templates and patterns for their own projects.
