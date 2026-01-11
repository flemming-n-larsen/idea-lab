Two articles:

1st Article:
===========

- My intention with this article is to advocate that taking advantage of AI tools like GitHub Copilot, Claude Code etc.
  gets better when we have a monorepo for the entire software system, and when we have everything as code. It is not
  a requirement, but it is both good practice, and makes the AI tools work better. Especially when we apply spec-driven
  development (next article)
- This article is the foundation for the next article about spec-driven development using AI tools.

- Single Repository
    - “Everything as Code” (EaC) mindset
        - `Understanding Everything as Code: A Taxonomy and Conceptual Model` (https://arxiv.org/pdf/2507.05100):
            - The paper defines Everything as Code (EaC) as an emerging paradigm where all aspects of modern software
              systems are codified in code, not just infrastructure.
        - EaC aims to codify all aspects of modern software systems, not just infrastructure.
    - Monorepo (short for “monolithic repository”) (https://en.wikipedia.org/wiki/Monorepo)
        - Monorepo philosophy
        - Single Source of Truth (SSOT)
        - DRY (Don’t Repeat Yourself)
        - In a monorepo‑centric organization, these ideas merge into a single worldview:
            - The monorepo is the canonical truth of the system.
            - Anything outside it is a derivative artifact.

  We already know how to build a monorepo for code.
  But how to build a monorepo for everything else?
    - Infrastructure as Code (IaC) (https://en.wikipedia.org/wiki/Infrastructure_as_Code)
    - Documentation as Code (DaC) (https://www.thoughtworks.com/insights/blog/documentation-as-code)
    - Design as Code (DeaC) (https://martinfowler.com/bliki/DesignAsCode.html)
    - Test as Code (TaC) (https://martinfowler.com/bliki/TestAsCode.html)
    - Security as Code (SaC) (https://www.contrastsecurity.com/security-influencers/security-as-code)
    - Policy as Code (PaC) (https://www.openpolicyagent.org/docs/latest/policy-as-code/)
    - AI Guidelines as Code (AGaC) (new term?)
        - Guidelines for using AI tools like GitHub Copilot, OpenAI, Claude, etc
    - Architecture as Code (AaC) - My approach:
        - Take advantage of what Source code management (SCM) like GitHub and GitLab already provide + most modern IDEs
          like VSCode and IntelliJ provide support for Markdown and Mermaid.
        - Extensions for Mermaid might be required for some SCMs and IDEs
        - Architecture decision records (ADRs) (https://adr.github.io/)
        - My Approach: Architecture diagrams as code using Markdown and Mermaid

    - We don't need to use expensive tools to create architecture diagrams. We write "plain text" as mermaid and let the
      IDE view the diagrams or use https://mermaid.live
    - Use SVG for vector graphics that is not applicable for Mermaid which is designed for diagrams only. SVG is a good
      choice for static diagrams that are not interactive. You can use https://app.diagrams.net/ to create SVG diagrams
      and save them as SVG.

    - Human + AI assisted
    - Avoid binaries. Those should only be generated like class files
        - Exception is screenshorts, photos, and image-generated images
    - If possible, programming language ignostic, e.g., schemas like JSON schema, API first approach using
      code-generators
    - Important. The architecture must be documented and should live and with with the code and the other way around.
    - Separate concerns:
        - Code
        - Tests
        - Documentation + Diagrams
        - Specifications
        - AI guidelines

- Is there a term for all of this?

2nd article:
===========
Builds on top of 1st article.

- spec driven development

- specs
- AI guidelines (AGENTS.md). Redirect to this from ./github/copilot-instructions.md and CLAUDE.md
- OpenSpec
