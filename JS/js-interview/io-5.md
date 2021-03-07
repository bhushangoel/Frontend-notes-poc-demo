## Question:
### What will be the output?
```javascript
    var obj = {a: 5};
    var obj2 = Object.create(obj);
    delete obj2.a;

    console.log(obj2.a);    //?
```

## Solution:
```javascript
    var obj = {a: 5};
    var obj2 = Object.create(obj);
    delete obj2.a;

    console.log(obj2.a);    //5
```
**There are two things happening here -**

- We are copying `obj` to `obj2` using `Object.create()`. Object.create() *copies the existing object to the prototype(__ __proto____) of new obj*(obj2 in this case).
```javascript
var obj2 = Object.create(obj);

// obj2 can be visualised as

/* 
obj2 = {
     __proto__: {
         a: 5
     }
} 
*/
```

- Deleting the property using `delete` operator. This operator *only deletes the value which is present directly on the object* and does not delete any value present on the prototype(__ __proto____) of an object. That is why deleting property `a` does not have any effect.