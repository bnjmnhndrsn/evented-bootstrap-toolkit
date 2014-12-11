# Evented Bootstrap Toolkit

This is a modification of Maciej Gurban's Responsive Bootstrap Toolkit. To quote Maciej, the toolkit "provides an easy way of breakpoint detection in JavaScript, detecting changes in currently active breakpoint, as well as executing any breakpoint-specific JavaScript code."

This modification adds events 
Current version: 0.0.0

### JavaScript
#### Checking which breakpoint is active

````javascript
if (viewport.is('xs')) {
  // do stuff in the lowest resolutions only!
}

if (viewport.is('lg')) {
  // do stuff on huge screens only
}
````

### How do I include it in my project?
#### JavaScript

Include just before `</body>`

````html
<!-- Mandatory for Responsive Bootstrap Toolkit to operate -->
<div class="device-xs visible-xs"></div>
<div class="device-sm visible-sm"></div>
<div class="device-md visible-md"></div>
<div class="device-lg visible-lg"></div>

<!-- Responsive Bootstrap Toolkit -->
<script src="js/bootstrap-toolkit.min.js"></script>

<!-- Your scripts using Bootstrap Toolkit -->
<script src="js/main.js"></script>
````

#### SASS

Copy contents of `compass/bootstrap-toolkit` directory into your project. File `style.scss` contains lines that need to be in your own style.scss for the mixin to work. You'll need SASS 3.3+.


### Dependencies

**JavaScript features:**
  1. Bootstrap's responsive utility css classes included in its standard stylesheet package
  2. jQuery library

**CSS features:**
  1. SASS 3.3+
  2. Compass


