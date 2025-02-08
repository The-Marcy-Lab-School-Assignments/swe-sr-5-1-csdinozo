# Technical Writing Assignment

For guidance on setting up and submitting this assignment, refer to the Marcy lab School Docs How-To guide for [Working with Short Response and Coding Assignments](https://marcylabschool.gitbook.io/marcy-lab-school-docs/fullstack-curriculum/how-tos/working-with-assignments#how-to-work-on-assignments).

## Prompt 1

Imagine you are teaching a friend about OOP. They mainly want to understand what is Encapsulation. Write a brief lesson on Encapsulation that includes the following:

* What is encapsulation?
* What major goal does this help to achieve in software engineering?
* Give an example (in code) of encapsulation.
* An explanation of how the code example demonstrates encapsulation

### Response 1
_OOP_ is an acronym for **Object-Oriented Programming**. _OOP_ is a programming paradigm that uses objects to store and manage data. However, programming is much deeper than that.
The first concept we must discuss is the four pillars that define OOP: _encapsulation_, _abstraction_, _inheritance_, and _polymorphism_.
Today, we'll focus on **encapsulation**. Encapsulation refers to creating methods that operate on data while simultaneously restricting direct access to that data from outside the method.
For instance, when Amazon develops Ring doorbells, they allow you to access your doorbell camera—but not everyone can, as that would cause many problems.
The way encapsulation is achieved is creating closure.
An example of closure
```
const amazon =()=>{
    let allRingDoorbells = [];
    const doorbells = {
        addDoorbell(address) {
            allRingDoorbells.push(address)
        }
    }
    return doorbells
}
const avionteHouse = amazon()
avionteHouse.addDoorbell(123 street)
```
In the example above closure is used to _hide access_ to allRingDoorbells array. Even thought the array exist it can be access inside the scope of the function unlike the methods because is create inside of a object. The contents of a object can access with dot notation. So if the function is invoked you can access its objects with dot notation.

## Prompt 2

The following `friendsManager` object is an example of an interface that is **NOT** consistent and predictable:

```js
const friendsManager = {
    friends: [],
    addFriend(newFriend) {
        if (typeof newFriend !== 'string') return;
        this.friends.push(newFriend);
    }
}


friendsManager.addFriend('daniel');
friendsManager.addFriend(true);
friendsManager.friends.push('emmaneul');
friendsManager.friends.push(42);
```

Explain how the code is not consistent or predictable, then provide an example in code that uses closure to make it more consistent and predictable.

### Response 2
The code snippet above demonstrates unpredictable and inconsistent behavior. This friends manager object allows you to add a friend both with and without the designated method. Additionally, it grants direct access to the friends array, which means anything—not just friends—can be added.
A better way to implement your friends manager is by using closures.
```
const createFriendsManager=()=>{
    const friends = [];
    friendsManager={
        addFriend(newFriend) {
            if (typeof newFriend !== "string") return;
            this.friends.push(newFriend);
        },
    }
}
```

## Prompt 3

With OOP in JavaScript, it's possible to use factory functions to achieve encapsulation and re-use them to make objects that look alike. However, factory functions have drawbacks and we often use classes instead. 

How would you explain to a budding developer what the drawbacks of using factory functions are and why it is better to use classes instead?

### Response 3
Although factory functions are beneficial in how they can be used repeatedly to create similar objects, it is better to use classes instead because each part of the object reserves its own space in memory. This is unlike how, in classes, each variable and method created has its own memory value, shared by all instances of the class. Classes are also advantageous in cases where inheritance will be necessary. Superclasses make available their properties and methods to their children. For factory functions, an entirely separate factory function would be necessary to create an object of the similar yet modified properties and methods, again using more space than would be necessary.While it could be more convenient to use factory functions given their simplicity in how the `new` and `this` keywords are not needed for implementation, in scalable projects for which many instances of a type of object may eventually be necessary, it is better to use classes to prevent memory storage being used unnecessarily.

## Prompt 4

Do some research on the history of when / how classes were introduced into JavaScript and share your findings. Your response should include:

* What version of JavaScript were classes introduced in and when did it come out?
* Why were classes introduced into JavaScript?


### Response 4
ECMAScript 2015 (ES6, ES2015) introduced a new syntax for creating classes and their instances to Javascript. Classes were used as a substitute prototype-based inheritance, providing a more familiar syntax for object-oriented programming. Classes are a structured way to create objects and manage inheritance, allowing clean and concise implementation of objects. Class structure makes Javascript development more similar to other object-oriented, programming languages, making it easier for other developers to transition from such languages.

## Prompt 5

OOP can still be achieved in JavaScript without using the `class` keyword and instead using the "Constructor Functions" and the "Prototype Chain" (look them up!)

```js
function Person(name, age) {
 this.name = name;
 this.age = age;
}


Person.prototype.greet = function () {
 return `Hi, I'm ${this.name}, and I'm ${this.age} years old.`;
};


const alice = new Person('Alice', 30);
console.log(alice.greet());
```

Provide one point that advocates for the use of this syntax and then provide a counter-argument for the use of classes instead.

### Response 5
Prototype syntax is beneficial in how its lack of rigid structure allows greater flexibility for developers. Developers can add new methods and properties dynamically rather than returning to the prototype's declaration. This allows for quick updates wherever necessary, without constraining developers to a specific location where such updates can be added — anywhere post-definition is fine.
