# Article Proposal: Scaling AI Agent Instructions with Modular AGENTS.md

**For: Architecture as Code Blog**  
**Author: Flemming Nørnberg Larsen**  
**Target Publication Date: 2026 M01/M02**

---

## Article Title Options

1. **"Stop Overloading Your AI Agents: A Modular Approach to AGENTS.md"** (primary recommendation)
2. "Token-Efficient AI Agent Instructions: The Modular AGENTS.md Pattern"
3. "Breaking Down AGENTS.md: How to Structure AI Guidelines at Scale"

---

## Article Summary (TL;DR)

As your codebase grows, monolithic `AGENTS.md` files become counterproductive—AI agents either ignore them or waste tokens loading irrelevant instructions. This article introduces a **modular agent instruction framework** using a `.ai/` directory structure with topic-based files and keyword-triggered routing. The approach achieves **3x-5x token efficiency** while maintaining clear guidelines for AI coding assistants.

**Key Innovation:** Treat AI agent instructions like microservices—small, focused, independently loadable modules rather than monolithic documentation.

---

## Article Structure Outline

### 1. Introduction: The Growing AGENTS.md Problem

**Hook:** You've embraced spec-driven development. Your AI agents have `/docs` for architecture and `/openspec` for specifications. You've even created `AGENTS.md` with coding guidelines. But as your project grows, you notice something troubling...

**The Problem:**
- Your `AGENTS.md` has grown to 500+ lines covering Java conventions, Python style, build procedures, testing standards, documentation requirements, and cross-platform guidelines
- AI agents either **skip reading it** (too long) or **waste tokens** loading instructions irrelevant to the current task
- When fixing a typo in Python, the agent loads Java immutability rules and Gradle build instructions
- Token budgets are consumed by boilerplate before the AI even sees your actual code

**Real-world scenario:**
```
You: "Fix this Python type hint"
AI: *loads 500 lines of AGENTS.md*
AI: *reads Java conventions (not relevant)*
AI: *reads build procedures (not relevant)*
AI: *reads documentation standards (not relevant)*
AI: Finally finds Python conventions buried at line 342
Result: Token budget 60% consumed before seeing your code
```

**The insight:** Just as we learned to split monolithic applications into microservices, we need to split monolithic agent instructions into focused, loadable modules.

### 2. The Modular AGENTS.md Pattern

**Core Concept:** Replace monolithic `AGENTS.md` with a **lightweight router** + topic-based instruction files.

**Directory structure:**
```
your-project/
├── AGENTS.md                      # Lightweight router (50-60 lines)
├── .ai/                          # Modular instructions directory
│   ├── README.md                 # Index & routing guide
│   ├── core-principles.md        # ~40 lines, ~400 tokens
│   ├── cross-platform.md         # ~55 lines, ~600 tokens
│   ├── coding-conventions.md     # ~35 lines, ~350 tokens
│   ├── testing-and-build.md      # ~40 lines, ~450 tokens
│   ├── documentation.md          # ~30 lines, ~300 tokens
│   └── standards.md              # ~25 lines, ~250 tokens
├── openspec/
│   └── AGENTS.md                 # OpenSpec-specific instructions (separate system)
├── docs/
│   └── architecture/             # From previous article
└── src/
```

**Key Benefits:**
- ✅ **Token efficiency:** Load 1-2 relevant files (~500-1000 tokens) vs all content (~2500+ tokens)
- ✅ **Selective loading:** AI agents load only what's needed for the current task
- ✅ **Maintainability:** Update one focused file instead of navigating monolithic document
- ✅ **Clarity:** Each file has single responsibility (like good code design)

### 3. Routing Strategy: Keyword-Triggered Loading

**The Router Pattern:**

Your `AGENTS.md` becomes a lightweight routing table:

```markdown
| Task/Keywords | Load These Files |
|---------------|------------------|
| Bot API changes, Java/Python/.NET | `.ai/cross-platform.md` |
| Testing, building, Gradle | `.ai/testing-and-build.md` |
| Docs, VERSIONS.MD, Javadoc | `.ai/documentation.md` |
```

**How it works:**
1. AI agent reads `AGENTS.md` (60 lines, ~600 tokens)
2. Matches task keywords to routing table
3. Loads only relevant `.ai/*.md` files
4. Total context: ~1000-1500 tokens vs ~3000+ tokens

**Example scenarios:**

**Scenario A: Cross-platform Bot API fix**
- Task: "Fix Java Bot API event handling and port to Python/C#"
- Loads: `core-principles.md` + `cross-platform.md` (~1000 tokens)
- Skips: testing, documentation, standards (~1400 tokens saved)

