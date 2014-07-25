promises
========

http://github.com/bengl/forwardjs-promise-talk
terminal font - Perfect DOS VGA 437

- has reject function
- has fulfill function
- returns an object that handles 
	- .then(function(value){});
	- .then(function(result){});
		- .then() returns promises
	- .catch(function(err){});

issues
------
- built-in node constructs use callbacks, not promises
- modules don't reliably use promises

solutions
---------
- bluebird
	- install and require
- hue
- in es6 draft (not reliably on spec)

using bluebird
--------------
```
$ npm i --save bluebird
```

```
var Promise = require('bluebird');
var fs = require('fs');
Promise.promisfyAll(fs);
readFile('stuff.json', {encoding: 'utf8'})
.then(JSON.parse)
.then(function(stuff){
	console.log(stuff.thing);
});
```

- promise libaries can be resource intensive
- leverage at init, avoid in actual process flow

backwards compatibility
-----------------------
- API considerations
- very simple (not necessarily realistic)
``` 
function getUser(someArt){
	return getFromDBAsync(someArg)
	.then(function(data){
		return getFromotherDBAsync(data);
	}).nodeify(cb);
}
```
- hook function
```
function getUser(hook, cb){
	//...
	return safelyPromisify(hook)()
	.then()
}
```
*again, code needs to be minimal, step through*

avoiding callback hell
----------------------
```
async.parallel([
	function(next){
		obj.doSomething1(next);
	},
	function(next){
		obj.doSomething2(next);
	}
]);
```
- in promise format
```
Promise.all([
	obj.doSomething1Async(),
	obj.doSomething2Async()
])
```
- waterfall
```
async.waterfall([
	function(next){
		obj.doSomething1(next);
	},
	function(next){
		obj.doSomething2(somevalue, next);
	}
])
```

- in promise format
```
Promise.all(obj.doSomething1Async().then(function(data){
	obj.doSomething2(somevalue);
}));
```

- whilst
``` 
function whilst(condition, aciton){
	return (function loop(){
		if (condition()){
			return action().then(loop);
		}
	})
})();

in practice
-----------
- Thrush library github.com/DeNA/thrush
```
Promise.safelyPromisify
Promise.series
Promise.whilst
```

edge cases
----------
- spread 
	- raises value to higher scope so it is available to all calls
	- can be called with config obj of {spread:true}

stack traces
------------
- bluebird adds a lot of stack frames
- adds "From previous event"
	- Promise.longStackTraces();

testing
-------
- using mocha < 1.18.0
	- have to call done at end of callback
- newer mocha, can return promise
- 

worth it?
---------
