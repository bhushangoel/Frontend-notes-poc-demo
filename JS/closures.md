# Closures

An act of function which remembers its lexical scope in which it gets created is known as a closure.

A closure allows a function to access and manipulate variables that are external to that function.

It allows a function to access all the variables, as well as other functions, that are in scope when the function itself
is **defined**.

The closure isn’t just a snapshot of the state of the scope at the time of creation, but an active encapsulation of that
state that we can modify as long as the closure exists.

### A simple closure

```javascript
var outerValue = "car";

function outerFunction() {
    console.log(outerValue === 'car');  // true
}

outerFunction();
```

### Another example

```javascript
var outerValue = "car";
var later;

// outer scope:START
function outerFunction() {
    var innerValue = "bus";

    // inner scope:START
    function innerFunction() {
        console.log(outerValue === "car");  // true
        console.log(innerValue === "bus");  // true
    }

    // inner scope:ENDS

    later = innerFunction;
}

// outer scope:ENDS

outerFunction();
later();    
```

`innerFunction` here can not be invoked directly because its scope is limited to the `outerFunction`. So, we need to
invoke `innerFunction` using `later`.

See, how `innerFunction` which gets invoked at some later point in time, can access the variables(`innerValue`) that
were present at the time of its definition.

When we declare `innerFunction` inside the `outer function`, not only is the function declaration defined, but a *
closure is created* that encompasses the function definition as well as all variables in scope at the point of function
definition.

## Uses of a closure

### - mimicking private variables

### - using with callbacks
