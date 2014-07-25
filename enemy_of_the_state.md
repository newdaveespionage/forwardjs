Enemy of the State
==================

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