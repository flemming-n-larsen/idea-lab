# Change Specification: Customer Loyalty Points System

**Status:** Active  
**Created:** 2026-01-15  
**AI Agent:** Claude Opus (Planning)  
**Implementation:** GitHub Copilot (Execution)

## Overview

Add a customer loyalty points system to the existing e-commerce platform. Customers earn points for purchases and can redeem them for discounts on future orders.

## Requirements

### Core Functionality
- Customers earn 1 point per dollar spent on confirmed orders
- Points can be redeemed for order discounts (1 point = $0.01 discount)
- Points expire 12 months after earning date
- Points are awarded only when order status reaches "delivered"
- Points are deducted immediately when redeemed during checkout

### Business Rules

#### Point Earning
- Points are calculated on order total after taxes and shipping
- Points are NOT earned on discounted amounts (if points were used)
- Points are awarded per order completion, not per payment
- Minimum order value for point earning: $5.00
- Maximum points per order: 500 points

#### Point Redemption
- Minimum redemption: 100 points ($1.00 discount)
- Maximum redemption per order: 50% of order total
- Points must be redeemed at checkout, not retroactively
- Partial point redemption is allowed
- Redeemed points cannot be refunded if order is cancelled

#### Point Expiration
- Points expire exactly 12 months after earning date
- Expiration occurs daily at midnight UTC
- Customers are notified 30 days before expiration
- Expired points cannot be recovered

### Edge Cases

#### Refunds and Returns
- If a delivered order is returned/refunded, earned points are deducted
- If customer has insufficient points for deduction, account goes negative
- Negative point balances must be resolved before earning new points
- Redeemed points on returned orders are restored to customer

#### Account Management
- Points are transferred if customer accounts are merged
- Points are permanently lost if account is deleted
- Suspended accounts cannot earn or redeem points

#### System Constraints
- Point balance cannot exceed 50,000 points per customer
- Point transactions are immutable once created (audit trail)
- All point operations must be atomic with order operations

## Data Model

### New Entity: LoyaltyPoints
```
LoyaltyPoints {
  id: uuid (PK)
  customerId: uuid (FK -> Customer.id)
  orderId: uuid (FK -> Order.id, nullable)
  pointsEarned: integer (positive for earned, negative for redeemed)
  transactionType: enum ['EARNED', 'REDEEMED', 'EXPIRED', 'REFUND_ADJUSTMENT']
  expirationDate: datetime (nullable, only for EARNED points)
  createdAt: datetime
  description: string
}
```

### Customer Entity Updates
```
Customer {
  // ...existing fields...
  currentPointBalance: integer (computed field)
  totalPointsEarned: integer (lifetime total)
  totalPointsRedeemed: integer (lifetime total)
}
```

### Order Entity Updates
```
Order {
  // ...existing fields...
  pointsEarned: integer (calculated at delivery)
  pointsRedeemed: integer (applied at checkout)
  pointsDiscountAmount: decimal (dollar value of redeemed points)
}
```

## Implementation Tasks

### Phase 1: Core Infrastructure
1. Create LoyaltyPoints entity with migrations
2. Add loyalty-related fields to Customer and Order entities
3. Create point calculation service
4. Create point expiration background job

### Phase 2: Point Earning
1. Add point earning logic to order delivery process
2. Create point earning notification system
3. Add point history tracking
4. Create customer point balance API endpoints

### Phase 3: Point Redemption
1. Modify checkout process to allow point redemption
2. Add point redemption validation logic
3. Update order total calculations
4. Add point redemption UI components

### Phase 4: Point Management
1. Create point expiration notification system
2. Add customer point history dashboard
3. Implement point transfer functionality
4. Add admin point management tools

## Integration Points

### Existing Architecture
- **Order State Machine:** Point earning triggers on "delivered" state
- **Payment Processing:** Point redemption affects order total calculation
- **Customer Management:** Point balance becomes part of customer profile
- **Notification System:** Point expiration and earning notifications

### AI Implementation Guidelines
- Use GitHub Copilot Plan mode to break down each phase into individual tasks
- Reference existing Order and Customer entity patterns for consistency
- Follow existing validation patterns for business rule implementation
- Use existing notification patterns for point-related communications

## Testing Strategy

### Unit Tests
- Point calculation algorithms
- Expiration date calculations
- Business rule validation
- Edge case handling (refunds, account deletion)

### Integration Tests
- End-to-end point earning flow
- Point redemption during checkout
- Point expiration process
- Cross-entity consistency checks

## Success Criteria

- [ ] Customers can earn points on delivered orders
- [ ] Points correctly expire after 12 months
- [ ] Point redemption reduces order total at checkout
- [ ] All business rules are enforced with appropriate error messages
- [ ] Point transactions maintain audit trail
- [ ] System performance is not degraded by point calculations

## Questions for Review

1. Should points round to nearest integer or truncate decimal values?
2. How should we handle timezone differences for expiration calculations?
3. Should we allow partial point redemption or require full 100-point increments?
4. What happens to points if a customer's account is temporarily suspended?
5. Should we implement point multipliers for special promotions in this phase?

**Next Steps:** Review this specification with stakeholders, then proceed to Phase 1 implementation using GitHub Copilot for task execution.
