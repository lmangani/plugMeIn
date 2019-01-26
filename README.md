# PlugMeIn

PlugMeIn is an extended and pluggable version of [Aggro](https://github.com/borgar/aggro), a very basic utility to filter and sort a collection of items for use in reports or visualizations.

## Usage
```
const plugMeIn = require('plugmein');
const population = [
  { "method": "INVITE", "count": 35, "response": "407" },
  { "method": "REGISTER", "count": 38, "response": "407" },
  { "method": "INVITE", "count": 29, "response": "200" },
  { "method": "REGISTER", "count": 19, "response": "200" },
  { "method": "INVITE", "count": 31, "response": "200" },
  { "method": "REGISTER", "count": 22, "response": "200" },
  { "method": "INVITE", "count": 22, "response": "200" },
  { "method": "OPTIONS", "count": 33, "response": "486" }
];

plugMeIn()
  .filter('method', 'INVITE')
  .groupBy('response')


```

## Plug Functions
PlugMeIn supports function injection from local or remote (npm) modules
#### Module Export
```
module.exports = function plugin() {
  this.chain = function() {
    // return this to allow chaining on this function
    return this;
  }
}
```

### Module Import
```javascript
// Initialize
var plugmein = require('plugmein');

// Re-Initialize w/ Plugins
plugmein = plugmein().plug([ require('my-npm-module'), require('./my-local-module').myFunc ]);

plugmein().myFunc()

```


###### Why Forking?
This version will be heavily modified to work within [paStash](https://github.com/sipcapture/pastash). Assuming we don't drift too far off, we'll propose changes back to Aggro whenever mature.
