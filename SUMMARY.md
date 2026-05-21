# Orders Checkout

## Description

Orders Checkout is the bounded context that owns the commercial commitment to
buy. It starts the checkout, reacts to stock and payment outcomes, and decides
whether the order is created, confirmed, or cancelled.

It is the service that marks the transition from customer purchase intent into a
real order that other operational contexts can act on.

## Scope

- Start customer checkout for selected items
- Own the order lifecycle from creation to confirmation or cancellation
- Publish the pivotal `OrderConfirmed` event that shifts the flow into operations
- React to stock and payment outcomes without owning payment or inventory rules

## Main domain elements

- `Order`: aggregate for the checkout commitment
- `OrdersCheckoutService`: commands for starting checkout, confirming, and cancelling orders
- `OrderCreated`: event announcing that checkout successfully created an order
- `OrderConfirmed`: event that hands the flow off to downstream operational contexts
- `OrderCancelled`: event announcing the commercial flow could not complete
- `StockUnavailable`: commercial outcome when checkout cannot secure scarce stock
