# Javascript Methods Overview

Which function returns which value?

## Boolean

- [ ] []()
- [ ] []()

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

## Number

- [ ] []()
- [ ] []()

## [Array-Methods](#array-methods-1)

### without retun value

- [ ] [forEach()](#foreach)

### returns a number

- [ ] [findeIndex()]()

### returns an array

- [ ] [filter()]()
- [ ] [map()](#map)

### returns the same modified array

- [ ] [sort()]()
- [ ] [fill()]()

### returns the first arrays element

- [ ] [find()]()

### returns a boolean

- [ ] [some()]()
- [ ] [every()]()
- [ ] [includes()]()
- [ ] []()

- [ ] []()
- [ ] []()

## Object

- [ ] []()
- [ ] []()

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
```

#### Parameters

- **includes**(`searchString`), **includes**(`searchString`, `position`)

`searchString`

A string to be searched for within `str`. Cannot be a regex. All values that are not regexes are coerced to strings, so omitting it or passing `undefined` causes `includes()` to search for the string "undefined", which is rarely what you want.

`position` Optional

The `position` within the string at which to begin searching for `searchString`. (Defaults to 0.)

#### Return value

`true` if the search string is found anywhere within the given string, including when `searchString` is an empty string; otherwise, `false`.

> #### -> see more about `includes()`: [here](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/String/includes)

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

> #### see more about split(): [here](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/String/split)

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

- ### map()

The `map()` method creates a new array populated with the results of calling
a provided function on every element in the calling array.

The `map()` method is an iterative method. It calls a provided callbackFn function once for each element in an array and constructs a new array from the results.
callbackFn is invoked only for array indexes which have assigned values. It is not invoked for empty slots in sparse arrays.
The `map()` method is a copying method. It does not alter this. However, the function provided as callbackFn can mutate the array. Note, however, that the length of the array is saved before the first invocation of callbackFn.

```js
const array1 = [1, 4, 9, 16];

// Pass a function to map
const map1 = array1.map((x) => x * 2);

console.log(map1);
// Expected output: Array [2, 8, 18, 32]
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
