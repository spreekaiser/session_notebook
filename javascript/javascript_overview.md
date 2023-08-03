# Javascript Overview

- [ ] [JavaScript Basics](#javascript-basics)
- [ ] [Loops](#js-loops)
- [ ] [Conditions and Booleans](#js-conditions-and-booleans)
- [ ] [Inputs and Strings](#js-inputs-and-strings)
- [ ] [Objects and Arrays](#js-objects-and-arrays)
- [ ] [Array Methods](#js-array-methods)
- [ ] [Array Methods 2](#js-array-methods-2)
- [ ] [Forms](#js-forms)
- [ ] [Forms 2](#js-forms-2)
- [ ] [createElement](#js-createelement)
- [ ] [Functions](#js-functions)
- [ ] [Functions 2](#js-functions-2)
- [ ] [Callback Functions](#js-callback-functions)
- [ ] [Async Functions](#js-async-functions)
- [ ] [Fetch](#js-fetch)

## JavaScript Basics

### Learning Objectives

- Connect a JavaScript file with `<script>`
- Log to the console
- Select elements with `querySelector`
- Add, remove and toggle CSS classes on `click` with `addEventListener`

---

### Connect a JavaScript file

```html
<head>
  ...
  <script src="./index.js" defer></script>
</head>
<body>
  ...
</body>
```

The `script` tag has two attributes:

`src="./index.js"` sets the URL to our JavaScript file

`defer` tells the browser to delay the loading of the script until all HTML elements are loaded.

> 💡 Alternative: `script` tag at the end of the body element, so `defer` attribute is not
> necessary. Less modern.

```html
<head>
  ...
</head>
<body>
  ...
  <script src="./index.js"></script>
</body>
```

---

### Hello World: `console.log()`

In JavaScript we can print text to the console of the web browser. We can use this for debugging or
error logging for example.

```js
console.log("Hello World!"); // logs into console
console.clear(); // clears console
console.error("Error!"); // logs as error into console
```

---

### Selecting HTML Elements: `.querySelector()`

Before we can add interactivity, we need to select the necessary HTML-Elements:

```html
<body>
  <main class="main" id="main" data-js="main">...</main>
</body>
```

There are multiple ways to select the above main section within our JavaScript. A good practice is
to use a
[data-\* attribute](https://developer.mozilla.org/en-US/docs/Web/HTML/Global_attributes/data-*),
like the **data-js** in the following example:

```js
const mainElement = document.querySelector('[data-js="main"]');
```

Other css selectors work as well, but the data-\* attribute selectors should be preferred.

```js
// tag as identifier
const mainElement = document.querySelector("main");
// class as identifier -> .
const mainElement = document.querySelector(".main");
// id as identifier -> #
const mainElement = document.querySelector("#main");
```

> 💡 We try to separate our concerns: Classes are for CSS and data-\* attributes are for JavaScript.

---

### Add Interaction: `.addEventListener()`

We can listen to **events** like **clicks** on an Element and execute code when the event is
triggered. The method `addEventListener` is used to react to events.

```html
<button type="button" data-js="button">Log into console</button>
```

```js
const button = document.querySelector('[data-js="button"]');
button.addEventListener("click", () => {});
```

First you specify the kind of event, e.g. **click**, then you define what code should be executed
when the event is triggered. You write that code between the `{}` brackets, e.g. a `console.log`.

```js
const button = document.querySelector('[data-js="button"]');
button.addEventListener("click", () => {
  console.log("Yeah");
});
```

There different events you can listen to, for example:

```js
button.addEventListener("mouseover", () => {});
```

```js
button.addEventListener("keydown", () => {});
```

> 💡 Here you can find a
> [list of event types](https://developer.mozilla.org/en-US/docs/Web/Events#event_listing).

> 💡 You don't have to understand the syntax for now, we will cover this in a later session.

---

### Add/remove & toggle classes: `.classList.`

You can add, remove and toggle classes, e.g. to change the styling of an element.

```html
<main data-js="main">
  <button type="button" data-js="button">Add a class</button>
</main>
```

Add **page--primary** class to the above main section by using the `selectedElement.classList.add`
method:

```js
const main = document.querySelector('[data-js="main"]');
const button = document.querySelector('[data-js="button"]');

button.addEventListener("click", () => {
  main.classList.add("page--primary");
});
```

A click on the button adds the class **page--primary** to the main element:

```html
<main data-js="main" class="page--primary">
  <button type="button" data-js="button">Add a class</button>
</main>
```

You can also remove or toggle a class in the same way:

```js
main.classList.remove("page--primary");
```

```js
main.classList.toggle("page--primary");
```

---

### Resources

#### Connect a JavaScript file

[The Script element](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/script)

#### Hello World

[Console](https://developer.mozilla.org/en-US/docs/Web/API/Console)

#### Selecting HTML Elements

[Document](https://developer.mozilla.org/en-US/docs/Web/API/Document)

[Using data attributes](https://developer.mozilla.org/en-US/docs/Learn/HTML/Howto/Use_data_attributes)

[document.querySelector](https://developer.mozilla.org/en-US/docs/Web/API/Document/querySelector)

[data-\* attribute](https://developer.mozilla.org/en-US/docs/Web/HTML/Global_attributes/data-*)

#### Add Interaction

[.addEventListener()](https://developer.mozilla.org/en-US/docs/Web/API/EventTarget/addEventListener)

[Event reference](https://developer.mozilla.org/en-US/docs/Web/Events#event_listing)

#### Add/remove & toggle classes

[classList](https://developer.mozilla.org/de/docs/Web/API/Element/classList)

## JS Loops

### Learning Objectives

- understanding the concept of loops
- understanding classic `for` loops
- understanding modern `for...in` and `for...of` loops
- understanding `while` loops

---

### What is a loop

A loop executes a respective block of code over and over again until an end criteria is met. In
JavaScript, two basic types of loops exist:

- `while` loop: are used when a task needs to be executed until a specific criteria is met.
- `for` loop: are commonly used when a given task needs to be executed x times or for each element
  in an object / array.

---

### `while`

The while loop is the most fundamental type of loop. It repeats a code block as long as the stated
criteria is `true`.

```js
let string = "a";

while (string.length <= 8) {
  console.log(string);
  string = string + string;
}

// 'a'
// 'aa'
// 'aaaa'
// 'aaaaaaaa'
```

In this example, the while loop repeats itself 4 times, until the string becomes too long and the
loop criteria changes to `false`.

---

### `for`

`for` loops are intended for repeating a task a certain number of times. They consist of three
internal parts:

- an internal counter which is increased / decreased every iteration.
- a criteria which checks the value of the counter. As long as the criteria is `true`, the loop is
  executed.
- a rule how the counter is increased / decreased (in most cases it is increased by 1)

```js
for (let counter = 0; counter < 4; counter++) {
  console.log(counter);
}
// 0
// 1
// 2
// 3
```

The body of the for loop contains the code which is executed on each iteration. For the example
above it is a `console.log` which logs the value of the counter on each iteration until the value of
`counter` reached 4 and the loop is terminated.

---

### `for...in`

The `for...in` is a shorthand notation to loop through all keys of an object:

```js
const user = {
  name: "Alex",
  age: 28,
  email: "alex@mail.com",
};

for (const key in user) {
  console.log(user[key]);
}

// 'Alex'
// 28
// 'alex@mail.com'
```

The loop has an iterator variable, in this case `key` which is assigned the respective key value in
each iteration (first 'name', then 'age' and finally 'email').

---

### `for...of`

Similar to `for...in` the `for...of` loop is a shorthand notation, but for looping through all items
of an array.

```js
const fruits = ["apple", "banana", "melon"];

for (const fruit of fruits) {
  console.log(fruit);
}

// 'apple'
// 'banana'
// 'melon'
```

This time the iterator variable `fruit` is assigned the respective array item in each iteration.

---

### Resources

- [MDN article about loops and iterations](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Guide/Loops_and_iteration)

## JS Conditions and Booleans

### Learning Objectives

- using conditions to control the program flow
- understanding what booleans and truthy/falsy values are
- working with comparison and logical operators
- writing ternary expressions

---

### Boolean Values

A boolean value, named after George Boole, only has two states. It can either be **true** or
**false**. Booleans are often used in conditional statements which can execute different code
depending on their value.

### Truthy and Falsy Values

Sometimes you want to have a condition depending on another type of value. JavaScript can transform
any value into a boolean with _type coercion_. That means that some values act as if they were true
and others as if they were false: _Truthy_ values become true, _falsy_ values become false.

- _truthy_ values:

  - non zero numbers: `1`, `2`, `-3`, etc.
  - non empty strings: `"hello"`
  - `true`

- _falsy_ values:
  - `0` / `-0`
  - `null`
  - `false`
  - `undefined`
  - empty string: `""`

---

### Comparison Operators

Comparison operators produce boolean values by comparing two expressions:

| Operator  | Effect                                                                           |
| --------- | -------------------------------------------------------------------------------- |
| A `===` B | strict equal: is `true` if both values are equal (including their type).         |
| A `!==` B | strict not equal: is `true` if both values are not equal (including their type). |
| A `>` B   | strictly greater than: is `true` if A is greater than B.                         |
| A `<` B   | strictly less than: is `true` if A is less than B.                               |
| A `>=` B  | greater than or equal: is `true` if A is greater than or equal B.                |
| A `<=` B  | less than or equal: is `true` if A is less than or equal B.                      |

> 💡 You might notice that JavaScript uses three equal signs (`===`) to check for equality. This can
> seem very strange at first.
>
> - `=` (`const x = 0`) is the assignment operator and has nothing to do with comparison.
> - `==` and `!=` are non-strict equality operators. You should **avoid them 99% of the time**.  
>   Non-strict equality tries to use type coercion to convert both values to the same type:
>   `"3" == 3` is `true`, which is seldomly what you want.
> - `===` and `!==` are strict equality operators. **This is what you need almost always**.  
>   Strict equality checks if type _and_ value are the same: `"3" === 3` is `false`.

---

### Logical Operators

Logical operators combine up to two booleans into a new boolean.

| Operator                      | Effect                                                 |
| ----------------------------- | ------------------------------------------------------ |
| `!`A                          | `not`: flips a `true` value to `false` and vice versa. |
| A <code>&#124;&#124;</code> B | `or`: is `true` if either A `or` B is true.            |
| A `&&` B                      | `and`: is `true` if both A `and` B is true.            |

> 💡 You can combine logical operators with brackets to define which operator should be evaluated
> first, e.g:
>
> - `(A || B) && (C || D)`
> - `!(A || B)`

> 💡 Be careful when using `&&` or `||` with non-boolean values. They actually return one of the
> original values. That can be useful, but can also quickly lead to confusion. This behaviour is
> called
> [short-circut evaluation](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators/Logical_AND#short-circuit_evaluation)
> and is a more advanced topic.
>
> - `"some string" || "some other string"` evaluates to `"some string"`
> - `0 || 100` evaluates to `100`
> - `null && "yet another string"` evaluates to `null`

---

### Control Flow: `if / else`

With an if statement we can control whether a part of our code is executed or not, based on a
condition.

```js
const isSunShining = true;

if (isSunShining) {
  // code that is executed only if condition "isSunShining" is true
}
```

The else block is executed only if the condition is `false`.

```js
const isSunShining = false;

if (isSunShining) {
  // code that is executed only if condition "isSunShining" is true
} else {
  // code that is executed only if condition "isSunShining" is false
}
```

The condition expression between the `()` brackets can be composed of logical or comparison
operators as well. You can distinguish between more cases by chaining `else if` statements:

```js
if (hour < 12) {
  console.log("Good Morning.");
} else if (hour < 18) {
  console.log("Good afternoon.");
} else if (hour === 24) {
  console.log("Good night.");
} else {
  console.log("Good evening.");
}
```

If the condition is not a boolean, it is converted into one by type coercion. This can be used to
check whether a value is not 0 or an empty string:

```js
const name = "Alex";
if (name) {
  console.log("Hi " + name + "!"); // only executed if name is not an empty string
}
```

---

#### Switch

Sometimes we want to check a variable or expression, to see if its value is one of a few very specific possible values. In this situation, we can make use of the **switch** statement.

The `switch` statement works by taking the variable or expression, then moving sequentially through a list of possible **cases** for its value. In each `case` that it gets to, it compares the checked value with the case's value. If they match, the code in this `case` will be run. If they don't match, JavaScript will move on to the next `case` in the sequence.

Here's an example:

```js
console.log("Which is your favorite season of the year?");
const userAnswer = "spring";

switch (userAnswer) {
  case "summer":
    console.log("Heat, sun and waves for you 😎");
    break;
  case "autumn":
    console.log("Crunchy, colorful leaves and cool breezes 🍁");
    break;
  case "winter":
    console.log("Ice, snow, warm clothes and hot drinks ☕️");
    break;
  case "spring":
    console.log("Growth, green, and new beginnings! 🌿");
    break;
  default:
    console.log("Sorry, I don't think that's a season!");
}
```

Important notes about the `switch`:

1. Like an `if`, you need to wrap the checked value/expression in parentheses
2. Like an `if`, wrap the entire body of the `switch` in braces/curly brackets
3. Each `case` offers one single value (not an expression!) to check for
4. After the `case`'s value, there must be a colon (`:`)
5. To prevent JavaScript from flowing from one `case` to another, be sure to end off each `case` with a `break`!
6. You can add a `default` case if you like; generally a good idea. It does not need to end with `break`

---

### Ternary Operator: `? :`

With if / else statements whole blocks of code can be controlled. The ternary operator can be used
if you want to decide between two _expressions_, e.g. which value should be stored in a variable:

```js
const greetingText = time < 12 ? "Good morning." : "Good afternoon.";
```

The ternary operator has the following structure:

```js
condition ? expressionIfTrue : expressionIfFalse;
```

If the condition is true, the first expression is evaluated, otherwise the second expression. The
ternary operator can be used to decide which function should be called:

```js
isUserLoggedIn ? logoutUser() : loginUser();
```

It can also distinguish which value should be passed as an argument to a function:

```js
moveElement(xPos > 300 ? 300 : xPos); // the element can't be moved further than 300.
```

> ❗️ The operator can only distinguish between two _expressions_ like values, math / logical
> operations or function calls, not between _statements_ like variable declarations, if / else
> statements or multi-line code blocks.

---

### Advanced: The strangeness of boolean coercion and making use of non-strict equality

<details>
<summary>🫣 This is an advanced topic and not important for the challenges. Click to expand if you're curious.</summary>

Assume you want to check if a variable has a useful value for us to work with. `if(variable)` does
in fact not check if `variable` is defined but rather if it is truthy. Take a look at these
examples:

- `if(undefined)` → falsy, won't execute
- `if(null)` → falsy, won't execute
- `if("")` → falsy, won't execute, but might still be a useful variable  
  (e.g. when user clears an input field)
- `if(0)` → falsy, won't execute, but might still be a useful variable  
  (e.g. when user wants to set the volume to `0`)
- `if(" ")` → truthy, will execute
- `if(-1)` → truthy, will execute

It's useful to define a variable as not having a value when it's `undefined` or `null`. We can check
for that like this:

```js
if (variable != null) {
  console.log('This will be logged even if variable is 0 or ""');
}
```

This is one of the rare valid use cases for non-strict comparison (`!=` instead of `!==`).

JavaScript tries to coerce the compared values into the same type. And just like `"3" == 3` is
`true`, `undefined == null` is also `true`. This also works with `!=` instead of `==`.

> ⚠️ Remember that this is an exception for using non-strict equality. **Strict equality should
> otherwise always be preferred.**

</details>

---

### Resources

#### Operators

[MDN Comparison Operators](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Guide/Expressions_and_Operators#comparison_operators)

[MDN Logical Operators](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Guide/Expressions_and_Operators#logical_operators)

#### if / else statements

[MDN about if else](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Statements/if...else)

#### Ternary Operator

[MDN Ternary Operator](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators/Conditional_Operator)

## JS Inputs and Strings

### Learning Objectives

- learning different ways of writing strings
- using string properties and methods
- working with input elements

---

### Strings

There are three ways to create strings using _string literals_:

1. `'string'`: single quotes
2. `"string"`: double quotes
3. `` `string` ``: back ticks or **template literals**.

> 💡 In general there is no preference for using either single or double quotes, except for stylistic
> reasons. Tools like prettier convert all strings to use the same style quotes. We have configured
> prettier to use double quotes by default. One reason to prefer one style of quotes over another on
> a case-by-case basis is when a quotation mark is part of the string:
>
> - `"It's such a nice day!"`
> - `'"Nice work", they said.'` or `'[data-js="foo"]'`
>
> Prettier detects these cases automatically.

Strings can be chained together by using the `+` operator (yes, the same as the maths operator).
This is called **string concatination**:

```js
const name = "Alex";
const stringConcatination = "Hello " + name + ", good to see you!";
```

### Template Literals

The third method to write strings has the useful property that you can insert variables into the
string by wrapping placeholders with a dollar sign and curly brackets `${}` . This is also called
**string interpolation**.

This way you don't have to concat multiple strings if you want to use a variable in your string:

```js
const stringConcatination = "Hello " + name + ", good to see you!";

const withTemplateString = `Hello ${name}, good to see you!`;
```

Any **expression** can be placed into these placeholders:

```js
const greeting = `Hello ${
  name !== null ? name : "mysterious person"
}, good to see you!`;
```

With template literals you can also write **multi-line strings**:

```js
`Hello,
this is in a new line.
Good bye!`;
```

### String Properties and Methods

Strings in JavaScript have some build-in **properties** and functionalities called **methods**. You
can call them with the dot notation followed by the name of the property / method.

```js
"A normal string".length; // evaluates to 15
"A normal string".toUpperCase(); // evaluates to "A NORMAL STRING"
```

> 💡 Methods are functions, thus they need to be invoked by placing `()` brackets after the name of
> the method.

| Property / Method                   | Effect                                                                   |
| ----------------------------------- | ------------------------------------------------------------------------ |
| `.length`                           | returns the number of characters in a string.                            |
| `.toUpperCase()`                    | returns a all uppercase version of the string.                           |
| `.toLowerCase()`                    | returns a all lowercase version of the string.                           |
| `.trim()`                           | returns a string with all whitespace removed from the beginning and end. |
| `.replaceAll(oldString, newString)` | replaces all occurrences of `oldString` with the `newString`.            |
| `.startsWith(subString)`            | returns `true` if the string starts with subString.                      |
| `.endsWith(subString)`              | returns `true` if the string ends with subString.                        |
| `.includes(subString)`              | returns `true` if the string contains the subString.                     |

> 💡 Go to the
> [MDN Docs](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/String#instance_properties)
> for even more string methods.

---

### Input Fields

Every input field in HTML holds a **value** in form of a string. You can access the value by using
`.value` on the input Element:

```html
<form>
  <input data-js="textInput" type="text" value="test 123" />
  <input data-js="numberInput" type="number" value="42" />
</form>
```

```js
const textInput = document.querySelector('[data-js="textInput"]');
const numberInput = document.querySelector('[data-js="numberInput"]');

textInput.value; // evaluates to 'test 123'
numberInput.value; // evaluates to '42' (still a string!)
```

You can also change the value of the input by assigning a new value to this input property:

```js
textInput.value = "changed value!";
```

This change is immediately visible on the website.

For example, you can enforce all uppercase letters in a form by combining this functionality with an
`input` event listener on the input element:

```js
// transform on every change the input value to uppercase letters
textInput.addEventListener("input", () => {
  const oldValue = textInput.value;
  const newValue = oldValue.toUpperCase();
  textInput.value = newValue;
});
```

---

### Resources

#### String Methods

[MDN Docs: String Methods](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/String#instance_properties)

## JS Objects and Arrays

### Learning Objectives

- Creating, accessing, and manipulating arrays
- Creating, accessing, and manipulating objects
- Knowing how to find properties and methods of objects by logging

---

### Arrays

Arrays are a structured data type which can store multiple values in one variable.

You can declare an array using `[]` square brackets (array literals):

```js
const shoppingList = ["apple", "tomato"];
```

Each item in the array has an index, which starts at 0. You can access individual items using the
bracket notation and the item's index:

```js
shoppingList[0]; // "apple"
shoppingList[1]; // "tomato"
```

Arrays can hold any type of value, even another array. This is called a nested array. The values of
nested arrays can be accessed by choosing the index of the nested array first and then stating the
index of the element inside the nested array.

```js
const nestedArray = ["a", 1, ["a", "new", "sentence"], false];
nestedArray[2][1]; // "new"
```

You can overwrite individual values in an array:

```js
const shoppingList = ["apple", "tomato"];
shoppingList[0] = "banana";
shoppingList; // ["banana","tomato"];
```

#### Common Array Attributes and Methods

| Attribute / Method       | Effect                                           |
| ------------------------ | ------------------------------------------------ |
| `array.length`           | returns the number of elements in the array      |
| `array.push(element)`    | adds `element` to the end of the array           |
| `array.pop()`            | removes the last element of an array             |
| `array.unshift(element)` | adds `element` as the first element of the array |
| `array.shift()`          | removes the first element of the array           |

> 💡 There are much more array methods and attributes which we will discover in later sessions. Go
> to the
> [MDN Docs](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array#instance_methods)
> for more information.

---

### Objects

Objects are a structured data type, which couple their values not to an index, but to a unique key.

You can declare an object using `{}` curly brackets (object literals):

```js
const person = {
  name: "Max Paddington",
  age: 21,
  isStudent: false,
};
```

You can access the properties using the dot notation:

```js
person.name; //"Max Paddington"
```

You can also access the properties using the bracket notation:

```js
person["age"]; // 21
```

Objects can be nested:

```js
const person = {
  name: "Max Paddington",
  age: 21,
  isStudent: false,
  address: {
    street: "Berliner Str.",
    houseNumber: 42,
    city: "Leipzig",
    zipCode: "12345",
  },
};
```

Nested values can be accessed by chaining the dot notation and/or the bracket notation together.

```js
person.address.street; // "Berliner Str."
person.address["city"]; // "Leipzig"
```

You can change values of object properties by reassigning them using the dot or bracket notation:

```js
person.name = "Max Paddington";
person["age"] = 33;
```

You can add new properties in the same way:

```js
person.score = 15;
```

You can delete properties using the delete keyword:

```js
delete person.score;
```

### Nested Objects / Arrays

Arrays can contain objects and vice versa:

```js
const peopleArray = [
  {
    name: "John",
    age: 22,
  },
  {
    name: "Alex",
    age: 33,
  },
];
```

```js
const user = {
  userId: "1234",
  mail: "test@mail.com",
  shoppingCart: ["tomato", "banana", "chocolate"],
};
```

You can access elements via chained dot / bracket notation:

```js
peopleArray[1].name; // "Alex"
user.shoppingCart[0]; // "tomato"
```

---

### Resources

#### Array

[MDN Docs: Array](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array)

#### Object

[MDN Docs: Object](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Object)

## JS Array Methods

### Learning Objectives

- Understanding array iteration with `forEach`
- Understanding array iteration with `map`
- Knowing the difference between `forEach` and `map`
- Using `filter` to exclude array elements
- Using `document.querySelectorAll`

---

### Introduction to array methods

All array methods presented here have a lot in common and can be used in the same way.

- You provide a callback function with one parameter
- The array method iterates over an array
- The provided callback function gets called for each element in the array
- With each call to the function the current array element gets passed as first argument

This way you can write code and apply it to each element within an array

---

### `forEach`

The array method `forEach` executes some logic for each element within an array.

```js
const pets = ["bird", "cat", "dog", "ferret", "fish"];
pets.forEach((pet) => {
  const petElement = document.createElement("p");
  petElement.textContent = pet;
  document.body.append(petElement);
});
```

> ❗️ The callback function provided to `forEach` **must not** use a `return` statement. `forEach` >
> **does not return** a new array.

> ❗️ You **should** use `forEach` to use a side-effect, like `document.createElement`

![array-methods-forEach](./assets/array-methods-forEach.png)

---

### `map`

The array method `map` is used to apply a transformation to each element of an array.

The transformed elements are stored in the **newly created array** returned by `map`. The elements
in the original array are not being altered.

You can define the kind of transformation applied to each element in the callback function and
**return** the transformed element.

The created and the original array have the same length.

```js
const pets = ["bird", "cat", "dog", "ferret", "fish"];
const uppercasePets = pets.map((pet) => {
  return pet.toUpperCase();
});
console.log(uppercasePets); // ['BIRD', 'CAT', 'DOG', 'FERRET', 'FISH']
```

![array-methods-map](./assets/array-methods-map.png)

> ❗️ The callback function provided to `map` **must** use a `return` statement to return a
> transformed element. `map` **returns** a new array.

> ❗️ You **should not** use `map` to trigger a side-effect, like `document.createElement`

---

### `filter`

The array method `filter` is used to **create a new array** with a subset of the elements of the
original array.

The callback function **returns** a **boolean value** to define, if an element is being included in
the resulting array or not. The original array is not being altered.

The created array is likely to have a shorter length than the original array.

```js
const pets = ["bird", "cat", "dog", "ferret", "fish"];
const petsWithF = pets.filter((pet) => {
  return pet.startsWith("f");
});
console.log(petsWithF); // ['ferret', 'fish']
```

> ❗️ The callback function provided to `filter` **must** use a `return` statement to return a
> boolean value.

![array-methods-filter](./assets/array-methods-filter.png)

---

### Chaining array methods

Often times you need to combine multiple array methods to achieve a desired result. Array methods
like `map` and `filter`, that return a new array, can be **chained**. Instead of storing each array
in a separated variable, the methods can be called directly after another. This reduces the amount
of code and improves readable.

```js
const pets = ["bird", "cat", "dog", "ferret", "fish"];
const uppercasePetsWithF = pets
  .filter((pet) => {
    return pet.startsWith("f");
  })
  .map((pet) => {
    return pet.toUpperCase();
  });
console.log(uppercasePetsWithF); // ['FERRET', 'FISH']
```

---

### `document.querySelectorAll`

With `document.querySelectorAll` you can select a list of elements from the DOM. This is in contrast
to `document.querySelector`, which provides only the first occurrence of an element matching the
selector.

```js
const pets = document.querySelectorAll('[data-js="pet"]');
console.log(pets.length); // 5
```

The `NodeList` returned by `document.querySelectorAll` is an array-like object. You can use the
`forEach` method to iterate over the DOM elements.

```js
const pets = document.querySelectorAll('[data-js="pet"]');
pets.forEach((pet) => {
  pet.addEventListener("click", () => {
    // [...]
  });
});
```

> ❗️ A `NodeList` is not an array! Other array methods like `map` or `filter` can't be used. If you
> need to use array methods, you can convert the `NodeList` to an array using `Array.from()`

---

### Resources

- [MDN web docs: Array forEach](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/forEach)
- [MDN web docs: Array map](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/map)
- [MDN web docs: Array filter](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/filter)
- [MDN web docs: NodeList](https://developer.mozilla.org/en-US/docs/Web/API/NodeList)

## JS Array Methods 2

### Learning Objectives

- [ ] Understanding advanced array methods
  - [ ] `includes`
  - [ ] `find` and `findIndex`
  - [ ] `sort` and `reverse`
    - [ ] know how to use `slice()` to make a copy
  - [ ] `some` and `every`
  - [ ] `reduce`

---

### `includes`

Use `array.includes()` to check whether the array contains the specified value. If it does, `true`
is returned, otherwise `false`.

```js
const colors = ["hotpink", "aquamarine", "granite"];

colors.includes("aquamarine"); // true
colors.includes("nemo"); // false
```

---

### `find` and `findIndex`

Use `find()` to receive **the first element** of the array that satisfies the provided testing
function. Otherwise, it returns `undefined`.

```js
const colors = ["hotpink", "aquamarine", "granite", "grey"];

colors.find((color) => color.startsWith("g")); // 'granite'
colors.find((color) => color.startsWith("b")); // undefined
```

Use `findIndex()` to receive the index **of the first element** of the array that satisfies the
provided testing function. If there is no such element, `-1` is returned.

```js
const colors = ["hotpink", "aquamarine", "granite", "grey"];

colors.findIndex((color) => color.startsWith("g")); // 2
colors.findIndex((color) => color.startsWith("b")); // -1
```

---

### `sort` and `reverse`

Use `sort()` to sort the elements of an array. You need to provide a callback function in order to
tell how the array is sorted.

### Sorting Numbers

```js
const numbers = [4, 42, 23, 1];

numbers.sort((a, b) => a - b); // [1, 4, 23, 42]
numbers.sort((a, b) => b - a); // [42, 23, 4, 1]
```

The sorted order is based on the return value of `a - b` / `b - a` :

| Return value of `a - b` | sort order                         |
| ----------------------- | ---------------------------------- |
| > 0                     | sort `a` after `b`                 |
| < 0                     | sort `a` before `b`                |
| === 0                   | keep original order of `a` and `b` |

> 💡 `sort()` converts the elements into strings, then compares their sequences of UTF-16 Code units
> values. This is why `array.sort()` without a callback is mostly useless.

### Sorting Strings

In order to sort strings, you need to tell the `sort()` method two things inside of the callback
function:

- lowercase both strings before comparing them (uppercase works as well)
- using if-statements, be explicit about the return values dependent on the result of the comparison
  (`nameA < nameB` and `nameA > nameB`)

```js
const strings = ["Xbox", "PlayStation", "GameBoy"];

strings.sort((a, b) => {
  const nameA = a.toLowerCase();
  const nameB = b.toLowerCase();
  if (nameA < nameB) {
    return -1;
  }
  if (nameA > nameB) {
    return 1;
  }
  return 0;
});

console.log(strings); // ['GameBoy', 'PlayStation', 'Xbox']
```

> 💡 In UTF-16, the upper- and lowercase version of the same letter do not have the same value. An
> uppercase 'H' has the UTF-16 decimal value of 72, while the lowercase 'h' has a value of 104.
>
> For example, an uppercase 'W' (87) and a lowercase 'd' (100) are sorted behind the uppercase 'H'
> (72), but before the lowercase 'h' (104); the result would look like ['H', 'W', 'd', 'h']. This is
> why it's necessary to upper- or lowercase all letters before sorting them.

### `reverse`

In order to reverse an array, simply use `array.reverse()`. This can be combined with `sort()` as
well:

```js
const numbers = [4, 42, 23, 1];

const reversedNumbers = numbers.reverse(); // [1, 23, 42, 4]
```

### `slice`

It's important to note that some array methods, as `sort()`, do not create a new array, but mutate
the original one.

```js
const numbers = [4, 42, 23, 1];

console.log(numbers); // [4, 42, 23, 1]

const sortedNumbers = numbers.sort((a, b) => a - b);

console.log(sortedNumbers); // [1, 4, 23, 42]
console.log(numbers); // [1, 4, 23, 42]

// What happens if sortedNumbers is reversed?

const reversedSortedNumbers = sortedNumbers.reverse();

console.log(reversedSortedNumbers); // [42, 23, 4, 1]
console.log(sortedNumbers); // [42, 23, 4, 1]
console.log(numbers); // [42, 23, 4, 1]
```

This behaviour will often cause errors. To prevent it, just make a copy of the original array using
`slice()`.

```js
const numbers = [4, 42, 23, 1];

console.log(numbers); // [4, 42, 23, 1]

const sortedNumbers = numbers.slice().sort((a, b) => a - b);

console.log(sortedNumbers); // [1, 4, 23, 42]
console.log(numbers); // [4, 42, 23, 1]
```

---

### `some` and `every`

Use `some()` to test whether **at least one element** in the array passes the provided test.

```js
const colors = ["hotpink", "aquamarine", "granite"];

colors.some((color) => color.startsWith("g")); // true
colors.some((color) => color.startsWith("i")); // false
```

In order to check if **all elements** pass the test, use `every()`.

```js
const colors = ["hotpink", "aquamarine", "granite"];

colors.every((color) => color.length > 5); // true
colors.every((color) => color.length < 3); // false
```

---

### `reduce`

`Array.reduce()` is an array method to reduce a list of values into a single value.

It has the following core features:

- starting from the beginning, it executes the callback function on each element of the array,
- the return value of each calculation is passed to the next calculation (i.e. it becomes the new
  starting value for the next iteration through the array)
- the final result is a single value.

It's main use case is to calculate the sum of an array of numbers.

```js
const numbers = [4, 42, 23, 1];

numbers.reduce((a, b) => a + b);

console.log(numbers); // 70
```

> ❗️ If you find yourself doing anything more complex than this with reduce (like reducing an array
> to an object, etc.) you should try to find another solution to your problem. Complex reduce
> functions are very hard to read and thus error prone.
>
> Example of reducing an array to an object without `reduce()`:
>
> ```js
> const myArray = [
>   { foo: 1, bar: "hi" },
>   { foo: 4, bar: "hey" },
>   { foo: 2, bar: "ho" },
> ];
> const myObject = {};
> myArray.forEach((element) => {
>   myObject[element.bar] = element.foo;
> });
>
> console.log(myObject); // {hi: 1, hey: 4, ho: 2}
> ```

---

### Resources

- [Searching Arrays (javascript.info)](https://javascript.info/array-methods#searching-in-array)
- [sort (javascript.info)](https://javascript.info/array-methods#sort-fn)
- [reduce (javascript.info)](https://javascript.info/array-methods#reduce-reduceright)

## JS Forms

### Learning Objectives

- knowing the default behavior of form submit
  - understanding why to prevent this behavior with `.preventDefault()`
- knowing how to listen to submit events: the `event` object and its `target` property
- reading input values:
  - `event.target.elements`
  - `FormData`
  - the role of `name` attributes for form fields

---

#### Understanding the Default Behavior of Form Submit

If you click the submit button of a form, it triggers the following default behavior (without
writing _any_ JavaScript):

- The form sends a GET request with names and their values as prop inside an URL like
  `/?firstName=value1&lastName=value2&...`.
- The page is reloaded and thus the data is lost for us.

None of that is useful, if we want to do something with the submitted data in our frontend code. You
can prevent this behavior with a method called `.preventDefault()`.

---

#### Listening to the `submit` event and preventing the Default Behavior

In order to prevent this behavior of the `submit` event, you need to

- receive the event object as an argument of the event listener arrow function
- call `event.preventDefault()`

```js
const form = document.querySelector('[data-js="form"]');

form.addEventListener("submit", (event) => {
  event.preventDefault();
});
```

By calling `event.preventDefault()` the browser will not perform a GET request that would cause the
page to reload on submit.

---

#### The `event` Object and `event.target`

The `event` object is created whenever an event is triggered. You can accept it as the first
parameter in the callback function and thus access it inside the function body (e.g. via
`event.preventDefault()`).

For now, the most important method of the `event` object is `.preventDefault()`.

`event.target` is a reference to the element to which the event originated from - in this case - the
form.

```js
form.addEventListener("submit", (event) => {
  event.preventDefault();

  console.log(event.target);
});
// Output:
// <form data-js="form">
//		<fieldset>...</fieldset>
//		...
//		<button type="submit">Submit</button>
//	</form>
```

---

#### Accessing Interactive Fields: `event.target.elements` and the `name` Attribute

While `event.target` represents the entire form, `event.target.elements` is a collection of all form
elements (form fields, field sets and buttons).

You get access to a specific form field via its `name` attribute and dot notation:

```js
form.addEventListener("submit", (event) => {
  event.preventDefault();

  const formElements = event.target.elements;

  console.log(formElements.firstName);
  console.log(formElements.firstName.value);
});
```

Note that

- `event.target.elements` is stored in the variable `formElements` for better readability,
- `firstName` is the string value of the corresponding `name` attribute, as in
  `<input name="firstName"/>`, and
- `firstName.value` returns the user input for the field with `name="firstName"`.

---

#### Using Input Values

You can access all input values of the form by using `FormData()`. This constructor uses
`event.target` and can be transformed into a usable object afterwards:

```js
form.addEventListener("submit", (event) => {
  event.preventDefault();

  const formData = new FormData(event.target);
  const data = Object.fromEntries(formData);

  console.log(data);
});
```

This is very useful to easily access the input data of an entire form.

> 💡 Despite the fact that using `FormData` is much less verbose, `event.target.elements` is very
> useful if you want to access single form field. (Spoiler alert: In case you want to focus a
> specific field after resetting the form, for example.)

#### Exception: Reading Values from Checkboxes

Checkboxes have two states: checked ("true") and not checked ("false"). In contrast to other input
types, the `value` attribute does not reflect this change, but is only used as an identifier for the
checkbox.

You can access the checkbox's state via the `.checked` property instead.

Imagine the following checkbox

```html
<input type="checkbox" name="colorBlue" value="blue" />
```

and its corresponding JavaScript:

```js
console.log(formElements.colorBlue.checked); // output: true or false
console.log(formElements.colorBlue.value); // output (always): blue
```

---

### Resources

- [Event interface](https://developer.mozilla.org/en-US/docs/Web/API/Event#properties)

## JS Forms 2

### Learning Objectives

- knowing ways for client-side form validation
- understanding the input event
- knowing how to focus an input field programmatically
- knowing how to reset a form

---

#### HTML Form Validation

Before submitting a form, it is important to ensure all required form fields are filled out, in the
correct format. This is called **client-side form validation**.

HTML provides several form field attributes to enable validation features build into the browser.

| Attribute                 | Description                                                                                                                                        |
| ------------------------- | -------------------------------------------------------------------------------------------------------------------------------------------------- |
| `required`                | if present, a form field needs to be filled in before the form can be submitted                                                                    |
| `minlength` / `maxlength` | minimum and maximum length of textual data (strings)                                                                                               |
| `min` / `max`             | minimum and maximum values of numerical input types                                                                                                |
| `type`                    | each input type has its own prefigured validation (like `email`)                                                                                   |
| `pattern`                 | [a regular expression pattern](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Guide/Regular_Expressions) the entered data needs to follow |

The following input field is valid if its value exists and it is a string between 3 and 30
characters:

```html
<input
  id="input-name"
  type="text"
  name="name"
  minlength="3"
  maxlength="30"
  required
/>
```

> ❗️ If the `required` attribute is omitted, the field is valid if it is empty or has a content
> between 3 and 30 characters, but invalid if 1 or 2 characters are entered.

`type="email"` will check if the input is a valid email address.

```html
<input id="input-email" type="email" name="email" />
```

---

#### The `input` Event

Occasionally, you may want to do something if the value of a single field changes even before the
form is submitted.

The `input` event is fired every time when the value of a form field has been changed. For example,
a `<textarea />` will fire this event with every keystroke.

```js
const messageField = document.querySelector('[data-js="message"]');

messageField.addEventListener("input", (event) => {
  console.log(event.target.value);
});
```

> ❗️ Don't confuse the `input` event with the `change` event, which is only fired after a field's
> content has been committed by the user by pressing enter or moving the focus to the next field.

---

#### Focus Input Fields

You can focus an input field with the `.focus()` method. This can be used to improve the user
experience after submitting a form.

```js
const messageField = document.querySelector('[data-js="message"]');

form.addEventListener("submit", (event) => {
  event.preventDefault();
  // [...] handle form data
  messageField.focus();
});
```

Instead of querying the input element using `querySelector`, it can also be obtained via the
`event.target.elements` collection:

```js
form.addEventListener("submit", (event) => {
  event.preventDefault();
  // [...] handle form data
  event.target.elements.message.focus();
});
```

This will focus a form field with the attribute `name="message"`.

---

#### Resetting Forms

You can reset all form fields to their default value with the `.reset()` method.

```js
form.addEventListener("submit", (event) => {
  event.preventDefault();
  // [...] handle form data
  event.target.reset();
});
```

This often comes in handy in combination with `.focus()`. Think of a chat: After the message was
send, the input field is cleared and re-focussed, so users can write the next message.

---

### Resources

- [MDN web docs: Client-side form validation](https://developer.mozilla.org/en-US/docs/Learn/Forms/Form_validation)
- [MDN web docs: input event](https://developer.mozilla.org/en-US/docs/Web/API/HTMLElement/input_event)

## JS createElement

### Learning Objectives

- knowing what the DOM is
- learning how to generate HTML in JavaScript
- using HTML element object properties and methods
- learning how to use `.innerHTML`

---

### The DOM

The **Document Object Model** is a representation of the HTML document. Each HTML Tag is modelled as
a **node** in a tree structure, which shows how HTML elements are nested. A computer program such as
your JavaScript file can access and manipulate the HTML website by changing the DOM via the
`document` object. ![the DOM](assets/DOM.png)

### `document.createElement`

You can generate an HTML element with JavaScript by using the `document.createElement` method. It
expects the type of element as an argument.

```js
const article = document.createElement("article");
const button = document.createElement("button");
```

After generating an element, you need to place the element into the DOM. For this, you can use the
`.append` method. It places the element as the **last child** into the respective element.

```js
document.body.append(article); // placing the created article at the end of the body
article.append(button); // placing the created button into the article
```

The result looks like this:

```html
<body>
  ...
  <article>
    <button></button>
  </article>
</body>
```

---

### Element Properties and Methods

As well as with queried HTML elements (via `querySelector`), we can add classes, event listeners and
more to the created HTML elements.

```js
article.classList.add("card");

button.addEventListener("click", () => {
  console.log("It works!");
});
```

The text of an element can be changed by reassigning the `.textContent` property:

```js
button.textContent = "Click me!";
```

#### Common Element Properties and Methods

| Property          | Effect                                                             |
| ----------------- | ------------------------------------------------------------------ |
| `classList`       | add, toggle or remove classes from element                         |
| `textContent`     | get or set text inside element                                     |
| `style`           | define inline style, e.g. `element.style.backgroundColor = "red" ` |
| `hidden`          | boolean whether element is hidden or not                           |
| `focus()`         | focusses the element on the website                                |
| `hasAttribute()`  | returns true if the element has the given attribute                |
| `querySelector()` | returns the first child that matches the given CSS selector        |

> 💡 You can assign HTML attributes by using the element properties. Go to the
> [MDN Docs](https://developer.mozilla.org/en-US/docs/Web/API/Element#properties) for a
> comprehensive list of element properties.

---

### `.innerHTML`

> ❗️ innerHTML can be unsafe when user input is passed into the template literal. Use it with
> caution. Read
> [this article](https://developer.mozilla.org/en-US/docs/Web/API/Element/innerHTML#replacing_the_contents_of_an_element)
> for more information about it.

The `innerHTML` property can be used to create the entire html layout of an element by passing the
html code as a string. By using **template literals** the content of the html can be dynamically
created.

```js
const cityName = "Lissabon";

article.innerHTML = `
	<h2> ${cityName} </h2>
	<p class="card__content">
		${cityName} is a very beautiful city in Portugal. 
		Go there and enjoy the stay!
	</p>
	<button type='button' class="card__booking-button"> 
		Book Trip 
	</button>
`;
```

This HTML code is rendered then **inside** the article element:

```html
<body>
  ...
  <article>
    <h2>Lissabon</h2>
    <p class="card__content">
      Lissabon is a very beautiful city in Portugal. Go there and enjoy the
      stay!
    </p>
    <button type="button" class="card__booking-button">Book Trip</button>
  </article>
</body>
```

#### Resetting Element Content

`.innerHTML` can also be used to **reset** the content of an element, e.g. a container:

HTML before:

```html
<ul data-js="cardContainer">
  <li class="card">...</li>
  <li class="card">...</li>
  <li class="card">...</li>
</ul>
```

By setting the innerHTML to an empty string, the content is deleted:

```js
const cardContainer = document.querySelector('[data-js="cardContainer"]');
cardContainer.innerHTML = "";
```

The result:

```html
<ul data-js="cardContainer"></ul>
```

---

### Resources

#### Element Properties

[MDN Docs about element Properties](https://developer.mozilla.org/en-US/docs/Web/API/Element#properties)

#### innerHTML

[MDN Docs about securtiy risks with innerHTML](https://developer.mozilla.org/en-US/docs/Web/API/Element/innerHTML#replacing_the_contents_of_an_element)

## JS Functions

### Learning Objectives

- writing functions in JavaScript
- calling functions
- using function parameters
- learning what 'scope' is

---

### Functions

Functions are a fundamental concept in JavaScript. They contain a set of statements - in other
words: They contain JavaScript code. Functions have to be defined. When a function is defined it can
be called an arbitrary number of times.

---

### Function Declarations

You can define a function using a **function declaration** which consists of:

- the function keyword
- the function name
- the function body (JavaScript statements / JavaScript code)

```js
function greet() {
  console.log("Hi Friends!");
  console.log("Nice to be here.");
}
```

> ❗️ Defining a function does not cause the JavaScript code in the function body to be executed.
> You have to call the function for the code to be executed.

#### Parameters

Functions can accept parameters. Parameters can be used like predefined variables inside the
function body. When declaring a function we are free to choose a name for the parameters, but
descriptive, short names should be chosen.

```js
function printLetter(name) {
  console.log("Hi " + name + ", hope you are fine. Love, Johnny");
}

function printSum(first, second, third) {
  const sum = first + second + third;
  console.log("The sum of your numbers is: " + sum);
}
```

---

### Function Calls

When functions are defined you can call them by writing their name, followed by parentheses
("round brackets"). If the functions consume parameters you can pass them as arguments in the
brackets.

```js
greet();
/*
This will cause the following to be logged into the console:
Hi Friends!
Nice to be here.
*/

printLetter("Max");
printLetter("Jordan");
/*
This will cause the following to be logged into the console:
Hi Max, hope you are fine. Love, Johnny
Hi Jordan, hope you are fine. Love, Johnny
*/

printSum(1, 2, 3);
printSum(3, 4, 5);
/*
This will cause the following to be logged into the console:
The sum of your numbers is: 6
The sum of your numbers is: 12
*/
```

---

### Scope

The scope defines where variables are visible and where they can be referenced. In JavaScript there
are different kinds of scope, for example:

- global scope
- function scope

#### Function scope

Variables defined **inside a function** are not accessible from outside. But all variables **outside
of the function** can be accessed from inside the function body:

```js
const globalVariable = "some Text";

function myFunction() {
  const localVariable = true;

  console.log(globalVariable);
  console.log(localVariable);
}

myFunction();
// logs:
// some Text
// true

console.log(localVariable); // Error! Variable not available outside of function
```

#### Global scope

A variable is in the **global scope** when it is declared outside of any function, in a JavaScript
file. Global variables are visible and can be accessed from anywhere in that JavaScript file after
declaration.

---

### Resources

[MDN docs: Functions](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Guide/Functions)
[MDN docs: Scope](https://developer.mozilla.org/en-US/docs/Glossary/Scope)

## JS Functions 2

### Learning Objectives

- What a return statement of a function is and how to use it in your JavaScript functions
- What an `early return` is
- How to write functions with the `fat arrow notation`

---

### Return Statements

Functions are an incredible versatile and central tool in most programming languages. We already
learned how to pass values into a function with input parameters. But a function can also return a
value back to the place where it was called. This is done via a `return statement`.

```js
function add3Numbers(first, second, third) {
  const sum = first + second + third;
  return sum;
}
```

The `return statement` begins with the keyword `return` followed by an expression. This this case,
the expression is the variable sum. Its value is returned by the function and can be stored when the
function is called:

```js
const firstSum = add3Numbers(1, 2, 3);
// the return value is stored in "firstSum", namely 6

const secondSum = add3Numbers(4, 123, 33);
// the return value is now stored in "secondSum", namely 160
```

> 💡 An expression is anything that produces a value: a variable, a hardcoded value like `true` or
> `6`, a math operation like `2 + 3` or even another function call!
> [This article](https://www.joshwcomeau.com/javascript/statements-vs-expressions/) explains this in
> greater depth.

By this, we can outsource computations and / or decision processes and continue using the returned
value in the program.

A function can return only one expression value, but can have multiple return statements, in
combination with if else statements for example:

```js
function checkInputLength(inputString) {
  if (inputString.length > 3) {
    return true;
  } else {
    return false;
  }
}
```

### Early Return Statements

As soon as a return statement is reached in a function call, the function execution is ended. The
following `console.log()` is therefore never reached:

```js
function testFunction() {
  return "a returned string";

  console.log("I am never logged in the console.");
}
```

This behavior can be used to our advantage as early return statements. Sometimes we want to execute
certain parts of our code only if a condition applies. We can check this with an if else statement.
When multiple conditions are in place, the code becomes harder to read and to understand:

```js
function setBackgroundColor(color) {
  if (typeof color === "String") {
    if (color.startsWith("#")) {
      if (color.length >= 7) {
        document.body.style.backgroundColor = color;
      }
    }
  }
}
```

An alternative approach is to terminate the function with early return statements:

```js
function setBackgroundColor(color) {
	// first condition
	if(typeOf color !== 'String') {
		return;
	}

	// second condition
	if(!color.startsWith('#')) {
		return;
	}

	// third condition
	if(color.length < 7) {
		return;
	}

	// only if all 3 conditions are passed the final line of code is executed.
	body.style.backgroundColor = color;
}

```

This way of writing the code is more readable

💡 Hint: A return statement can be left empty, the returned value is then `undefined`.

### Arrow Function Expressions

Next to the classic function declaration, JavaScript has a second way to write functions as
`arrow function expressions`:

```js
const addNumbers = (first, second) => {
  return first + second;
};
```

The function is saved like a variable with the keyword `const`. The parameters are written normally
in round brackets followed by an fat arrow `=>`. Then the function body is written in curly
brackets.

#### Implicit Return Statements

The advantage of arrow functions are possible shorter notations when certain criteria apply:

1. Omit the round brackets around the parameters: This is possible, if there is only one input:
   ```js
   const addOne = (number) => {
     return number + 1;
   };
   ```
2. Implicit return statements: If the function consists only of a return statement, the curly
   brackets and the return keyword can be omitted:
   ```js
   const addNumbers = (first, second) => {
     return first + second;
   };
   ```
   can be rewritten as:
   ```js
   const addNumbers = (first, second) => first + second;
   ```

> 💡 This shorthand notation comes in handy as soon as we work with callback functions in a few
> days. So try to remember this feature.

> 💡 Maybe you remember the syntax of the `addEventListener` method. We encountered these arrow
> functions there already!
>
> ```js
> button.addEventListener('click',() => {
> 	...
> })
> ```

---

### Resources

- [Statements vs Expressions by Josh Comeau](https://www.joshwcomeau.com/javascript/statements-vs-expressions/)

## JS Callback Functions

### Learning Objectives

- Understanding the concept of callback functions
- Using an anonymous callback function
- Using a named function as a callback function
- Knowing what a higher order function is

---

### Callback Functions

A callback function is a function that is passed **as an argument** into another function.

The outer function can execute this callback function at the correct moment or multiple times, for
example:

- when an event is triggered
- when the fetched data arrived on your computer
- for each element in an array.

Callback functions are used, whenever the program itself needs to figure out **when** or **how many
times** the function needs to be executed. We already used callback functions in **event
listeners**:

```js
button.addEventListener("click", () => {
  console.log("Inside the callback function.");
});
```

Here the structure is as follows:

- outer function: `addEventListener()`
- first argument: `'click'`
- second argument: callback function
  ```js
  () => {
    console.log("Inside the callback function.");
  };
  ```

This type of function is called **anonymous function**, since it is declared without giving it a
name.

### Named Callback Functions

Any function can be used as a callback function. It just needs to be passed to another function. You
can declare a normal function and then use the **name of the function** to pass it into another
function:

```js
function sayHello() {
  console.log("Hey Dude!");
}

button.addEventListener("click", sayHello);
```

> ❗️ Note that we do not call the function here (we wrote `sayHello` instead of `sayHello()`). We
> only pass the function to the event listener. The function is only called when the event happens.

### Higher Order Functions

A higher order function is a function that takes a **callback function as an argument** and **calls
the callback function** inside their body, e.g. the `addEventListener` method.

```js
// this function calls its callback function 3 times!
function myHigherOrderFunction(callback) {
  callback();
  callback();
  callback();
}
```

We will encounter these higher order functions in future sessions:

- `.then`
- `.forEach`
- `.map`
- `.filter`

> 💡 Don't worry, you don't have to write higher order functions yourself, you only apply them to
> solve certain problems.

### Parameters in Callback Functions

A callback function can accept parameters. The values for the parameters are provided by the
function, that calls the callback function (the "higher order function").

In this example the callback function can accept a parameter to retrieve information about the
occurred event:

```js
button.addEventListener("click", (event) => {
  console.log("This button was clicked:", event.target);
});
```

---

### Resources

- [MDN Callback Functions](https://developer.mozilla.org/en-US/docs/Glossary/Callback_function)

## JS Async Functions

### Learning Objectives

- Understanding how asynchronous code works
- Working with promises
- Using the `async` and `await` keywords

---

### Asynchronous Code

Asynchronous code is code that runs in the background. This is useful for tasks that can take a long
time to complete, but don't need to block the main thread.

JavaScript is a single-threaded language, meaning that only one thing can happen at a time.

Blocking the main thread is bad because it prevents the user from interacting with the page because
no other JavaScript code can be executed. Examples of asynchronous code include: network requests,
file system access, animations and timers.

### Promises

A Promise is an object that represents the eventual completion (or failure) of an asynchronous
operation, and its resulting value. Most of the time it is returned by a function that performs an
asynchronous operation.

The Promise object has the following properties and methods:

| Property / Method | Description                                                                                                                                             |
| ----------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `state`           | the state of the Promise object, can be `"pending"`, `"resolved"` or `"rejected"`                                                                       |
| `result`          | the result of the asynchronous operation (you'll almost never need to access this directly)                                                             |
| `then()`          | a method that takes a callback function that will be called when the asynchronous operation is complete                                                 |
| `catch()`         | a method that takes a callback function that will be called when the asynchronous operation fails                                                       |
| `finally()`       | a method that takes a callback function that will be called when the asynchronous operation is complete, regardless of whether it was successful or not |

```js
functionThatReturnsAPromise().then((value) => {
  console.log(value);
});
```

> 💡 Promises are almost always created for you by other asynchronous APIs, only rarely do you
> create them yourself. If you create a Promise yourself (`new Promise()`), you either know exactly
> what you are doing, or you are probably doing something wrong.

---

### Asnyc Functions and the `await` Keyword

Asnyc functions are a syntactic sugar for Promises. Using the `await` keyword, you can write
asynchronous code that looks synchronous. Any function can be prefixed with the `async` keyword:

```js
async function myAsyncFunction() {
  // ...
}

const myAsyncArrowFunction = async () => {
  // ...
};
```

Inside an async function, you can use the `await` keyword to wait for a Promise to be resolved:

```js
async function myAsyncFunction() {
  const value = await functionThatReturnsAPromise();
  console.log(value);
}
```

This is can be easier to read than the Promise syntax especially when you have multiple asynchronous
operations that depend on each other.

```js
async function myAsyncFunction() {
  const value1 = await functionThatReturnsAPromise1();
  const value2 = await functionThatReturnsAPromise2(value1);
  const value3 = await functionThatReturnsAPromise3(value2);
  console.log(value3);
}
```

Compared to:

```js
// avoid doing this:
function myFunction() {
  functionThatReturnsAPromise1()
    .then((value1) => {
      return functionThatReturnsAPromise2(value1);
    })
    .then((value2) => {
      return functionThatReturnsAPromise3(value2);
    })
    .then((value3) => {
      console.log(value3);
    });
}
```

> 💡 `async` functions always return a Promise. If the function returns a value, the Promise will be
> resolved with that value. Even if you're not using the `return` keyword the function will return a
> Promise that resolves to `undefined` when it reaches the end of it's scope. If the function throws
> an error, the Promise will be rejected with that error.

---

### Handling Errors

When using Promises, you can use the `catch()` method to handle errors. Using `async` functions, you
can use the `try`/`catch` syntax.

### `try`/`catch`

```js
async function myAsyncFunction() {
  try {
    const value = await functionThatReturnsAPromise();
    console.log(value);
  } catch (error) {
    console.error(error);
  }
}
```

The `try` block will be executed, and if an error is thrown, the `catch` block will be executed. The
`catch` block has access to the error that was thrown.

If any error is thrown in the `try` block, the `catch` block will be executed immediately aborting
the execution of any further code in the `try` block:

```js
async function functionThatThrowsAnError() {
  throw new Error("ooops 🫣");
}

async function myAsyncFunction() {
  try {
    const value = await functionThatThrowsAnError();
    // The following code will never be executed because
    // `functionThatThrowsAnError()` throws an error.
    // The execution will jump to the `catch` block.
    console.log(value);
    const value2 = await functionThatReturnsAPromise2();
    console.log(value2);
  } catch (error) {
    console.error(error);
  }
}
```

### `finally`

You can also use a `finally` block after any `try` block to run code after the `try` block is
resolved, regardless of whether it was successful or not:

```js
async function myAsyncFunction() {
  try {
    const value = await functionThatReturnsAPromise();
    console.log(value);
  } catch (error) {
    console.error(error);
  } finally {
    console.log("done");
  }
}
```

### `try`/`catch` is not limited to `async` Functions

The `try`/`catch`/(`finally`) syntax is not limited to `async` functions, you can use it with any
JavaScript code that might throw an error.

```js
function functionThatThrowsAnError() {
  throw new Error("ooops 🫣");
}

function myFunction() {
  try {
    functionThatThrowsAnError();
    console.log("this will never be executed");
  } catch (error) {
    console.error(error);
  } finally {
    console.log("done");
  }
}
```

### Parallel Promises

#### `Promise.all()`

If you have multiple asynchronous operations that you want to run in parallel, you can use
`Promise.all()`.

`Promise.all()` takes an array of Promises and returns a Promise that resolves to an array of the
results of the Promises in the same order.

```js
async function myAsyncFunction() {
  try {
    const values = await Promise.all([
      functionThatReturnsAPromise1(),
      functionThatReturnsAPromise2(),
      functionThatReturnsAPromise3(),
    ]);
    console.log(values); // [value1, value2, value3]
  } catch (error) {
    console.error(error);
  }
}
```

This will run all three asynchronous operations in parallel, and wait for all of them to complete
before continuing. If any of the asynchronous operations fail, `Promise.all()` will fail as well.

#### Controlling when to Resolve or Reject Parallel Promises

There are advanced use cases where you might want to control when to resolve or reject a Promise.
`Promise.allSettled()` (does not care if Promises are rejected or resolved) and `Promise.any()`
(resolves once the first Promise is resolved) are two methods that allow you to do that.

### Asynchronous Browser APIs

Here are some examples of asynchronous browser APIs that return a Promise:

- `fetch()` — makes an HTTP request and returns a Promise that resolves to a `Response` object
- `element.animate().finished` — animates an element and returns a Promise that resolves when the
  animation is complete
- `navigator.getBattery()` — gets the current battery level and returns a Promise that resolves with
  the battery level

---

### Resources

- [Thread on mdn](https://developer.mozilla.org/en-US/docs/Glossary/Thread)
- [Asynchronous on mdn](https://developer.mozilla.org/en-US/docs/Glossary/Asynchronous)
- [Using Promises on mdn](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Guide/Using_promises)
- [Async functions on mdn](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Statements/async_function)
- [Promise.all() on mdn](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Promise/all)
- [try...catch on mdn](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Statements/try...catch)

## JS Fetch

### Learning Objectives

- [ ] Understanding the fetch API
  - [ ] with async/await
  - [ ] JSON
  - [ ] HTTP Response Codes
  - [ ] REST API
  - [ ] Error Handling

---

### What is an API?

The term _API_ is short for _Application Programming Interface_.

An _API_ provides a way one software (the _application_) can interact with another software.
Therefore, an application can define a set of features and rules on how other software can interact
with it. This is called an _interface_. Think of a contract between two softwares that explains how
they can work together.

APIs can be seen from different perspectives and occur on various levels.

A browser provides a lot of [Web APIs](https://developer.mozilla.org/en-US/docs/Web/API). Each Web
API defines a way on how a JavaScript application can use a feature given by the browser, like:

- [Web Animations API](https://developer.mozilla.org/en-US/docs/Web/API/Web_Animations_API)
- [Battery API](https://developer.mozilla.org/en-US/docs/Web/API/Battery_Status_API)
- [Fetch API](https://developer.mozilla.org/en-US/docs/Web/API/Fetch_API)

APIs running on a server environment are a different type of API. They are provided by a _server_,
opposing to the APIs provided by the browser (which is also called the _client_). A common use-case
for such APIs is to read / load data. Other operations like writing or deleting data is also
possible. There are common approaches regarding the architecture of a serve-side API. One such
approach are REST-APIs, which is explained later in this document.

---

### Fetch API (with async & await)

`fetch` is a [web API](https://developer.mozilla.org/en-US/docs/Web/API) to asynchronously fetch
(load) resources from the network, like text documents.

```js
async function fetchData() {
  const response = await fetch("/url/to/something");
  const data = await response.json();
  return data;
}
```

This is what happens in the example above:

1. We mark the function with the `async` keyword, because we want to use `await` inside the
   function.
2. We declare a variable named `response`. It stores the Response object that is returned by
   `fetch`.
3. Once this promise resolves (the network request is finished), we call the `.json` method on the
   `response` variable. This function returns another Promise.
4. This second promise resolves with the actual data (payload) converted from JSON (a formatted
   string) to a JavaScript value or object. This result is stored in the variable named `data`.
5. The function returns the value stored in the `data` variable.

> 💡 The `async` and `await` syntax helps with handling the two consecutive promises required to get
> the response data (opposing to the nested syntax using `.then()`)

> 💡The `Response` object features other useful methods (all returning promises), among which are
> the following:
>
> - `response.json()` returns a Promise that resolves to the downloaded data JSON-parsed as a
>   JavaScript value or object
> - `response.text()` returns a Promise that resolves to the downloaded data as raw text
> - `response.formData()` returns a Promise that resolves to the downloaded data parsed as FormData
> - `response.blob()` returns a Promise that resolves to the downloaded data as a raw blob (that's a
>   machine readable format using zeros and ones)

---

### JSON

JavaScript Object Notation (JSON) is a standard text-based format for representing structured data
based on JavaScript object syntax. It is commonly used for transmitting data between a client
(browser) and a server in web applications.

JSON is very close to being a subset of JavaScript syntax. Most valid JSON is also valid JavaScript
code. This means that you can copy JSON into any `.js` file, put a `const myData =` in front, and
watch Prettier make it look like _real_ JavaScript. On the flip side valid JavaScript is not valid
JSON. It looks like this:

```json
{
  "groupName": "Students",
  "groupSize": 100,
  "students": [
    {
      "name": "John Doe",
      "age": 42,
      "location": "Pleasantville",
      "member": true,
      "groups": ["students", "citizens", "new"]
    },
    {
      "name": "Jane Doe",
      "age": 44,
      "location": "Pleasantville",
      "member": true,
      "groups": ["students", "citizens", "new"]
    },
    {
      "name": "Sam Doe",
      "age": 24,
      "location": "Pleasantville",
      "member": true,
      "groups": ["students", "citizens", "new"]
    }
  ]
}
```

Even though it closely resembles JavaScript object literal syntax, it can be used outside of
JavaScript. Other programming languages often feature the ability to read (parse) JSON.

JSON exists as a string that needs to be converted to a native JavaScript object when you want to
access the data. No problem! - JavaScript provides a global JSON object that features conversion
methods in either direction.

> 💡 JSON Conversion Methods
>
> `JSON.parse()`
>
> This method parses a JSON string and constructs the JavaScript value or object described by the
> string.
>
> `JSON.stringify()`
>
> This methods converts a JavaScript value or object to a JSON string.

---

### HTTP Response Status Codes

HTTP response status codes usually indicate whether a specific HTTP request has been successfully
completed. For the most part, _any_ sort of response is considered a successful completion of the
request.

With the exception of custom server software, these responses are standardized. You can find a list
of HTTP response status codes [here](https://developer.mozilla.org/en-US/docs/Web/HTTP/Status).

One of the most well-known HTTP response status codes is
[`404 not found`](https://developer.mozilla.org/en-US/docs/Web/HTTP/Status/404), which most users of
the web might have already encountered at some point.

> 💡 Do you need a cute explanation of what the HTTP response codes mean? Just search for 'HTTP
> status dogs' (or cats if you like them better).

---

### Error Handling

It might be surprising that `fetch()` doesn't throw an error when the server returns a bad HTTP
status, e.g. client or server errors.

```js
async function fetchSomething() {
  const response = await fetch("/bad/url/oops");
  const something = await response.json();
  return something;
}
```

Assuming that in the above example `'bad/url/oops` doesn't lead to an existing location, the server
would respond with the status code `404` and the text `Page not found`. This is a **completed** HTTP
request.

A request will only register as rejected if a response cannot be retrieved. This may be due to
network problems, such as no internet connection, the host not being found, or the server not
responding.

We can separate _good_ from _bad_ HTTP response statuses by relying on the boolean `response.ok`
property. It is set to `true` only if the HTTP response code is between `200-299`.

In our example above, `response.ok` would be set to `false` and the response code would be `404`.

If something goes wrong that causes that we do not receive a response the fetch API throws an error.
Once an error is thrown execution stops and JavaScript looks for the closest `catch` block.

Any production `fetch` call should be inside a `try...catch` block:

```js
async function fetchSomething() {
  try {
    const response = await fetch("/bad/url/oops");

    if (response.ok) {
      // Success (Good Response)
      const data = await response.json();
      return data;
    } else {
      // Failure (Bad Response)
      console.error("Bad Response");
    }
  } catch (error) {
    // Failure (Network error, etc)
    console.error("An Error occurred");
  }
}
```

---

### REST API

When you create an API, you need to come up with ideas on how to structure your API, shape the
features you provide and which rules to apply. This is referred to as the architecture of your API.

There are different common approaches used across the web. A very popular one is REST API or RESTful
API.

REST is a set of architectural constraints, not a protocol or a standard. You as an API developer
can implement REST in a variety of ways.

> 💡 REST is short for REpresentational State Transfer

The overall idea is like this:

- A _client_ requests a _resource_ from a _server_ (like a document containing information on a
  specific topic)
- The _server_ formulates a response that represents the resource in a format the _client_
  understands (like JSON - other formats like HTML, XML oder plain text are also possible)
- This transfer of data changes the state of the web application.

Each resource has a unique address. The whole communication is done via HTTP and uses different HTTP
methods (like GET/POST/PUT/DELETE) to describe desired actions.

> 💡 This is a very basic and incomplete explanation. If you're interested in learning more about
> what makes an API RESTful, you can read about it [here](https://restfulapi.net/).
