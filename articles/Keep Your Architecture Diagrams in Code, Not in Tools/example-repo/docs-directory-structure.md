# Docs Directory Structure - Modular, Document-Driven Architecture

This is the recommended directory structure for organizing architecture diagrams and documentation in your monorepo, following the modular, hyperlinked approach (not linear/chronological).

```
docs/
├── README.md
│   └── Entry point to all documentation
│       Links to: architecture overview, requirements, user stories, setup guides
│
├── requirements.md
│   └── Functional and non-functional requirements
│       - Business requirements
│       - Quality attributes (performance, scalability, security)
│       - Constraints and assumptions
│
├── architecture/
│   │
│   ├── README.md
│   │   └── Architecture Overview (Big Picture)
│   │       - System architecture diagram (all entities + relationships)
│   │       - High-level explanation
│   │       - Links to individual domain entities
│   │       - Links to workflow/flow diagrams
│   │       - Links to deployment/infrastructure (if applicable)
│   │
│   ├── domain/
│   │   │
│   │   ├── customer.md
│   │   │   └── Customer entity
│   │   │       - Business logic explanation
│   │   │       - Class diagram (Customer only, no relations)
│   │   │       - Database schema (ER diagram for CUSTOMER table)
│   │   │       - Fields and attributes
│   │   │       - Relationships to other entities (with links)
│   │   │
│   │   ├── order.md
│   │   │   └── Order entity
│   │   │       - Business logic explanation
│   │   │       - Class diagram (Order only, no relations)
│   │   │       - Database schema (ER diagram for ORDER table)
│   │   │       - Fields and attributes
│   │   │       - Relationships to other entities (with links)
│   │   │
│   │   ├── order-item.md
│   │   │   └── OrderItem entity
│   │   │       - Business logic explanation
│   │   │       - Class diagram (OrderItem only, no relations)
│   │   │       - Database schema (ER diagram for ORDER_ITEM table)
│   │   │       - Fields and attributes
│   │   │       - Relationships to other entities (with links)
│   │   │
│   │   ├── product.md
│   │   │   └── Product entity
│   │   │       - Business logic explanation
│   │   │       - Class diagram (Product only, no relations)
│   │   │       - Database schema (ER diagram for PRODUCT table)
│   │   │       - Fields and attributes
│   │   │       - Relationships to other entities (with links)
│   │   │
│   │   └── payment.md
│   │       └── Payment entity
│   │           - Business logic explanation
│   │           - Class diagram (Payment only, no relations)
│   │           - Database schema (ER diagram for PAYMENT table)
│   │           - Fields and attributes
│   │           - Relationships to other entities (with links)
│   │
│   ├── flows/
│   │   │
│   │   ├── create-order.md
│   │   │   └── Create Order Flow
│   │   │       - High-level description
│   │   │       - Sequence diagram (request flow through services)
│   │   │       - Step-by-step explanation
│   │   │       - Error handling considerations
│   │   │       - References to involved entities (with links)
│   │   │
│   │   ├── payment-processing.md
│   │   │   └── Payment Processing Flow
│   │   │       - High-level description
│   │   │       - Sequence diagram (payment service interactions)
│   │   │       - Step-by-step explanation
│   │   │       - Error handling and rollback strategy
│   │   │       - References to involved entities (with links)
│   │   │
│   │   └── inventory-management.md
│   │       └── Inventory Management Flow
│   │           - High-level description
│   │           - Sequence diagram (stock updates)
│   │           - Step-by-step explanation
│   │           - Concurrency considerations
│   │           - References to involved entities (with links)
│   │
│   └── decisions/
│       │
│       └── adr-0001-uuid-primary-keys.md
│           └── Architecture Decision Record (ADR)
│               - Decision: Use UUIDs for all primary keys
│               - Context: Distributed systems, horizontal scaling
│               - Consequences: Slightly larger keys, easier distributed ID generation
│               - Related decisions (with links)
│
├── user-stories/
│   │
│   ├── README.md
│   │   └── User Stories Index
│   │       Lists all user stories with links
│   │
│   ├── story-001-customer-registration.md
│   │   └── User Story: Customer Registration
│   │       - As a user, I want to...
│   │       - Acceptance criteria
│   │       - Related entities (with links)
│   │       - Related flows (with links)
│   │
│   ├── story-002-place-order.md
│   │   └── User Story: Place Order
│   │       - As a customer, I want to...
│   │       - Acceptance criteria
│   │       - Related entities (with links)
│   │       - Related flows (with links)
│   │
│   └── story-003-manage-inventory.md
│       └── User Story: Manage Inventory
│           - As an admin, I want to...
│           - Acceptance criteria
│           - Related entities (with links)
│           - Related flows (with links)
│
└── api/
    │
    └── README.md
        └── API Documentation (Optional)
            - API endpoints overview
            - Links to endpoint specifications
            - General error handling patterns
            - Authentication/Authorization
```

---

## Navigation Pattern (Hyperlinked Structure)

The documentation is **NOT** meant to be read linearly. Instead:

1. **Start at `docs/README.md`** — Overview of what's available
2. **Navigate based on your needs:**
   - Interested in the Customer entity? → `docs/architecture/domain/customer.md`
   - Want to understand order creation? → `docs/architecture/flows/create-order.md`
   - Need user stories? → `docs/user-stories/`
   - Want requirements? → `docs/requirements.md`
3. **Each file is self-contained** with its own diagrams and explanations
4. **Cross-link freely** using relative Markdown links: `[Customer](../domain/customer.md)`

---

## Key Principles

- **One file per concept:** Each entity, flow, or story gets its own page
- **Self-contained:** Each page has enough context to stand alone
- **Hyperlinked:** Navigate between related pages via relative Markdown links
- **DRY:** Diagrams defined once, referenced from multiple pages via links
- **Modular:** Add new entities/flows without restructuring existing docs
- **Version controlled:** Each file can be reviewed, diffed, and tracked independently
- **AI-friendly:** Agents can help improve individual files without touching entire architecture
- **Export ready:** Export individual pages or aggregate views (PNG/SVG/Confluence)

---

## Example Markdown Links

```markdown
# In docs/architecture/domain/order.md

See the [Customer](customer.md) entity for more details.

This order flows through the [Create Order Flow](../flows/create-order.md).

Related user story: [Place Order](../../user-stories/story-002-place-order.md)
```

---

## For Your Article

When presenting this to your readers:

1. **Show the full tree structure** (as above)
2. **Emphasize the hyperlinked nature** — readers navigate based on their needs, not a linear order
3. **Show example files** from `docs/architecture/domain/` and `docs/architecture/flows/`
4. **Contrast with Confluence:** Old approach = top-to-bottom reading order; New approach = navigate what you need
5. **Show cross-linking** via relative Markdown paths
6. **Emphasize benefits:** Modular, maintainable, AI-friendly, version controlled, no sync issues


