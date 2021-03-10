# Interview Questions

This file consists of complete list of questions related to frontend development.

# JS (js-interview)

## Theory (theory)

1. [Closures](./JS/closures.md)
2. Object.create()
3. [Classical inheritance](./JS/classical-inheritance.md) vs [prototypal inheritance]()
4. Prototypes
5. Async - Promises vs async-await vs observables
6. Different ways to create an object in javascript
7. Function expression vs Function declaration
8. Significance of "use strict"
9. Null vs undefined with explanation
10. Number of ways to delete an element from array
11. A deep copy of an object
12. Currying in javascript
13. HTTP, CORS, Caching
14. Storage in a browser : LocalStorage vs SessionStorage
15. Debouncing vs throttling
16. Destructuring in array and object
17. Spread operator in array and object
18. Rest parameter
19. Web workers
20. event propagation
21. service workers
22. `stopPropagation` vs `stopImmediatePropagation`
23. iterable vs enumerable
24. `for of` vs `for in`
25. application cache vs browser cache
26. How can you implement Encapsulation and Abstraction in JS?
27. How can you implement Inheritance in JS?
28. call(), [`bind()`](./JS/bind.md), apply()
29. [slice vs splice](./JS/js-interview/theory-29.md)

## Input/Output (io)

1. What will be printed in a console?
   ```javascript
   "use strict"
   let x = 1;
   let x = 2;
   console.log(x);

   "use strict"
   var x = 1;
   var x = 2;
   console.log(x);

   var x = 1;
   var x = 2;
   console.log(x);
   ```
2. Is this statement correct?
   ```javascript
   let bob = a => a + 100;

   bob(2); //?
   ```
3. What value will be displayed in the alert?
   ```javascript
   var arr = []; 
   arr[0] = 'a'; 
   arr[1] = 'b'; 
   arr.foo = 'c'; 

   alert(arr.length); 
   ```
4. What will happen, if I declare an array using a const and try to change one of its values ?
   ```javascript
   const s = [5, 6, 7];
   s[2] = 45;
   console.log(s);
   ```
5. What will be the output?
    ```javascript
    var obj = {a: 5};
    var obj2 = Object.create(obj);
    delete obj2.a;

    console.log(obj2.a);    //?
    ```
   [Solution here](./JS/js-interview/io-5.md)

# Angular JS (angular-interview)

## Theory based (theory)

1. components vs directives
2. componentFactoryResolver
3. angular concepts revision
4. decorator pattern
5. what are the modules, component and service
    - how many types of modules are there?
        - root and feature
        - can you add multiple modules in a single angular application?
6. how to detect changes in the input property passed from parent to child component?
7. how to pass data from child to parent component?
8. lifecycle methods in angular
9. observables vs promises
10. Data sharing between a parent to child using -
    `@Input`
11. Data sharing between a child to parent using -
    `@ViewChild, @Output and Event-emiiter`
12. AOT vs JIT, which one is better
13. Dependency injection
14. How would you create a filter using angularJs?
15. Constructor vs ngOnInit
16. change detection and strategies - how to forcefully detect changes?
17. DOM Sanitization
18. Security Practices in angular
19. View Encapsulation
20. IVY
21. Route-guards

## Scenario Based (scenario)

1. If same service is added to root and feature a module, what will be the behavior?
2. An observable returning a stream of data and if you subscribe at a later stage then how can you get previous data
   that have been missed?
3. digest cycle vs change detection
4. can you load and unload an angular feature module?

# HTML ([html](./html))

1. Direct tag to implement dropdown with search in HTML
2. Semantic tags
3. What's new in HTML 5?
4. [Script loading strategies](./html/html-4.md)

# CSS (css)

1. How to align a div vertically and horizontally centered ?
    - Fixed dimension
    - Dynamic dimension
2. Box model ?
3. Pseudo classes `(:hover, :active)` vs pseudo elements `(:after, :before)`
4. Positions - fixed, relative, absolute, static, sticky
5. Explain following CSS selectors
   ```
   div, p
   div p
   div > p
   div + p
   div ~ p
   ```
6. What is CSS media queries and what are they used for?
7. Bootstrap
8. CSS Pre-processors
    - Sass (scss)
    - Less
9. Flex box
10. box shadow
11. box model
12. box sizing
13. display properties - none, block, inline, inline-block
14. vm, em, rem, vh, vw font size properties
15. animations
16. How would you align an image to a circular div, just like on instagram
17. how would you write a code to freeze top row and column

# TypeScript

1. Static vs dynamic typing
2. generic in typescript
3. optional value without using question mark

# Other Reference Links

[Advance JS ($)](https://www.pluralsight.com/courses/advanced-javascript)

[DailyJS](https://medium.com/dailyjs)

[JS interview questions](https://www.toptal.com/javascript)

[AngularJS interview questions ](https://www.toptal.com/angular-js/interview-questions)

[ParseInt mystery](https://medium.com/dailyjs/parseint-mystery-7c4368ef7b21)

[isArray](https://medium.com/dailyjs/parseint-mystery-7c4368ef7b21)

[HTTP Concept](https://developer.mozilla.org/en-US/docs/Web/HTTP)

