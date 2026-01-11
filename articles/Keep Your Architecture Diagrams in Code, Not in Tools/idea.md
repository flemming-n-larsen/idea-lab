Two articles:

1st Article: Keep Your Architecture Diagrams in Code, Not in Tools
==================================================================

- My intention with this article is to advocate that architecture diagrams must live in your monorepo alongside source
  code, not in expensive proprietary tools. This approach makes collaboration with AI agents better, keeps diagrams
  versioned with code, and ensures a single source of truth. Especially when combined with spec-driven development
  (next article).
- This article is the foundation for the next article about spec-driven development using AI agents.

- Single Repository + Architecture as Code
    - Monorepo (short for "monolithic repository") (https://en.wikipedia.org/wiki/Monorepo)
        - Monorepo philosophy: Single Source of Truth (SSOT)
        - The monorepo is the canonical truth of the system
        - Anything outside it is a derivative artifact

    - Architecture as Code (AaC) - My approach:
        - Architecture diagrams must live WITH the code, not beside it
        - Take advantage of what Source code management (SCM) like GitHub and GitLab already provide + most modern IDEs
          like VSCode and IntelliJ provide support for Markdown and Mermaid
        - We don't need expensive tools to create architecture diagrams
        - Write architecture diagrams as plain text Mermaid in Markdown files
        - Let the IDE view the diagrams natively, or use https://mermaid.live for preview
        - Diagrams are versioned with code, reviewable in PRs, diffable in Git
        - AI agents can understand, review, and help improve Markdown + Mermaid diagrams

    - Export flexibility (diagrams are derivatives, not the source):
        - Mermaid → PNG/SVG (for docs, presentations, PRs)
        - Mermaid → Confluence (manual or AI-assisted conversion)
        - Mermaid → draw.io (via Mermaid Live or export tools)
        - C4 Context diagrams via Structurizr (optional advanced approach)
2nd article:
===========
Builds on top of 1st article.

- spec driven development
- specs
- AI guidelines (AGENTS.md)
- OpenSpec
