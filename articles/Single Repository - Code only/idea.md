Two articles:

1st Article:
===========
- Single Repository
  - Code is everything mindset
  - Single repository
    - Single source of truth. Everything is in one place and should never exist in multiple places or an external location unless it is exported.
    - Treat your repository as you would treat a software system with internal and external. External stuff must be exported. For example, export to Confluence, if you need to.
  - Source code, Documentation in Markdown, diagrams in Mermaid, complex illustrations in SVG
  - GitHub, GitLab etc.
  - Human + AI assisted
  - Avoid binaries. Those should only be generated like class files
    - Exception is screenshorts, photos, and image-generated images
  - If possible, programming language ignostic, e.g., schemas like JSON schema, API first approach using code-generators
  - Important. The architecture must be documented and should live and with with the code and the other way around. 

- Is there a term for all of this?

2nd article:
===========
Builds on top of 1st article.
- spec driven development

- specs
- AI guidelines (AGENTS.md). Redirect to this from ./github/copilot-instructions.md and CLAUDE.md
- OpenSpec
