# `Egg.js`

Egg.js is a simple JS library that has no prerequisites and allows you to easily add web easter eggs by watching the user's key strokes.

### Example

It's really easy to use. Just include the egg.js file on the page...

```
<script type="text/javascript" src="/path/to/egg.js"></script>
```

...then use the `AddCode()` function to add in your easter eggs. You need to pass it the list of [keycodes](http://www.cambiaresearch.com/articles/15/javascript-char-codes-key-codes), a function to trigger when it happens, and an optional set of metadata. Metadata can be anything from a string to an object.

```js
var egg = new Egg();
egg.AddCode("38,38,40,40,37,39,37,39,66,65", function() {
  jQuery('#egggif').fadeIn(500, function() {
    window.setTimeout(function() { jQuery('#egggif').hide(); }, 5000);
  }, "konami-code");
});
egg.AddHook(function(){
  console.log("Hook called for: " + this.activeEgg.keys);
  console.log(this.activeEgg.metadata);
});
egg.Listen();
```

You can also add a hook, as shown above using `AddHook()`, that will run after any egg code is triggered. You could use it to fire a Google Analytics event or send out a tweet that someone finally found your easter egg. Hooks get access to the whole Egg.js object so you can pull information about the easter egg that fired via `this.activeEgg`


### Why?

I put an easter egg in pretty much everything I make and after copying the same basic code over and over again I figured I should make it in to a simple library for my own use.

### Credits

Created by Mike Flynn / [@thatmikeflynn](http://twitter.com/thatmikeflynn)
