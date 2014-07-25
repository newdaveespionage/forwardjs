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
		- livecoding inline in an html5 document
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
			

		</script>
		```



