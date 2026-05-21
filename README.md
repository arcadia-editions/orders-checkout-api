# orders-checkout-api

Orders Checkout is the bounded context that owns the commercial commitment to buy.
In the Place Order flow it is the pivot between shopping intent and downstream
operations: it starts the checkout, reacts to stock and payment outcomes, and
decides whether the order is created, confirmed, or cancelled.

Following the bounded-context heuristic from the architecture article, this
service exists because order lifecycle and commercial rules are a center of
gravity distinct from stock management, payment processing, or shipping.

## Bounded context scope

- Start customer checkout for selected items
- Own the order lifecycle from creation to confirmation or cancellation
- Publish the pivotal `OrderConfirmed` event that shifts the flow into operations
- React to stock and payment outcomes without owning those subdomains

This service does not authorize payments, reserve stock internally, or arrange
shipping. It coordinates with those contexts through contracts and events.

## Contents

- `domain-model.zdl`: source of truth for the order aggregate, lifecycle, and events
- `README.md`: repository overview and bounded-context explanation

## Main domain elements

- `Order`: aggregate for the checkout commitment
- `OrdersCheckoutService`: commands for starting checkout, confirming, and cancelling orders
- `OrderCreated`, `OrderConfirmed`, and `OrderCancelled`: business events consumed by other services
- `StockUnavailable`: commercial outcome when checkout cannot secure scarce stock
