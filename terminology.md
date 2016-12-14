

# Terminology

**Aggregate** - The entity, or target of a process. In Bookings, a booking. In Customer Payments, a payment.

**Process** - The way services interact with each other. After this occurs in service A, we make a request to Service B. Often drawn as a sequence diagrams with the services. Easy to draw on a whiteboard.

**Business Logic** - The meat of the domain. The implementation of how a customer is charged; How loyalty points are awarded; If an email or an SMS is sent to a user for a notification.

**Command** - An outgoing request for a service to do something. Service A requests Service B to perform some operation using its business logic. For example, Bookings requests Customer Payments to charge a customer money.

**Event** - A fact that something happened. Booking was created, order was received, a step was unsuccessful.

**Event Handler** - A reaction to an event that has occurred. An order was received, reduce the inventory count by 1.

**Applicator** - Over time, the current state of an aggregate changes. A booking can go from booked to cancelled. An applicator, takes each event, extracts the interesting information out and applies it to a model.

Projection - The result of iterating through all of the applicators is the projection of the model.

**Saga/Coordinator/Orchestrator** - Is responsible for the flow of the process. Can take wait for multiple events to occur, then continue on with the process. The implementation of what is usually drawn in a sequence diagram. For example, The process will not take charge a customer until all the items in the shopping cart are reserved\(a parallel process\).

