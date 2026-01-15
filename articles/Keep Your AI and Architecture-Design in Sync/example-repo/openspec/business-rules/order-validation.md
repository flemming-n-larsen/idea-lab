# Business Rules: Order Validation

**Domain:** Order Management  
**Last Updated:** 2026-01-15  
**Related Entities:** Order, OrderItem, Product, Customer

## Core Validation Rules

### Order Creation Validation

#### Customer Validation
- Customer must exist and be active
- Customer account must not be suspended
- Customer must have valid contact information (email)

#### Product Validation
- All ordered products must exist and be active
- Product quantities must be positive integers
- Product prices must match current catalog prices
- Out-of-stock products cannot be ordered (unless pre-order enabled)

#### Order Total Validation
- Order total must be at least $5.00 (minimum order value)
- Order total cannot exceed $50,000 (fraud prevention)
- Tax calculation must be applied based on shipping address
- Shipping cost must be calculated based on weight and destination

### Order State Transition Rules

#### Pending → Confirmed
- Payment must be authorized successfully  
- All ordered items must have sufficient inventory
- Customer billing address must be validated
- Order total must match payment amount

#### Confirmed → Shipped
- Payment must be captured (not just authorized)
- All items must be picked and packed
- Shipping label must be generated
- Customer must be notified of shipment

#### Shipped → Delivered
- Package must be marked as delivered by carrier
- Delivery confirmation must be recorded
- Customer notification must be sent
- Loyalty points must be awarded (if loyalty system is active)

#### Any State → Cancelled
- **From Pending:** Always allowed, no payment to refund
- **From Confirmed:** Allowed, payment must be refunded
- **From Shipped:** Not allowed (order must be returned instead)
- **From Delivered:** Not allowed (order must be returned instead)

## Business Logic Validation

### Inventory Management
```typescript
// Pseudo-code for inventory validation
function validateInventoryAvailability(orderItems: OrderItem[]): ValidationResult {
  for (item of orderItems) {
    const availableStock = getAvailableStock(item.productId);
    const reservedStock = getReservedStock(item.productId);
    const totalAvailable = availableStock - reservedStock;
    
    if (item.quantity > totalAvailable) {
      return ValidationResult.fail(`Insufficient stock for ${item.productName}`);
    }
  }
  return ValidationResult.success();
}
```

### Price Consistency
```typescript
// Ensure order item prices match current product prices
function validatePriceConsistency(orderItems: OrderItem[]): ValidationResult {
  for (item of orderItems) {
    const currentPrice = getCurrentProductPrice(item.productId);
    
    if (item.unitPrice !== currentPrice) {
      return ValidationResult.fail(`Price mismatch for ${item.productName}`);
    }
  }
  return ValidationResult.success();
}
```

### Order Total Calculation
```typescript
// Order total must be calculated consistently
function calculateOrderTotal(orderItems: OrderItem[], shippingAddress: Address): OrderTotal {
  const subtotal = orderItems.reduce((sum, item) => sum + (item.quantity * item.unitPrice), 0);
  const taxRate = getTaxRate(shippingAddress);
  const taxAmount = subtotal * taxRate;
  const shippingCost = calculateShipping(orderItems, shippingAddress);
  
  return {
    subtotal,
    taxAmount,
    shippingCost,
    total: subtotal + taxAmount + shippingCost
  };
}
```

## Error Handling Rules

### Validation Error Types
- **INVALID_CUSTOMER:** Customer ID not found or inactive
- **INSUFFICIENT_INVENTORY:** Not enough stock for requested quantity
- **PRICE_MISMATCH:** Product price changed since cart creation
- **MINIMUM_ORDER_NOT_MET:** Order total below $5.00 minimum
- **MAXIMUM_ORDER_EXCEEDED:** Order total above $50,000 limit
- **INVALID_STATE_TRANSITION:** Attempted transition not allowed
- **PAYMENT_AUTHORIZATION_FAILED:** Payment could not be processed

### Error Response Format
```json
{
  "error": "VALIDATION_FAILED",
  "message": "Order validation failed",
  "details": [
    {
      "field": "orderItems[0].quantity",
      "code": "INSUFFICIENT_INVENTORY",
      "message": "Only 5 units available for product 'Wireless Headphones'"
    }
  ]
}
```

## Performance Considerations

### Validation Optimization
- Cache product prices for 5 minutes to reduce database calls
- Batch inventory checks for multiple products
- Use database constraints for critical validations
- Implement circuit breaker for external payment validation

### Concurrency Handling
- Use optimistic locking for inventory updates
- Implement idempotency keys for order creation
- Handle race conditions in inventory reservation
- Use distributed locks for high-concurrency scenarios

## AI Implementation Guidelines

When implementing order validation logic:

1. **Follow existing patterns:** Use the same validation structure as Customer and Product entities
2. **Create reusable validators:** Build composable validation functions
3. **Implement comprehensive tests:** Cover all business rule edge cases
4. **Use appropriate error messages:** Provide clear, actionable feedback to users
5. **Consider performance:** Minimize database queries and external API calls

### GitHub Copilot Usage
```typescript
// Prompt for AI assistant:
// "Implement order validation following the business rules in /openspec/business-rules/order-validation.md"
// "Use the existing ValidationResult pattern from the Customer entity"
// "Include comprehensive error messages for each validation failure"
```

## Related Specifications

- **Main Spec:** Order entity definition and state machine
- **Change Specs:** Any active changes affecting order validation
- **Architecture:** Order domain entity and sequence diagrams in /docs

## Audit Requirements

- All validation failures must be logged with customer ID and order details
- Validation performance metrics must be tracked
- Business rule violations must be reported to fraud detection system
- Critical validations (payment, inventory) must have audit trails
