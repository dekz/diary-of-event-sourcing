# Event Sourcing

# Services

## Bookings

Bookings is our exterior facing, Process Coordinating service. There is low Business Logic residing in this service. It ultimately exists to initiate and coordinate process with other services.

The flow of a scenario is described over multiple event handlers, for example, during the create booking process, Y commands are initiated with other services and X events are handled.

## Reservations

Reservations is the interface to our multiple suppliers. Our inventory is supplied Locally and by Third Parties. There is **high** amounts of Business Logic residing in this service. The Reservation service is responsible for providing a unified interface to a reservation with a supplier. This includes creation, cancellation and changes.

## Customer Payments

Customer payments is the service responsible for performing financial transactions with a customer. There is **high** amounts of Business logic residing in this service. It is concerned with multiple payment types, refunds, partial refunds.





