# Sagas/Process Coordination

When a service starts to grow and more complex coordination is required, using Event Handlers starts to break down.

It is difficult to maintain a complex enough, long lived transaction that has been split across many event handlers. Each event handler comes with its own file and tests. It quickly becomes difficult to reason about.

Eventually a dynamic flow may appear as a scenario. Make multiple reservations, cancel multiple reservations. A business may not want to change a customer until all reservations have been made. A flow across multiple event handlers in this situation, requires one of these event handlers to become a coordinating gate service which doesn't continue until everything is successful.

This is a class of problems which can appear in many processes. Rather than solving it in an event handler, we solve it in a generic case with Sagas.



Sagas have **zero** business logic and only control process flow. No if, elses or buts should live inside of a Saga, as these usually are indicative of business logic. Rather than solve it as a conditional statement in a saga, it should live as a condition statement in a certain event handler.

The Saga simply coordinates with services using command or events. For example, the Saga is aware that 2 reservations are being made. When handing the first reservation\_creation\_successful event, it checks if all are complete. Only upon receiving the second reservation\_creation\_successful event, would it trigger some action. This Sagas action may be to call another service, such as Capture Payment. Or it could emit an event like booking\_reserved.