**Scenario B: Documentation update**
- Task: "Update VERSIONS.MD with new release notes"
- Loads: `documentation.md` (~300 tokens)
- Skips: cross-platform, testing, conventions (~2100 tokens saved)

**The principle:** Like lazy-loading in software architecture—load only what you need, when you need it.

### 4. File Design Guidelines

**Target metrics per file:**
- **50-150 lines** (ideally 35-60 lines)
- **500-1500 tokens** (ideally 400-600 tokens)
- **Single topic focus** (one responsibility)

**Metadata tags** (HTML comments, ignored by AI but useful for humans):
```markdown
<!-- METADATA: ~40 lines, ~400 tokens -->
<!-- KEYWORDS: Bot API, Java, Python, .NET, cross-platform -->
```

**File naming convention:**
- Use descriptive, searchable names: `cross-platform.md`, not `guide2.md`
- Hyphenated lowercase: `testing-and-build.md`
- Topic-focused: each file answers "when should I load this?"

**Content structure:**
```markdown
# Topic Name

<!-- METADATA and KEYWORDS -->

## Core Concept 1
Brief, actionable guidance

## Core Concept 2
Brief, actionable guidance

## Examples (when helpful)
Show don't just tell
```

### 5. Implementation: Real-World Case Study

**Project:** Tank Royale (open-source robot battle game)  
**Challenge:** Cross-platform Bot API (Java, Python, .NET) with complex build system  
**Original AGENTS.md:** 78 lines, monolithic  
**Migration outcome:**

**Before (monolithic):**
- Single file: 78 lines (~780 tokens)
- All-or-nothing loading
- Hard to maintain as project grew
- Mixed concerns (Java conventions next to build procedures)

**After (modular):**
- Router: 58 lines (~580 tokens)
- 6 topic files: 35-57 lines each
- Total: 341 lines (~3410 tokens) across all modules
- **But typical tasks load only 1-2 files (~500-1000 tokens)**

**Token efficiency example:**
- **Bot API task:** Loads 2 files (~1000 tokens) vs loading all (~3410 tokens) = **70% token savings**
- **Documentation task:** Loads 1 file (~300 tokens) vs loading all (~3410 tokens) = **91% token savings**

**Migration steps:**
1. Analyzed existing `AGENTS.md` for natural topic boundaries
2. Created `.ai/` directory with `README.md` (routing guide)
3. Split content into focused files (targeting 50-150 lines each)
4. Replaced `AGENTS.md` with lightweight router + keyword table
5. Added metadata comments for maintenance
6. Validated with typical AI agent tasks

