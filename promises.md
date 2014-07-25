promises
========

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
