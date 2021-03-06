Enemy of the State
==================
@ammeep
amy.palamounta.in
github.com/ammeep
- are we managing state in a scalable fashion
- can we do it with clarity in code

Amy, from New Zeland

- previous js dev, current c#

Things apps have in common
--------------------------
- managing state
- managing events

Issues
------
- as complexity increases sanity decreases
- easy to confuse layers and create tangle

Solutions
---------
- design patterns
- mv* 
	- model -> core
	- view/template -> display and logic for display
	- other (controller, view/controller) -> managing flow
	- routes -> mapping destinations

Client/Server
-------------
- web server frameworks
- client frameworks

Ideas in mv* that stick
-----------------------
- keeping state off the server
- persisting to a data store
- addressable state and actions
- linear architecture for state transitions
- routes should be light, used as a feature, not as the focus
- routes should address state, not transitions of state
- events as part of the architecture
- build small, molecular components
	- modules
- modules never place themselves in the application 
- layout composition controls layout
	- defines a shell
	- marionette js?
- dispatcher
	- listens for new module calls
	- hands new modules to layout manager

Result
------
- event driven, composable application

- use as a basis, but not absolute
- don't built servers on the client
- use event mediation to decouple communication between modules
- define events carefully, don't just flag everything as an event
- chaplin -> worth looking into
- when does one break into modules -> no easy answer, depends on when

when to not mix routes and transitions
- delete
	- don't use a route to address a delete, use a transitional connection