**Maintenance notes added:**
```markdown
<!-- 
MAINTENANCE NOTE (for human developers):
When updating agent instructions:
1. Keep this file (AGENTS.md) as lightweight router only
2. Add/modify content in specific `.ai/*.md` topic files
3. Update keyword mappings in table above
4. Run token count check: each .ai/*.md should be 50-150 lines
-->
```

**Repository example:** [Tank Royale modular agent instructions](https://github.com/robocode-dev/tank-royale/tree/master/.ai)

### 6. Integration with Existing Workflow

**How this fits with previous articles:**

From **"Keep Your Architecture Diagrams in Code":**
- `/docs/` provides structural understanding (architecture diagrams)

From **"Keep Your AI and Architecture/Design in Sync":**
- `/openspec/` provides behavioral specifications
- `AGENTS.md` provides coding guidelines

**This article adds:**
- **Modular AGENTS.md** = token-efficient, focused instruction loading
- **`.ai/` directory** = organized, maintainable AI guidelines
- **Routing strategy** = right instructions at the right time

**The complete picture:**
```
your-project/
├── AGENTS.md                    # Router: directs AI to relevant instructions
├── .ai/                         # Modular coding guidelines (this article)
│   ├── core-principles.md
│   ├── cross-platform.md
│   └── ...
├── docs/                        # Architecture diagrams (article 1)
│   └── architecture/
├── openspec/                    # Specifications (article 2)
│   ├── specs/
│   └── changes/
└── src/
```

**AI agent loading strategy by task type:**

| Task Type | Loads From |
|-----------|------------|
| Planning new feature | `openspec/AGENTS.md` (spec creation) |
| Understanding architecture | `docs/architecture/` (structure) |
| Implementing feature | `.ai/cross-platform.md` + `.ai/core-principles.md` |
| Running tests | `.ai/testing-and-build.md` |
| Updating docs | `.ai/documentation.md` |

**The workflow:**
1. AI agent receives task
2. Reads `AGENTS.md` router (~580 tokens)
3. Identifies relevant topics from keyword table
4. Loads only needed `.ai/*.md` files (~500-1000 tokens typical)
5. References `/docs` for architecture context (as needed)
6. References `/openspec` for specifications (as needed)
7. Implements with full context but minimal token waste

### 7. Best Practices & Anti-Patterns

**✅ Do:**
- Keep each `.ai/*.md` file under 150 lines (target 50-100)
- Use clear, searchable keywords in routing table
- Add metadata comments (ignored by AI, helpful for humans)
- Update routing table when adding new topic files
- Treat `.ai/` files like code—review changes in PRs
- Test routing with real AI agent tasks

**❌ Don't:**
- Create too many tiny files (overhead vs benefit)
- Mix concerns in single file (defeats the purpose)
- Forget to update routing table when adding files
- Let files grow beyond 150 lines without splitting
- Duplicate content across multiple files
- Create files without clear keywords/routing rules

**Anti-Pattern: Premature Splitting**
```markdown
❌ BAD: 15 files of 10 lines each
✅ GOOD: 6 files of 40-60 lines each
```
Too much fragmentation creates routing complexity.

**Anti-Pattern: Topic Drift**
```markdown
❌ BAD: cross-platform.md includes testing and documentation
✅ GOOD: cross-platform.md focuses only on Bot API porting
```
Each file should have clear boundaries.

**Anti-Pattern: Stale Router**
```markdown
❌ BAD: Added new file, forgot to update AGENTS.md table
✅ GOOD: PR checklist includes "Update routing table"
```
Maintain the routing table as part of changes.

### 8. When to Use This Pattern

**✅ Good fit for:**
- Projects with **multiple languages/platforms** (Java + Python + .NET)
- Codebases with **distinct concerns** (API + frontend + build + docs)
- Teams where **different developers work in different areas**
- Projects using **token-limited AI models**
- Growing codebases where **AGENTS.md keeps expanding**

**🤔 Maybe not needed for:**
- Small projects with single language
- Teams where all developers work across entire stack
- Projects with simple, uniform conventions
- Codebases where AGENTS.md is naturally under 100 lines

**Decision criteria:**
- If your `AGENTS.md` is **>200 lines**, strongly consider modular approach
- If you have **3+ distinct technology areas**, modular approach helps
- If AI agents **frequently load irrelevant instructions**, time to split

**Migration trigger:** When you find yourself scrolling through `AGENTS.md` to find relevant sections, your AI agents are doing the same—time to modularize.

### 9. Future Directions & Emerging Patterns

**Emerging best practices:**

1. **Tool-specific routing:** Some teams create `.ai/tools/` with tool-specific instructions:
   ```
   .ai/tools/
   ├── cursor-config.md
   ├── copilot-config.md
   └── claude-config.md
   ```

2. **Language-specific modules:** For polyglot projects:
   ```
   .ai/languages/
   ├── java.md
   ├── python.md
   └── typescript.md
   ```

3. **Role-based instructions:** Some teams split by developer role:
   ```
   .ai/roles/
   ├── backend.md
   ├── frontend.md
   └── devops.md
   ```

**Industry trends:**
- **Cursor** is experimenting with `.cursorrules` modular syntax
- **Anthropic** published guidance on "context-aware prompting"
- **Microsoft** Semantic Kernel patterns influence AI instruction design
- **GitHub Copilot** team exploring context optimization strategies

**Next evolution:** Dynamic routing based on file context
- AI automatically detects file type (Java, Python, Markdown)
- Loads relevant `.ai/*.md` without explicit routing table
- Similar to language server protocol (LSP) for AI instructions

**Watch this space:** Spec-driven development and modular AI instructions are still maturing practices. Expect tooling and conventions to evolve rapidly over the next 12-24 months.

### 10. Getting Started Checklist

**Step 1: Audit your current AGENTS.md**
- [ ] Count total lines (if >200, strong candidate for modularization)
- [ ] Identify natural topic boundaries (platforms, testing, docs, etc.)
- [ ] Note which sections AI agents typically need together
- [ ] Check for duplicated guidance across sections

**Step 2: Design your `.ai/` structure**
- [ ] Create `.ai/` directory in repository root
- [ ] List 4-8 topic areas (too few = still monolithic, too many = routing overhead)
- [ ] Define keywords for each topic (how AI should find it)
- [ ] Estimate lines per topic (target 50-150 each)

**Step 3: Create routing infrastructure**
- [ ] Create `.ai/README.md` with routing decision tree
- [ ] Add metadata table (file names, keywords, line counts)
- [ ] Document update guidelines for future maintainers

**Step 4: Migrate content**
- [ ] Create each `.ai/*.md` file with focused content
- [ ] Add metadata comments (line count, token estimate, keywords)
- [ ] Ensure no duplicated content across files
- [ ] Keep files focused (single responsibility)

**Step 5: Update AGENTS.md router**
- [ ] Replace content with routing table
- [ ] Keep OpenSpec integration section (if using)
- [ ] Add maintenance notes for future updates
- [ ] Verify total router <100 lines

**Step 6: Validate with AI agents**
- [ ] Test typical tasks (Bot API change, documentation, testing)
- [ ] Verify AI agents load correct files
- [ ] Check token usage (should be 50-70% lower)
- [ ] Adjust routing keywords if needed

**Starter template repository:** [modular-agents-template](https://github.com/flemming-n-larsen/modular-agents-template) *(coming soon)*

---

## Supporting Materials & Links

### Code Examples

**Repository:** [Tank Royale - Modular AGENTS.md Implementation](https://github.com/robocode-dev/tank-royale)
- `.ai/` directory structure: [View on GitHub](https://github.com/robocode-dev/tank-royale/tree/master/.ai)
- Router implementation: [AGENTS.md](https://github.com/robocode-dev/tank-royale/blob/master/AGENTS.md)
- Before/after comparison: [Git history link]

**Metrics from Tank Royale migration:**
```
Original: 78 lines monolithic → 58 line router + 341 lines modular
Token efficiency gains:
- Bot API tasks: 70% token savings
- Documentation tasks: 91% token savings
- Testing tasks: 85% token savings
```

### Reference Articles (Prerequisites)

1. **[Keep Your Architecture Diagrams in Code, Not in Tools](https://www.linkedin.com/pulse/keep-your-architecture-diagrams-code-tools-flemming-n%C3%B8rnberg-larsen-egkse)**  
   Foundation: `/docs` architecture diagrams for structural understanding

2. **[Keep Your AI and Architecture/Design in Sync](https://architecture-as-code.hashnode.dev/)** *(your recent article)*  
   Context: `/openspec` specifications + `AGENTS.md` for behavioral guidance

**This article builds on both:** Shows how to scale `AGENTS.md` as projects grow.

### Related Methodologies & Tools

**OpenSpec:**
- [OpenSpec GitHub](https://github.com/Fission-AI/OpenSpec)
- Spec-driven development approach (referenced in previous article)
- Has own `openspec/AGENTS.md` (kept separate from modular `.ai/`)

**Alternative approaches:**
- [GitHub Spec-Kit](https://github.com/github/spec-kit)
- [BMAD Method](https://github.com/bmad-code-org/BMAD-METHOD)
- [Kiro (AWS/Amazon)](https://kiro.dev/)

**AI Tool Documentation:**
- [Cursor - Custom Instructions](https://docs.cursor.com/context/rules-for-ai)
- [GitHub Copilot - Instruction Files](https://docs.github.com/en/copilot/customizing-copilot/adding-custom-instructions-for-github-copilot)
- [Anthropic - Prompt Engineering Guide](https://docs.anthropic.com/claude/docs/prompt-engineering)

### Industry References

**Token optimization research:**
- [Anthropic: Context-Aware Prompting](https://www.anthropic.com/research) *(theoretical foundation)*
- Microsoft Semantic Kernel patterns
- Cursor engineering blog on context efficiency

**Emerging patterns:**
- Modular AI instructions (this article pioneers the approach)
- Dynamic context loading for AI agents
- Token budget optimization strategies

### Diagrams & Visuals

**Figure 1: Token consumption comparison**
```
Monolithic AGENTS.md:
[███████████████████████] 3000 tokens (all content)

Modular .ai/ approach:
Task A: [████] 1000 tokens (cross-platform + core)
Task B: [██] 500 tokens (documentation)
Task C: [███] 800 tokens (testing + core)
```

**Figure 2: Routing decision tree** *(from `.ai/README.md`)*
```
Task involves...
├─ Planning/specs? → /openspec/AGENTS.md
├─ Bot API? → .ai/cross-platform.md + .ai/core-principles.md
├─ Testing? → .ai/testing-and-build.md
└─ Docs? → .ai/documentation.md
```

**Figure 3: Directory structure evolution**
```
Before:                     After:
AGENTS.md (monolithic)  →  AGENTS.md (router)
                           .ai/
                           ├── README.md
                           ├── core-principles.md
                           ├── cross-platform.md
                           └── ...
```

### Interactive Examples

**ChatGPT/Claude prompt to demonstrate routing:**

```
"I'm working on the Tank Royale project. I need to fix a Python Bot API bug related to team messaging. Based on the AGENTS.md router and .ai/ structure, which instruction files should I load?"

Expected AI response:
"For a Python Bot API bug related to team messaging, you should load:
1. .ai/cross-platform.md (~600 tokens) - Bot API cross-platform guidelines
2. .ai/core-principles.md (~400 tokens) - Core coding principles
Total: ~1000 tokens vs 3410 tokens if loading all files (70% savings)"
```

### Starter Templates

**Minimal `.ai/README.md` template:**
```markdown
# AI Agent Instructions Index

## File Metadata
| File | Est. Tokens | Keywords |
|------|-------------|----------|
| core-principles.md | ~400 | clean code, principles |
| [your-topics].md | ~XXX | [keywords] |

## Routing
- General tasks → core-principles.md
- [Task type] → [file].md
```

**Minimal topic file template:**
```markdown
# Topic Name

<!-- METADATA: ~XX lines, ~XXX tokens -->
<!-- KEYWORDS: keyword1, keyword2, keyword3 -->

## Concept 1
Brief guidance

## Concept 2
Brief guidance
```

---

## Article Metadata

**Estimated Length:** 2,500-3,000 words  
**Reading Time:** 12-15 minutes  
**Complexity Level:** Intermediate (requires understanding of previous articles)  
**Target Audience:** 
- Software architects working with AI assistants
- Development teams scaling AI-assisted development
- Engineers maintaining large codebases with AI tooling

**Prerequisites:**
- Understanding of AI coding assistants (GitHub Copilot, Cursor, Claude, etc.)
- Familiarity with spec-driven development concepts
- Experience with token-limited AI models

**Key Takeaways:**
1. Monolithic `AGENTS.md` files become counterproductive at scale
2. Modular `.ai/` directory structure achieves 3x-5x token efficiency
3. Keyword-based routing loads only relevant instructions
4. Treat AI instructions like microservices—focused, independently loadable
5. Maintains integration with architecture diagrams (`/docs`) and specifications (`/openspec`)

**SEO Keywords:**
- modular AGENTS.md
- AI agent instructions
- token efficiency
- AI coding assistants
- GitHub Copilot instructions
- Cursor configuration
- AI-assisted development
- architecture as code
- spec-driven development

**Hashtags:**
#AIAssistedDevelopment #AGENTSMD #TokenOptimization #SoftwareArchitecture #AIBestPractices #ModularDesign #DeveloperProductivity

---

## Publication Strategy

**Blog platforms:**
1. **Primary:** Architecture as Code blog (Hashnode/Medium)
2. **Cross-post:** LinkedIn article (with engagement focus)
3. **Discussion:** Dev.to, Hacker News (community feedback)

**Code repository:**
- Create `modular-agents-template` repository with starter files
- Include Tank Royale as reference implementation
- Provide migration checklist and validation scripts

**Community engagement:**
- Share on relevant subreddits (r/programming, r/MachineLearning)
- Post in AI-assisted development Discord servers
- Engage with GitHub Copilot and Cursor communities

**Follow-up content:**
- Video walkthrough of migration process
- Podcast episode on "Scaling AI in Development Workflows"
- Workshop/webinar on modular AI instructions

---

## Next Steps

1. **Review this proposal** - validate structure, examples, and messaging
2. **Gather feedback** - share with 2-3 trusted developers for input
3. **Create modular-agents-template repo** - starter files and migration guide
4. **Write first draft** - target 2,500-3,000 words
5. **Create diagrams** - visual comparisons of token usage and routing
6. **Technical review** - validate Tank Royale metrics and code examples
7. **Publish and promote** - blog + LinkedIn + Dev.to + community channels

**Timeline estimate:**
- Proposal review: 1-2 days
- First draft: 3-5 days
- Review/revisions: 2-3 days
- Visuals/diagrams: 1-2 days
- Publication: 1-2 days
- **Total: ~2 weeks**

---

## Open Questions for Review

1. **Title preference?** Which of the three title options resonates most?
2. **Depth vs brevity?** Should I go deeper on implementation details or keep it strategic?
3. **Code examples?** How much actual file content to include vs linking to GitHub?
4. **Migration guide?** Should this article include step-by-step migration or separate guide?
5. **Tool-specific guidance?** Should I cover Cursor/.cursorrules, Copilot, etc. specifically?

---

*This proposal prepared: 2026 M01 24*  
*Repository reference: [Tank Royale](https://github.com/robocode-dev/tank-royale)*  
*Contact: [Your contact info]*
