# Main System Specification

**E-commerce Platform Specification**

This document contains the aggregated specifications for the e-commerce platform, combining all implemented change specifications.

## System Overview

The e-commerce platform manages customers, orders, products, and payments with the following core entities:

- **Customer**: User account management and profile data
- **Order**: Purchase transactions with lifecycle management  
- **OrderItem**: Individual line items within orders
- **Product**: Catalog items with inventory tracking
- **Payment**: Transaction processing and status tracking

## Core Business Rules

### Order Management
- Orders have a state machine: pending → confirmed → shipped → delivered
- Orders can be cancelled only in pending state
- Confirmed orders require payment before shipping
- Shipped orders cannot be cancelled (only returned)

### Payment Processing
- Payment must be validated before order confirmation
- Failed payments automatically cancel the order
- Refunds are processed for cancelled confirmed orders
- Payment retry is allowed up to 3 attempts

### Inventory Management
- Stock validation occurs at order creation
- Inventory is reserved when order moves to confirmed
- Reserved inventory is released if order is cancelled
- Out-of-stock items prevent order confirmation

## Integration Points

### Architecture Documentation
This specification works alongside the architecture documentation in `/docs`:
- Entity diagrams define structure → specifications define behavior
- Sequence diagrams show flow → specifications define business rules
- State diagrams show transitions → specifications define validation logic

### AI Agent Usage
- Strong AI agents (Claude Opus level) are used for planning and specification creation
- Regular AI agents (GitHub Copilot) are used for implementation following specifications
- All code changes must reference relevant specifications for context

## Change Log

### Implemented Changes
- ✅ Basic e-commerce functionality (baseline)
- ✅ Payment processing with retry logic  
- ✅ Inventory reservation system

### Active Change Specifications
- 🔄 Customer loyalty points system (in progress)

**Last Updated:** 2026-01-15
**Version:** 1.2
