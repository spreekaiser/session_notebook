# Javascript Methods Overview

Which function returns which value?

## Boolean

- [ ] []()
- [ ] []()

## [String-Methods](#string-methods-1)

### returns a boolean

- [ ] [startsWith()](#startswith)
- [ ] [endsWith()]()
- [ ] [includes()]()

### returns a string

- [ ] [slice()](#slice)
- [ ] [replace()](#replace)
- [ ] [substring()]()
- [ ] [toUpperCase()]()
- [ ] [toLowerCase()]()
- [ ] [toString()]()
- [ ] [trim()]()
- [ ] [valueOf()]()

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

- ### slice()

The `slice()` method extracts a section of a string and returns it as a new string, without modifying the original string.

`slice()` extracts the text from one string and returns a new string. Changes to the text in one string do not affect the other string.

`slice()` extracts up to but not including indexEnd. For example, str.slice(1, 4) extracts the second character through
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

- ### split()

The split() method takes a pattern and divides a String into an ordered list of substrings by searching for the pattern, puts these substrings into an array, and returns the array.

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
