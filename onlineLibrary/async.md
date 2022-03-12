[source]()

### __Asynchronous flow control using async__

**Installing async**
```javascript
npm install async
```
___

**Asynchronous operations in parallel**
```javascript
async.parallel({
  one: function(callback) { ... },
  two: function(callback) { ... },
  ...
  something_else: function(callback) { ... }
  },
  // optional callback
  function(err, results) {
    // 'results' is now equal to: {one: 1, two: 2, ..., something_else: some_value}
  }
);
```
...

**Asynchronous operations in series**
The method **async.series()** essentially declared and behaves in the same way as **async.parallel()**.

```javascript
async.series({
  one: function(callback) { ... },
  two: function(callback) { ... },
  ...
  something_else: function(callback) { ... }
  },
  // optional callback after the last asynchronous function completes.
  function(err, results) {
    // 'results' is now equal to: {one: 1, two: 2, ..., something_else: some_value}
  }
);
```

...

**Note**: The ECMAScript (JavaScript) language specification states that the order of enumeration of an object is undefined, so it is possible that the functions will not be called in the same order as you specify them on all platforms. If the order really is important, then you should pass an array instead of an object, as shown below.

```javascript
async.series([
  function(callback) {
    // do some stuff ...
    callback(null, 'one');
  },
  function(callback) {
    // do some more stuff ...
    callback(null, 'two');
  }
 ],
  // optional callback
  function(err, results) {
  // results is now equal to ['one', 'two']
  }
);
```