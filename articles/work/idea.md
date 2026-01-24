I should like an "triangle" illustration with these in the corners:
- Human (developers, architects, product owners etc.)
- AI Agents
- Documentation (design, architecture etc.)

And the output (code) would be in the middle

All of those are liked like:

Humans <--> Documentation: Keeping the documentation up-to-date and relevant
AI <--> Documentation: Giving AI access to up-to-date documentation to make right decisions
Humans <--> AI: How AI and Humans supplement each other. AI code, debug, review, and humans can the same

Humans <--> Code: Humans must be able to read, understand, create and maintain the code
AI <--> Code: AI must be able to do the same here as humans. But we humans expect it to work the same way as we do. Perhaps even better (expectations from most humans)

Documentation <--> Code: Documentation and code should stay in sync

AI is used for automation, sparring, reviewing, and trivial stuff.
Humans should do the more fun and creative work, which is both in documentation as well as in code

I think we need to use SVG or png for the illustration.


---------
This is a propose from Le Chat AI:

It is a way to frame your approach to modern software development. It ties your previous articles together and sets the stage for future work. Here’s how you could structure it, including a suggestion for the illustration and key messages:

Title Suggestion:
"The Human-AI-Documentation Triangle: A Mindset for Modern Software Development"

Core Message:
The triangle illustrates three equal partners (Humans, AI, Documentation) working together to produce high-quality, maintainable code. Each corner has a unique role, but the real power comes from their interactions and synergy.

The Triangle Illustration
You can describe it like this (or create it using Mermaid!):
mermaid
Copy

graph TD
A[Humans] -->|Create, Review, Maintain| B[Code]
B -->|Sync, Reflect, Validate| A
A -->|Update, Clarify, Communicate| C[Documentation]
C -->|Guide, Inform, Constrain| A
C -->|Read, Parse, Learn| D[AI Agents]
D -->|Generate, Review, Automate| B
D -->|Assist, Spar, Explain| A
B -->|Reflect, Validate, Inspire| C

Visual Notes:

Place Code in the center.
Label the edges with the interactions you described (e.g., "Humans <--> Documentation: Keep up-to-date").
Use arrows to show the bidirectional flow between all three corners.

Key Sections for the Article:
1. Introduction: Why This Mindset?

Traditional software development often treats documentation as an afterthought and AI as a tool, not a collaborator.
Your mindset: All three corners are equal partners. Documentation is not just for humans—it’s for AI too. AI is not just a code generator—it’s a sparring partner.
Goal: Reduce manual toil, improve consistency, and free humans for creative work.
2. The Three Corners

Humans: Developers, architects, product owners.

Role: Creative problem-solving, design decisions, reviewing AI output, maintaining documentation.
Strengths: Context, intuition, empathy, innovation.

AI Agents: LLMs, coding assistants, automation tools.

Role: Automation, code generation, reviews, trivial tasks.
Strengths: Speed, scalability, pattern recognition, tirelessness.

Documentation: Architecture diagrams, specs, decisions, constraints.

Role: Single source of truth, bridge between humans and AI, enforces consistency.
Strengths: Clarity, longevity, shareability.

3. The Interactions

Humans ↔ Documentation:

Humans create and maintain documentation (e.g., Mermaid diagrams, OpenSpec).
Documentation guides humans in understanding the system.
Your approach: Documentation lives in the repo (Markdown + Mermaid), so it’s always in sync with code.

AI ↔ Documentation:

AI reads documentation to understand the system (e.g., OpenSpec for constraints, Mermaid for structure).
AI updates documentation (e.g., generating diagrams from code, drafting specs).
Your approach: Plain-text, AI-readable formats (no proprietary tools).

Humans ↔ AI:

Humans guide AI with clear prompts and constraints.
AI assists humans with code, reviews, and suggestions.
Your approach: Use AI for automation and sparring, but humans make final decisions.

Humans ↔ Code:

Humans write, review, and refactor code.
Code must be readable and maintainable for humans.

AI ↔ Code:

AI generates, reviews, and debugs code.
Expectation: AI should work at least as well as humans (and ideally better for repetitive tasks).

Documentation ↔ Code:

Documentation describes the code (e.g., architecture diagrams, specs).
Code validates the documentation (e.g., tests, ArchUnit checks).
Your approach: Keep them in sync via version control and automation.

4. The Output: Code

Code is the tangible result of this collaboration.
It must be:

Human-readable (clean, well-structured, documented).
AI-readable (consistent, patterned, well-documented).
Self-validating (tests, linting, ArchUnit checks).

Example: Your architecture-as-code-example repo shows this in action.
5. How This Plays Out in Practice

Example 1: Adding a Feature

Human writes a spec (OpenSpec).
AI generates tasks and code from the spec.
Human reviews and refines the output.
Documentation is updated automatically (e.g., Mermaid diagrams regenerated).

Example 2: Debugging

Human identifies an issue.
AI suggests fixes and updates documentation if needed.
Human verifies the fix and merges.

Example 3: Onboarding

New team members read documentation to understand the system.
AI answers questions based on the docs.
Humans clarify and improve docs as they work.

6. Why This Works

Humans focus on creativity: Design, architecture, innovation.
AI handles repetition: Boilerplate, reviews, trivial tasks.
Documentation stays alive: Always in sync with code, always useful.
Code quality improves: Fewer bugs, better consistency, faster iteration.
7. Common Pitfalls (and How to Avoid Them)

Pitfall 1: Documentation becomes outdated.

Solution: Treat docs as code—version it, review it, automate updates.

Pitfall 2: AI generates low-quality code.

Solution: Give AI clear constraints (e.g., OpenSpec, AGENTS.md).

Pitfall 3: Humans resist AI.

Solution: Start small—use AI for reviews or trivial tasks, then scale.

8. The Future

As AI improves, the triangle becomes stronger.
Goal: Humans spend less time on maintenance and more on design and innovation.
Next steps: More automation (e.g., ArchUnit for enforcement, AI for doc updates).
9. Call to Action

Try this mindset on a small project.
Start with one corner (e.g., move docs into the repo).
Experiment with AI tools (e.g., GitHub Copilot, OpenSpec).
Share your results!

Why This Article Works:

Ties Your Previous Articles Together:

Links to your architecture-as-code and spec-driven development articles.
Acts as an introduction for future readers.

Simple but Powerful:

The triangle is an easy-to-remember mental model.
It’s technical but accessible—appeals to developers, architects, and managers.

Actionable:

Readers can start small (e.g., move docs to Markdown) and scale.

Visual:

The Mermaid diagram makes it easy to share and reference.
