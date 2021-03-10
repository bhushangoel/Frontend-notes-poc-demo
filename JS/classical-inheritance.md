# Classical Inheritance

Inheritance in JavaScript is quite different from the concept of inheritance in other languages. It would be right to
call it as *delegation*.

**Why delegation ??**

Because during inheritance in JavaScript, properties and methods from parent class doesn’t gets copied to the child
class, instead they are linked together via a prototypal chain. So, it is also known as prototypal inheritance.

So let’s get started with this.

Before that make sure you know about basics of JavaScript Objects .

### Prerequisites for this lesson:

![Prerequisites](https://cdn-images-1.medium.com/max/1600/1*_IxLm9Bsgm9VtptX8Y7yWw.png)

So how does inheritance works in JS. Let’s understand this with the help of an example.

![Inheritance in JS](https://cdn-images-1.medium.com/max/1600/1*NDnFXn5PtZhcQ7EzoBi83Q.png)

### Objective:

We want `Teacher` and `Student` to share some generic features from `Person` and then create object instance from those
child classes.

As you can see, we have a parent class (or constructor function in JS) called `Person` which have some properties and
methods of its own. Now when we create any child object like – Teacher and Student in our case, we want them to have the
access of all the properties and methods available on the parent class.

**So how will they access ??**

***PROTOTYPAL INHERITANCE*** comes into the picture here.

Let’s see some sample code here and try to understand that line by line.

```javascript
function Person(first, last, age, gender, interests) {
    this.name = {first, last};
    this.age = age;
    this.gender = gender;
    this.interests = interests;
}

Person.prototype.greeting = function () {
    alert(`Hi! Iam ${this.name.first}.`);
}

function Teacher(first, last, age, gender, interests, subject) {
    Person.call(this, first, last, age, gender, interests); // 1
    this.subject = subject;
}

Teacher.prototype = Object.create(Person.prototype);    // 2

Teacher.prototype.constructor = Teacher;    // 4

var T1 = new Teacher('John', 'Doe', 50, 'M', ['Solving puzzles'], 'Math');
var T1 = new Teacher('Tracy', 'Trevor', 38, 'F', ['Reading'], 'Computers');
```

### Explanation:

```javascript
function Person(first, last, age, gender, interests) {
    this.name = {first, last};
    this.age = age;
    this.gender = gender;
    this.interests = interests;
}
```

Here we have created a function called `Person`, which is basically a constructor function in our case and defined some
generic properties related to a person like (`name, age, gender, interests`).

```javascript
Person.prototype.greeting = function () {
    alert(`Hi! Iam ${this.name.first}.`);
}
```

Notice, that we have created a greeting method on the prototype of Person and not on the constructor/Person directly.

#### Why?

Because if we create a method on the prototype than it will get stored in the memory once and all the instances will
stop at common prototype object when they try to access whereas, if we had created greeting method on the constructor
itself then it will get re-declared every time an instance is created, which will consume more memory.

```javascript
function Teacher(first, last, age, gender, interests, subject) {
    Person.call(this, first, last, age, gender, interests); // 1
    this.subject = subject;
}
```

Now, we create a new `function` called `Teacher` which we want to inherit from Person. Note that we have passed one more
argument called subject, as teacher would have some more qualities than a normal Person. Inside Teacher we have called
Person function using call(), why ?? Because call() lets us pass the current context to the function and in this case
Person will set all the passed properties onto this object of current context.

It is equivalent to, defining all the properties on this object inside the Teacher itself. But we want to make use of
Person function.

![Why Object.create( ) ??](https://cdn-images-1.medium.com/max/1600/1*zlZ4vdlbzm1LGQ3_wRoHJQ.png)

Now, we have a problem. We have defined a new `constructor function (Teacher)`, and it has a prototype property, which
by default just contains a reference to the constructor function itself.

It does not contain the methods of the Person constructor’s prototype property which we want to inherit.

In order to get `Teacher()` to inherit the methods defined on `Person()’s` prototype we need to use `Object.create()`
and pass Person’s prototype object as an argument. `create()` <span style="color: #009988">*simply copies the passed
object value to the prototype*</span> (__proto__ in case of an object)of the target Object.

Now, when you `console.log(Teacher.prototype.__proto__ )` you will see the greeting method that is defined on the
Person’s prototype.

```javascript
// 4
Teacher.prototype.constructor = Teacher;
```

After adding the 2 line, `Teacher.prototype’s` constructor property has become equal to `Person()`, because we had set
`Teacher.prototype` equal to an object that inherits its properties from Person.prototype!

You can verify the same by doing `console.log(Teacher.prototype.constructor)`

So we can fix this by explicitly pointing Teacher’s constructor to Teacher function.

Now, everything looks good. We can also override the greeting method present on `Person.prototype` and create a new
greeting method on the Teacher by typing. <span style="color: #009988">This is also called Polymorphism.</span>

```javascript
Teacher.prototype.greeting = function () {
    /*function code*/
}
```

```javascript
var T1 = new Teacher('John', 'Doe', 50, 'M', ['Solving puzzles'], 'Math');
var T1 = new Teacher('Tracy', 'Trevor', 38, 'F', ['Reading'], 'Computers');
```

Creating object instances from Teacher In the last step, we need to create instances of the child class. Here we need to
pass the required arguments and we will get a new object containing all the details that we have passed.

Try to print the output of the following statements:

```javascript
T1.name.first;
T1.interests[0];
T1.subject;
T1.greeting();
```

```javascript
T2.name.first;
T2.interests[0];
T2.subject;
T2.greeting();
```
