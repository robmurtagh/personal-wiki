# javascript

## Spread syntax

Use the [Spread Syntax](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators/Spread_syntax) to expand an iterable e.g. an object into its components.

An example of merging with shallow clone would be:

```javascript
var obj1 = {"a": "b"};
var obj2 = {"c": "b"};
var obj3 = { ...obj1, ...obj2 };
console.log(obj3);
```

* `obj3` contains a copy of `obj1` and `obj2` as they were when `obj3` was created
* `obj3` is not a reference to the current state of `obj1` and `obj2`