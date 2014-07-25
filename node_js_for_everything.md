Node.js For Everything
======================
@zwigby

Charlie Key
modulus.io (node.js mongoDB hosting)

2008
Love and Javascript
Wanted to make a game
Wanted to use Javascript everywhere
Multiplayer game
Decided to use Node
0.6.8
Made Tic-Tac-Together, still runs, production server has not been restarted in over 2 years

Lessons
-------
- Let your process crash
	- pm2 has built-in load balancer (newer)
	- forever (older, more established)
- Find issues
	- node-inspector
		- can inspect run-time
		- in browser (web-inspector)
- Possible to build entire infrastructure in node
- Don't use node for decrypting SSL 
- Backbone.js front-end
- No asterisks in npm versions (too risky)
	- use specific version
	- build strategy to update
	- do not rely on devs using semver
- Stateless applications
	- allows for easy scaling
- If you do have to use state
	- Redis
	- session storage
- API building
	- use express
		- great for building apis
		- unopinionated
		- minimalistic
		- production ready
	- possibly happy
		- newer
		- production ready
		- logging validations
	- restify
		- straightforward
		- quick
		- easy
- Horizontal scalability is imperitive for production ready
	- run node app multiple times
	- balance traffic accross apps
- Don't reinvent everything
	- don't start from scratch
	- use npm
	- there is probably a package for what you do
	- research it
	- check support / roadmap
- Testing
	- DO IT
	- Jasmine (BDD)
- Streams
	- Learn how streams work
	- Streamadventure
- Keep it simple
	- Easier to fix
	- Easier to document/maintain
- Load testing
	- Apache AB
	- Standard suites work for normal http carls
	- Websockets are hard to test
- CSRF Tokens
	- Frameworks have solutions for this






