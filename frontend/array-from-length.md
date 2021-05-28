# Use `Array.from()` to create an array of a given length

With `Array.from()`, we can [create an array of a given length](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/from#using_arrow_functions_and_array.from):

```js
// [undefined, undefined, undefined]
Array.from({ length: 3 });

// [undefined, undefined, undefined, undefined, undefined]
Array.from({ length: 5 });
```

We can even prefill an array with a mapper function:

```js
// [0, 1, 2, 3, 4]
Array.from({ length: 5 }, (element, index) => index);

// [0, 2, 4, 6, 8]
Array.from({ length: 5 }, (element, index) => 2 * index);

// [1, 3, 5, 7, 9]
Array.from({ length: 5 }, (element, index) => (2 * index) + 1);
```
