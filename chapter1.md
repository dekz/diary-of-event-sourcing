# Sagas/Process Coordination

When a service starts to grow and more complex coordination is required, using Event Handlers starts to break down. 

It is difficult to maintain a complex enough, long lived transaction that has been split across many event handlers. Each event handler comes with its own file and tests. It quickly becomes difficult to reason about.

Eventually a dynamic flow may appear as a scenario. Make multiple reservations, cancel multiple reservations. A business may not want to change a customer until all reservations have been made. A flow across multiple event handlers in this situation, requires one of these event handlers to become a coordinating gate service which doesn't continue until everything is successful.

This is a class of problems which can appear in many processes. Rather than solving it in an event handler, we solve it in a generic case with Sagas.



