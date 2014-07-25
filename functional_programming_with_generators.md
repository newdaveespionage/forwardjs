Functional Programming With Generators
======================================

Requirements
------------
- node 11

Async Challenges
----------------
- Callback hell
- Promises
	- need a new stack
	- no original scope callback

Generators
----------
- Restartable function
```
var Gen = function *(){}
var gen = Gen();
var val = gen.next().value 

while (!val.done)

```
- .next() returns a Yieldable
- lazy evaluation
- coroutines
	- stack of code that runs independently of the main thread
	- can eventually be used in browser (ecmascript 6 adoption rate?)

real world
----------
- co by holloway chuck

functional programming
----------------------
- first class
- can merge two gens?
- koa style flow control?
- generators can make generators

