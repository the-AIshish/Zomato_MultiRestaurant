# PRD: Multi-Restaurant Single Order

## 1. Summary
Enable users to place a single order that contains items from multiple restaurants, while preserving delivery, billing, and experience integrity. This feature should reduce friction for groups, households, and corporate orders, improving average order value and conversion.

## 2. Objective
- Increase order convenience for customers ordering for groups
- Drive higher basket size and revenue per checkout
- Differentiate Zomato with a unique multi-restaurant ordering experience
- Improve retention by reducing need to place multiple orders separately

## 3. Target Users
- Groups ordering for friends/colleagues from different restaurants
- Families who want multiple cuisines in one checkout
- Office lunch ordering for teams
- Users who want to consolidate payment and delivery tracking

## 4. Success Metrics
- Adoption rate: percentage of eligible users who use multi-restaurant checkout
- Conversion lift: increase in checkout completion for multi-restaurant carts
- Average order value (AOV) for multi-restaurant orders
- Time-to-checkout decrease versus separate restaurant orders
- Customer satisfaction / NPS for group ordering experience
- Operational metrics: number of orders handled correctly across restaurants, delivery SLA compliance

## 5. Scope
### In Scope
- UI flow for adding items from multiple restaurants
- Single checkout experience with consolidated cart
- Payment capture with multi-merchant settlement
- Delivery coordination and routing for multi-leg delivery
- Order tracking with restaurant-level status updates
- Cart management rules and promotions
- Fees, commissions, and split billing logic
- Order confirmation and notifications

### Out of Scope (initial launch)
- Partner kitchen consolidation or cloud kitchen routing
- Full dine-in / pickup combination with delivery
- International expansion-specific localization
- Complex split-payments between multiple payers

## 6. User Problems
- Users must place separate orders when ordering from different restaurants
- Multiple checkouts increase friction and time
- Tracking multiple deliveries is confusing
- Payment and billing become fragmented
- Group orders across cuisines are cumbersome

## 7. User Journey
1. User searches or browses restaurants
2. Adds an item from Restaurant A to cart
3. Continues browsing, selects items from Restaurant B
4. System prompts that multi-restaurant order is possible
5. User reviews consolidated cart
6. User checks out once with one payment
7. System confirms order and displays separate restaurant order statuses
8. Delivery partner(s) optionally combine pickups or deliver separately
9. User tracks fulfillment and receives delivery updates

## 8. Functional Requirements
### 8.1 Cart & Browsing
- Allow adding items from multiple restaurants into the same cart
- Show restaurant tags, item origins, and estimated preparation times
- Enforce compatibility rules (e.g., delivery zone restrictions)
- Display warnings if a restaurant item is unavailable due to cross-restaurant constraints

### 8.2 Checkout
- Single checkout screen with:
  - consolidated item list grouped by restaurant
  - per-restaurant sub-totals
  - aggregate fees and taxes
  - combined delivery fee calculation
  - promotions that can apply globally or per-restaurant
- Payment flow remains one transaction
- Support wallet, card, UPI, and pay-later options as usual

### 8.3 Fees and Settlement
- Calculate and present:
  - item totals per restaurant
  - restaurant-specific taxes and commissions
  - delivery fee structure for multi-restaurant orders
- Support payouts to multiple merchant accounts
- Record data for accounting and partner settlement

### 8.4 Delivery
- Option A: separate delivery partners pick up from each restaurant and deliver separately
- Option B: single delivery partner optimized for multi-restaurant pickups (longer delivery time expected)
- Display estimated time as the maximum of all restaurant prep times plus delivery routing
- Track delivery per restaurant order component
- Support delivery status updates at both global and restaurant levels

### 8.5 Order Management
- Create one master order with restaurant sub-orders
- Each sub-order must surface:
  - restaurant status
  - item fulfillment
  - ETA
- Allow cancellations and modifications according to restaurant-specific policy
- Provide order receipts with breakdowns

## 9. Non-Functional Requirements
- Performance: cart updates and checkout must remain responsive
- Reliability: correct split of orders and settlement
- Scalability: support multi-restaurant cart growth without impacting normal checkout
- Security: protect payment and customer data in one transaction
- UX: maintain clarity and avoid confusion over multiple restaurants

## 10. UI/UX Requirements
- Clear cart UI with grouped restaurant sections
- Easy add/remove items per restaurant
- Visual cues for estimated prep time disparity
- Messaging clarifying delivery may take longer
- Transparent fee and tax breakdown
- Order tracking UI with restaurant-level cards and global summary
- Notification templates for multi-restaurant order updates

## 11. Edge Cases
- Restaurant A becomes unavailable after item addition
- One restaurant cancels while others remain active
- Different delivery zones or timing incompatibility
- Cross-restaurant promo applicability
- Partial order failure due to payment or logistics
- User attempts to add items from too many restaurants (impose limit, e.g., 3-4 restaurants)

## 12. Dependencies
- Menu/cart service changes for multi-restaurant grouping
- Checkout/payment gateway changes for multi-party settlement
- Delivery routing and assignment logic updates
- Restaurant order management and partner systems integration
- Notification and tracking system updates

## 13. Success Criteria
- Feature launched to select cities or users
- Operational stability with less than 1% failure rate for multi-restaurant orders
- Positive user feedback and increased order size
- At least 10-15% of eligible group orders using the feature within rollout period
- Delivery and fulfillment reliability maintained

## 14. Rollout Plan
1. Pilot with select high-density cities
2. Launch to premium or loyalty users first
3. Expand to all users after validation
4. Monitor partner capacity and delivery SLAs
5. Iterate on UI messaging, fee structure, and routing

## 15. Risks
- Increased delivery complexity and SLA breaches
- User confusion if not communicated clearly
- Restaurant partners may object to combined delivery timing
- Higher operational cost if not optimized
- Payment reconciliation complexity

## 16. Future Enhancements
- Split payment among multiple payers
- Restaurant recommendation bundles
- Corporate group ordering workflow
- Smart routing to minimize delivery time and cost
- Integration with party order and shared baskets

## 17. Appendix
- Recommended limit: 2-3 restaurants per order for MVP
- Example flow: “Order from KFC + Domino’s + McDonald’s in one checkout”
- KPI cadence: weekly adoption, daily operational health, monthly revenue impact
