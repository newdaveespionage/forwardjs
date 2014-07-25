The Low Down on Web Components
==============================

[Erik Bryn](erikbryn.com)
Prototypal
[@ebryn](http://twitter.com/ebryn)

background: ember.js core team

Web Components
--------------
- 1/3 of the audience has used ish
- group of proposed standards that aim to make it easier to build, share, and reuse code on the web
- Google Chrome has been primary driving force
- Over the past 2-3 years in development, some longer
- Dimitri Glaskov "godfather of web components"
- four specs
	- Custom Elements
		- Standard way of creating your own html tags
		- Done today using jQuery plugins, polyfills, etc. 
		- simplify to actual custom tag

		```
		<mycustomtag></mycustomtag>
		```
		
		- create using 
		
		```
		var MyElement = Object.create(HTMLElement.prototype);

		// callback hooks follow
		// createdCallback
		// attachedCallback
		// detachedCallback
		// attributechangedCallback
		// document.registerElement
		```

		- ES6 will have cleaner API (encapsulated in build)
		- livecoding inline in an html5 document, ES5 style

		```
		<my-component></my-component>
		<script>
			var MyComponentPrototype = Object.create(HTMLElement.prototype);
			MyComponentPrototype.createdCallback = function() {
				debugger;
			}
			MyComponentPrototype.attachedCallback = function() {
				debugger;
			}
			MyComponentPrototype.detachedCallback = function() {
				debugger;
			}
			MyComponentPrototype.attributeChangedCallback = function(name, oldVal, newVal) {
				debugger;
			}
			var MyComponent = document.registerElement('my-component', {prototype:MyComponentPrototype});

			debugger;

			document.body.appendChild(myComponent);

			debugger;

			myComponent.setAttribute('foo','bar');

			debugger

			document.body.removeChild(myComponent);

		</script>
		```

		- Today's solutions
			- jQuery plugin (simplest)
			- Ember components (leveraging framework/handlebars helpers)
			- Ember components (future) = allowing actual tags that retroactively define
			- Angular 1.x: directives
			- Angular 2.0: components - web component full support 
			- Polymer - leverages spec using declarative formmat
		- enabling interop
			- under exploration (open for collaboration)
			- no current spec for data passing
			- Node.bind is a promising proposal
		- native browser support
			- custom elements in chrome
			- firefox in development
			- polyfill using platform.js (Google Polymer team, evergreen browser support)
	- Templates
		- mechanism for declaring fragments for cloning and inserting
		- are inert: 
			- img src's do not load until cloned
			- script tags do not execute until cloned 
			- rendering triggers do not occur unless cloned
		- low level primitive (better than using procedural javascript to move dom around)
		- livecoding 
		``` 
		<template id="my-template">
			hello world
			<img src="success.jpg" />
		</template>

		<script>
			var template = document.getElementById('my-template');
			// clone recursively
			var clone = template.content.cloneNode(true);
			document.body.appendChild(template);
		</script>
		```
		- today's equivalents
			- ember with custom typed script tag
		- wouldn't be nice if we could do data binding?
			- libs and frameworks will have to fill the void
	- Imports
		- include and reuse HTML documents in other HTML documents
		- shared dependencies are only loaded once
		- several open questions regarding production use
		- quick way to build component libraries
		- livecoding
		my-button.html
		```
		<script>
			(function(document){
				var MyComponentPrototype = Object.create(HTMLElement.prototype);
				MyComponentPrototype.attachedCallback = function() {
					this.innerHTML='this is an attached component';
				}
				var MyComponent = document.registerElement('imported-element', {prototype:MyComponentPrototype});

			})(document.currentScript.ownerDocument);
		</script>
		```
		index.html
		``` 
		<head>
			<link rel="import" href="my-button.html"/>
		</head>
		<body>
			<imported-element></imported-element> <!-- imported from my-button.html -->
		</body>
		```
	- Shadow DOM
		- provides DOM encapsulation
		- allows you to package styles/js/etc. into one place
		- leverage dom apis
		- no declarative api
		- Polymer exposes a declarative api
		- create a template
		- using element.createShadowRoot();
		- the layout of your component, separate from content