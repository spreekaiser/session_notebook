# Javascript Methods Overview

Which function type returns which value?

## [Boolean-Methods](#boolean-methods-1)

- [ ] [toString()](#tostring)
- [ ] [valueOf()](#valueof)

## [String-Methods](#string-methods-1)

### returns a boolean

- [ ] [startsWith()](#startswith)
- [ ] [endsWith()](#endswith)
- [ ] [includes()](#includes)

### returns a number

- [ ] [indexOf()](#indexof)

### returns a string

- [ ] [at()](#at)
- [ ] [concat()](#concat)
- [ ] [slice()](#slice)
- [ ] [replace()](#replace)
- [ ] [substring()](#substring)
- [ ] [toUpperCase()](#touppercase)
- [ ] [toLowerCase()](#tolowercase)
- [ ] [toString()](#tostring)
- [ ] [trim()](#trim)
- [ ] [valueOf()](#valueof)

### returns an array

- [ ] [split()](#split)

## [Math-Methods for numbers](#math-methods-for-numbers-1)

### all methods return numbers

- [ ] [Math.abs()](#mathabs)
- [ ] [Math.ceil()](#mathceil)
- [ ] [Math.floor()](#mathfloor)
- [ ] [Math.max()](#mathmax)
- [ ] [Math.min()](#mathmin)
- [ ] [Math.pow()](#mathpow)
- [ ] [Math.random()](#mathrandom)
- [ ] [Math.round()](#mathround)
- [ ] [Math.sign()](#mathsign)
- [ ] [Math.sqrt()](#mathsqrt)
- [ ] [Math.trunc()](#mathtrunc)

## [Array-Methods](#array-methods-1)

### without retuns value

- [ ] [forEach()](#foreach)

### returns a boolean

- [ ] [some()](#some)
- [ ] [every()](#every)
- [ ] [includes()](#includes-1)
- [ ] [isArray()](#isarray)

### returns a String

- [ ] [join()](#join)

### returns a number

- [ ] [at()](#at-1)
- [ ] [findIndex()](#findindex)
- [ ] [push()](#push)
- [ ] [unshift()](#unshift)

### returns an array

- [ ] [concat()](#concat-1)
- [ ] [flat()](#flat)
- [ ] [filter()](#filter)
- [ ] [from()](#from)
- [ ] [map()](#map)
- [ ] [of()](#of)
- [ ] [slice()](#slice-1)

### returns the same modified array

- [ ] [fill()](#fill)
- [ ] [sort()](#sort)

### returns an element of the array

- [ ] [find()](#find)
- [ ] [findLast()](#findlast)
- [ ] [pop()](#pop)
- [ ] [shift()](#shift)

### returns an object

- [ ] [entries()](#entries)
- [ ] [values()](#values)

## [Object-Methods](#object-methods-1)

### returns a boolean

- [ ] [hasOwn()](#hasown)
- [ ] [is()](#is)
- [ ] [isFrozen()](#isfrozen)
- [ ] [isPrototypeOf()](#isprototypeof)
- [ ] [isSealed()](#issealed)

### returns a string object

- [ ] [toString()](#tostring-2)

### returns an array

- [ ] [entries()](#entries-1)
- [ ] [keys()](#keys)
- [ ] [values()](#values-1)

### returns an object

- [ ] [assign()](#assign)
- [ ] [create()](#create)
- [ ] [fromEntries()](#fromentries)
- [ ] [seal()](#seal)
- [ ] [valueOf()](#valueof-2)

## Boolean-Methods

- ### toString()

The `toString()` method returns a string representing the specified boolean value.

The Boolean object overrides the `toString` method of Object; it does not inherit
`Object.prototype.toString()`. For Boolean values, the `toString` method returns a
string representation of the boolean value, which is either `"true"` or `"false"`.

The `toString()` method requires its this value to be a Boolean primitive or wrapper object.
It throws a TypeError for other this values without attempting to coerce them to boolean values.

Because Boolean doesn't have a [@@toPrimitive]() method, JavaScript calls the `toString()`
method automatically when a Boolean object is used in a context expecting a string, such
as in a template literal. However, boolean primitive values do not consult the `toString()`
method to be coerced to strings — rather, they are directly converted using the same algorithm
as the initial `toString()` implementation.

```js
const flag1 = new Boolean(true);
console.log(flag1.toString()); // Expected output: "true"

const flag2 = new Boolean(1);
console.log(flag2.toString()); // Expected output: "true"

Boolean.prototype.toString = () => "Overridden";
console.log(`${true}`); // "true"
console.log(`${new Boolean(true)}`); // "Overridden"

const flag = new Boolean(true);
console.log(flag.toString()); // "true"
console.log(false.toString()); // "false"
```

#### Return value

A string representing the specified boolean value.

> #### -> see more about `toString()`: [here](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Boolean/toString)
>
> #### 👆🏽 go up to [Boolean-Methods](#boolean-methods)

- ### valueOf()

The `valueOf()` method of `Boolean` returns the primitive value of a `Boolean`
object or literal `Boolean` as a `Boolean` data type.

This method is usually called internally by JavaScript and not explicitly in code.

```js
const x = new Boolean();
console.log(x.valueOf()); // Expected output: false

const y = new Boolean("Mozilla");
console.log(y.valueOf()); // Expected output: true

x = new Boolean();
myVar = x.valueOf(); // assigns false to myVar
```

#### Return value

The primitive value of the given Boolean object.

> #### -> see more about `valueOf()`: [here](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Boolean/valueOf)
>
> #### 👆🏽 go up to [Boolean-Methods](#boolean-methods)

## String Methods

- ### startsWith()
  The `startsWith()` method determines whether a string begins with the characters of a
  specified string, returning `true` or `false` as appropriate.
  This method lets you determine whether or not a string begins with another string.
  This method is case-sensitive.

```js
const str1 = "Saturday night plans";

console.log(str1.startsWith("Sat"));
// Expected output: true
console.log(str1.startsWith("Sat", 3));
// Expected output: false
```

#### Parameters

- **startsWith**(`searchString`), **startsWith**(`searchString`, `position`)

`searchString`

The characters to be searched for at the start of this string. Cannot be a regex.
All values that are not regexes are coerced to strings, so omitting it or passing
undefined causes startsWith() to search for the string "undefined", which is rarely what you want.

`position` Optional

The start position at which searchString is expected to be found (the index of searchString's first character). Defaults to 0.

#### Return value

`true` if the given characters are found at the beginning of the string, including when searchString is an empty string; otherwise, `false`.

> #### -> see more about `startsWith()`: [here](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/String/startsWith)
>
> #### 👆🏽 go up to [String-Methods #returns a boolean](#returns-a-boolean)

- ### endsWith()

The `endsWith()` method determines whether a string ends with the characters of a specified string,
returning `true` or `false` as appropriate. This method is case-sensitive.

```js
const str1 = "Cats are the best!";

console.log(str1.endsWith("best!"));
// Expected output: true

console.log(str1.endsWith("best", 17));
// Expected output: true

const str2 = "Is this a question?";

console.log(str2.endsWith("question"));
// Expected output: false
```

#### Parameters

- **_endsWith_**(`searchString`), **_endsWith_**(`searchString`, `endPosition`)

`searchString`

The characters to be searched for at the end of `str`. Cannot be a regex. All values that are not regexes are coerced to strings, so omitting it or passing undefined causes `endsWith()` to search for the string "undefined", which is rarely what you want.

`endPosition` Optional

The end position at which `searchString` is expected to be found (the index of `searchString`'s last character plus 1). Defaults to `str.length`.

#### Return value

true if the given characters are found at the end of the string, including when `searchString` is an empty string; otherwise, false.

> #### -> see more about `endsWith()`: [here](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/String/endsWith#parameters)
>
> #### 👆🏽 go up to [String-Methods #returns a boolean](#returns-a-boolean)

- ### includes()

The includes() method performs a case-sensitive search to determine whether one string may be found within another string, returning true or false as appropriate.

```js
const sentence = "The quick brown fox jumps over the lazy dog.";

const word = "fox";

console.log(
  `The word "${word}" ${
    sentence.includes(word) ? "is" : "is not"
  } in the sentence`
);
// Expected output: "The word "fox" is in the sentence"

[1, 2, 3].includes(2); // true
[1, 2, 3].includes(4); // false
[1, 2, 3].includes(3, 3); // false
[1, 2, 3].includes(3, -1); // true
[1, 2, NaN].includes(NaN); // true
["1", "2", "3"].includes(3); // false
```

The `includes()` method compares searchElement to elements of the array using
the SameValueZero algorithm. Values of zero are all considered to be equal,
regardless of sign. (That is, `-0` is equal to `0`), but false is not considered
to be the same as 0. NaN can be correctly searched for.

When used on sparse arrays, the `includes()` method iterates empty slots as if they have the value undefined.

The `includes()` method is generic. It only expects the this value to have a length property and integer-keyed properties.

#### Parameters

- **includes**(`searchString`), **includes**(`searchString`, `position`)

`searchString`

A string to be searched for within `str`. Cannot be a regex. All values that are not regexes are coerced to strings, so omitting it or passing `undefined` causes `includes()` to search for the string "undefined", which is rarely what you want.

`position` Optional

The `position` within the string at which to begin searching for `searchString`. (Defaults to `0`.)

#### Return value

`true` if the search string is found anywhere within the given string, including when `searchString` is an empty string; otherwise, `false`.

> #### -> see more about `includes()`: [here](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/String/includes)
>
> #### 👆🏽 go up to [String-Methods #returns a boolean](#returns-a-boolean)

- ### indexOf()

The indexOf() method of String values searches this string and returns the index of the first occurrence of the specified substring. It takes an optional starting position and returns the first occurrence of the specified substring at an index greater than or equal to the specified number.

Strings are zero-indexed: The index of a string's first character is 0, and the index of a string's last character is the length of the string minus 1.

```js
const paragraph =
  "The quick brown fox jumps over the lazy dog. If the dog barked, was it really lazy?";

const searchTerm = "dog";
const indexOfFirst = paragraph.indexOf(searchTerm);

console.log(
  `The index of the first "${searchTerm}" from the beginning is ${indexOfFirst}`
);
// Expected output: "The index of the first "dog" from the beginning is 40"

console.log(
  `The index of the 2nd "${searchTerm}" is ${paragraph.indexOf(
    searchTerm,
    indexOfFirst + 1
  )}`
);
// Expected output: "The index of the 2nd "dog" is 52"
```

The `indexOf()` method is case sensitive. For example, the following expression returns -1:

```js
"Blue Whale".indexOf("blue"); // returns -1
```

#### Parameters

- **indexOf**(`searchString`), **indexOf**(`searchString`, `position`)

`searchString`

Substring to search for. All values are coerced to strings, so omitting it or passing undefined causes indexOf() to search for the string "undefined", which is rarely what you want.

`position` Optional

The method returns the index of the first occurrence of the specified substring at a `position` greater than or equal to `position`, which defaults to 0. If `position` is greater than the length of the calling string, the method doesn't search the calling string at all. If `position` is less than zero, the method behaves as it would if `position` were 0.

-`'hello world hello'.indexOf('o', -5)` returns `4` — because it causes the method to behave as if the second argument were `0`, and the first occurrence of o at a `position` greater or equal to `0` is at `position` `4`.

-`'hello world hello'.indexOf('world', 12)` returns `-1` — because, while it's true the substring world occurs at index `6`, that `position` is not greater than or equal to `12`.

-`'hello world hello'.indexOf('o', 99)` returns `-1` — because 99 is greater than the length of hello world hello, which causes the method to not search the string at all.

#### Return value

The index of the first occurrence of `searchString` found, or `-1` if not found.
Return value when using an empty search string

Searching for an empty search string produces strange results. With no second argument, or with a second argument whose value is less than the calling string's length, the return value is the same as the value of the second argument:

```js
"hello world".indexOf(""); // returns 0
"hello world".indexOf("", 0); // returns 0
"hello world".indexOf("", 3); // returns 3
"hello world".indexOf("", 8); // returns 8
```

However, with a second argument whose value is greater than or equal to the string's length, the return value is the string's length:

```js
"hello world".indexOf("", 11); // returns 11
"hello world".indexOf("", 13); // returns 11
"hello world".indexOf("", 22); // returns 11
```

In the former instance, the method behaves as if it found an empty string just after the position specified in the second argument. In the latter instance, the method behaves as if it found an empty string at the end of the calling string.

> #### -> see more about `indexOf()`: [here](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/String/indexOf)
>
> #### 👆🏽 go up to [String-Methods #returns a number](#returns-a-number)

- ### at()

The `at()` method takes an integer value and returns a new `String` consisting of the single UTF-16 code unit located at the specified offset. This method allows for positive and negative integers. Negative integers count back from the last string character.

```js
const sentence = "The quick brown fox jumps over the lazy dog.";

let index = 5;
console.log(
  `Using an index of ${index} the character returned is ${sentence.at(index)}`
); // Expected output: "Using an index of 5 the character returned is u"

index = -4;
console.log(
  `Using an index of ${index} the character returned is ${sentence.at(index)}`
); // Expected output: "Using an index of -4 the character returned is d"
```

#### Parameters

- **at**(index)

`index`

The `index` (position) of the string character to be returned. Supports relative indexing from
the end of the string when passed a negative `index`; i.e. if a negative number is used, the
character returned will be found by counting back from the end of the string.

#### Return value

A String consisting of the single UTF-16 code unit located at the specified position.
Returns undefined if the given `index` can not be found.

> #### -> see more about `at()`: [here](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/String/at)
>
> #### 👆🏽 go up to [String-Methods #returns a string](#returns-a-string)

- ### concat()

The `concat()` function concatenates the string arguments to the calling string and returns a new string.
Changes to the original string or the returned string don't affect the other.

If the arguments are not of the type string, they are converted to string values before concatenating.

The `concat()` method is very similar to the addition/string concatenation operators (`+`, `+=`), except
that `concat()` coerces its arguments directly to strings, while addition coerces its operands to primitives
first. For more information, see the reference page for the `+` operator.

```js
const str1 = "Hello";
const str2 = "World";

console.log(str1.concat(" ", str2));
// Expected output: "Hello World"

console.log(str2.concat(", ", str1));
// Expected output: "World, Hello"
```

#### Parameters

- **concat**(str1), **concat**(str1, str2), **concat**(str1, str2, /_ …, _/ strN)

`strN`

One or more strings to concatenate to `str`.

#### Return value

A new string containing the combined text of the strings provided.

> #### -> see more about `concat()`: [here](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/String/concat)
>
> #### 👆🏽 go up to [String-Methods #returns a string](#returns-a-string)

- ### slice()

The `slice()` method extracts a section of a string and returns it as a new string, without modifying the original string.

`slice()` extracts the text from one string and returns a new string. Changes to the text in one string do not affect the other string.

`slice()` extracts up to but not including indexEnd. For example, `str.slice(1, 4)` extracts the second character through
the fourth character (characters indexed 1, 2, and 3).

```js
const str = "The quick brown fox jumps over the lazy dog.";

console.log(str.slice(31));
// Expected output: "the lazy dog."

console.log(str.slice(4, 19));
// Expected output: "quick brown fox"

console.log(str.slice(-4));
// Expected output: "dog."

console.log(str.slice(-9, -5));
// Expected output: "lazy"
```

#### Parameters

- **slice**(`indexStart`), **slice**(`indexStart`, `indexEnd`)

`indexStart`

The index of the first character to include in the returned substring.

`indexEnd` Optional

The index of the first character to exclude from the returned substring.

#### Return value

A new string containing the extracted section of the string.

> #### -> see more about `slice()`: [here](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/String/slice)
>
> #### 👆🏽 go up to [String-Methods #returns a string](#returns-a-string)

- ### replace()

The `replace()` method returns a new string with one, some, or all matches of a `pattern` replaced by a `replacement`. The `pattern` can be a string or a RegExp, and the `replacement` can be a string or a function called for each match. If `pattern` is a string, only the first occurrence will be replaced. The original string is left unchanged.

A string `pattern` will only be replaced once. To perform a global search and replace, use a regular expression with the g flag, or use replaceAll() instead.

If `pattern` is an object with a `Symbol.replace` method (including `RegExp` objects), that method is called with the target string and `replacement` as arguments. Its return value becomes the return value of `replace()`. In this case the behavior of `replace()` is entirely encoded by the `replace` method — for example, any mention of "capturing groups" in the description below is actually functionality provided by `RegExp.prototype[@@replace]`.

If the `pattern` is an empty string, the `replacement` is prepended to the start of the string.

```js
const p =
  "The quick brown fox jumps over the lazy dog. If the dog reacted, was it really lazy?";

console.log(p.replace("dog", "monkey"));
// Expected output: "The quick brown fox jumps over the lazy monkey. If the dog reacted, was it really lazy?"

const regex = /Dog/i;
console.log(p.replace(regex, "ferret"));
// Expected output: "The quick brown fox jumps over the lazy ferret. If the dog reacted, was it really lazy?"
```

```js
"xxx".replace("", "_"); // "_xxx"
```

#### Parameters

`pattern`

Can be a string or an object with a Symbol.replace method — the typical example being a regular expression. Any value that doesn't have the Symbol.replace method will be coerced to a string.

`replacement`

Can be a string or a function.

If it's a string, it will replace the substring matched by `pattern`. A number of special `replacement` patterns are supported; see the Specifying a string as the `replacement` section below.
If it's a function, it will be invoked for every match and its return value is used as the `replacement` text. The arguments supplied to this function are described in the Specifying a function as the `replacement` section below.

#### Return value

A new string, with one, some, or all matches of the `pattern` replaced by the specified `replacement`.

> #### -> see more about `replace()`: [here](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/String/replace)
>
> #### 👆🏽 go up to [String-Methods #returns a string](#returns-a-string)

- ### substring()

The `substring()` method returns the part of the string from the start index up to and excluding the end index,
or to the end of the string if no end index is supplied.
`substring()` extracts characters from `indexStart` up to but not including `indexEnd`. In particular:

- If `indexEnd` is omitted, `substring()` extracts characters to the end of the string.
- If `indexStart` is equal to `indexEnd`, `substring()` returns an empty string.
- If `indexStart` is greater than `indexEnd`, then the effect of `substring()` is as if the two arguments were swapped; see example below.

Any argument value that is less than 0 or greater than `str.length` is treated as if it were 0 and `str.length`, respectively.

Any argument value that is `NaN` is treated as if it were 0.

```js
const str = "Mozilla";

console.log(str.substring(1, 3)); // Expected output: "oz"
console.log(str.substring(2)); // Expected output: "zilla"

console.log(str.substring(4, 7)); // 'lla'
console.log(str.substring(7, 4)); // 'lla'
```

#### Parameters

- **substring**(`indexStart`), **substring**(`indexStart`, `indexEnd`)

`indexStart`

The index of the first character to include in the returned `substring`.

`indexEnd` Optional

The index of the first character to exclude from the returned `substring`.

#### Return value

A new string containing the specified part of the given string.

> #### -> see more about `substring()`: [here](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/String/substring)
>
> #### 👆🏽 go up to [String-Methods #returns a string](#returns-a-string)

- ### toUpperCase()

The `toUpperCase()` method returns the calling string value converted to uppercase (the value will be converted to a string if it isn't one). This method does not affect the value of the string itself since JavaScript strings are immutable.

```js
const sentence = "The quick brown fox jumps over the lazy dog.";

console.log(sentence.toUpperCase());
// Expected output: "THE QUICK BROWN FOX JUMPS OVER THE LAZY DOG."
```

#### Return value

A new string representing the calling string converted to upper case.

> #### -> seemore about `toUpperCase()`: [here](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/String/toUpperCase)
>
> #### 👆🏽 go up to [String-Methods #returns a string](#returns-a-string)

- ### toLowerCase()

The `toLowerCase()` method returns the value of the string converted to lower case. `toLowerCase()` does not affect the value of the string str itself.

```js
const sentence = "The quick brown fox jumps over the lazy dog.";

console.log(sentence.toLowerCase());
// Expected output: "the quick brown fox jumps over the lazy dog."
```

#### Return value

A new string representing the calling string converted to lower case.

> #### -> seemore about `toLowerCase()`: [here](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/String/toLowerCase)
>
> #### 👆🏽 go up to [String-Methods #returns a string](#returns-a-string)

- ### toString()

The `String` object overrides the `toString` method of Object; it does not inherit `Object.prototype.toString()`. For `String` values, the `toString` method returns the string itself (if it's a primitive) or the string that the `String` object wraps. It has the exact same implementation as `String.prototype.valueOf()`.

The `toString()` method requires its this value to be a `String` primitive or wrapper object. It throws a TypeError for other this values without attempting to coerce them to string values.

Because `String` doesn't have a `[@@toPrimitive]()` method, JavaScript calls the `toString()` method automatically when a `String` object is used in a context expecting a string, such as in a template literal. However, `String` primitive values do not consult the `toString()` method to be coerced to strings — since they are already strings, no conversion is performed.

```js
const stringObj = new String("foo");
console.log(stringObj); // Expected output: String { "foo" }
console.log(stringObj.toString()); // Expected output: "foo"

const str = new String("Hello world");
console.log(str.toString()); // "Hello world"

String.prototype.toString = () => "Overridden";
console.log(`${"foo"}`); // "foo"
console.log(`${new String("foo")}`); // "Overridden"
```

#### Return value

A string representing the specified string value.

> #### -> seemore about `toString()`: [here](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/String/toString)
>
> #### 👆🏽 go up to [String-Methods #returns a string](#returns-a-string)

- ### trim()

The `trim()` method removes whitespace from both ends of a string and returns a new string, without modifying the original string.
To return a new string with whitespace trimmed from just one end, use `trimStart()` or `trimEnd()`.

```js
const greeting = "   Hello world!   ";

console.log(greeting);
// Expected output: "   Hello world!   ";

console.log(greeting.trim());
// Expected output: "Hello world!";
```

#### Return value

A new string representing `str` stripped of whitespace from both its beginning and end.
Whitespace is defined as white space characters plus line terminators.

If neither the beginning or end of `str` has any whitespace, a new string is still returned
(essentially a copy of `str`).

> #### -> seemore about `trim()`: [here](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/String/trim)
>
> #### 👆🏽 go up to [String-Methods #returns a string](#returns-a-string)

- ### valueOf()

The `valueOf()` method of `String` returns the primitive value of a `String` object as a string data type.
This value is equivalent to `String.prototype.toString()`.
This method is usually called internally by JavaScript and not explicitly in code.

```js
const stringObj = new String("foo");

console.log(stringObj); // Expected output: String { "foo" }
console.log(stringObj.valueOf()); // Expected output: "foo"

const x = new String("Hello world");
console.log(x.valueOf()); // 'Hello world'
```

#### Return value

A string representing the primitive value of a given `String` object.

> #### -> seemore about `valueOf()`: [here](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/String/valueOf)
>
> #### 👆🏽 go up to [String-Methods #returns a string](#returns-a-string)

- ### split()

The split() method takes a pattern and divides a `String` into an ordered list of substrings by searching for the pattern, puts these substrings into an array, and returns the array.

If `separator` is a non-empty string, the target string is split by all matches of the `separator` without including `separator` in the results. For example, a string containing tab separated values (TSV) could be parsed by passing a tab character as the `separator`, like `myString.split("\t")`. If `separator` contains multiple characters, that entire character sequence must be found in order to split.

If `separator` appears at the beginning (or end) of the string, it still has the effect of splitting, resulting in an empty (i.e. zero length) string appearing at the first (or last) position of the returned array. If `separator` does not occur in `str`, the returned array contains one element consisting of the entire string.

If `separator` is an empty string (""), `str` is converted to an array of each of its UTF-16 "characters", without empty strings on either ends of the resulting string.

```js
const str = "The quick brown fox jumps over the lazy dog.";

const words = str.split(" ");
console.log(words[3]);
// Expected output: "fox"

const chars = str.split("");
console.log(chars[8]);
// Expected output: "k"

const strCopy = str.split();
console.log(strCopy);
// Expected output: Array ["The quick brown fox jumps over the lazy dog."]
```

#### Parameters

- **split**(`separator`), **split**(`separator`, `limit`)

`separator`

The pattern describing where each split should occur. Can be undefined, a string, or an object with a Symbol.split method — the typical example being a regular expression. Omitting `separator` or passing undefined causes split() to return an array with the calling string as a single element. All values that are not undefined or objects with a @@split method are coerced to strings.

`limit` Optional

A non-negative integer specifying a `limit` on the number of substrings to be included in the array. If provided, splits the string at each occurrence of the specified `separator`, but stops when `limit` entries have been placed in the array. Any leftover text is not included in the array at all.

- The array may contain fewer entries than `limit` if the end of the string is reached before the limit is reached.
- If `limit` is 0, [] is returned.

#### Return value

An Array of strings, split at each point where the `separator` occurs in the given string.

> #### see more about `split()`: [here](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/String/split)
>
> #### 👆🏽 go up to [String-Methods #returns an array](#returns-an-array)

## Math-Methods for numbers

- ### Math.abs()

The Math.abs() static method returns the absolute value of a number.
Because abs() is a static method of Math, you always use it as Math.abs(),
rather than as a method of a Math object you created (Math is not a constructor).

```js
function difference(a, b) {
  return Math.abs(a - b);
}

console.log(difference(3, 5)); // Expected output: 2
console.log(difference(5, 3)); // Expected output: 2
console.log(difference(1.23456, 7.89012)); // Expected output: 6.6555599999999995
```

#### Parameters

- **Math.abs**(x)

`x`

A number.

#### Return value

The absolute value of `x`. If `x` is negative (including `-0`), returns `-x`. Otherwise, returns `x`.
The result is therefore always a positive number or `0`.

> #### see more about `Math.abs()`: [here](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Math/abs)
>
> #### 👆🏽 go up to [Math-Methods](#math-methods-for-numbers)

- ### Math.ceil()

The `Math.ceil()` static method always rounds up and returns the smallest integer greater than or equal to a given number.
Because `ceil()` is a static method of Math, you always use it as `Math.ceil()`, rather than as a method of a
`Math` object you created (`Math` is not a constructor).

```js
console.log(Math.ceil(0.95)); // Expected output: 1
console.log(Math.ceil(4)); // Expected output: 4
console.log(Math.ceil(7.004)); // Expected output: 8
console.log(Math.ceil(-7.004)); // Expected output: -7
```

#### Parameters

- **Math.ceil**(x)

`x`

A number.

#### Return value

The smallest integer greater than or equal to `x`. It's the same value as `-Math.floor(-x)`.

> #### see more about `Math.ceil()`: [here](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Math/ceil)
>
> #### 👆🏽 go up to [Math-Methods](#math-methods-for-numbers)

- ### Math.floor()

The Math.floor() static method always rounds down and returns the largest integer less than
or equal to a given number. Because floor() is a static method of Math, you always use it as
Math.floor(), rather than as a method of a Math object you created (Math is not a constructor).

```js
Math.floor(-Infinity); // -Infinity
Math.floor(-45.95); // -46
Math.floor(-45.05); // -46
Math.floor(-0); // -0
Math.floor(0); // 0
Math.floor(4); // 4
Math.floor(45.05); // 45
Math.floor(45.95); // 45
Math.floor(Infinity); // Infinity
```

#### Decimal adjustment

In this example, we implement a method called `decimalAdjust()` that is an enhancement method of
`Math.floor()`, `Math.ceil()`, and `Math.round()`. While the three `Math` functions always adjust
the input to the units digit, `decimalAdjust` accepts an `exp` parameter that specifies the number
of digits to the left of the decimal point to which the number should be adjusted.
For example, -1 means it would leave one digit after the decimal point (as in "× 10-1").
In addition, it allows you to select the means of adjustment — `round`, `floor`, or `ceil` — through the type parameter.

It does so by multiplying the number by a power of 10, then rounding the result to the nearest integer,
then dividing by the power of 10. To better preserve precision, it takes advantage of Number's
`toString()` method, which represents large or small numbers in scientific notation (like `6.02e23`).

> #### see more about `Math.floor()`: [here](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Math/floor)
>
> #### 👆🏽 go up to [Math-Methods](#math-methods-for-numbers)

- ### Math.max()

The `Math.max()` static method returns the largest of the numbers given as input parameters, or `-Infinity`
if there are no parameters.
Because `max()` is a static method of Math, you always use it as `Math.max()`, rather than as a method
of a `Math` object you created (`Math` is not a constructor).

`Math.max.length` is `2`, which weakly signals that it's designed to handle at least two parameters.

```js
console.log(Math.max(1, 3, 2)); // Expected output: 3
console.log(Math.max(-1, -3, -2)); // Expected output: -1

const array1 = [1, 3, 2];
console.log(Math.max(...array1)); // Expected output: 3
```

#### Parameters

- **Math.max**(), **Math.max**(value0), **Math.max**(value0, value1), **Math.max**(value0, value1, /_ …, _/ valueN)

`value1`, `value2`, … , `valueN`

Zero or more numbers among which the largest value will be selected and returned.

#### Return value

The largest of the given numbers. Returns NaN if any of the parameters is or is converted into `NaN`.
Returns `-Infinity` if no parameters are provided.

> #### see more about `Math.max()`: [here](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Math/max)
>
> #### 👆🏽 go up to [Math-Methods](#math-methods-for-numbers)

- ### Math.min()

The `Math.min()` static method returns the smallest of the numbers given as input parameters, or `Infinity`
if there are no parameters.
Because `min()` is a static method of Math, you always use it as `Math.min()`, rather than as a method of a
`Math` object you created (`Math` is not a constructor). `Math.min.length` is 2, which weakly signals that
it's designed to handle at least two parameters.

```js
console.log(Math.min(2, 3, 1)); // Expected output: 1
console.log(Math.min(-2, -3, -1)); // Expected output: -3

const array1 = [2, 3, 1];
console.log(Math.min(...array1)); // Expected output: 1
```

#### Parameters

`value1`, …, `valueN`

Zero or more numbers among which the lowest value will be selected and returned.

#### Return value

The smallest of the given numbers. Returns NaN if any of the parameters is or is
converted into `NaN`. Returns `Infinity` if no parameters are provided.

> #### see more about `Math.min()`: [here](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Math/min)
>
> #### 👆🏽 go up to [Math-Methods](#math-methods-for-numbers)

- ### Math.pow()

The `Math.pow()` static method returns the value of a base raised to a power.

That is `𝙼𝚊𝚝𝚑.𝚙𝚘𝚠 ( 𝚡 , 𝚢 )` = x<sup>y</sup>

`Math.pow()` is equivalent to the ** operator, except `Math.pow()` only accepts numbers.
`Math.pow(NaN, 0)` (and the equivalent `NaN ** 0`) is the only case where NaN doesn't 
propagate through mathematical operations — it returns `1`despite the operand being`NaN`. 
In addition, the behavior where `base`is`1`and`exponent`is non-finite (±Infinity or`NaN`)
is different from IEEE 754, which specifies that the result should be 1, whereas JavaScript
returns NaN to preserve backward compatibility with its original behavior.

Because `pow()` is a static method of `Math`, use it as `Math.pow()`, rather than as a method
of a `Math` object you created (`Math` is not a constructor).

```js
console.log(Math.pow(7, 3)); // Expected output: 343
console.log(Math.pow(4, 0.5)); // Expected output: 2
console.log(Math.pow(7, -2));
// Expected output: 0.02040816326530612
//                  (1/49)

console.log(Math.pow(-7, 0.5)); // Expected output: NaN
```

#### Parameters

- **Math.pow**(`base`, `exponent`)

`base`

The `base` number.

`exponent`

The `exponent` number.

#### Return value

A number representing `base` taken to the power of `exponent`. Returns `NaN` in one of the following cases:

- `exponent` is `NaN`.
- `base` is `NaN` and `exponent` is not `0`.
- `base` is `±1` and `exponent` is `±Infinity`.
- `base` `< 0` and `exponent` is not an `integer`.

> #### see more about `Math.pow()`: [here](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Math/pow)
>
> #### 👆🏽 go up to [Math-Methods](#math-methods-for-numbers)

- ### Math.random()

The `Math.random()` static method returns a floating-point, pseudo-random number that's greater
than or equal to `0` and less than `1`, with approximately uniform distribution over that range
— which you can then scale to your desired range. The implementation selects the initial seed
to the random number generation algorithm; it cannot be chosen or reset by the user.

```js
function getRandomInt(max) {
  return Math.floor(Math.random() * max);
}

console.log(getRandomInt(3)); // Expected output: 0, 1 or 2
console.log(getRandomInt(1)); // Expected output: 0
console.log(Math.random()); // Expected output: a number from 0 to <1
```

#### Return value

A floating-point, pseudo-random number between `0` (inclusive) and `1` (exclusive).

##### Getting a random number between 0 (inclusive) and 1 (exclusive)

```js
function getRandom() {
  return Math.random();
}
```

##### Getting a random number between two values

This example returns a random number between the specified values. The returned value
is no lower than (and may possibly equal) `min`, and is less than (and not equal) `max`.

```js
function getRandomArbitrary(min, max) {
  return Math.random() * (max - min) + min;
}
```

##### Getting a random integer between two values

This example returns a random integer between the specified values. The value
is no lower than `min` (or the next integer greater than `min` if `min` isn't an integer),
and is less than (but not equal to) `max`.

```js
function getRandomInt(min, max) {
  min = Math.ceil(min);
  max = Math.floor(max);
  return Math.floor(Math.random() * (max - min) + min);
  // The maximum is exclusive and the minimum is inclusive
}
```

##### Getting a random integer between two values, inclusive

While the `getRandomInt()` function above is inclusive at the minimum,
it's exclusive at the maximum. What if you need the results to be inclusive
at both the minimum and the maximum? The `getRandomIntInclusive()` function
below accomplishes that.

```js
function getRandomIntInclusive(min, max) {
  min = Math.ceil(min);
  max = Math.floor(max);
  return Math.floor(Math.random() * (max - min + 1) + min);
  // The maximum is inclusive and the minimum is inclusive
}
```

> #### -> see more about `Math.random()`: [here](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Math/random)
>
> #### 👆🏽 go up to [Math-Methods](#math-methods-for-numbers)

- ### Math.round()

The `Math.round()` static method returns the value of a number rounded to the nearest integer.

If the fractional portion of the argument is greater than `0.5`, the argument is rounded to
the integer with the next higher absolute value. If it is less than `0.5`, the argument is
rounded to the integer with the lower absolute value. If the fractional portion is exactly `0.5`,
the argument is rounded to the next integer in the direction of `+∞`.

`Math.round(x)` is not exactly the same as Math.floor(x + `0.5`). When `x` is `-0`, or `-0.5 ≤ x < 0`,
`Math.round(x)` returns `-0`, while `Math.floor(x + 0.5)` returns `0`. However, neglecting that difference
and potential precision errors, `Math.round(x)` and `Math.floor(x + 0.5)` are generally equivalent.

Because `round()` is a static method of `Math`, you always use it as `Math.round()`, rather
than as a method of a `Math` object you created (`Math` has no constructor).

```js
console.log(Math.round(0.9)); // Expected output: 1
console.log(Math.round(5.95), Math.round(5.5), Math.round(5.05)); // Expected output: 6 6 5
console.log(Math.round(-5.05), Math.round(-5.5), Math.round(-5.95)); // Expected output: -5 -5 -6

Math.round(-Infinity); // -Infinity
Math.round(-20.51); // -21
Math.round(-20.5); // -20
Math.round(-0.1); // -0
Math.round(0); // 0
Math.round(20.49); // 20
Math.round(20.5); // 21
Math.round(42); // 42
Math.round(Infinity); // Infinity
```

#### Parameters

`x`

A number.

#### Return value

The value of `x` rounded to the nearest integer.

> #### -> see more about `Math.round()`: [here](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Math/round)
>
> #### 👆🏽 go up to [Math-Methods](#math-methods-for-numbers)

- ### Math.sign()

The `Math.sign()` static method returns `1` or `-1`, indicating the sign of the number
passed as argument. If the input is 0 or `-0`, it will be returned as-is.
Because `sign()` is a static method of `Math`, you always use it as `Math.sign()`,
rather than as a method of a `Math` object you created (`Math` is not a constructor).

```js
console.log(Math.sign(3)); // Expected output: 1
console.log(Math.sign(-3)); // Expected output: -1
console.log(Math.sign(0)); // Expected output: 0
console.log(Math.sign("-3")); // Expected output: -1

Math.sign(3); // 1
Math.sign(-3); // -1
Math.sign("-3"); // -1
Math.sign(0); // 0
Math.sign(-0); // -0
Math.sign(NaN); // NaN
Math.sign("foo"); // NaN
Math.sign(); // NaN
```

#### Parameters

- **Math.sign**(x)

`x`

A number.

#### Return value

A number representing the sign of `x`:

- If `x` is positive, returns `1`.
- If `x` is negative, returns `-`1.
- If `x` is positive zero, returns `0`.
- If `x` is negative zero, returns `-`0.
- Otherwise, returns `NaN`.

> #### -> see more about `Math.sign()`: [here](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Math/sign)
>
> #### 👆🏽 go up to [Math-Methods](#math-methods-for-numbers)

- ### Math.sqrt()

The `Math.sqrt()` static method returns the square root of a number. That is

∀x ≥ 0 , 𝙼𝚊𝚝𝚑.𝚜𝚚𝚛𝚝(𝚡) = √x = the unique y ≥ 0 such that y<sup>2</sup> = x

Because `sqrt()` is a static method of `Math`, you always use it as `Math.sqrt()`,
rather than as a method of a `Math` object you created (`Math` is not a constructor).

```js
function calcHypotenuse(a, b) {
  return Math.sqrt(a * a + b * b);
}

console.log(calcHypotenuse(3, 4)); // Expected output: 5
onsole.log(calcHypotenuse(5, 12)); // Expected output: 13
console.log(calcHypotenuse(0, 0)); // Expected output: 0

Math.sqrt(-1); // NaN
Math.sqrt(-0); // -0
Math.sqrt(0); // 0
Math.sqrt(1); // 1
Math.sqrt(2); // 1.414213562373095
Math.sqrt(9); // 3
Math.sqrt(Infinity); // Infinity
```

#### Parameters

- **Math.sqrt**(x)

`x`

A number greater than or equal to `0`.

#### Return value

The square root of `x`, a nonnegative number. If `x < 0`, returns `NaN`.

> #### -> see more about `Math.sqrt()`: [here](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Math/sqrt)
>
> #### 👆🏽 go up to [Math-Methods](#math-methods-for-numbers)

- ### Math.trunc()

The `Math.trunc()` static method returns the integer part of a number by removing any
fractional digits.

Unlike the other three Math methods: `Math.floor()`, `Math.ceil()` and `Math.round()`,
the way `Math.trunc()` works is very simple. It truncates (cuts off) the dot and the
digits to the right of it, no matter whether the argument is a positive or negative number.

Because `trunc()` is a static method of `Math`, you always use it as `Math.trunc()`,
rather than as a method of a `Math` object you created (`Math` is not a constructor).

```js
console.log(Math.trunc(13.37)); // Expected output: 13
console.log(Math.trunc(42.84)); // Expected output: 42
console.log(Math.trunc(0.123)); // Expected output: 0
console.log(Math.trunc(-0.123)); // Expected output: -0

Math.trunc(-Infinity); // -Infinity
Math.trunc("-1.123"); // -1
Math.trunc(-0.123); // -0
Math.trunc(-0); // -0
Math.trunc(0); // 0
Math.trunc(0.123); // 0
Math.trunc(13.37); // 13
Math.trunc(42.84); // 42
Math.trunc(Infinity); // Infinity
```

#### Parameters

- **Math.trunc**(x)

`x`

A number.

#### Return value

The integer part of `x`.

> #### -> see more about `Math.trunc()`: [here](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Math/trunc)
>
> #### 👆🏽 go up to [Math-Methods](#math-methods-for-numbers)

## Array-Methods

- ### forEach()

The `forEach()` method executes a provided function once for each array element.
The `forEach()` method is an iterative method. It calls a provided callbackFn function
once for each element in an array in ascending-index order. Unlike map(), `forEach()`
always returns undefined and is not chainable. The typical use case is to execute
side effects at the end of a chain.

```js
const array1 = ["a", "b", "c"];
array1.forEach((element) => console.log(element));
// Expected output: "a"
// Expected output: "b"
// Expected output: "c"
```

#### Parameters

- **forEach**(`callbackFn`), **forEach**(`callbackFn`, `thisArg`)

`callbackFn`

A function to execute for each `element` in the array.
Its return value is discarded. The function is called
with the following arguments:

- `element`

  The current `element` being processed in the array.

- `index`

  The index of the current `element` being processed in the array.

- `array`

  The array `forEach()` was called upon.

`thisArg` Optional

A value to use as this when executing `callbackFn`. See iterative methods.

#### Return value

undefined

> #### -> see more about `forEach()`: [here](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/forEach#parameters)
>
> #### 👆🏽 go up to [Array-Methods #without returns value](#without-retuns-value)

- ### some()

The `some()` method tests whether at least one element in the array passes the test implemented
by the provided function. It returns `true` if, in the array, it finds an element for which the
provided function returns `true`; otherwise it returns `false`. It doesn't modify the array.

The `some()` method is an iterative method. It calls a provided `callbackFn` function once for
each element in an array, until the `callbackFn` returns a truthy value. If such an element is
found, `some()` immediately returns `true` and stops iterating through the array. Otherwise, if
`callbackFn` returns a falsy value for all elements, `some()` returns `false`.

`some()` acts like the "there exists" quantifier in mathematics. In particular, for an empty array,
it returns `false` for any condition.

`callbackFn` is invoked only for array indexes which have assigned values. It is not invoked for
empty slots in sparse arrays.

`some()` does not mutate the array on which it is called, but the function provided as `callbackFn` can.
Note, however, that the length of the array is saved before the first invocation of `callbackFn`. Therefore:

- `callbackFn` will not visit any elements added beyond the array's initial length when the call to `some()` began.
- Changes to already-visited indexes do not cause `callbackFn` to be invoked on them again.
- If an existing, yet-unvisited element of the array is changed by `callbackFn`, its value passed to the
  `callbackFn` will be the value at the time that element gets visited. Deleted elements are not visited.

The `some()` method is generic. It only expects the this value to have a length property and integer-keyed properties.

```js
const array = [1, 2, 3, 4, 5];

// Checks whether an element is even
const even = (element) => element % 2 === 0;

console.log(array.some(even));
// Expected output: true
```

#### Parameters

- **some**(`callbackFn`), **some**(`callbackFn`, `thisArg`)

`callbackFn`

A function to execute for each `element` in the `array`. It should return a truthy value to indicate the
element passes the test, and a falsy value otherwise. The function is called with the following arguments:

`element`

The current `element` being processed in the `array`.

`index`

The `index` of the current `element` being processed in the `array`.

`array`

The `array` some() was called upon.

`thisArg` Optional

A value to use as this when executing `callbackFn`. See iterative methods.

#### Return value

true if the callback function returns a truthy value for at least one element in the array. Otherwise, false.

> #### -> see more about `some()`: [here](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/some)
>
> #### 👆🏽 go up to [Array-Methods #returns a boolean](#returns-a-boolean-1)

- ### every()

The `every()` method tests whether all elements in the array pass the test implemented by the provided function.
It returns a Boolean value.

The `every()` method is an iterative method. It calls a provided callbackFn function once for each element in an array,
until the callbackFn returns a falsy value. If such an element is found, `every()` immediately returns false and stops
iterating through the array. Otherwise, if callbackFn returns a truthy value for all elements, `every()` returns true.

every acts like the "for all" quantifier in mathematics. In particular, for an empty array, it returns true.
(It is vacuously true that all elements of the empty set satisfy any given condition.)

callbackFn is invoked only for array indexes which have assigned values. It is not invoked for empty slots in sparse arrays.

`every()` does not mutate the array on which it is called, but the function provided as callbackFn can. Note, however,
that the length of the array is saved before the first invocation of callbackFn. Therefore:

- callbackFn will not visit any elements added beyond the array's initial length when the call to `every()` began.
- Changes to already-visited indexes do not cause callbackFn to be invoked on them again.
- If an existing, yet-unvisited element of the array is changed by callbackFn, its value passed to the callbackFn
  will be the value at the time that element gets visited. Deleted elements are not visited.

The `every()` method is generic. It only expects the this value to have a length property and integer-keyed properties.

```js
const isBelowThreshold = (currentValue) => currentValue < 40;

const array1 = [1, 30, 39, 29, 10, 13];

console.log(array1.every(isBelowThreshold));
// Expected output: true
```

#### Parameters

- **every**(`callbackFn`), **every**(`callbackFn`, `thisArg`)

`callbackFn`

A function to execute for each `element` in the `array`. It should return a truthy value to indicate the `element` passes the test, and a falsy value otherwise. The function is called with the following arguments:

`element`

The current `element` being processed in the `array`.

`index`

The `index` of the current `element` being processed in the `array`.

`array`

The `array` `every()` was called upon.

`thisArg` Optional

A value to use as this when executing `callbackFn`. See iterative methods.

#### Return value

true if `callbackFn` returns a truthy value for every array element. Otherwise, false.

> #### -> see more about `every()`: [here](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/every)
>
> #### 👆🏽 go up to [Array-Methods #returns a boolean](#returns-a-boolean-1)

- ### includes()

The `includes()` method determines whether an array includes a certain value among its entries,
returning true or false as appropriate.

The `includes()` method compares searchElement to elements of the array using the SameValueZero algorithm.
Values of zero are all considered to be equal, regardless of sign. (That is, `-0` is equal to `0`),
but false is not considered to be the same as `0`. NaN can be correctly searched for.

When used on sparse arrays, the `includes()` method iterates empty slots as if they have the value undefined.

The `includes()` method is generic. It only expects the this value to have a length property and integer-keyed properties.

```js
const array1 = [1, 2, 3];
console.log(array1.includes(2)); // Expected output: true

const pets = ["cat", "dog", "bat"];
console.log(pets.includes("cat")); // Expected output: true
console.log(pets.includes("at")); // Expected output: false

[1, 2, 3].includes(2); // true
[1, 2, 3].includes(4); // false
[1, 2, 3].includes(3, 3); // false
[1, 2, 3].includes(3, -1); // true
[1, 2, NaN].includes(NaN); // true
["1", "2", "3"].includes(3); // false
```

If `fromIndex` is greater than or equal to the length of the array, `false` is returned. The array will not be searched.

```js
const arr = ["a", "b", "c"];
arr.includes("c", 3); // false
arr.includes("c", 100); // false
```

If `fromIndex` is negative, the computed index is calculated to be used as a position in the
array at which to begin searching for `searchElement`. If the computed index is less than or
equal to `0`, the entire array will be searched.

```js
// array length is 3
// fromIndex is -100
// computed index is 3 + (-100) = -97

const arr = ["a", "b", "c"];

arr.includes("a", -100); // true
arr.includes("b", -100); // true
arr.includes("c", -100); // true
arr.includes("a", -2); // false
```

You can search for undefined in a sparse array and get true.

```js
console.log([1, , 3].includes(undefined)); // true
```

The includes() method reads the length property of this and then accesses each property whose
key is a nonnegative integer less than length.

```js
const arrayLike = {
  length: 3,
  0: 2,
  1: 3,
  2: 4,
  3: 1, // ignored by includes() since length is 3
};
console.log(Array.prototype.includes.call(arrayLike, 2)); // true
console.log(Array.prototype.includes.call(arrayLike, 1)); // false
```

#### Parameters

- **includes**(`searchElement`), **includes**(`searchElement`, `fromIndex`)

`searchElement`

The value to search for.

`fromIndex` Optional

Zero-based index at which to start searching, converted to an integer.

- Negative index counts back from the end of the array — if `fromIndex < 0`, `fromIndex + array.length`
  is used. However, the array is still searched from front to back in this case.
- If `fromIndex < -array.length` or `fromIndex` is omitted, `0` is used, causing the entire array to be searched.
- If `fromIndex >= array.length`, the array is not searched and `false` is returned.

#### Return value

A boolean value which is `true` if the value `searchElement` is found within the array
(or the part of the array indicated by the index fromIndex, if specified).

> #### -> see more about `includes()`: [here](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/includes)
>
> #### 👆🏽 go up to [Array-Methods #returns a boolean](#returns-a-boolean-1)

- ### isArray()

The `Array.isArray()` static method determines whether the passed value is an Array.

`Array.isArray()` checks if the passed value is an Array. It does not check the value's prototype chain,
nor does it rely on the Array constructor it is attached to. It returns true for any value that was
created using the array literal syntax or the Array constructor. This makes it safe to use with
cross-realm objects, where the identity of the Array constructor is different and would therefore cause
instanceof Array to fail.

See the article "Determining with absolute accuracy whether or not a JavaScript object is an array" for more details.

`Array.isArray()` also rejects objects with Array.prototype in its prototype chain but aren't actual arrays,
which instanceof Array would accept.

```js
console.log(Array.isArray([1, 3, 5])); // Expected output: true
console.log(Array.isArray("[]")); // Expected output: false
console.log(Array.isArray(new Array(5))); // Expected output: true
console.log(Array.isArray(new Int16Array([15, 33]))); // Expected output: false

// all following calls return true
Array.isArray([]);
Array.isArray([1]);
Array.isArray(new Array());
Array.isArray(new Array("a", "b", "c", "d"));
Array.isArray(new Array(3));
// Little known fact: Array.prototype itself is an array:
Array.isArray(Array.prototype);

// all following calls return false
Array.isArray();
Array.isArray({});
Array.isArray(null);
Array.isArray(undefined);
Array.isArray(17);
Array.isArray("Array");
Array.isArray(true);
Array.isArray(false);
Array.isArray(new Uint8Array(32));
// This is not an array, because it was not created using the
// array literal syntax or the Array constructor
Array.isArray({ __proto__: Array.prototype });
```

#### instanceof vs. Array.isArray()

When checking for Array instance, `Array.isArray()` is preferred over `instanceof` because it works across realms.

```js
const iframe = document.createElement("iframe");
document.body.appendChild(iframe);
const xArray = window.frames[window.frames.length - 1].Array;
const arr = new xArray(1, 2, 3); // [1, 2, 3]

// Correctly checking for Array
Array.isArray(arr); // true
// The prototype of arr is xArray.prototype, which is a
// different object from Array.prototype
arr instanceof Array; // false
```

#### Parameters

- **Array.isArray**(`value`)

`value`

The `value` to be checked.

#### Return value

`true` if `value` is an Array; otherwise, `false`. `false` is always returned if `value` is a TypedArray instance.

> #### -> see more about `isArray()`: [here](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/isArray)
>
> #### 👆🏽 go up to [Array-Methods #returns a boolean](#returns-a-boolean-1)

- ### join()

The `join()` method creates and returns a new string by concatenating all of the elements in this array,
separated by commas or a specified separator string. If the array has only one item, then that item
will be returned without using the separator.

The string conversions of all array elements are joined into one string. If an element is `undefined`,
`null`, it is converted to an empty string instead of the string "null" or "undefined".

The join method is accessed internally by `Array.prototype.toString()` with no arguments.
Overriding join of an array instance will override its `toString` behavior as well.

`Array.prototype.join` recursively converts each element, including other arrays, to strings.
Because the string returned by `Array.prototype.toString` (which is the same as calling `join()`)
does not have delimiters, nested arrays look like they are flattened. You can only control the
separator of the first level, while deeper levels always use the default comma.

```js
const elements = ["Fire", "Air", "Water"];

console.log(elements.join()); // Expected output: "Fire,Air,Water"
console.log(elements.join("")); // Expected output: "FireAirWater"
console.log(elements.join("-")); // Expected output: "Fire-Air-Water"

const matrix = [
  [1, 2, 3],
  [4, 5, 6],
  [7, 8, 9],
];

console.log(matrix.join()); // 1,2,3,4,5,6,7,8,9
console.log(matrix.join(";")); // 1,2,3;4,5,6;7,8,9
```

When an array is cyclic (it contains an element that is itself), browsers avoid infinite
recursion by ignoring the cyclic reference.

```js
const arr = [];
arr.push(1, [3, arr, 4], 2);
console.log(arr.join(";")); // 1;3,,4;2
```

When used on sparse arrays, the `join()` method iterates empty slots as if they have the value undefined.

The `join()` method is generic. It only expects the this value to have a length property and integer-keyed properties.

#### Joining an array four different ways

The following example creates an array, a, with three elements, then joins the array four times:
using the default separator, then a comma and a space, then a plus and an empty string.

```js
const a = ["Wind", "Water", "Fire"];
a.join(); // 'Wind,Water,Fire'
a.join(", "); // 'Wind, Water, Fire'
a.join(" + "); // 'Wind + Water + Fire'
a.join(""); // 'WindWaterFire'
```

`join()` treats empty slots the same as undefined and produces an extra separator:

```js
console.log([1, , 3].join()); // '1,,3'
console.log([1, undefined, 3].join()); // '1,,3'
```

#### Calling join() on non-array objects

The join() method reads the length property of this and then accesses each property
whose key is a nonnegative integer less than length.

```js
const arrayLike = {
  length: 3,
  0: 2,
  1: 3,
  2: 4,
  3: 5, // ignored by join() since length is 3
};

console.log(Array.prototype.join.call(arrayLike)); // 2,3,4
console.log(Array.prototype.join.call(arrayLike, ".")); // 2.3.4
```

#### Parameters

- **join**(), **join**(`separator`)

`separator` Optional

A string to separate each pair of adjacent elements of the array. If omitted, the array elements are separated with a comma (",").

#### Return value

A string with all array elements joined. If `arr.length` is `0`, the empty string is returned.

> #### -> see more about `join()`: [here](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/join)
>
> #### 👆🏽 go up to [Array-Methods #returns a String](#returns-a-string-1)

- ### at()

The `at()` method takes an integer value and returns the item at that index, allowing for
positive and negative integers. Negative integers count back from the last item in the array.

The `at()` method is equivalent to the bracket notation when index is non-negative. For example,
`array[0]` and `array.at(0)` both return the first item. However, when counting elements from the
end of the array, you cannot use `array[-1]` like you may in Python or R, because all values inside
the square brackets are treated literally as string properties, so you will end up reading
`array["-1"]`, which is just a normal string property instead of an array index.

The usual practice is to access length and calculate the index from that — for example,
`array[array.length - 1]`. The `at()` method allows relative indexing, so this can be shortened to `array.at(-1)`.

The `at()` method is generic. It only expects the this value to have a length property and integer-keyed properties.

```js
const array1 = [5, 12, 8, 130, 44];
let index = 2;

console.log(
  `Using an index of ${index} the item returned is ${array1.at(index)}`
);
// Expected output: "Using an index of 2 the item returned is 8"

index = -2;

console.log(`Using an index of ${index} item returned is ${array1.at(index)}`);
// Expected output: "Using an index of -2 item returned is 130"
```

The following example provides a function which returns the last element found in a specified array.

```js
// Our array with items
const cart = ["apple", "banana", "pear"];

// A function which returns the last item of a given array
function returnLast(arr) {
  return arr.at(-1);
}

// Get the last item of our array 'cart'
const item1 = returnLast(cart);
console.log(item1); // 'pear'

// Add an item to our 'cart' array
cart.push("orange");
const item2 = returnLast(cart);
console.log(item2); // 'orange'
```

This example compares different ways to select the penultimate (last but one) item of an Array.
While all the methods shown below are valid, this example highlights the succinctness and readability of the at() method.

```js
// Our array with items
const colors = ["red", "green", "blue"];

// Using length property
const lengthWay = colors[colors.length - 2];
console.log(lengthWay); // 'green'

// Using slice() method. Note an array is returned
const sliceWay = colors.slice(-2, -1);
console.log(sliceWay[0]); // 'green'

// Using at() method
const atWay = colors.at(-2);
console.log(atWay); // 'green'
```

The at() method reads the length property of this and calculates the index to access.

```js
const arrayLike = {
  length: 2,
  0: "a",
  1: "b",
  2: "c", // ignored by at() since length is 2
};
console.log(Array.prototype.at.call(arrayLike, 0)); // "a"
console.log(Array.prototype.at.call(arrayLike, 2)); // undefined
```

#### Parameters

`index`

Zero-based `index` of the array element to be returned, converted to an integer. Negative `index`
counts back from the end of the array — if `index < 0`, `index + array.length` is accessed.

#### Return value

The element in the array matching the given `index`. Always returns undefined if `index < -array.length`
or `index >= array.length` without attempting to access the corresponding property.

> #### -> see more about `at()`: [here](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/at)
>
> #### 👆🏽 go up to [Array-Methods #returns a number](#returns-a-number-1)

- ### findIndex()

The `findIndex()` method returns the index of the first element in an array that satisfies the provided
testing function. If no elements satisfy the testing function, `-1` is returned.

See also the `find()` method, which returns the first element that satisfies the testing function (rather than its index).

The `findIndex()` is an iterative method. It calls a provided `callbackFn` function once for each element in an array in ascending-index order, until `callbackFn` returns a truthy value. `findIndex()` then returns the index of that element and stops iterating through the array. If `callbackFn` never returns a truthy value, `findIndex()` returns `-1`.

`callbackFn` is invoked for every index of the array, not just those with assigned values. Empty slots in sparse arrays behave the same as undefined.

`findIndex()` does not mutate the array on which it is called, but the function provided as `callbackFn` can. Note, however, that the length of the array is saved before the first invocation of `callbackFn`. Therefore:

- `callbackFn` will not visit any elements added beyond the array's initial length when the call to `findIndex()` began.
- Changes to already-visited indexes do not cause `callbackFn` to be invoked on them again.
- If an existing, yet-unvisited element of the array is changed by `callbackFn`, its value passed to the `callbackFn` will be the value at the time that element gets visited. Deleted elements are visited as if they were undefined.

The `findIndex()` method is generic. It only expects the this value to have a length property and integer-keyed properties.

```js
const array1 = [5, 12, 8, 130, 44];
const isLargeNumber = (element) => element > 13;

console.log(array1.findIndex(isLargeNumber));
// Expected output: 3
```

#### Find the index of a prime number in an array

The following example returns the index of the first element in the array that is a prime number,
or `-1` if there is no prime number.

```js
function isPrime(element) {
  if (element % 2 === 0 || element < 2) {
    return false;
  }
  for (let factor = 3; factor <= Math.sqrt(element); factor += 2) {
    if (element % factor === 0) {
      return false;
    }
  }
  return true;
}

console.log([4, 6, 8, 9, 12].findIndex(isPrime)); // -1, not found
console.log([4, 6, 7, 9, 12].findIndex(isPrime)); // 2 (array[2] is 7)
```

You can search for undefined in a sparse array and get the index of an empty slot.

```js
console.log([1, , 3].findIndex((x) => x === undefined)); // 1
```

The `findIndex()` method reads the length property of this and then accesses each
property whose key is a nonnegative integer less than length.

```js
const arrayLike = {
  length: 3,
  "-1": 0.1, // ignored by findIndex() since -1 < 0
  0: 2,
  1: 7.3,
  2: 4,
};
console.log(
  Array.prototype.findIndex.call(arrayLike, (x) => !Number.isInteger(x))
); // 1
```

#### Parameters

- **findIndex**(`callbackFn`), **findIndex**(`callbackFn`, `thisArg`)

`callbackFn`

A function to execute for each `element` in the `array`. It should return a truthy value to indicate a matching `element` has been found, and a falsy value otherwise. The function is called with the following arguments:

`element`

The current `element` being processed in the `array`.

`index`

The `index` of the current `element` being processed in the `array`.

`array`

The `array` `findIndex()` was called upon.

`thisArg` Optional

A value to use as this when executing `callbackFn`. See iterative methods.

#### Return value

The `index` of the first `element` in the `array` that passes the test. Otherwise, `-1`.

> #### -> see more about `findIndex()`: [here](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/findIndex)
>
> #### 👆🏽 go up to [Array-Methods #returns a number](#returns-a-number-1)

- ### push()

The push() method appends values to an array, it adds the specified elements to the end of
an array and returns the new length of the array.

Array.prototype.unshift() has similar behavior to push(), but applied to the start of an array.

The push() method is a mutating method. It changes the length and the content of this.
In case you want the value of this to be the same, but return a new array with elements
appended to the end, you can use arr.concat([element0, element1, /* ... ,*/ elementN]) instead.
Notice that the elements are wrapped in an extra array — otherwise, if the element is an
array itself, it would be spread instead of pushed as a single element due to the behavior of concat().

The push() method is generic. It only expects the this value to have a length property and
integer-keyed properties. Although strings are also array-like, this method is not suitable
to be applied on them, as strings are immutable.

```js
const animals = ["pigs", "goats", "sheep"];

const count = animals.push("cows");
console.log(count);
// Expected output: 4
console.log(animals);
// Expected output: Array ["pigs", "goats", "sheep", "cows"]

animals.push("chickens", "cats", "dogs");
console.log(animals);
// Expected output: Array ["pigs", "goats", "sheep", "cows", "chickens", "cats", "dogs"]
```

#### Adding elements to an array

The following code creates the sports array containing two elements,
then appends two elements to it. The total variable contains the new length of the array.

```js
const sports = ["soccer", "baseball"];
const total = sports.push("football", "swimming");

console.log(sports); // ['soccer', 'baseball', 'football', 'swimming']
console.log(total); // 4
```

#### Merging two arrays

This example uses spread syntax to push all elements from a second array into the first one.

```js
const vegetables = ["parsnip", "potato"];
const moreVegs = ["celery", "beetroot"];

// Merge the second array into the first one
vegetables.push(...moreVegs);

console.log(vegetables); // ['parsnip', 'potato', 'celery', 'beetroot']
```

> Merging two arrays can also be done with the concat() method.

#### Calling push() on non-array objects

The push() method reads the length property of this. It then sets each index of
this starting at length with the arguments passed to push(). Finally,
it sets the length to the previous length plus the number of pushed elements.

```js
const arrayLike = {
  length: 3,
  unrelated: "foo",
  2: 4,
};
Array.prototype.push.call(arrayLike, 1, 2);
console.log(arrayLike);
// { '2': 4, '3': 1, '4': 2, length: 5, unrelated: 'foo' }

const plainObj = {};
// There's no length property, so the length is 0
Array.prototype.push.call(plainObj, 1, 2);
console.log(plainObj);
// { '0': 1, '1': 2, length: 2 }
```

#### Using an object in an array-like fashion

As mentioned above, push is intentionally generic, and we can use that to our advantage.
Array.prototype.push can work on an object just fine, as this example shows.

Note that we don't create an array to store a collection of objects. Instead, we store
the collection on the object itself and use call on Array.prototype.push to trick the
method into thinking we are dealing with an array—and it just works, thanks to the way
JavaScript allows us to establish the execution context in any way we want.

```js
const obj = {
  length: 0,

  addElem(elem) {
    // obj.length is automatically incremented
    // every time an element is added.
    [].push.call(this, elem);
  },
};

// Let's add some empty objects just to illustrate.
obj.addElem({});
obj.addElem({});
console.log(obj.length); // 2
```

Note that although obj is not an array, the method push successfully incremented obj's
length property just like if we were dealing with an actual array.

#### Parameters

- **push**(), **push**(`element0`), **push**(`element0`, `element1`)
  **push**(`element0`, `element1`, /_ …, _/ `elementN`)

`elementN`

The element(s) to add to the end of the array.

#### Return value

The new length property of the object upon which the method was called.

> #### -> see more about `push()`: [here](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/push)
>
> #### 👆🏽 go up to [Array-Methods #returns a number](#returns-a-number-1)

- ### unshift()

The `unshift()` method adds the specified elements to the beginning of an array and returns the new length of the array.

The `unshift()` method inserts the given values to the beginning of an array-like object.

Array.prototype.push() has similar behavior to `unshift()`, but applied to the end of an array.

Please note that, if multiple elements are passed as parameters, they're inserted in chunk
at the beginning of the object, in the exact same order they were passed as parameters.
Hence, calling `unshift()` with n arguments once, or calling it `n` times with `1` argument
(with a loop, for example), don't yield the same results.

```js
const array1 = [1, 2, 3];

console.log(array1.unshift(4, 5)); // Expected output: 5

console.log(array1); // Expected output: Array [4, 5, 1, 2, 3]

let arr = [4, 5, 6];

arr.unshift(1, 2, 3);
console.log(arr); // [1, 2, 3, 4, 5, 6]

arr = [4, 5, 6]; // resetting the array

arr.unshift(1);
arr.unshift(2);
arr.unshift(3);

console.log(arr); // [3, 2, 1, 4, 5, 6]
```

The `unshift()` method is generic. It only expects the this value to have a length
property and integer-keyed properties. Although strings are also array-like, this
method is not suitable to be applied on them, as strings are immutable.

```js
const arr = [1, 2];

arr.unshift(0); // result of the call is 3, which is the new array length
// arr is [0, 1, 2]

arr.unshift(-2, -1); // the new array length is 5
// arr is [-2, -1, 0, 1, 2]

arr.unshift([-4, -3]); // the new array length is 6
// arr is [[-4, -3], -2, -1, 0, 1, 2]

arr.unshift([-7, -6], [-5]); // the new array length is 8
// arr is [ [-7, -6], [-5], [-4, -3], -2, -1, 0, 1, 2 ]
```

#### Calling unshift() on non-array objects

The `unshift()` method reads the `length` property of this. It shifts all indices in the
range `0` to `length -1` right by the number of arguments (incrementing their values by this number).
Then, it sets each index starting at 0 with the arguments passed to `unshift()`.
Finally, it sets the `length` to the previous `length` plus the number of prepended elements.

```js
const arrayLike = {
  length: 3,
  unrelated: "foo",
  2: 4,
};
Array.prototype.unshift.call(arrayLike, 1, 2);
console.log(arrayLike);
// { '0': 1, '1': 2, '4': 4, length: 5, unrelated: 'foo' }

const plainObj = {};
// There's no length property, so the length is 0
Array.prototype.unshift.call(plainObj, 1, 2);
console.log(plainObj); // { '0': 1, '1': 2, length: 2 }
```

#### Parameters

- **unshift**(), **unshift**(`element0`), **unshift**(`element0`, `element1`)
  **unshift**(`element0`, `element1`, /_ …, _/ `elementN`)

`elementN`

The elements to add to the front of the arr.

#### Return value

The new length property of the object upon which the method was called.

> #### -> see more about `unshift()`: [here](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/unshift)
>
> #### 👆🏽 go up to [Array-Methods #returns a number](#returns-a-number-1)

- ### concat()

The `concat()` method is used to merge two or more arrays. This method does not change
the existing arrays, but instead returns a new array.

The `concat()` method creates a new array. The array will first be populated by the elements
in the object on which it is called. Then, for each argument, its value will be concatenated
into the array — for normal objects or primitives, the argument itself will become an element
of the final array; for arrays or array-like objects with the property `Symbol.isConcatSpreadable`
set to a `truthy value`, each element of the argument will be independently added to the final array.
The `concat()` method does not recurse into nested array arguments.

The `concat()` method is a copying method. It does not alter this or any of the arrays provided as
arguments but instead returns a shallow copy that contains the same elements as the ones from the original arrays.

The `concat()` method preserves empty slots if any of the source arrays is sparse.

The `concat()` method is generic. The this value is treated in the same way as the other arguments
(except it will be converted to an object first), which means plain objects will be directly prepended
to the resulting array, while array-like objects with truthy @@isConcatSpreadable will be spread into the resulting array.

```js
const array1 = ["a", "b", "c"];
const array2 = ["d", "e", "f"];
const array3 = array1.concat(array2);

console.log(array3);
// Expected output: Array ["a", "b", "c", "d", "e", "f"]
```

#### Concatenating two arrays

The following code concatenates two arrays:

```js
const letters = ["a", "b", "c"];
const numbers = [1, 2, 3];
const alphaNumeric = letters.concat(numbers);

console.log(alphaNumeric);
// results in ['a', 'b', 'c', 1, 2, 3]
```

#### Concatenating three arrays

The following code concatenates three arrays:

```js
const num1 = [1, 2, 3];
const num2 = [4, 5, 6];
const num3 = [7, 8, 9];
const numbers = num1.concat(num2, num3);

console.log(numbers);
// results in [1, 2, 3, 4, 5, 6, 7, 8, 9]
```

#### Concatenating values to an array

The following code concatenates three values to an array:

```js
const letters = ["a", "b", "c"];
const alphaNumeric = letters.concat(1, [2, 3]);

console.log(alphaNumeric);
// results in ['a', 'b', 'c', 1, 2, 3]
```

#### Concatenating nested arrays

The following code concatenates nested arrays and demonstrates retention of references:

```js
const num1 = [[1]];
const num2 = [2, [3]];
const numbers = num1.concat(num2);

console.log(numbers); // results in [[1], 2, [3]]

// modify the first element of num1
num1[0].push(4);
console.log(numbers); // results in [[1, 4], 2, [3]]
```

#### Parameters

- **concat**(), **concat**(`value0`), **concat**(`value0`, `value1`)
  **concat**(`value0`, `value1`, /_ …, _/ `valueN`)

`valueN` Optional

Arrays and/or values to concatenate into a new array. If all `valueN` parameters are omitted,
concat returns a shallow copy of the existing array on which it is called.

#### Return value

A new Array instance.

> #### -> see more about `concat()`: [here](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/concat)
>
> #### 👆🏽 go up to [Array-Methods #returns an array](#returns-an-array-1)

- ### flat()

The `flat()` method creates a new array with all sub-array elements concatenated into it
recursively up to the specified depth.

The `flat()` method is a `copying method`. It does not alter this but instead returns a
`shallow copy` that contains the same elements as the ones from the original array.

The `flat()` method ignores empty slots if the array being flattened is `sparse`. For example,
if depth is `1`, both empty slots in the root array and in the first level of nested arrays are ignored, but empty slots in further nested arrays are preserved with the arrays themselves.

The `flat()` method is `generic`. It only expects the this value to have a length property and
integer-keyed properties. However, its elements must be arrays if they are to be flattened.

```js
const arr1 = [0, 1, 2, [3, 4]];
console.log(arr1.flat());
// Expected output: Array [0, 1, 2, 3, 4]

const arr2 = [0, 1, 2, [[[3, 4]]]];
console.log(arr2.flat(2));
// Expected output: Array [0, 1, 2, Array [3, 4]]

const arr1 = [1, 2, [3, 4]];
arr1.flat(); // [1, 2, 3, 4]

const arr2 = [1, 2, [3, 4, [5, 6]]];
arr2.flat(); // [1, 2, 3, 4, [5, 6]]

const arr3 = [1, 2, [3, 4, [5, 6]]];
arr3.flat(2); // [1, 2, 3, 4, 5, 6]

const arr4 = [1, 2, [3, 4, [5, 6, [7, 8, [9, 10]]]]];
arr4.flat(Infinity); // [1, 2, 3, 4, 5, 6, 7, 8, 9, 10]
```

#### Using flat() on sparse arrays

The flat() method removes empty slots in arrays:

```js
const arr5 = [1, 2, , 4, 5];
console.log(arr5.flat()); // [1, 2, 4, 5]

const array = [1, , 3, ["a", , "c"]];
console.log(array.flat()); // [ 1, 3, "a", "c" ]

const array2 = [1, , 3, ["a", , ["d", , "e"]]];
console.log(array2.flat()); // [ 1, 3, "a", ["d", empty, "e"] ]
console.log(array2.flat(2)); // [ 1, 3, "a", "d", "e"]
```

#### Calling flat() on non-array objects

The flat() method reads the length property of this and then accesses each property
whose key is a nonnegative integer less than length. If the element is not an array,
it's directly appended to the result. If the element is an array, it's flattened according to the depth parameter.

```js
const arrayLike = {
  length: 3,
  0: [1, 2],
  // Array-like objects aren't flattened
  1: { length: 2, 0: 3, 1: 4 },
  2: 5,
  3: 3, // ignored by flat() since length is 3
};
console.log(Array.prototype.flat.call(arrayLike));
// [ 1, 2, { '0': 3, '1': 4, length: 2 }, 5 ]
```

#### Parameters

- **flat**(), **flat**(`depth`)

`depth` Optional

The `depth` level specifying how deep a nested array structure should be flattened. Defaults to `1`.

#### Return value

A new array with the sub-array elements concatenated into it.

> #### -> see more about `flat()`: [here](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/flat)
>
> #### 👆🏽 go up to [Array-Methods #returns an array](#returns-an-array-1)

- ### filter()

The `filter()` method creates a shallow copy of a portion of a given array,
filtered down to just the elements from the given array that pass the test
implemented by the provided function.

The `filter()` method is an iterative method. It calls a provided `callbackFn` function once
for each element in an array, and constructs a new array of all the values for which `callbackFn`
returns a truthy value. Array elements which do not pass the `callbackFn` test are not included in the new array.

`callbackFn` is invoked only for array indexes which have assigned values.
It is not invoked for empty slots in sparse arrays.

The `filter()` method is a copying method. It does not alter this but instead returns a shallow copy
that contains the same elements as the ones from the original array (with some filtered out).
However, the function provided as `callbackFn` can mutate the array. Note, however, that the
length of the array is saved before the first invocation of `callbackFn`. Therefore:

- `callbackFn` will not visit any elements added beyond the array's initial length when the call to `filter()` began.
- Changes to already-visited indexes do not cause `callbackFn` to be invoked on them again.
- If an existing, yet-unvisited element of the array is changed by `callbackFn`, its value passed to
  the `callbackFn` will be the value at the time that element gets visited. Deleted elements are not visited.

The `filter()` method is generic. It only expects the this value to have a length property and integer-keyed properties.

```js
const words = [
  "spray",
  "limit",
  "elite",
  "exuberant",
  "destruction",
  "present",
];
const result = words.filter((word) => word.length > 6);

console.log(result);
// Expected output: Array ["exuberant", "destruction", "present"]
```

#### Filtering out all small values

The following example uses `filter()` to create a filtered array that has all elements with values less than 10 removed.

```js
function isBigEnough(value) {
  return value >= 10;
}

const filtered = [12, 5, 8, 130, 44].filter(isBigEnough);
// filtered is [12, 130, 44]
```

#### Find all prime numbers in an array

```js
The following example returns all prime numbers in the array:

const array = [-3, -2, -1, 0, 1, 2, 3, 4, 5, 6, 7, 8, 9, 10, 11, 12, 13];

function isPrime(num) {
  for (let i = 2; num > i; i++) {
    if (num % i === 0) {
      return false;
    }
  }
  return num > 1;
}

console.log(array.filter(isPrime)); // [2, 3, 5, 7, 11, 13]
```

#### Filtering invalid entries from JSON

The following example uses `filter()` to create a filtered `JSON` of all elements with non-zero, numeric `id`.

```js
const arr = [
  { id: 15 },
  { id: -1 },
  { id: 0 },
  { id: 3 },
  { id: 12.2 },
  {},
  { id: null },
  { id: NaN },
  { id: "undefined" },
];

let invalidEntries = 0;

function filterByID(item) {
  if (Number.isFinite(item.id) && item.id !== 0) {
    return true;
  }
  invalidEntries++;
  return false;
}

const arrByID = arr.filter(filterByID);

console.log("Filtered Array\n", arrByID);
// Filtered Array
// [{ id: 15 }, { id: -1 }, { id: 3 }, { id: 12.2 }]

console.log("Number of Invalid Entries =", invalidEntries);
// Number of Invalid Entries = 5
```

#### Searching in array

Following example uses `filter()` to filter array content based on search criteria.

```js
const fruits = ["apple", "banana", "grapes", "mango", "orange"];

/**
 * Filter array items based on search criteria (query)
 */
function filterItems(arr, query) {
  return arr.filter((el) => el.toLowerCase().includes(query.toLowerCase()));
}

console.log(filterItems(fruits, "ap")); // ['apple', 'grapes']
console.log(filterItems(fruits, "an")); // ['banana', 'mango', 'orange']
```

#### Using filter() on sparse arrays

`filter()` will skip empty slots.

```js
console.log([1, , undefined].filter((x) => x === undefined)); // [undefined]
console.log([1, , undefined].filter((x) => x !== 2)); // [1, undefined]
```

#### Parameters

- **filter**(`callbackFn`), **filter**(`callbackFn`, `thisArg`)

`callbackFn`

A function to execute for each `element` in the `array`. It should return a truthy value
to keep the `element` in the resulting array, and a falsy value otherwise.
The function is called with the following arguments:

`element`

The current `element` being processed in the array.

`index`

The `index` of the current `element` being processed in the `array`.

`array`

The `array` `filter()` was called upon.

`thisArg` Optional

A value to use as this when executing `callbackFn`. See iterative methods.

#### Return value

A `shallow copy` of a portion of the given `array`, filtered down to just the elements from
the given `array` that pass the test implemented by the provided function.
If no elements pass the test, an empty `array` will be returned.

> #### -> see more about `filter()`: [here](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/filter)
>
> #### 👆🏽 go up to [Array-Methods #returns an array](#returns-an-array-1)

- ### from()

The `Array.from()` static method creates a new, shallow-copied Array instance from an iterable or array-like object.

`Array.from()` lets you create Arrays from:

- iterable objects (objects such as Map and Set); or, if the object is not iterable,
- array-like objects (objects with a length property and indexed elements).

To convert an ordinary object that's not iterable or array-like to an array
(by enumerating its property keys, values, or both), use `Object.keys()`, `Object.values()`,
or `Object.entries()`. To convert an async iterable to an array, use `Array.fromAsync()`.

`Array.from()` never creates a sparse array. If the arrayLike object is missing some
index properties, they become undefined in the new array.

`Array.from()` has an optional parameter mapFn, which allows you to execute a function on
each element of the array being created, similar to `map()`. More clearly, `Array.from(obj, mapFn, thisArg)`
has the same result as `Array.from(obj).map(mapFn, thisArg)`, except that it
does not create an intermediate array, and `mapFn` only receives two arguments (`element`, `index`)
without the whole array, because the array is still under construction.

The `Array.from()` method is a generic factory method. For example, if a subclass of Array inherits
the `from()` method, the inherited `from()` method will return new instances of the subclass instead
of Array instances. In fact, the this value can be any constructor function that accepts a single
argument representing the length of the new array. When an iterable is passed as arrayLike, the
constructor is called with no arguments; when an array-like object is passed, the constructor is
called with the normalized length of the array-like object. The final length will be set again when
iteration finishes. If the this value is not a constructor function, the plain Array constructor is used instead.

```js
console.log(Array.from("foo"));
// Expected output: Array ["f", "o", "o"]

console.log(Array.from([1, 2, 3], (x) => x + x));
// Expected output: Array [2, 4, 6]
```

#### Array from a String

```js
Array.from("foo"); // [ "f", "o", "o" ]
```

#### Array from a Set

```js
const set = new Set(["foo", "bar", "baz", "foo"]);
Array.from(set); // [ "foo", "bar", "baz" ]
```

#### Array from a Map

```js
const map = new Map([
  [1, 2],
  [2, 4],
  [4, 8],
]);
Array.from(map); // [[1, 2], [2, 4], [4, 8]]

const mapper = new Map([
  ["1", "a"],
  ["2", "b"],
]);
Array.from(mapper.values()); // ['a', 'b'];
Array.from(mapper.keys()); // ['1', '2'];
```

#### Array from a NodeList

```js
// Create an array based on a property of DOM Elements
const images = document.querySelectorAll("img");
const sources = Array.from(images, (image) => image.src);
const insecureSources = sources.filter((link) => link.startsWith("http://"));
```

#### Using arrow functions and Array.from()

```js
// Using an arrow function as the map function to
// manipulate the elements
Array.from([1, 2, 3], (x) => x + x);
// [2, 4, 6]

// Generate a sequence of numbers
// Since the array is initialized with `undefined` on each position,
// the value of `v` below will be `undefined`
Array.from({ length: 5 }, (v, i) => i);
// [0, 1, 2, 3, 4]
```

#### Parameters

- **Array.from**(`arrayLike`), **Array.from**(`arrayLike`, `mapFn`)
  **Array.from**(`arrayLike`, `mapFn`, `thisArg`)

`arrayLike`

An iterable or array-like object to convert to an array.

`mapFn` Optional

A function to call on every `element` of the array. If provided, every value to be added to the array is first passed through this function, and `mapFn's` return value is added to the array instead. The function is called with the following arguments:

`element`

The current `element` being processed in the array.

`index`

The `index` of the current `element` being processed in the array.

`thisArg` Optional

Value to use as this when executing `mapFn`.

#### Return value

A new Array instance.

> #### -> see more about `from()`: [here](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/from#array_from_a_nodelist)
>
> #### 👆🏽 go up to [Array-Methods #returns an array](#returns-an-array-1)

- ### map()

The `map()` method creates a new array populated with the results of calling
a provided function on every `element` in the `calling array`.

The `map()` method is an iterative method. It calls a provided `callbackFn` function once for each
`element` in an array and constructs a new array from the results.

`callbackFn` is invoked only for array indexes which have assigned values. It is not invoked for empty slots in `sparse arrays`.

The `map()` method is a copying method. It does not alter this. However, the function provided as
`callbackFn` can mutate the array. Note, however, that the length of the array is saved before the
first invocation of `callbackFn`. Therefor:

- `callbackFn` will not visit any elements added beyond the array's initial length when the call to `map()` began.
- Changes to already-visited indexes do not cause `callbackFn` to be invoked on them again.
- If an existing, yet-unvisited `element` of the array is changed by `callbackFn`, its value passed
  to the `callbackFn` will be the value at the time that `element` gets visited. Deleted elements are not visited.

The `map()` method is generic. It only expects the this value to have a length property and integer-keyed properties.

Since `map()` builds a new array, calling it without using the returned array is an anti-pattern; use `forEach` or `for...of` instead.

```js
const array1 = [1, 4, 9, 16];

// Pass a function to map
const map1 = array1.map((x) => x * 2);

console.log(map1);
// Expected output: Array [2, 8, 18, 32]
```

#### Mapping an array of numbers to an array of square roots

The following code takes an array of numbers and creates a new array containing
the square roots of the numbers in the first array.

```js
const numbers = [1, 4, 9];
const roots = numbers.map((num) => Math.sqrt(num));

// roots is now     [1, 2, 3]
// numbers is still [1, 4, 9]
```

#### Using map to reformat objects in an array

The following code takes an array of objects and creates a new array containing the newly reformatted objects.

```js
const kvArray = [
  { key: 1, value: 10 },
  { key: 2, value: 20 },
  { key: 3, value: 30 },
];

const reformattedArray = kvArray.map(({ key, value }) => ({ [key]: value }));

console.log(reformattedArray); // [{ 1: 10 }, { 2: 20 }, { 3: 30 }]
console.log(kvArray);
// [
//   { key: 1, value: 10 },
//   { key: 2, value: 20 },
//   { key: 3, value: 30 }
// ]
```

#### Mapping an array of numbers using a function containing an argument

The following code shows how map works when a function requiring one argument is used with it.
The argument will automatically be assigned from each `element` of the array as map loops through the `original array`.

```js
const numbers = [1, 4, 9];
const doubles = numbers.map((num) => num * 2);

console.log(doubles); // [2, 8, 18]
console.log(numbers); // [1, 4, 9]
```

#### Using map() generically on a NodeList

This example shows how to iterate through a collection of objects collected by querySelectorAll.
This is because querySelectorAll returns a NodeList (which is a collection of objects).

In this case, we return all the selected options' values on the screen:

```js
const elems = document.querySelectorAll("select option:checked");
const values = Array.prototype.map.call(elems, ({ value }) => value);
```

#### Using parseInt() with map()

(inspired by this blog post)

It is common to use the callback with one argument (the element being traversed).
Certain functions are also commonly used with one argument, even though they take
additional optional arguments. These habits may lead to confusing behaviors.

Consider:

```js
["1", "2", "3"].map(parseInt);
```

While one might expect `[1, 2, 3]`, the actual result is `[1, NaN, NaN]`.

parseInt is often used with one argument, but takes two. The first is an expression
and the second is the radix to the callback function, Array.prototype.map passes 3 arguments:

- the element
- the index
- the array

The third argument is ignored by parseInt—but not the second one! This is the source of possible confusion.

Here is a concise example of the iteration steps:

```js
// parseInt(string, radix) -> map(parseInt(value, index))
/* first iteration  (index is 0): */ parseInt("1", 0); // 1
/* second iteration (index is 1): */ parseInt("2", 1); // NaN
/* third iteration  (index is 2): */ parseInt("3", 2); // NaN
```

Then let's talk about solutions:

```js
const returnInt = (element) => parseInt(element, 10);

["1", "2", "3"].map(returnInt); // [1, 2, 3]
// Actual result is an array of numbers (as expected)

// Same as above, but using the concise arrow function syntax
["1", "2", "3"].map((str) => parseInt(str)); // [1, 2, 3]

// A simpler way to achieve the above, while avoiding the "gotcha":
["1", "2", "3"].map(Number); // [1, 2, 3]

// But unlike parseInt(), Number() will also return a float or (resolved) exponential notation:
["1.1", "2.2e2", "3e300"].map(Number); // [1.1, 220, 3e+300]

// For comparison, if we use parseInt() on the array above:
["1.1", "2.2e2", "3e300"].map((str) => parseInt(str)); // [1, 2, 3]
```

One alternative output of the map method being called with `parseInt` as a parameter runs as follows:

```js
const strings = ["10", "10", "10"];
const numbers = strings.map(parseInt);

console.log(numbers);
// Actual result of [10, NaN, 2] may be unexpected based on the above description.
```

#### Mapped array contains undefined

When `undefined` or nothing is returned:

```js
const numbers = [1, 2, 3, 4];
const filteredNumbers = numbers.map((num, index) => {
  if (index < 3) {
    return num;
  }
});

// index goes from 0, so the filterNumbers are 1,2,3 and undefined.
// filteredNumbers is [1, 2, 3, undefined]
// numbers is still [1, 2, 3, 4]
```

#### Parameters

- **map**(`callbackFn`), **map**(`callbackFn`, `thisArg`)

`callbackFn`

A function to execute for each element in the array.
Its return value is discarded. The function is called
with the following arguments:

- `element`

  The current element being processed in the array.

- `index`

  The index of the current element being processed in the array.

- `array`

  The array `map()` was called upon.

`thisArg` Optional

A value to use as this when executing `callbackFn`. See iterative methods.

#### Return value

A new array with each element being the result of the callback function.

> #### -> see more about `map()`: [here](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/map)
>
> #### 👆🏽 go up to [Array-Methods #returns an array](#returns-an-array-1)

- ### of()

The `Array.of()` static method creates a new Array instance from a variable number
of arguments, regardless of number or type of the arguments.

```js
console.log(Array.of("foo", 2, "bar", true));
// Expected output: Array ["foo", 2, "bar", true]

console.log(Array.of());
// Expected output: Array []
```

The difference between `Array.of()` and the Array() constructor is in the handling
of single arguments: `Array.of(7)` creates an array with a single element, `7`, whereas
`Array(7)` creates an empty array with a length property of `7`. (That implies an array
of 7 empty slots, not slots with actual undefined values.)

```js
Array.of(7); // [7]
Array(7); // array of 7 empty slots

Array.of(1, 2, 3); // [1, 2, 3]
Array(1, 2, 3); // [1, 2, 3]
```

The `Array.of()` method is a generic factory method. For example, if a subclass
of Array inherits the `of()` method, the inherited `of()` method will return new instances
of the subclass instead of Array instances. In fact, the this value can be any constructor
function that accepts a single argument representing the length of the new array, and
the constructor will be called with the number of arguments passed to `of()`. The final
length will be set again when all elements are assigned. If the this value is not a
constructor function, the plain Array constructor is used instead.

```js
Array.of(1); // [1]
Array.of(1, 2, 3); // [1, 2, 3]
Array.of(undefined); // [undefined]
```

#### Calling of() on non-array constructors

The `of()` method can be called on any constructor function that accepts a single
argument representing the length of the new array.

```js
function NotArray(len) {
  console.log("NotArray called with length", len);
}

console.log(Array.of.call(NotArray, 1, 2, 3));
// NotArray called with length 3
// NotArray { '0': 1, '1': 2, '2': 3, length: 3 }

console.log(Array.of.call(Object)); // [Number: 0] { length: 0 }
```

#### Parameters

- **Array.of**(), **Array.of**(`element0`), **Array.of**(`element0`, `element1`)
  **Array.of**(`element0`, `element1`, /_ …, _/ `elementN`)

`elementN`

Elements used to create the array.

#### Return value

A new Array instance.

> #### -> see more about `of()`: [here](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/of)
>
> #### 👆🏽 go up to [Array-Methods #returns an array](#returns-an-array-1)

- ### slice()

The `slice()` method returns a `shallow copy` of a portion of an array into a new array
object selected from start to end (end not included) where start and end represent the
index of items in that array. The `original array` will not be modified.

The `slice()` method is a copying method. It does not alter this but instead returns
a `shallow copy` that contains some of the same elements as the ones from the `original array`.

The `slice()` method preserves empty slots. If the sliced portion is sparse, the `returned array`
is sparse as well.

The `slice()` method is generic. It only expects the this value to have a length property and
integer-keyed properties.

```js
const animals = ["ant", "bison", "camel", "duck", "elephant"];

console.log(animals.slice(2));
// Expected output: Array ["camel", "duck", "elephant"]

console.log(animals.slice(2, 4));
// Expected output: Array ["camel", "duck"]

console.log(animals.slice(1, 5));
// Expected output: Array ["bison", "camel", "duck", "elephant"]

console.log(animals.slice(-2));
// Expected output: Array ["duck", "elephant"]

console.log(animals.slice(2, -1));
// Expected output: Array ["camel", "duck"]

console.log(animals.slice());
// Expected output: Array ["ant", "bison", "camel", "duck", "elephant"]
```

#### Return a portion of an existing array

```js
const fruits = ["Banana", "Orange", "Lemon", "Apple", "Mango"];
const citrus = fruits.slice(1, 3);

// fruits contains ['Banana', 'Orange', 'Lemon', 'Apple', 'Mango']
// citrus contains ['Orange','Lemon']
```

#### Using slice

In the following example, `slice()` creates a new array, newCar, from myCar.
Both include a reference to the object myHonda. When the color of myHonda is
changed to purple, both arrays reflect the change.

```js
// Using slice, create newCar from myCar.
const myHonda = {
  color: "red",
  wheels: 4,
  engine: { cylinders: 4, size: 2.2 },
};
const myCar = [myHonda, 2, "cherry condition", "purchased 1997"];
const newCar = myCar.slice(0, 2);

console.log("myCar =", myCar);
console.log("newCar =", newCar);
console.log("myCar[0].color =", myCar[0].color);
console.log("newCar[0].color =", newCar[0].color);

// Change the color of myHonda.
myHonda.color = "purple";
console.log("The new color of my Honda is", myHonda.color);

console.log("myCar[0].color =", myCar[0].color);
console.log("newCar[0].color =", newCar[0].color);
```

> This script writes:

```
myCar = [
{ color: 'red', wheels: 4, engine: { cylinders: 4, size: 2.2 } },
2,
'cherry condition',
'purchased 1997'
]
newCar = [ { color: 'red', wheels: 4, engine: { cylinders: 4, size: 2.2 } }, 2 ]
myCar[0].color = red
newCar[0].color = red
The new color of my Honda is purple
myCar[0].color = purple
newCar[0].color = purple
```

#### Parameters

- **slice**(), **slice**(`start`), **slice**(`start`, `end`)

`start` Optional

Zero-based index at which to `start` extraction, converted to an integer.

- Negative index counts back from the `end` of the array — if `start < 0`, `start + array.length` is used.
- If `start < -array.length` or start is omitted, `0` is used.
- If `start >= array.length`, nothing is extracted.

`end` Optional

Zero-based index at which to end extraction, converted to an `integer.slice()` extracts up to but not including `end`.

- Negative index counts back from the end of the array — if `end < 0`, `end + array.length` is used.
- If `end < -array.length`, `0` is used.
- If `end >= array.length` o`r` `end` is omitted, `array.length` is used, causing all elements until the `end` to be extracted.
- If `end` is positioned before or at `start` after normalization, nothing is extracted.

#### Return value

A new array containing the extracted elements.

> #### -> see more about `slice()`: [here](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/slice)
>
> #### 👆🏽 go up to [Array-Methods #returns an array](#returns-an-array-1)

- ### fill()

The `fill()` method of Array instances changes all elements within a range of indices in an array
to a static value. It returns the modified array.

The `fill()` method is a mutating method. It does not alter the length of this, but it will
change the content of this.

The `fill()` method fills empty slots in sparse arrays with value as well.

The `fill()` method is generic. It only expects the this value to have a length property.
Although strings are also array-like, this method is not suitable to be applied on them, as strings are immutable.

```js
const array1 = [1, 2, 3, 4];

// Fill with 0 from position 2 until position 4
console.log(array1.fill(0, 2, 4));
// Expected output: Array [1, 2, 0, 0]

// Fill with 5 from position 1
console.log(array1.fill(5, 1));
// Expected output: Array [1, 5, 5, 5]

console.log(array1.fill(6));
// Expected output: Array [6, 6, 6, 6]

console.log([1, 2, 3].fill(4)); // [4, 4, 4]
console.log([1, 2, 3].fill(4, 1)); // [1, 4, 4]
console.log([1, 2, 3].fill(4, 1, 2)); // [1, 4, 3]
console.log([1, 2, 3].fill(4, 1, 1)); // [1, 2, 3]
console.log([1, 2, 3].fill(4, 3, 3)); // [1, 2, 3]
console.log([1, 2, 3].fill(4, -3, -2)); // [4, 2, 3]
console.log([1, 2, 3].fill(4, NaN, NaN)); // [1, 2, 3]
console.log([1, 2, 3].fill(4, 3, 5)); // [1, 2, 3]
console.log(Array(3).fill(4)); // [4, 4, 4]

// A single object, referenced by each slot of the array:
const arr = Array(3).fill({}); // [{}, {}, {}]
arr[0].hi = "hi"; // [{ hi: "hi" }, { hi: "hi" }, { hi: "hi" }]
```

#### Using fill() to create a matrix of all 1

This example shows how to create a matrix of all 1, like the `ones()` function of Octave or MATLAB.

```js
const arr = new Array(3);
for (let i = 0; i < arr.length; i++) {
  arr[i] = new Array(4).fill(1); // Creating an array of size 4 and filled of 1
}
arr[0][0] = 10;
console.log(arr[0][0]); // 10
console.log(arr[1][0]); // 1
console.log(arr[2][0]); // 1
```

#### Using fill() to populate an empty array

This example shows how to populate an array, setting all elements to a
specific value. The end parameter does not have to be specified.

```js
const tempGirls = Array(5).fill("girl", 0);
```

#### Calling fill() on non-array objects

The fill() method reads the length property of this and sets the value of
each integer-keyed property from start to end.

```js
const arrayLike = { length: 2 };
console.log(Array.prototype.fill.call(arrayLike, 1));
// { '0': 1, '1': 1, length: 2 }
```

#### Parameters

- **fill**(`value`), **fill**(`value`, `start`), **fill**(`value`, `start`, `end`)

`value`

Value to fill the array with. Note all elements in the array will be this exact `value`:
if `value` is an object, each slot in the array will reference that object.

`start` Optional

Zero-based index at which to `start` filling, converted to an integer.

- Negative index counts back from the `end` of the array — if `start < 0`, `start + array.length` is used.
- If start < -array.length or `start` is omitted, 0 is used.
- If start >= array.length, no index is filled.

`end` Optional

Zero-based index at which to `end` filling, converted to an integer. `fill()` fills up to but not including `end`.

- Negative index counts back from the `end` of the array — if `end < 0`, `end + array.length` is used.
- If `end < -array.length`, `0` is used.
- If `end >= array.length` or `end` is omitted, `array.length` is used, causing all indices until the `end` to be filled.
- If `end` is positioned before or at `start` after normalization, no index is filled.

#### Return value

The modified array, filled with `value`.

> #### -> see more about `fill()`: [here](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/fill)
>
> #### 👆🏽 go up to [Array-Methods #returns the same modified array](#returns-the-same-modified-array)

- ### sort()

The `sort()` method of Array instances sorts the elements of an array in place and returns
the reference to the same array, now sorted. The default sort order is ascending, built upon
converting the elements into strings, then comparing their sequences of UTF-16 code units values.

The time and space complexity of the sort cannot be guaranteed as it depends on the implementation.

To sort the elements in an array without mutating the original array, use toSorted().

```js
const months = ["March", "Jan", "Feb", "Dec"];
months.sort();
console.log(months);
// Expected output: Array ["Dec", "Feb", "Jan", "March"]

const array1 = [1, 30, 4, 21, 100000];
array1.sort();
console.log(array1);
// Expected output: Array [1, 100000, 21, 30, 4]
```

If `compareFn` is not supplied, all non-`undefined` array elements are sorted by converting them to
strings and comparing strings in UTF-16 code units order. For example, "banana" comes before "cherry".
In a numeric sort, 9 comes before 80, but because numbers are converted to strings, "80" comes before "9"
in the Unicode order. All `undefined` elements are sorted to the end of the array.

The sort() method preserves empty slots. If the source array is sparse, the empty slots are moved to the
end of the array, and always come after all the `undefined`.

If `compareFn` is supplied, all non-`undefined` array elements are sorted according to the return value of
the compare function (all `undefined` elements are sorted to the end of the array, with no call to `compareFn`).

| `compareFn`(a, b) return value | sort order                     |
| ------------------------------ | ------------------------------ |
| > 0                            | sort a after b, e.g. [b, a]    |
| < 0                            | sort a before b, e.g. [a, b]   |
| === 0                          | keep original order of a and b |

So, the compare function has the following form:

```js
function compareFn(a, b) {
  if (a is less than b by some ordering criterion) {
    return -1;
  }
  if (a is greater than b by the ordering criterion) {
    return 1;
  }
  // a must be equal to b
  return 0;
}
```

More formally, the comparator is expected to have the following properties, in order to ensure proper sort behavior:

- Pure: The comparator does not mutate the objects being compared or any external state.
  (This is important because there's no guarantee when and how the comparator will be called,
  so any particular call should not produce visible effects to the outside.)
- Stable: The comparator returns the same result with the same pair of input.
- Reflexive: `compareFn(a, a) === 0`.
- Anti-symmetric: `compareFn(a, b)` and `compareFn(b, a)` must both be `0` or have opposite signs.
- Transitive: If `compareFn(a, b)` and `compareFn(b, c)` are both positive, zero, or negative,
  then `compareFn(a, c)` has the same positivity as the previous two.

A comparator conforming to the constraints above will always be able to return all of `1`, `0`,
and `-1`, or consistently return `0`. For example, if a comparator only returns `1` and `0`, or only
returns 0 and `-1`, it will not be able to sort reliably because anti-symmetry is broken.
A comparator that always returns `0` will cause the array to not be changed at all, but is reliable nonetheless.

The default lexicographic comparator satisfies all constraints above.

To compare numbers instead of strings, the compare function can subtract `b` from `a`.
The following function will sort the array in ascending order (if it doesn't contain Infinity and `NaN`):

```js
function compareNumbers(a, b) {
  return a - b;
}
```

The `sort()` method is generic. It only expects the this value to have a length property
and integer-keyed properties. Although strings are also array-like, this method is not
suitable to be applied on them, as strings are immutable.

#### Creating, displaying, and sorting an array

The following example creates four arrays and displays the original array,
then the sorted arrays. The numeric arrays are sorted without a compare function, then sorted using one.

```js
const stringArray = ["Blue", "Humpback", "Beluga"];
const numberArray = [40, 1, 5, 200];
const numericStringArray = ["80", "9", "700"];
const mixedNumericArray = ["80", "9", "700", 40, 1, 5, 200];

function compareNumbers(a, b) {
  return a - b;
}

stringArray.join(); // 'Blue,Humpback,Beluga'
stringArray.sort(); // ['Beluga', 'Blue', 'Humpback']

numberArray.join(); // '40,1,5,200'
numberArray.sort(); // [1, 200, 40, 5]
numberArray.sort(compareNumbers); // [1, 5, 40, 200]

numericStringArray.join(); // '80,9,700'
numericStringArray.sort(); // ['700', '80', '9']
numericStringArray.sort(compareNumbers); // ['9', '80', '700']

mixedNumericArray.join(); // '80,9,700,40,1,5,200'
mixedNumericArray.sort(); // [1, 200, 40, 5, '700', '80', '9']
mixedNumericArray.sort(compareNumbers); // [1, 5, '9', 40, '80', 200, '700']
```

#### Sorting array of objects

Arrays of objects can be sorted by comparing the value of one of their properties.

```js
const items = [
  { name: "Edward", value: 21 },
  { name: "Sharpe", value: 37 },
  { name: "And", value: 45 },
  { name: "The", value: -12 },
  { name: "Magnetic", value: 13 },
  { name: "Zeros", value: 37 },
];

// sort by value
items.sort((a, b) => a.value - b.value);

// sort by name
items.sort((a, b) => {
  const nameA = a.name.toUpperCase(); // ignore upper and lowercase
  const nameB = b.name.toUpperCase(); // ignore upper and lowercase
  if (nameA < nameB) {
    return -1;
  }
  if (nameA > nameB) {
    return 1;
  }

  // names must be equal
  return 0;
});
```

Sorting non-ASCII characters

For sorting strings with non-ASCII characters, i.e. strings with accented characters
(e, é, è, a, ä, etc.), strings from languages other than English, use `String.prototype.localeCompare()`.
This function can compare those characters so they appear in the right order.

```js
const items = ["réservé", "premier", "communiqué", "café", "adieu", "éclair"];
items.sort((a, b) => a.localeCompare(b));

// items is ['adieu', 'café', 'communiqué', 'éclair', 'premier', 'réservé']
```

#### Sorting with map

The compareFn can be invoked multiple times per element within the array.
Depending on the compareFn's nature, this may yield a high overhead. The more work a
compareFn does and the more elements there are to sort, it may be more efficient to
use `map()` for sorting. The idea is to traverse the array once to extract the actual
values used for sorting into a temporary array, sort the temporary array,
and then traverse the temporary array to achieve the right order.

```js
// the array to be sorted
const data = ["delta", "alpha", "charlie", "bravo"];

// temporary array holds objects with position and sort-value
const mapped = data.map((v, i) => {
  return { i, value: someSlowOperation(v) };
});

// sorting the mapped array containing the reduced values
mapped.sort((a, b) => {
  if (a.value > b.value) {
    return 1;
  }
  if (a.value < b.value) {
    return -1;
  }
  return 0;
});

const result = mapped.map((v) => data[v.i]);
```

There is an open source library available called mapsort which applies this approach.

#### sort() returns the reference to the same array

The `sort()` method returns a reference to the original array, so mutating
the returned array will mutate the original array as well.

```js
const numbers = [3, 1, 4, 1, 5];
const sorted = numbers.sort((a, b) => a - b);
// numbers and sorted are both [1, 1, 3, 4, 5]
sorted[0] = 10;
console.log(numbers[0]); // 10
```

In case you want `sort()` to not mutate the original array, but return a
`shallow-copied array` like other array methods (e.g. `map()`) do, use the `toSorted()` method.
Alternatively, you can do a shallow copy before calling `sort()`, using the spread syntax or `Array.from()`.

```js
const numbers = [3, 1, 4, 1, 5];
// [...numbers] creates a shallow copy, so sort() does not mutate the original
const sorted = [...numbers].sort((a, b) => a - b);
sorted[0] = 10;
console.log(numbers[0]); // 3
```

#### Parameters

- **sort**(), **sort**(`compareFn`)

`compareFn` Optional

A function that defines the sort order. The return value should be a number whose sign
indicates the relative order of the two elements: negative if `a` is less than `b`, positive
if `a` is greater than `b`, and zero if they are equal. `NaN` is treated as `0`.
The function is called with the following arguments:

`a`

The first element for comparison. Will never be `undefined`.

`b`

The second element for comparison. Will never be `undefined`.

If omitted, the array elements are converted to strings, then sorted according to each character's Unicode code point value.

#### Return value

The reference to the original array, now sorted. Note that the array is sorted in place, and no copy is made.

> #### -> see more about `sort()`: [here](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/sort)
>
> #### 👆🏽 go up to [Array-Methods #returns the same modified array](#returns-the-same-modified-array)

- ### find()

The `find()` method of Array instances returns the first element in the provided array
that satisfies the provided testing function. If no values satisfy the testing function,
undefined is returned.

- If you need the index of the found element in the array, use `findIndex()`.
- If you need to find the index of a value, use `indexOf()`. (It's similar to `findIndex()`,
  but checks each element for equality with the value instead of using a testing function.)
- If you need to find if a value exists in an array, use `includes()`. Again, it checks
  each element for equality with the value instead of using a testing function.
- If you need to find if any element satisfies the provided testing function, use `some()`.

```js
const array1 = [5, 12, 8, 130, 44];

const found = array1.find((element) => element > 10);

console.log(found);
// Expected output: 12
```

The `find()` method is an iterative method. It calls a provided `callbackFn` function
once for each element in an array in ascending-index order, until `callbackFn` returns
a truthy value. `find()` then returns that element and stops iterating through the array.
If `callbackFn` never returns a truthy value, `find()` returns undefined.

`callbackFn` is invoked for every index of the array, not just those with assigned values.
Empty slots in sparse arrays behave the same as undefined.

`find()` does not mutate the array on which it is called, but the function provided as
`callbackFn` can. Note, however, that the length of the array is saved before the first
invocation of `callbackFn`. Therefore:

- `callbackFn` will not visit any elements added beyond the array's initial length when the call to `find()` began.
- Changes to already-visited indexes do not cause `callbackFn` to be invoked on them again.
- If an existing, yet-unvisited element of the array is changed by `callbackFn`, its value
  passed to the `callbackFn` will be the value at the time that element gets visited.
  Deleted elements are visited as if they were undefined.

The `find()` method is generic. It only expects the this value to have a length property and integer-keyed properties.

#### Find an object in an array by one of its properties

```js
const inventory = [
  { name: "apples", quantity: 2 },
  { name: "bananas", quantity: 0 },
  { name: "cherries", quantity: 5 },
];

function isCherries(fruit) {
  return fruit.name === "cherries";
}

console.log(inventory.find(isCherries));
// { name: 'cherries', quantity: 5 }
```

#### Using arrow function and destructuring

```js
const inventory = [
  { name: "apples", quantity: 2 },
  { name: "bananas", quantity: 0 },
  { name: "cherries", quantity: 5 },
];

const result = inventory.find(({ name }) => name === "cherries");

console.log(result); // { name: 'cherries', quantity: 5 }
```

#### Find a prime number in an array

The following example finds an element in the array that is a prime number
(or returns undefined if there is no prime number):

```js
function isPrime(element, index, array) {
  let start = 2;
  while (start <= Math.sqrt(element)) {
    if (element % start++ < 1) {
      return false;
    }
  }
  return element > 1;
}

console.log([4, 6, 8, 12].find(isPrime)); // undefined, not found
console.log([4, 5, 8, 12].find(isPrime)); // 5
```

#### Parameters

- **find**(`callbackFn`), **find**(`callbackFn`, `thisArg`)

`callbackFn`

A function to execute for each `element` in the `array`. It should return a truthy value to indicate a matching `element` has been found, and a falsy value otherwise. The function is called with the following arguments:

`element`

The current `element` being processed in the `array`.

`index`

The `index` of the current `element` being processed in the `array`.

`array`

The `array find()` was called upon.

`thisArg` Optional

A value to use as this when executing `callbackFn`. See iterative methods.

#### Return value

The first element in the array that satisfies the provided testing function.
Otherwise, undefined is returned.

> #### -> see more about `find()`: [here](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/find)
>
> #### 👆🏽 go up to [Array-Methods #returns an element of the array](#returns-an-element-of-the-array)

- ### findLast()

The `findLast()` method of Array instances iterates the array in reverse order
and returns the value of the first element that satisfies the provided testing function.
If no elements satisfy the testing function, undefined is returned.

If you need to find:

- the first element that matches, use `find()`.
- the index of the last matching element in the array, use `findLastIndex()`.
- the index of a value, use `indexOf()`. (It's similar to `findIndex()`,
  but checks each element for equality with the value instead of using a testing function.)
- whether a value exists in an array, use `includes()`. Again, it checks
  each element for equality with the value instead of using a testing function.
- if any element satisfies the provided testing function, use `some()`.

```js
const array1 = [5, 12, 50, 130, 44];
const found = array1.findLast((element) => element > 45);

console.log(found);
// Expected output: 130
```

The `findLast()` method is an iterative method. It calls a provided callbackFn function
once for each element in an array in descending-index order, until callbackFn returns
a truthy value. `findLast()` then returns that element and stops iterating through
the array. If callbackFn never returns a truthy value, `findLast()` returns undefined.

callbackFn is invoked for every index of the array, not just those with assigned values.
Empty slots in sparse arrays behave the same as undefined.

`findLast()` does not mutate the array on which it is called, but the function provided as
callbackFn can. Note, however, that the length of the array is saved before the first invocation of callbackFn.
Therefore:

- callbackFn will not visit any elements added beyond the array's initial length when the call to `findLast()` began.
- Changes to already-visited indexes do not cause callbackFn to be invoked on them again.
- If an existing, yet-unvisited element of the array is changed by callbackFn,
  its value passed to the callbackFn will be the value at the time that element
  gets visited. Deleted elements are visited as if they were undefined.

The `findLast()` method is generic. It only expects the this value to have a length property and integer-keyed properties.

#### Find last object in an array matching on element properties

This example shows how you might create a test based on the properties of array elements.

```js
const inventory = [
  { name: "apples", quantity: 2 },
  { name: "bananas", quantity: 0 },
  { name: "fish", quantity: 1 },
  { name: "cherries", quantity: 5 },
];

// return true inventory stock is low
function isNotEnough(item) {
  return item.quantity < 2;
}

console.log(inventory.findLast(isNotEnough));
// { name: "fish", quantity: 1 }
```

#### Using arrow function and destructuring

The previous example might be written using an arrow function and object destructuring:

```js
const inventory = [
  { name: "apples", quantity: 2 },
  { name: "bananas", quantity: 0 },
  { name: "fish", quantity: 1 },
  { name: "cherries", quantity: 5 },
];

const result = inventory.findLast(({ quantity }) => quantity < 2);

console.log(result);
// { name: "fish", quantity: 1 }
```

#### Find the last prime number in an array

The following example returns the last element in the array that is a prime number, or undefined if there is no prime number.

```js
function isPrime(element) {
  if (element % 2 === 0 || element < 2) {
    return false;
  }
  for (let factor = 3; factor <= Math.sqrt(element); factor += 2) {
    if (element % factor === 0) {
      return false;
    }
  }
  return true;
}

console.log([4, 6, 8, 12].findLast(isPrime)); // undefined, not found
console.log([4, 5, 7, 8, 9, 11, 12].findLast(isPrime)); // 11
```

#### Parameters

- **findLast**(`callbackFn`), **findLast**(`callbackFn`, `thisArg`)

`callbackFn`

A function to execute for each `element` in the `array`. It should return a
truthy value to indicate a matching `element` has been found, and a falsy value
otherwise. The function is called with the following arguments:

`element`

The current `element` being processed in the `array`.

`index`

The `index` of the current `element` being processed in the `array`.

`array`

The `array findLast()` was called upon.

`thisArg` Optional

A value to use as this when executing `callbackFn`. See iterative methods.

#### Return value

The value of the `element` in the `array` with the highest `index` value that satisfies
the provided testing function; `undefined` if no matching `element` is found.

> #### -> see more about `findLast()`: [here](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/findLast)
>
> #### 👆🏽 go up to [Array-Methods #returns an element of the array](#returns-an-element-of-the-array)

- ### pop()

The `pop()` method of Array instances removes the last element from an array and
returns that element. This method changes the length of the array.

The `pop()` method removes the last element from an array and returns that value
to the caller. If you call `pop()` on an empty array, it returns undefined.

`Array.prototype.shift()` has similar behavior to `pop()`, but applied to the first element in an array.

The `pop()` method is a mutating method. It changes the length and the content of this.
In case you want the value of this to be the same, but return a new array with the
last element removed, you can use `arr.slice(0, -1)` instead.

The `pop()` method is generic. It only expects the this value to have a length property and
integer-keyed properties. Although strings are also array-like, this method is not
suitable to be applied on them, as strings are immutable.

```js
const plants = ["broccoli", "cauliflower", "cabbage", "kale", "tomato"];

console.log(plants.pop());
// Expected output: "tomato"

console.log(plants);
// Expected output: Array ["broccoli", "cauliflower", "cabbage", "kale"]

plants.pop();

console.log(plants);
// Expected output: Array ["broccoli", "cauliflower", "cabbage"]
```

#### Removing the last element of an array

The following code creates the myFish array containing four elements, then removes its last element.

```js
const myFish = ["angel", "clown", "mandarin", "sturgeon"];
const popped = myFish.pop();

console.log(myFish); // ['angel', 'clown', 'mandarin' ]
console.log(popped); // 'sturgeon'
```

#### Calling pop() on non-array objects

The `pop()` method reads the `length` property of this. If the normalized `length` is `0`,
`length` is set to `0` again (whereas it may be negative or undefined before).
Otherwise, the property at `length - 1` is returned and deleted.

```js
const arrayLike = {
  length: 3,
  unrelated: "foo",
  2: 4,
};
console.log(Array.prototype.pop.call(arrayLike)); // 4
console.log(arrayLike); // { length: 2, unrelated: 'foo' }

const plainObj = {};
// There's no length property, so the length is 0
Array.prototype.pop.call(plainObj);
console.log(plainObj); // { length: 0 }
```

#### Return value

The removed element from the array; `undefined` if the array is empty.

> #### -> see more about `pop()`: [here](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/pop)
>
> #### 👆🏽 go up to [Array-Methods #returns an element of the array](#returns-an-element-of-the-array)

- ### shift()

The `shift()` method of Array instances removes the first element from an array
and returns that removed element. This method changes the length of the array.

```js
const array1 = [1, 2, 3];
const firstElement = array1.shift();

console.log(array1); // Expected output: Array [2, 3]

console.log(firstElement); // Expected output: 1
```

The `shift()` method removes the element at the zeroth index and shifts the values
at consecutive indexes down, then returns the removed value. If the length property is `0`, `undefined` is returned.

The `pop()` method has similar behavior to `shift()`, but applied to the last element in an array.

The `shift()` method is a mutating method. It changes the length and the content of this.
In case you want the value of this to be the same, but return a new array with the
first element removed, you can use `arr.slice(1)` instead.

The `shift()` method is generic. It only expects the this value to have a length property
and integer-keyed properties. Although strings are also array-like, this method is
not suitable to be applied on them, as strings are immutable.

#### Removing an element from an array

The following code displays the myFish array before and after removing
its first element. It also displays the removed element:

```js
const myFish = ["angel", "clown", "mandarin", "surgeon"];
console.log("myFish before:", myFish);
// myFish before: ['angel', 'clown', 'mandarin', 'surgeon']

const shifted = myFish.shift();
console.log("myFish after:", myFish);
// myFish after: ['clown', 'mandarin', 'surgeon']

console.log("Removed this element:", shifted);
// Removed this element: angel
```

#### Using shift() method in while loop

The shift() method is often used in condition inside while loop.
In the following example every iteration will remove the next element
from an array, until it is empty:

```js
const names = ["Andrew", "Tyrone", "Paul", "Maria", "Gayatri"];

while (typeof (i = names.shift()) !== "undefined") {
  console.log(i);
}
// Andrew, Tyrone, Paul, Maria, Gayatri
```

#### Return value

The removed element from the array; `undefined` if the array is empty.

> #### -> see more about `shift()`: [here](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/shift)
>
> #### 👆🏽 go up to [Array-Methods #returns an element of the array](#returns-an-element-of-the-array)

- ### entries()

The `entries()` method of Array instances returns a new array iterator object
that contains the key/value pairs for each index in the array.

When used on sparse arrays, the `entries()` method iterates empty slots as if they have the value `undefined`.

The `entries()` method is generic. It only expects the this value to have a
`length` property and integer-keyed properties.

```js
const array1 = ["a", "b", "c"];

const iterator1 = array1.entries();

console.log(iterator1.next().value);
// Expected output: Array [0, "a"]

console.log(iterator1.next().value);
// Expected output: Array [1, "b"]
```

#### Iterating with index and element

```js
const a = ["a", "b", "c"];

for (const [index, element] of a.entries()) {
  console.log(index, element);
}

// 0 'a'
// 1 'b'
// 2 'c'
```

#### Using a for...of loop

```js
const array = ["a", "b", "c"];
const arrayEntries = array.entries();

for (const element of arrayEntries) {
  console.log(element);
}

// [0, 'a']
// [1, 'b']
// [2, 'c']
```

#### Iterating sparse arrays

`entries()` will visit empty slots as if they are undefined.

```js
for (const element of [, "a"].entries()) {
  console.log(element);
}
// [0, undefined]
// [1, 'a']
```

#### Calling entries() on non-array objects

The `entries()` method reads the `length` property of this and then accesses
each property whose key is a nonnegative integer less than `length`.

```js
const arrayLike = {
  length: 3,
  0: "a",
  1: "b",
  2: "c",
  3: "d", // ignored by entries() since length is 3
};
for (const entry of Array.prototype.entries.call(arrayLike)) {
  console.log(entry);
}
// [ 0, 'a' ]
// [ 1, 'b' ]
// [ 2, 'c' ]
```

#### Return value

A new iterable iterator object.

> #### -> see more about `entries()`: [here](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/entries)
>
> #### 👆🏽 go up to [Array-Methods #returns an object](#returns-an-object)

- ### values()

The `values()` method of Array instances returns a new array iterator
object that iterates the value of each item in the array.

```js
const array1 = ["a", "b", "c"];
const iterator = array1.values();

for (const value of iterator) {
  console.log(value);
}

// Expected output: "a"
// Expected output: "b"
// Expected output: "c"
```

`Array.prototype.values()` is the default implementation of `Array.prototype[@@iterator]()`.

```js
Array.prototype.values === Array.prototype[Symbol.iterator]; // true
```

When used on sparse arrays, the `values()` method iterates empty slots as if they have the value `undefined`.

The `values()` method is generic. It only expects the this value to have a length property and integer-keyed properties.

#### Iteration using for...of loop

Because `values()` returns an iterable iterator, you can use a `for...of` loop to iterate it.

```js
const arr = ["a", "b", "c", "d", "e"];
const iterator = arr.values();

for (const letter of iterator) {
  console.log(letter);
} // "a" "b" "c" "d" "e"
```

#### Iteration using next()

Because the return value is also an iterator, you can directly call its `next()` method.

```js
const arr = ["a", "b", "c", "d", "e"];
const iterator = arr.values();
iterator.next(); // { value: "a", done: false }
iterator.next(); // { value: "b", done: false }
iterator.next(); // { value: "c", done: false }
iterator.next(); // { value: "d", done: false }
iterator.next(); // { value: "e", done: false }
iterator.next(); // { value: undefined, done: true }
console.log(iterator.next().value); // undefined
```

#### Reusing the iterable

The iterable returned from `values()` is not reusable. When `next().done = true` or
`currentIndex > length`, the `for...of` loop ends, and further iterating it has no effect.

```js
const arr = ["a", "b", "c", "d", "e"];
const values = arr.values();
for (const letter of values) {
  console.log(letter);
}
// "a" "b" "c" "d" "e"
for (const letter of values) {
  console.log(letter);
}
// undefined
```

If you use a break statement to end the iteration early, the iterator can resume
from the current position when continuing to iterate it.

```js
const arr = ["a", "b", "c", "d", "e"];
const values = arr.values();
for (const letter of values) {
  console.log(letter);
  if (letter === "b") {
    break;
  }
}
// "a" "b"

for (const letter of values) {
  console.log(letter);
}
// "c" "d" "e"
```

#### Mutations during iteration

There are no values stored in the array iterator object returned from `values()`;
instead, it stores the address of the array used in its creation, and reads the
currently visited index on each iteration. Therefore, its iteration output depends
on the value stored in that index at the time of stepping. If the values in the
array changed, the array iterator object's values change too.

```js
const arr = ["a", "b", "c", "d", "e"];
const iterator = arr.values();
console.log(iterator); // Array Iterator { }
console.log(iterator.next().value); // "a"
arr[1] = "n";
console.log(iterator.next().value); // "n"
```

#### Return value

A new iterable iterator object.

> #### -> see more about `values()`: [here](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/values)
>
> #### 👆🏽 go up to [Array-Methods #returns an object](#returns-an-object)

## Object-Methods

- ### hasOwn()

The `Object.hasOwn()` static method returns true if the specified object has the
indicated property as its own property. If the property is inherited, or does not exist,
the method returns false.

The `Object.hasOwn()` method returns true if the specified property is a direct
property of the object — even if the property value is null or undefined.
The method returns false if the property is inherited, or has not been declared at all.
Unlike the in operator, this method does not check for the specified property in the object's prototype chain.

It is recommended over `Object.prototype.hasOwnProperty()` because it works for
objects created using `Object.create(null)` and with objects that have overridden
the inherited `hasOwnProperty()` method. While it is possible to workaround these
problems by calling `Object.prototype.hasOwnProperty()` on an external object,
`Object.hasOwn()` is more intuitive.

```js
const object1 = {
  prop: "exists",
};

console.log(Object.hasOwn(object1, "prop"));
// Expected output: true

console.log(Object.hasOwn(object1, "toString"));
// Expected output: false

console.log(Object.hasOwn(object1, "undeclaredPropertyValue"));
// Expected output: false
```

#### Using hasOwn to test for a property's existence

The following code shows how to determine whether the example object contains a property named prop.

```js
const example = {};
Object.hasOwn(example, "prop"); // false - 'prop' has not been defined

example.prop = "exists";
Object.hasOwn(example, "prop"); // true - 'prop' has been defined

example.prop = null;
Object.hasOwn(example, "prop"); // true - own property exists with value of null

example.prop = undefined;
Object.hasOwn(example, "prop"); // true - own property exists with value of undefined
```

#### Direct vs. inherited properties

The following example differentiates between direct properties and properties inherited through the prototype chain:

```js
const example = {};
example.prop = "exists";

// `hasOwn` will only return true for direct properties:
Object.hasOwn(example, "prop"); // true
Object.hasOwn(example, "toString"); // false
Object.hasOwn(example, "hasOwnProperty"); // false

// The `in` operator will return true for direct or inherited properties:
"prop" in example; // true
"toString" in example; // true
"hasOwnProperty" in example; // true
```

#### Iterating over the properties of an object

To iterate over the enumerable properties of an object, you should use:

```js
const example = { foo: true, bar: true };
for (const name of Object.keys(example)) {
  // …
}
```

But if you need to use `for...in`, you can use `Object.hasOwn()` to skip the inherited properties:

```js
const example = { foo: true, bar: true };
for (const name in example) {
  if (Object.hasOwn(example, name)) {
    // …
  }
}
```

#### Checking if an Array index exists

The elements of an Array are defined as direct properties, so you can use `hasOwn()` method to check whether a particular index exists:

```js
const fruits = ["Apple", "Banana", "Watermelon", "Orange"];
Object.hasOwn(fruits, 3); // true ('Orange')
Object.hasOwn(fruits, 4); // false - not defined
```

#### Problematic cases for hasOwnProperty

This section demonstrates that `hasOwn()` is immune to the problems that affect
hasOwnProperty. Firstly, it can be used with objects that have reimplemented `hasOwnProperty()`:

```js
const foo = {
  hasOwnProperty() {
    return false;
  },
  bar: "The dragons be out of office",
};

if (Object.hasOwn(foo, "bar")) {
  console.log(foo.bar); // true - re-implementation of hasOwnProperty() does not affect Object
}
```

It can also be used to test objects created using `Object.create(null)`.
These do not inherit from `Object.prototype`, and so `hasOwnProperty()` is inaccessible.

```js
const foo = Object.create(null);
foo.prop = "exists";
if (Object.hasOwn(foo, "prop")) {
  console.log(foo.prop); // true - works irrespective of how the object is created.
}
```

#### Parameters

- **Object.hasOwn**(`obj`, `prop`)

`obj`

The JavaScript object instance to test.

`prop`

The String name or Symbol of the property to test.

#### Return value

true if the specified object has directly defined the specified property. Otherwise false

> #### -> see more about `hasOwn()`: [here](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Object/hasOwn)
>
> #### 👆🏽 go up to [Object-Methods #returns a boolean](#returns-a-boolean-2)

- ### is()

The `Object.is()` static method determines whether two values are the same value.

```js
console.log(Object.is("1", 1));
// Expected output: false

console.log(Object.is(NaN, NaN));
// Expected output: true

console.log(Object.is(-0, 0));
// Expected output: false

const obj = {};
console.log(Object.is(obj, {}));
// Expected output: false
```

`Object.is()` determines whether two values are the same value. Two values are the same if one of the following holds:

- both `undefined`
- both `null`
- both `true` or both `false`
- both strings of the same `length` with the same characters in the same order
- both the same object (meaning both values reference the same object in memory)
- both `BigInts` with the same numeric value
- both symbols that reference the same symbol value
- both numbers and
  - both `+0`
  - both `-0`
  - both `NaN`
  - or both non-zero, not `NaN`, and have the same value

`Object.is()` is not equivalent to the `==` operator. The `==` operator applies various coercions to both sides (if they are not the same type) before testing for equality (resulting in such behavior as `"" == false` being `true`), but `Object.is()` doesn't coerce either value.

`Object.is()` is also not equivalent to the `===` operator. The only difference between `Object.is()` and `===` is in their treatment of signed zeros and NaN values. The `===` operator (and the `==` operator) treats the number values `-0` and `+0` as equal, but treats `NaN` as not equal to each other.

```js
// Case 1: Evaluation result is the same as using ===
Object.is(25, 25); // true
Object.is("foo", "foo"); // true
Object.is("foo", "bar"); // false
Object.is(null, null); // true
Object.is(undefined, undefined); // true
Object.is(window, window); // true
Object.is([], []); // false
const foo = { a: 1 };
const bar = { a: 1 };
const sameFoo = foo;
Object.is(foo, foo); // true
Object.is(foo, bar); // false
Object.is(foo, sameFoo); // true

// Case 2: Signed zero
Object.is(0, -0); // false
Object.is(+0, -0); // false
Object.is(-0, -0); // true

// Case 3: NaN
Object.is(NaN, 0 / 0); // true
Object.is(NaN, Number.NaN); // true
```

#### Parameters

- **Object.is**(`value1`, `value2`)

`value1`

The first value to compare.

`value2`

The second value to compare.

#### Return value

A boolean indicating whether or not the two arguments are the same value.

> #### -> see more about `is()`: [here](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Object/is)
>
> #### 👆🏽 go up to [Object-Methods #returns a boolean](#returns-a-boolean-2)

- ### isFrozen()

The `Object.isFrozen()` static method determines if an object is `frozen`.

```js
const object1 = {
  property1: 42,
};

console.log(Object.isFrozen(object1));
// Expected output: false

Object.freeze(object1);

console.log(Object.isFrozen(object1));
// Expected output: true
```

An object is frozen if and only if it is not extensible, all its properties
are non-configurable, and all its data properties (that is, properties which are
not accessor properties with getter or setter components) are non-writable.

```js
// A new object is extensible, so it is not frozen.
Object.isFrozen({}); // false

// An empty object which is not extensible
// is vacuously frozen.
const vacuouslyFrozen = Object.preventExtensions({});
Object.isFrozen(vacuouslyFrozen); // true

// A new object with one property is also extensible,
// ergo not frozen.
const oneProp = { p: 42 };
Object.isFrozen(oneProp); // false

// Preventing extensions to the object still doesn't
// make it frozen, because the property is still
// configurable (and writable).
Object.preventExtensions(oneProp);
Object.isFrozen(oneProp); // false

// Deleting that property makes the object vacuously frozen.
delete oneProp.p;
Object.isFrozen(oneProp); // true

// A non-extensible object with a non-writable
// but still configurable property is not frozen.
const nonWritable = { e: "plep" };
Object.preventExtensions(nonWritable);
Object.defineProperty(nonWritable, "e", {
  writable: false,
}); // make non-writable
Object.isFrozen(nonWritable); // false

// Changing that property to non-configurable
// then makes the object frozen.
Object.defineProperty(nonWritable, "e", {
  configurable: false,
}); // make non-configurable
Object.isFrozen(nonWritable); // true

// A non-extensible object with a non-configurable
// but still writable property also isn't frozen.
const nonConfigurable = { release: "the kraken!" };
Object.preventExtensions(nonConfigurable);
Object.defineProperty(nonConfigurable, "release", {
  configurable: false,
});
Object.isFrozen(nonConfigurable); // false

// Changing that property to non-writable
// then makes the object frozen.
Object.defineProperty(nonConfigurable, "release", {
  writable: false,
});
Object.isFrozen(nonConfigurable); // true

// A non-extensible object with a configurable
// accessor property isn't frozen.
const accessor = {
  get food() {
    return "yum";
  },
};
Object.preventExtensions(accessor);
Object.isFrozen(accessor); // false

// When we make that property non-configurable it becomes frozen.
Object.defineProperty(accessor, "food", {
  configurable: false,
});
Object.isFrozen(accessor); // true

// But the easiest way for an object to be frozen
// is if Object.freeze has been called on it.
const frozen = { 1: 81 };
Object.isFrozen(frozen); // false
Object.freeze(frozen);
Object.isFrozen(frozen); // true

// By definition, a frozen object is non-extensible.
Object.isExtensible(frozen); // false

// Also by definition, a frozen object is sealed.
Object.isSealed(frozen); // true
```

#### Non-object argument

In ES5, if the argument to this method is not an object (a primitive),
then it will cause a TypeError. In ES2015, it will return true without any
errors if a non-object argument is passed, since primitives are, by definition, immutable.

```js
Object.isFrozen(1);
// TypeError: 1 is not an object (ES5 code)

Object.isFrozen(1);
// true                          (ES2015 code)
```

#### Parameters

- **Object.isFrozen**(`obj`)

`obj`

The object which should be checked.

#### Return value

A Boolean indicating whether or not the given object is frozen.

> #### -> see more about `isFrozen()`: [here](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Object/isFrozen)
>
> #### 👆🏽 go up to [Object-Methods #returns a boolean](#returns-a-boolean-2)

- ### isPrototypeOf()

The `isPrototypeOf()` method of Object instances checks if this object
exists in another object's prototype chain.

```js
function Foo() {}
function Bar() {}

Bar.prototype = Object.create(Foo.prototype);

const bar = new Bar();

console.log(Foo.prototype.isPrototypeOf(bar));
// Expected output: true
console.log(Bar.prototype.isPrototypeOf(bar));
// Expected output: true
```

All objects that inherit from Object.prototype (that is, all except
null-prototype objects) inherit the `isPrototypeOf()` method. This method
allows you to check whether or not the object exists within another object's
prototype chain. If the object passed as the parameter is not an object
(i.e. a primitive), the method directly returns false. Otherwise, the this
value is converted to an object, and the prototype chain of object is searched
for the this value, until the end of the chain is reached or the this value is found.

#### Using isPrototypeOf()

This example demonstrates that `Baz.prototype`, `Bar.prototype`,
`Foo.prototype` and `Object.prototype` exist in the prototype chain for object `baz`:

```js
class Foo {}
class Bar extends Foo {}
class Baz extends Bar {}

const foo = new Foo();
const bar = new Bar();
const baz = new Baz();

// prototype chains:
// foo: Foo --> Object
// bar: Bar --> Foo --> Object
// baz: Baz --> Bar --> Foo --> Object
console.log(Baz.prototype.isPrototypeOf(baz)); // true
console.log(Baz.prototype.isPrototypeOf(bar)); // false
console.log(Baz.prototype.isPrototypeOf(foo)); // false
console.log(Bar.prototype.isPrototypeOf(baz)); // true
console.log(Bar.prototype.isPrototypeOf(foo)); // false
console.log(Foo.prototype.isPrototypeOf(baz)); // true
console.log(Foo.prototype.isPrototypeOf(bar)); // true
console.log(Object.prototype.isPrototypeOf(baz)); // true
```

The `isPrototypeOf()` method — along with the instanceof operator — comes
in particularly handy if you have code that can only function when dealing
with objects descended from a specific prototype chain; e.g., to guarantee
that certain methods or properties will be present on that object.

For example, to execute some code that's only safe to run if a `baz` object has
`Foo.prototype` in its prototype chain, you can do this:

```js
if (Foo.prototype.isPrototypeOf(baz)) {
  // do something safe
}
```

However, `Foo.prototype` existing in baz's prototype chain doesn't imply baz
was created using `Foo` as its constructor. For example, `baz` could be directly
assigned with `Foo.prototype` as its prototype. In this case, if your code reads
private fields of `Foo` from `baz`, it would still fail:

```js
class Foo {
  #value = "foo";
  static getValue(x) {
    return x.#value;
  }
}

const baz = { __proto__: Foo.prototype };

if (Foo.prototype.isPrototypeOf(baz)) {
  console.log(Foo.getValue(baz)); // TypeError: Cannot read private member #value from an object whose class did not declare it
}
```

The same applies to instanceof. If you need to read private fields in
a secure way, offer a branded check method using in instead.

```js
class Foo {
  #value = "foo";
  static getValue(x) {
    return x.#value;
  }
  static isFoo(x) {
    return #value in x;
  }
}

const baz = { __proto__: Foo.prototype };

if (Foo.isFoo(baz)) {
  // Doesn't run, because baz is not a Foo
  console.log(Foo.getValue(baz));
}
```

#### Parameters

- **isPrototypeOf**(`object`)

`object`

The `object` whose prototype chain will be searched.

#### Return value

A boolean indicating whether the calling object (this) lies in the prototype
chain of object. Directly returns false when object is not an object (i.e. a primitive).

> #### -> see more about `isPrototypeOf()`: [here](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Object/isPrototypeOf)
>
> #### 👆🏽 go up to [Object-Methods #returns a boolean](#returns-a-boolean-2)

- ### isSealed()

The `Object.isSealed()` static method determines if an object is sealed.

```js
const object1 = {
  property1: 42,
};

console.log(Object.isSealed(object1));
// Expected output: false

Object.seal(object1);

console.log(Object.isSealed(object1));
// Expected output: true
```

Returns `true` if the object is sealed, otherwise `false`. An object is sealed
if it is not extensible and if all its properties are non-configurable and
therefore not removable (but not necessarily non-writable).

#### Using Object.isSealed

```js
// Objects aren't sealed by default.
const empty = {};
Object.isSealed(empty); // false

// If you make an empty object non-extensible,
// it is vacuously sealed.
Object.preventExtensions(empty);
Object.isSealed(empty); // true

// The same is not true of a non-empty object,
// unless its properties are all non-configurable.
const hasProp = { fee: "fie foe fum" };
Object.preventExtensions(hasProp);
Object.isSealed(hasProp); // false

// But make them all non-configurable
// and the object becomes sealed.
Object.defineProperty(hasProp, "fee", {
  configurable: false,
});
Object.isSealed(hasProp); // true

// The easiest way to seal an object, of course,
// is Object.seal.
const sealed = {};
Object.seal(sealed);
Object.isSealed(sealed); // true

// A sealed object is, by definition, non-extensible.
Object.isExtensible(sealed); // false

// A sealed object might be frozen,
// but it doesn't have to be.
Object.isFrozen(sealed); // true
// (all properties also non-writable)

const s2 = Object.seal({ p: 3 });
Object.isFrozen(s2); // false
// ('p' is still writable)

const s3 = Object.seal({
  get p() {
    return 0;
  },
});
Object.isFrozen(s3); // true
// (only configurability matters for accessor properties)
```

#### Non-object argument

In ES5, if the argument to this method is not an object (a primitive),
then it will cause a TypeError. In ES2015, it will return true without any
errors if a non-object argument is passed, since primitives are, by definition, immutable.

```js
Object.isSealed(1);
// TypeError: 1 is not an object (ES5 code)

Object.isSealed(1);
// true                          (ES2015 code)
```

#### Parameters

- **Object.isSealed**(`obj`)

`obj`

The object which should be checked.

#### Return value

A Boolean indicating whether or not the given object is sealed.

> #### -> see more about `isSealed()`: [here](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Object/isSealed)
>
> #### 👆🏽 go up to [Object-Methods #returns a boolean](#returns-a-boolean-2)

- ### toString()

The toString() method of Object instances returns a string representing
this object. This method is meant to be overridden by derived objects for
custom type conversion logic.

```js
function Dog(name) {
  this.name = name;
}

const dog1 = new Dog("Gabby");

Dog.prototype.toString = function dogToString() {
  return `${this.name}`;
};

console.log(dog1.toString());
// Expected output: "Gabby"
```

JavaScript calls the `toString()` method to convert an object to a primitive value.
You rarely need to invoke the `toString()` method yourself; JavaScript automatically
invokes it when encountering an object where a primitive value is expected.

This method is called in priority by string conversion, but numeric conversion and
primitive conversion call `valueOf()` in priority. However, because the base `valueOf()`
method returns an object, the `toString()` method is usually called in the end,
unless the object overrides `valueOf()`. For example, `+[1]` returns `1`, because its
`toString()` method returns `"1"`, which is then converted to a number.

All objects that inherit from `Object.prototype` (that is, all except `null-prototype` objects)
inherit the `toString()` method. When you create a custom object, you can override
`toString()` to call a custom method, so that your custom object can be converted to a
string value. Alternatively, you can add a @@toPrimitive method, which allows even more
control over the conversion process, and will always be preferred over `valueOf()` or `toString()` for any type conversion.

To use the base `Object.prototype.toString()` with an object that has it overridden
(or to invoke it on null or undefined), you need to call `Function.prototype.call()`
or `Function.prototype.apply()` on it, passing the object you want to inspect as the first parameter (called `thisArg`).

```js
const arr = [1, 2, 3];

arr.toString(); // "1,2,3"
Object.prototype.toString.call(arr); // "[object Array]"
```

`Object.prototype.toString()` returns "[object Type]", where Type is the object type.
If the object has a `Symbol.toStringTag` property whose value is a string,
that value will be used as the Type. Many built-in objects, including Map and Symbol,
have a `Symbol.toStringTag`. Some objects predating ES6 do not have `Symbol.toStringTag`,
but have a special tag nonetheless. They include (the tag is the same as the type name given below):

- Array
- Function (anything whose typeof returns "function")
- Error
- Boolean
- Number
- String
- Date
- RegExp

The arguments object returns "[object `Arguments`]". Everything else, including user-defined
classes, unless with a custom `Symbol.toStringTag`, will return "[object `Object`]".

`Object.prototype.toString()` invoked on null and undefined returns [object `Null`]
and [object `Undefined`], respectively.

#### Overriding toString for custom objects

You can create a function to be called in place of the default `toString()` method.
The `toString()` function you create should return a string value. If it returns an
object and the method is called implicitly during type conversion, then its result
is ignored and the value of a related method, `valueOf()`, is used instead, or a
TypeError is thrown if none of these methods return a primitive.

The following code defines a Dog class.

```js
class Dog {
  constructor(name, breed, color, sex) {
    this.name = name;
    this.breed = breed;
    this.color = color;
    this.sex = sex;
  }
}
```

If you call the `toString()` method, either explicitly or implicitly, on an
instance of Dog, it returns the default value inherited from Object:

```js
const theDog = new Dog("Gabby", "Lab", "chocolate", "female");

theDog.toString(); // "[object Object]"
`${theDog}`; // "[object Object]"
```

The following code overrides the default `toString()` method. This method generates
a string containing the name, breed, color, and sex of the object.

```js
class Dog {
  constructor(name, breed, color, sex) {
    this.name = name;
    this.breed = breed;
    this.color = color;
    this.sex = sex;
  }
  toString() {
    return `Dog ${this.name} is a ${this.sex} ${this.color} ${this.breed}`;
  }
}
```

With the preceding code in place, any time an instance of Dog is used in
a string context, JavaScript automatically calls the `toString()` method.

```js
const theDog = new Dog("Gabby", "Lab", "chocolate", "female");

`${theDog}`; // "Dog Gabby is a female chocolate Lab"
```

#### Using toString() to detect object class

`toString()` can be used with every object and (by default) allows you to get its class.

```js
const toString = Object.prototype.toString;

toString.call(new Date()); // [object Date]
toString.call(new String()); // [object String]
// Math has its Symbol.toStringTag
toString.call(Math); // [object Math]

toString.call(undefined); // [object Undefined]
toString.call(null); // [object Null]
```

Using `toString()` in this way is unreliable; objects can change the behavior of
`Object.prototype.toString()` by defining a Symbol.toStringTag property,
leading to unexpected results. For example:

```js
const myDate = new Date();
Object.prototype.toString.call(myDate); // [object Date]

myDate[Symbol.toStringTag] = "myDate";
Object.prototype.toString.call(myDate); // [object myDate]

Date.prototype[Symbol.toStringTag] = "prototype polluted";
Object.prototype.toString.call(new Date()); // [object prototype polluted]
```

#### Parameters

By default `toString()` takes no parameters. However, objects that inherit
from Object may override it with their own implementations that do take
parameters. For example, the `Number.prototype.toString()` and
`BigInt.prototype.toString()` methods take an optional radix parameter.

#### Return value

A string representing the object.

> #### -> see more about `toString()`: [here](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Object/toString)
>
> #### 👆🏽 go up to [Object-Methods #returns a string object](#returns-a-string-object)

- ### entries()

The `Object.entries()` static method returns an array of a given object's
own enumerable string-keyed property key-value pairs.

```js
const object1 = {
  a: "somestring",
  b: 42,
};

for (const [key, value] of Object.entries(object1)) {
  console.log(`${key}: ${value}`);
}

// Expected output:
// "a: somestring"
// "b: 42"
```

`Object.entries()` returns an array whose elements are arrays corresponding
to the enumerable string-keyed property key-value pairs found directly upon object.
This is the same as iterating with a `for...in` loop, except that a `for...in` loop enumerates
properties in the prototype chain as well. The order of the array returned by
`Object.entries()` is the same as that provided by a `for...in` loop.

If you only need the property keys, use `Object.keys()` instead. If you only need
the property values, use `Object.values()` instead.

#### Using Object.entries()

```js
const obj = { foo: "bar", baz: 42 };
console.log(Object.entries(obj)); // [ ['foo', 'bar'], ['baz', 42] ]

// Array-like object
const obj = { 0: "a", 1: "b", 2: "c" };
console.log(Object.entries(obj)); // [ ['0', 'a'], ['1', 'b'], ['2', 'c'] ]

// Array-like object with random key ordering
const anObj = { 100: "a", 2: "b", 7: "c" };
console.log(Object.entries(anObj)); // [ ['2', 'b'], ['7', 'c'], ['100', 'a'] ]

// getFoo is a non-enumerable property
const myObj = Object.create(
  {},
  {
    getFoo: {
      value() {
        return this.foo;
      },
    },
  }
);
myObj.foo = "bar";
console.log(Object.entries(myObj)); // [ ['foo', 'bar'] ]
```

#### Using Object.entries() on primitives

Non-object arguments are coerced to objects. Only strings may have own
enumerable properties, while all other primitives return an empty array.

```js
// Strings have indices as enumerable own properties
console.log(Object.entries("foo")); // [ ['0', 'f'], ['1', 'o'], ['2', 'o'] ]

// Other primitives have no own properties
console.log(Object.entries(100)); // []
```

Converting an Object to a Map

The `Map()` constructor accepts an iterable of entries. With Object.entries,
you can easily convert from Object to Map:

```js
const obj = { foo: "bar", baz: 42 };
const map = new Map(Object.entries(obj));
console.log(map); // Map(2) {"foo" => "bar", "baz" => 42}
```

#### Iterating through an Object

Using array destructuring, you can iterate through objects easily.

```js
// Using for...of loop
const obj = { a: 5, b: 7, c: 9 };
for (const [key, value] of Object.entries(obj)) {
  console.log(`${key} ${value}`); // "a 5", "b 7", "c 9"
}

// Using array methods
Object.entries(obj).forEach(([key, value]) => {
  console.log(`${key} ${value}`); // "a 5", "b 7", "c 9"
});
```

#### Parameters

- **Object.entries**(`obj`)

`obj`

An object.

#### Return value

An array of the given object's own enumerable string-keyed property key-value pairs.
Each key-value pair is an array with two elements: the first element is the property
key (which is always a string), and the second element is the property value.

> #### -> see more about `entries()`: [here](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Object/entries)
>
> #### 👆🏽 go up to [Object-Methods #returns an array](#returns-an-array-2)

- ### keys()

The `Object.keys()` static method returns an array of a given object's
own enumerable string-keyed property names.

```js
const object1 = {
  a: "somestring",
  b: 42,
  c: false,
};

console.log(Object.keys(object1));
// Expected output: Array ["a", "b", "c"]
```

`Object.keys()` returns an array whose elements are strings corresponding to the
enumerable string-keyed property names found directly upon object. This is the
same as iterating with a `for...in` loop, except that a `for...in` loop enumerates
properties in the prototype chain as well. The order of the array returned by
`Object.keys()` is the same as that provided by a `for...in` loop.

If you need the property values, use `Object.values()` instead. If you need both
the property keys and values, use `Object.entries()` instead.

#### Using Object.keys()

```js
// Simple array
const arr = ["a", "b", "c"];
console.log(Object.keys(arr)); // ['0', '1', '2']

// Array-like object
const obj = { 0: "a", 1: "b", 2: "c" };
console.log(Object.keys(obj)); // ['0', '1', '2']

// Array-like object with random key ordering
const anObj = { 100: "a", 2: "b", 7: "c" };
console.log(Object.keys(anObj)); // ['2', '7', '100']

// getFoo is a non-enumerable property
const myObj = Object.create(
  {},
  {
    getFoo: {
      value() {
        return this.foo;
      },
    },
  }
);
myObj.foo = 1;
console.log(Object.keys(myObj)); // ['foo']
```

If you want all string-keyed own properties, including non-enumerable ones,
see `Object.getOwnPropertyNames()`.

#### Using Object.keys() on primitives

Non-object arguments are coerced to objects. Only strings may have own
enumerable properties, while all other primitives return an empty array.

```js
// Strings have indices as enumerable own properties
console.log(Object.keys("foo")); // ['0', '1', '2']

// Other primitives have no own properties
console.log(Object.keys(100)); // []
```

#### Parameters

- **Object.keys**(`obj`)

`obj`

An object.

#### Return value

An array of strings representing the given object's own enumerable string-keyed property keys.

> #### -> see more about `keys()`: [here](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Object/keys)
>
> #### 👆🏽 go up to [Object-Methods #returns an array](#returns-an-array-2)

- ### values()

The `Object.values()` static method returns an array of a given
object's own enumerable string-keyed property values.

```js
const object1 = {
  a: "somestring",
  b: 42,
  c: false,
};

console.log(Object.values(object1));
// Expected output: Array ["somestring", 42, false]
```

`Object.values()` returns an array whose elements are values of
enumerable string-keyed properties found directly upon object.
This is the same as iterating with a `for...in` loop, except that a
`for...in` loop enumerates properties in the prototype chain as well.
The order of the array returned by `Object.values()` is the same as
that provided by a `for...in` loop.

If you need the property keys, use `Object.keys()` instead. If you
need both the property keys and values, use `Object.entries()` instead.

#### Using Object.values()

```js
const obj = { foo: "bar", baz: 42 };
console.log(Object.values(obj)); // ['bar', 42]

// Array-like object
const arrayLikeObj1 = { 0: "a", 1: "b", 2: "c" };
console.log(Object.values(arrayLikeObj1)); // ['a', 'b', 'c']

// Array-like object with random key ordering
// When using numeric keys, the values are returned in the keys' numerical order
const arrayLikeObj2 = { 100: "a", 2: "b", 7: "c" };
console.log(Object.values(arrayLikeObj2)); // ['b', 'c', 'a']

// getFoo is a non-enumerable property
const myObj = Object.create(
  {},
  {
    getFoo: {
      value() {
        return this.foo;
      },
    },
  }
);
myObj.foo = "bar";
console.log(Object.values(myObj)); // ['bar']
```

#### Using Object.values() on primitives

Non-object arguments are coerced to objects. Only strings may have own
enumerable properties, while all other primitives return an empty array.

```js
// Strings have indices as enumerable own properties
console.log(Object.values("foo")); // ['f', 'o', 'o']

// Other primitives have no own properties
console.log(Object.values(100)); // []
```

#### Parameters

- **Object.values**(`obj`)

`obj`

An object.

#### Return value

An array containing the given object's own enumerable string-keyed property values.

> #### -> see more about `values()`: [here](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Object/values)
>
> #### 👆🏽 go up to [Object-Methods #returns an array](#returns-an-array-2)

- ### assign()

The `Object.assign()` static method copies all enumerable own properties from one or
more source objects to a target object. It returns the modified target object.

```js
const target = { a: 1, b: 2 };
const source = { b: 4, c: 5 };
const returnedTarget = Object.assign(target, source);

console.log(target);
// Expected output: Object { a: 1, b: 4, c: 5 }

console.log(returnedTarget === target);
// Expected output: true
```

Properties in the target object are overwritten by properties in the sources if
they have the same key. Later sources' properties overwrite earlier ones.

The `Object.assign()` method only copies enumerable and own properties from a source
object to a target object. It uses `[[Get]]` on the source and `[[Set]]` on the target,
so it will invoke getters and setters. Therefore it assigns properties, versus
copying or defining new properties. This may make it unsuitable for merging new
properties into a prototype if the merge sources contain getters.

For copying property definitions (including their enumerability) into prototypes,
use `Object.getOwnPropertyDescriptor()` and `Object.defineProperty()` instead.

Both `String` and `Symbol` properties are copied.

In case of an error, for example if a property is non-writable, a TypeError is raised,
and the target object is changed if any properties are added before the error is raised.

#### Cloning an object

```js
const obj = { a: 1 };
const copy = Object.assign({}, obj);
console.log(copy); // { a: 1 }
```

#### Warning for Deep Clone

For deep cloning, we need to use alternatives like `structuredClone()`,
because `Object.assign()` copies property values.

If the source value is a reference to an object, it only copies the reference value.

```js
const obj1 = { a: 0, b: { c: 0 } };
const obj2 = Object.assign({}, obj1);
console.log(obj2); // { a: 0, b: { c: 0 } }

obj1.a = 1;
console.log(obj1); // { a: 1, b: { c: 0 } }
console.log(obj2); // { a: 0, b: { c: 0 } }

obj2.a = 2;
console.log(obj1); // { a: 1, b: { c: 0 } }
console.log(obj2); // { a: 2, b: { c: 0 } }

obj2.b.c = 3;
console.log(obj1); // { a: 1, b: { c: 3 } }
console.log(obj2); // { a: 2, b: { c: 3 } }

// Deep Clone
const obj3 = { a: 0, b: { c: 0 } };
const obj4 = structuredClone(obj3);
obj3.a = 4;
obj3.b.c = 4;
console.log(obj4); // { a: 0, b: { c: 0 } }
```

#### Merging objects

```js
const o1 = { a: 1 };
const o2 = { b: 2 };
const o3 = { c: 3 };

const obj = Object.assign(o1, o2, o3);
console.log(obj); // { a: 1, b: 2, c: 3 }
console.log(o1); // { a: 1, b: 2, c: 3 }, target object itself is changed.
```

#### Merging objects with same properties

The properties are overwritten by other objects that have the same properties later in the parameters order.

```js
const o1 = { a: 1, b: 1, c: 1 };
const o2 = { b: 2, c: 2 };
const o3 = { c: 3 };

const obj = Object.assign({}, o1, o2, o3);
console.log(obj); // { a: 1, b: 2, c: 3 }
```

#### Parameters

- **Object.assign**(`target`, `...sources`)

`target`

The `target` object — what to apply the `sources`' properties to, which is returned after it is modified.

`sources`

The source object(s) — objects containing the properties you want to apply.

#### Return value

The target object.

> #### -> see more about `assign()`: [here](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Object/assign)
>
> #### 👆🏽 go up to [Object-Methods #returns an object](#returns-an-object-1)

- ### create()

The `Object.create()` static method creates a new object, using an existing
object as the prototype of the newly created object.

```js
const person = {
  isHuman: false,
  printIntroduction: function () {
    console.log(`My name is ${this.name}. Am I human? ${this.isHuman}`);
  },
};

const me = Object.create(person);

me.name = "Matthew"; // "name" is a property set on "me", but not on "person"
me.isHuman = true; // Inherited properties can be overwritten

me.printIntroduction();
// Expected output: "My name is Matthew. Am I human? true"
```

#### Classical inheritance with Object.create()

Below is an example of how to use `Object.create()` to achieve classical inheritance.
This is for a single inheritance, which is all that JavaScript supports.

```js
// Shape - superclass
function Shape() {
  this.x = 0;
  this.y = 0;
}

// superclass method
Shape.prototype.move = function (x, y) {
  this.x += x;
  this.y += y;
  console.info("Shape moved.");
};

// Rectangle - subclass
function Rectangle() {
  Shape.call(this); // call super constructor.
}

// subclass extends superclass
Rectangle.prototype = Object.create(Shape.prototype, {
  // If you don't set Rectangle.prototype.constructor to Rectangle,
  // it will take the prototype.constructor of Shape (parent).
  // To avoid that, we set the prototype.constructor to Rectangle (child).
  constructor: {
    value: Rectangle,
    enumerable: false,
    writable: true,
    configurable: true,
  },
});

const rect = new Rectangle();

console.log("Is rect an instance of Rectangle?", rect instanceof Rectangle); // true
console.log("Is rect an instance of Shape?", rect instanceof Shape); // true
rect.move(1, 1); // Logs 'Shape moved.'
```

Note that there are caveats to watch out for using `create()`, such as re-adding
the constructor property to ensure proper semantics. Although `Object.create()` is
believed to have better performance than mutating the prototype with `Object.setPrototypeOf()`,
the difference is in fact negligible if no instances have been created and property
accesses haven't been optimized yet. In modern code, the class syntax should be preferred in any case.

#### Using propertiesObject argument with Object.create()

`Object.create()` allows fine-tuned control over the object creation process.
The object initializer syntax is, in fact, a syntax sugar of `Object.create()`.
With `Object.create()`, we can create objects with a designated prototype and
also some properties. Note that the second parameter maps keys to property
descriptors — this means you can control each property's enumerability,
configurability, etc. as well, which you can't do in object initializers.

```js
o = {};
// Is equivalent to:
o = Object.create(Object.prototype);

o = Object.create(Object.prototype, {
  // foo is a regular data property
  foo: {
    writable: true,
    configurable: true,
    value: "hello",
  },
  // bar is an accessor property
  bar: {
    configurable: false,
    get() {
      return 10;
    },
    set(value) {
      console.log("Setting `o.bar` to", value);
    },
  },
});

// Create a new object whose prototype is a new, empty
// object and add a single property 'p', with value 42.
o = Object.create({}, { p: { value: 42 } });
```

With `Object.create()`, we can create an object with `null` as prototype.
The equivalent syntax in object initializers would be the **proto** key.

```js
o = Object.create(null);
// Is equivalent to:
o = { __proto__: null };
```

By default properties are not writable, enumerable or configurable.

```js
o.p = 24; // throws in strict mode
o.p; // 42

o.q = 12;
for (const prop in o) {
  console.log(prop);
}
// 'q'

delete o.p;
// false; throws in strict mode
```

To specify a property with the same attributes as in an initializer,
explicitly specify writable, enumerable and configurable.

```js
o2 = Object.create(
  {},
  {
    p: {
      value: 42,
      writable: true,
      enumerable: true,
      configurable: true,
    },
  }
);
// This is not equivalent to:
// o2 = Object.create({ p: 42 })
// which will create an object with prototype { p: 42 }
```

You can use `Object.create()` to mimic the behavior of the new operator.

```js
function Constructor() {}
o = new Constructor();
// Is equivalent to:
o = Object.create(Constructor.prototype);
```

Of course, if there is actual initialization code in the Constructor function,
the `Object.create()` method cannot reflect it.

#### Parameters

`proto`

The object which should be the prototype of the newly-created object.

`propertiesObject` Optional

If specified and not undefined, an object whose enumerable own properties specify property descriptors to be added to the newly-created object, with the corresponding property names. These properties correspond to the second argument of `Object.defineProperties()`.

#### Return value

A new object with the specified prototype object and properties.

#### Exceptions

`TypeError`

Thrown if `proto` is neither `null` nor an Object.

> #### -> see more about `create()`: [here](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Object/create)
>
> #### 👆🏽 go up to [Object-Methods #returns an object](#returns-an-object-1)

- ### fromEntries()

The `Object.fromEntries()` static method transforms a list of key-value pairs into an object.

```js
const entries = new Map([
  ["foo", "bar"],
  ["baz", 42],
]);

const obj = Object.fromEntries(entries);

console.log(obj);
// Expected output: Object { foo: "bar", baz: 42 }
```

The `Object.fromEntries()` method takes a list of key-value pairs and returns a new
object whose properties are given by those entries. The iterable argument is expected
to be an object that implements an @@iterator method. The method returns an iterator
object that produces two-element array-like objects. The first element is a value that
will be used as a property key, and the second element is the value to associate with that property key.

`Object.fromEntries()` performs the reverse of `Object.entries()`, except that `Object.entries()`
only returns string-keyed properties, while `Object.fromEntries()` can also create symbol-keyed properties.

#### Converting a Map to an Object

With `Object.fromEntries()`,you can convert from Map to Object:

```js
const map = new Map([
  ["foo", "bar"],
  ["baz", 42],
]);
const obj = Object.fromEntries(map);
console.log(obj); // { foo: "bar", baz: 42 }
```

#### Converting an Array to an Object

With `Object.fromEntries()`, you can convert from Array to Object:

```js
const arr = [
  ["0", "a"],
  ["1", "b"],
  ["2", "c"],
];
const obj = Object.fromEntries(arr);
console.log(obj); // { 0: "a", 1: "b", 2: "c" }
```

#### Object transformations

With `Object.fromEntries()`, its reverse method `Object.entries()`,
and array manipulation methods, you are able to transform objects like this:

```js
const object1 = { a: 1, b: 2, c: 3 };

const object2 = Object.fromEntries(
  Object.entries(object1).map(([key, val]) => [key, val * 2])
);

console.log(object2);
// { a: 2, b: 4, c: 6 }
```

#### Parameters

- **Object.fromEntries**(`iterable`)

`iterable`

An `iterable`, such as an `Array` or `Map`, containing a list of objects. Each object should have two properties:

`0`

A `string` or `symbol` representing the property key.

`1`

The property value.

Typically, this object is implemented as a two-element array, with the first
element being the property key and the second element being the property value.

#### Return value

A new object whose properties are given by the entries of the `iterable`.

> #### -> see more about `fromEntries()`: [here](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Object/fromEntries)
>
> #### 👆🏽 go up to [Object-Methods #returns an object](#returns-an-object-1)

- ### seal()

The `Object.seal()` static method seals an object. Sealing an object prevents
extensions and makes existing properties non-configurable. A sealed object has
a fixed set of properties: new properties cannot be added, existing properties
cannot be removed, their enumerability and configurability cannot be changed,
and its prototype cannot be re-assigned. Values of existing properties can still
be changed as long as they are writable. `seal()` returns the same object that was passed in.

```js
const object1 = {
  property1: 42,
};

Object.seal(object1);
object1.property1 = 33;
console.log(object1.property1);
// Expected output: 33

delete object1.property1; // Cannot delete when sealed
console.log(object1.property1);
// Expected output: 33
```

Sealing an object is equivalent to preventing extensions and then changing
all existing properties' descriptors to configurable: false. This has the effect
of making the set of properties on the object fixed. Making all properties
non-configurable also prevents them from being converted from data properties to
accessor properties and vice versa, but it does not prevent the values of data
properties from being changed. Attempting to delete or add properties to a sealed object,
or to convert a data property to accessor or vice versa, will fail, either silently or
by throwing a TypeError (most commonly, although not exclusively, when in strict mode code).

The prototype chain remains untouched. However, due to the effect of preventing
extensions, the `[[Prototype]]` cannot be reassigned.

Unlike `Object.freeze()`, objects sealed with `Object.seal()` may have their existing
properties changed, as long as they are writable.

#### Using Object.seal

```js
const obj = {
  prop() {},
  foo: "bar",
};

// New properties may be added, existing properties
// may be changed or removed.
obj.foo = "baz";
obj.lumpy = "woof";
delete obj.prop;

const o = Object.seal(obj);

o === obj; // true
Object.isSealed(obj); // true

// Changing property values on a sealed object
// still works.
obj.foo = "quux";

// But you can't convert data properties to accessors,
// or vice versa.
Object.defineProperty(obj, "foo", {
  get() {
    return "g";
  },
}); // throws a TypeError

// Now any changes, other than to property values,
// will fail.
obj.quaxxor = "the friendly duck";
// silently doesn't add the property
delete obj.foo;
// silently doesn't delete the property

// ...and in strict mode such attempts
// will throw TypeErrors.
function fail() {
  "use strict";
  delete obj.foo; // throws a TypeError
  obj.sparky = "arf"; // throws a TypeError
}
fail();

// Attempted additions through
// Object.defineProperty will also throw.
Object.defineProperty(obj, "ohai", {
  value: 17,
}); // throws a TypeError
Object.defineProperty(obj, "foo", {
  value: "eit",
}); // changes existing property value
```

#### Non-object argument

In ES5, if the argument to this method is not an object (a primitive),
then it will cause a TypeError. In ES2015, a non-object argument will be
returned as-is without any errors, since primitives are already, by definition, immutable.

```js
Object.seal(1);
// TypeError: 1 is not an object (ES5 code)

Object.seal(1);
// 1                             (ES2015 code)
```

#### Parameters

- **Object.seal**(`obj')

`obj'

The object which should be sealed.

#### Return value

The object being sealed.

> #### -> see more about `seal()`: [here](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Object/seal)
>
> #### 👆🏽 go up to [Object-Methods #returns an object](#returns-an-object-1)

- ### valueOf()

The `valueOf()` method of Object instances converts the this value to an object.
This method is meant to be overridden by derived objects for custom type conversion logic.

```js
function MyNumberType(n) {
  this.number = n;
}

MyNumberType.prototype.valueOf = function () {
  return this.number;
};

const object1 = new MyNumberType(4);

console.log(object1 + 3);
// Expected output: 7
```

JavaScript calls the `valueOf()` method to convert an object to a primitive value.
You rarely need to invoke the `valueOf()` method yourself; JavaScript automatically
invokes it when encountering an object where a primitive value is expected.

This method is called in priority by numeric conversion and primitive conversion,
but string conversion calls `toString()` in priority, and `toString()` is very likely
to return a string value (even for the `Object.prototype.toString()` base implementation),
so `valueOf()` is usually not called in this case.

All objects that inherit from Object.prototype (that is, all except null-prototype objects)
inherit the `toString()` method. The `Object.prototype.valueOf()` base implementation is
deliberately useless: by returning an object, its return value will never be used by any
primitive conversion algorithm. Many built-in objects override this method to return an
appropriate primitive value. When you create a custom object, you can override `valueOf()`
to call a custom method, so that your custom object can be converted to a primitive value.
Generally, `valueOf()` is used to return a value that is most meaningful for the object — unlike
`toString()`, it does not need to be a string. Alternatively, you can add a @@toPrimitive method,
which allows even more control over the conversion process, and will always be preferred
over `valueOf()` or `toString()` for any type conversion.

#### Using valueOf()

The base `valueOf()` method returns the this value itself, converted to an object if it isn't already.
Therefore its return value will never be used by any primitive conversion algorithm.

```js
const obj = { foo: 1 };
console.log(obj.valueOf() === obj); // true

console.log(Object.prototype.valueOf.call("primitive"));
// [String: 'primitive'] (a wrapper object)
```

#### Overriding valueOf for custom objects

You can create a function to be called in place of the default `valueOf()` method.
Your function should take no arguments, since it won't be passed any when called during type conversion.

For example, you can add a `valueOf()` method to your custom class Box.

```js
class Box {
  #value;
  constructor(value) {
    this.#value = value;
  }
  valueOf() {
    return this.#value;
  }
}
```

With the preceding code in place, any time an object of type Box is used in a context
where it is to be represented as a primitive value (but not specifically a string),
JavaScript automatically calls the function defined in the preceding code.

```js
const box = new Box(123);
console.log(box + 456); // 579
console.log(box == 123); // true
```

An object's `valueOf()` method is usually invoked by JavaScript, but you can invoke it yourself as follows:

```js
box.valueOf();
```

#### Return value

The `this` value, converted to an object.

**!** Note: In order for valueOf to be useful during type conversion,
it must return a primitive. Because all primitive types have their own `valueOf()` methods,
calling `aPrimitiveValue.valueOf()` generally does not invoke `Object.prototype.valueOf()`.

> #### -> see more about `valueOf()`: [here](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Object/valueOf)
>
> #### 👆🏽 go up to [Object-Methods #returns an object](#returns-an-object-1)
