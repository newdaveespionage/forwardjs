Flux and React
==============

Bill Fisher
Jing Chen

- Building apps with unidirectional data flow
- https://github.com/flux
- https://speakerdeck.com/fisherwebdev/fluxchat
- http://miniurl.com/fluxreact

General level
-------------
- app scale managed by minimal structure
- stores instead of models
- react js rendering library
	- virtual DOM, does diff, only renders changes
	- conceptual re-render only

Stores
------
- Fat models
- example: Chat: all messages
- setup 
	- register with dispatcher
	- dispatcher calls callback
	- emits change event
	- interface getters, no setters
- did she just say heisenbug?
- caretaker (watcher only interested in certain events)
- store has it's own management interface which is self-contained
- nothing updates the store, it updates itself
- pivots typically on the action type
- action types stored in private hash, only available with getters/setters
- payload has data and event information
- why?
	- to keep flows simplified for data events
	- to allow for scalability amongst data structures since each behaves with it's own logic map
	- avoid monolithic data interfaces
	- allow for testability

Interaction
-----------
- controller-views
	- componentDidMount/componentDidUpdate/componentWillMount
- actions are entry point into the system
- this architecture is way too complicated to explain with flowcharts
- code examples need more clarity/time
- views emitted to from stores, act depending on the events emitted
- individualized stores per type of entity, in messenger example
	- message store
	- thread store
	- unread thread store (why? why not have flag on thread store?)
- dispatcher manages update sequence (marshalling callbacks)

Evolving
--------
- add a store when you have a new type of entity
- segment data to stores depending on entity type
- scalable with simplified pathways for each

Flux
----
- where? 
	- Dataflow programming
		- distinct ways of getting data in and out
		- simplifies flow
		- waiting for imports to become valid
	- CQRS
		- action is like query cycle
		- does not exactly map to flux
	- Functional
		- React component is a pure function

Future
------
- Open source dispatcher
	- same as in use at FB
	- fires off error if circular dependency issued
- Example chat app / ToDo app
	- chat app is better overview/hands-on
- Create boilerplate code for init
- Needed Utils/Routers (Open Source), router needs to create action to fit into architecture

Questions
---------
- init
	- initial payload sent from server 
	- store doesn't just take payload, stores route to dispatcher so all stores and elements can view (read path vs write path)
	- web api utilities file for stores to call 
	- utility method is typically called in the action creator vs. in the stores
- How to enforce style
	- culture communication
- Dispatcher manages EVERYTHING
- action creators emit events that React manages
- error exists if circular dependency occurs between store updates (waitFor)
- waitfor is not global, it's per message type
- 
