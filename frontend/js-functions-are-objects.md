# JavaScript Functions are Objects

Previously, I showed we can build [compound components in React](https://github.com/mattscripted/react-compound-components) by adding components onto a parent:

```js
const Menu = props => /* render component */;
const Item = props => /* render component */;

Menu.Item = Item;
```

At first, this feature seems like a weird quirk of React, since we often add `propTypes` and `defaultProps` to components:

```js
Menu.propTypes = {
  title: PropTypes.string,
  children: PropTypes.node.isRequired,
};

Menu.defaultProps = {
  title: '',
};
```

However, we can actually add properties to every JavaScript function:

```js
// With regular functions
function func() {
  return true;
}

console.log(func()); // true

func.foo = 'foo';
console.log(func.foo); // foo

// With arrow functions
const arrowFunc = () => true;
console.log(arrowFunc()); // true

arrowFunc.bar = 'bar';
console.log(arrowFunc.bar); // bar
```

_But, why does this work?_

Well, according to MDN, it turns out that [every function is an object](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Function):

> Every JavaScript function is actually a Function object. This can be seen with the code `(function(){}).constructor === Function`, which returns true.

In fact, we can even create functions using `new Function`:

```js
// Without arguments
const func = new Function('return true;');
console.log(func()); // true

// With one argument
const identity = new Function('value', 'return value;');
console.log(identity(42)); // 42

// With multiple arguments
const multiply = new Function('x', 'y', 'return x * y;');
console.log(multiply(2, 3)); // 6
```

And, we can still add properties to these functions:

```js
const func = new Function('return true;');
console.log(func()); // true

func.foo = 'foo';
func.bar = 'bar';

console.log(func.foo); // foo
console.log(func.bar); // bar
```


In JavaScript, we can add properties to functions, because functions are objects.

## Further Reading
- [MDN - Function Object](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Function)
- [MDN - Functions](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Functions)
