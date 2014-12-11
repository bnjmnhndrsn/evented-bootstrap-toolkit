# Evented Bootstrap Toolkit

This is a extension of Maciej Gurban's [Responsive Bootstrap Toolkit](https://github.com/maciej-gurban/responsive-bootstrap-toolkit). To quote Maciej, the toolkit "provides an easy way of breakpoint detection in JavaScript, detecting changes in currently active breakpoint, as well as executing any breakpoint-specific JavaScript code."

This modification adds custom events which will trigger whenever the viewport switches between one of the specified viewport sizes, providing the old and new viewport size as data to the event.

Current version: 0.0.0

### JavaScript
#### Checking which breakpoint is active
Checking what size the viewport is remains the same as in [the original](https://github.com/maciej-gurban/responsive-bootstrap-toolkit).

````javascript
if (viewport.is('xs')) {
  // do stuff in the lowest resolutions only!
}

if (viewport.is('lg')) {
  // do stuff on huge screens only
}
````

#### Registering an object for breakpoint events
Registering events is the innovation of this modification. To register, just 

````javascript
var $content = $("#content");

//this adds the element to the list of elements to be triggered on a viewport resize event
App.viewport.registerTarget($content);


//an event handler can then be binded as normal
$content.on("viewportResize", function(event, oldSize, newSize){
	if (oldSize == "xs") {
		// do stuff
	}
});

//when you want to remove the event
$content.off("viewportResize");
App.viewport.removeTarget($content);
````

This allows for easy integration in Backbone.js and other frontend frameworks.
````javascript
	events: {
		"viewportResize": "resizeHandler"
	},
	initialize: function(){
		App.viewport.registerTarget(this.$el);
	},
    remove: function() {
		App.viewport.removeTarget(this.$el);
        Backbone.View.prototype.remove.apply(this, arguments);
    },
	resizeHandler: function(event, oldSize, newSize){
		//do stuff
	}
````
### How do I include it in my project?
#### JavaScript

(Again this is the same as the original [Responsive Bootstrap Toolkit](https://github.com/maciej-gurban/responsive-bootstrap-toolkit))

Include just before `</body>`

````html
<!-- Mandatory for Responsive Bootstrap Toolkit to operate -->
<div class="device-xs visible-xs"></div>
<div class="device-sm visible-sm"></div>
<div class="device-md visible-md"></div>
<div class="device-lg visible-lg"></div>

<!-- Responsive Bootstrap Toolkit -->
<script src="js/bootstrap-toolkit.js"></script>

<!-- Your scripts using Bootstrap Toolkit -->
<script src="js/main.js"></script>
````


### Dependencies

**JavaScript features:**
  1. Bootstrap's responsive utility css classes included in its standard stylesheet package
  2. jQuery library

