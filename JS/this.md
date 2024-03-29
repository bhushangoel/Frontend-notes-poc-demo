# `this`

`this` is basically a function context and its value depends on the style of function invocation.

### For methods

It is method’s own object.

```js
var hero = {
    _name: 'John Doe',
    getSecretIdentity: function () {
        return this._name;
    }
};

var stoleSecretIdentity = hero.getSecretIdentity;

console.log(stoleSecretIdentity()); // undefined
console.log(hero.getSecretIdentity());  // "John Doe"
```

The first `console.log` prints `undefined` because we are extracting the method from the hero object, so
`stoleSecretIdentity()` is being invoked in the global context (i.e., the `window` object) where the `_name` property
does not exist.

One way to fix the `stoleSecretIdentity()` function is by using [bind()](../implementations/bind.md):

`var stoleSecretIdentity = hero.getSecretIdentity.bind(hero);`

### For top-level functions

It is either equivalent to -

- `window`(non-strict mode) or
- `undefined`(strict mode)

### For constructors

It is a newly created object instance.



