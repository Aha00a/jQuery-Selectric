#jQuery Selectric ![icon](http://i.imgur.com/D2hcnUN.png)

jQuery Selectric is a jQuery plugin designed to help at stylizing and manipulating HTML selects.

* Keyboard navigation (Up/Down/Left/Right/Word search)
* Easily customizable
* Pretty lightweight
* Options box always stay visible
* Doesn't rely on external libraries (besides jQuery)
* Word search works with western latin characters set (e.g.: á, ñ, ç...)

###[Demo](http://lcdsantos.github.io/jQuery-Selectric/)

##How to use:

Make sure to include jQuery in your page:

```html
<script src="//ajax.googleapis.com/ajax/libs/jquery/1.11.2/jquery.min.js"></script>
```

Include **jQuery Selectric:**

```html
<script src="js/jquery.selectric.min.js"></script>
```

Include **jQuery Selectric** styles, and change it to your taste :D _(please refer to our [demo page](http://lcdsantos.github.io/jQuery-Selectric/demo.html) for more themes and other customizations)_

```html
<link rel="stylesheet" href="selectric.css">
```

Initialize **jQuery Selectric:**

```html
<script>
$(function(){
  $('select').selectric();
});
</script>
```

##Options:

You can pass an options object as the first parameter when you call the plugin. For example:
```js
$('select').selectric({
  maxHeight: 200
});
```

```js
{
  /*
   * Type: Function
   * Description: Function called before plugin initialize
   */
  onBeforeInit: function() {},

  /*
   * Type: Function
   * Description: Function called plugin has been fully initialized
   */
  onInit: function() {},

  /*
   * Type: Function
   * Description: Function called plugin has been fully initialized
   */
  onBeforeOpen: function() {},

  /*
   * Type: Function
   * Description: Function called after select options opens
   */
  onOpen: function() {},

  /*
   * Type: Function
   * Description: Function called before select options closes
   */
  onBeforeClose: function() {},

  /*
   * Type: Function
   * Description: Function called after select options closes
   */
  onClose: function() {},

  /*
   * Type: Function
   * Description: Function called before select options change
   */
  onBeforeChange: function() {},

  /*
   * Type: Function
   * Description: Function called when select options change
   */
  onChange: function(element) {
    $(element).change();
  },

  /*
   * Type: Function
   * Description: Function called when the Selectric is refreshed
   */
  onRefresh: function() {},

  /*
   * Type: Integer
   * Description: Maximum height options box can be
   */
  maxHeight: 300,

  /*
   * Type: Integer
   * Description: After this time without pressing
   *              any key, the search string is reset
   */
  keySearchTimeout: 500,

  /*
   * Type: String [HTML]
   * Description: Markup for open options button
   */
  arrowButtonMarkup: '&lt;b class=&quot;button&quot;&gt;&amp;#x25be;&lt;/b&gt;',

  /*
   * Type: Boolean
   * Description: Initialize plugin on mobile browsers
   */
  disableOnMobile: true,

  /*
   * Type: Boolean
   * Description: Open select box on hover, instead of click
   */
  openOnHover: false,

  /*
   * Type: Integer
   * Description: Timeout to close options box after mouse leave plugin area
   */
  hoverIntentTimeout: 500,

  /*
   * Type: Boolean
   * Description: Expand options box past wrapper
   */
  expandToItemText: false,

  /*
   * Type: Boolean
   * Description: The select element become responsive
   */
  responsive: false,

  /*
   * Type: Object
   * Description: Customize classes.
   *              Every class in 'postfixes' should be separate with a
   *              space and follow this exact order:
   *              'Input Items Open Disabled TempShow HideSelect Wrapper
   *              Hover Responsive Above Scroll Group GroupLabel'
   */
  customClass: {
    prefix: 'selectric',
    camelCase: false,
    overwrite: true
  },

  /*
   * Type: String or Function
   * Description: Define how each option should be rendered inside its &lt;li&gt; element.
   *
   *              If it's a string, all keys wrapped in brackets will be replaced by
   *              the respective values in itemData. Available keys are:
   *              'value', 'text', 'slug', 'disabled'.
   *
   *              If it's a function, it will be called with the following parameters:
   *              (itemData, element, index). The function must return a string,
   *              no keys will be replaced in this method.
   */
  optionsItemBuilder: '{text}',

  /*
   * Type: String or Function
   * Description: Define how each select label should be rendered. Allows HTML.
   *
   *              If it's a string, all keys wrapped in brackets will be replaced by
   *              the respective values in currItem. Available keys are:
   *              'value', 'text', 'slug', 'disabled'.
   *
   *              If it's a function, it will be called with the following parameters:
   *              (currItem). The function must return a string, no keys will be
   *              replaced in this method.
   */
  labelBuilder: '{text}',

  /*
   * Type: Boolean
   * Description: Prevent scroll on window when using mouse wheel inside options box
   *              to match common browsers behavior.
   */
  preventWindowScroll: true,

  /*
   * Type: Boolean
   * Description: Inherit width from original element
   */
  inheritOriginalWidth: false,

  /*
   * Type: Boolean
   * Description: Determine if current selected option should jump to
   *              first (or last) once reach the end (or start) item of list upon
   *              keyboard arrow navigation.
   */
  allowWrap: false
}
```

##Events:

All events are called on original element, first argument is the original element too. And can be bound like this:

```js
$('select').on('eventname', function(element){
  // your code
});
```

`eventname` can be one of the following:

<table>
  <tr>
    <td><strong>Event name</strong></td>
    <td><strong>Description</strong></td>
  </tr>
  <tr>
    <td><code>selectric-before-init</code></td>
    <td>Fired before plugin initialize</td>
  </tr>
  <tr>
    <td><code>selectric-init</code></td>
    <td>Fired plugin has been fully initialized</td>
  </tr>
  <tr>
    <td><code>selectric-before-open</code></td>
    <td>Fired before select options opens</td>
  </tr>
  <tr>
    <td><code>selectric-open</code></td>
    <td>Fired after select options opens</td>
  </tr>
  <tr>
    <td><code>selectric-before-close</code></td>
    <td>Fired before select options closes</td>
  </tr>
  <tr>
    <td><code>selectric-close</code></td>
    <td>Fired after select options closes</td>
  </tr>
  <tr>
    <td><code>selectric-before-change</code></td>
    <td>Fired before select options change</td>
  </tr>
  <tr>
    <td><code>selectric-change</code></td>
    <td>Fired when select options change</td>
  </tr>
  <tr>
    <td><code>selectric-refresh</code></td>
    <td>Fired when the Selectric is refreshed</td>
  </tr>
</table>

##Hooks:

Check [jquery.selectric.placeholder.js](plugins/jquery.selectric.placeholder.js) source for a usage example

```js
// Add a callback everytime 'callbackName' is called
$.fn.selectric.hooks.add('callbackName', 'hookName', function(element, data) {});

// Remove a callback
$.fn.selectric.hooks.remove('callbackName', 'hookName');
```

##Public methods:

```js
var Selectric = $('select').data('selectric');

Selectric.open();    // Open options
Selectric.close();   // Close options
Selectric.destroy(); // Destroy select and go back to normal
Selectric.refresh(); // Reconstruct the plugin options box
Selectric.init();    // Reinitialize the plugin

// Or...
$('select').selectric('open');    // Open options
$('select').selectric('close');   // Close options
$('select').selectric('destroy'); // Destroy select and go back to normal
$('select').selectric('refresh'); // Reconstruct the plugin options box
$('select').selectric('init');    // Reinitialize the plugin
```

##Browser support:

* Firefox
* Chrome
* Safari
* Internet Explorer 7+
* Opera
