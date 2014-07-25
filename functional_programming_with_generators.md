Functional Programming With Generators
======================================
@cultofmetatron

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
- context = call with this applied can be anything depending on call time. 
- koajs.com

* note to self: code examples should be step-by-step, clear as hell, these are not*
* also, needs real-world context *

- github.com/cultofmetatron/shen -- toolbox for building generators
	- can create cascades of function groups depending on desired flow
	- DEAR GOD MAKE THE CODE MORE READABLE. 

- biggest mistake from old paradigm:
	- yielding parallel values when yield is a sequential basis. 

