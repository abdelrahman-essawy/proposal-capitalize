# ECMAScript Proposal: `String.prototype.capitalize`

This is a proposal to add a new method to the `String.prototype` object in ECMAScript, `capitalize()`, that capitalizes the first letter of each word in a string.

## Status
This proposal is currently in Stage 0 of the TC39 Process.

## Motivation

The `capitalize()` function is a commonly used string manipulation function that capitalizes the first letter of each word in a string. While this functionality can be implemented using regular expressions or custom functions, it is a common enough use case that it warrants inclusion in the ECMAScript specification.

## Proposal

We propose adding a new method to the `String.prototype` object, `capitalize()`, that capitalizes the first letter of each word in a string. The method takes no arguments and returns a new string with the first letter of each word capitalized.

```javascript
String.prototype.capitalize = function(str) {
  // implementation details
  if (typeof str !== 'string') {
    throw new TypeError('Expected a string');
  }
  
  return str.replace(/(?:^|\s)\S/g, function(letter) {
    return letter.toUpperCase();
  });
};
```
The capitalize() method will be compatible with the existing String object and will work on any string value.

## Examples

```javascript
'hello world'.capitalize(); // 'Hello World'
'this is a test'.capitalize(); // 'This Is A Test'
'1234 one two three four'.capitalize(); // '1234 One Two Three Four'
'    extra spaces    '.capitalize(); // '    Extra Spaces    '
```

## Considerations
- This proposal introduces a new method to the String.prototype object, which may require implementation changes in browsers and other ECMAScript engines.
- The implementation should adhere to the ECMAScript specification and be compatible with existing language features.
- The `capitalize()` method should be thoroughly tested to ensure it works as intended and doesn't introduce any bugs.

## Alternatives
- Use a regular expression or custom function to implement the `capitalize()` functionality.
- Use an external library or utility function to provide the `capitalize()` functionality.

## Prior Art
The `capitalize()` function is a common string manipulation function that is available in many programming languages and libraries, including Python, Ruby, and Java. It is also available in popular JavaScript libraries and frameworks, such as lodash and React Native.

## References
- [lodash.capitalize](https://lodash.com/docs/4.17.15#capitalize)
- [React Native Text capitalize](https://reactnative.dev/docs/text#capitalize)
- [Python str.capitalize](https://docs.python.org/3/library/stdtypes.html#str.capitalize)
- [Ruby String#capitalize](https://ruby-doc.org/core-2.7.2/String.html#method-i-capitalize)
