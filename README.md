# sort-keys-recursive

![Last version](https://img.shields.io/github/tag/Kikobeats/sort-keys-recursive.svg?style=flat-square)
[![Build Status](https://img.shields.io/travis/Kikobeats/sort-keys-recursive/master.svg?style=flat-square)](https://travis-ci.org/Kikobeats/sort-keys-recursive)
[![Coverage Status](https://img.shields.io/coveralls/Kikobeats/sort-keys-recursive.svg?style=flat-square)](https://coveralls.io/github/Kikobeats/sort-keys-recursive)
[![Dependency status](https://img.shields.io/david/Kikobeats/sort-keys-recursive.svg?style=flat-square)](https://david-dm.org/Kikobeats/sort-keys-recursive)
[![Dev Dependencies Status](https://img.shields.io/david/dev/Kikobeats/sort-keys-recursive.svg?style=flat-square)](https://david-dm.org/Kikobeats/sort-keys-recursive#info=devDependencies)
[![NPM Status](https://img.shields.io/npm/dm/str-match.svg?style=flat-square)](https://www.npmjs.org/package/str-match)
[![Donate](https://img.shields.io/badge/donate-paypal-blue.svg?style=flat-square)](https://paypal.me/Kikobeats)

> Sort the keys of an object recursively.

## Install

```bash
npm install sort-keys-recursive --save
```

## Usage

```js
const sortKeysRecursive = require('sort-keys-recursive')

const object = {
  c: 0,
  a: {
    c: ['c', 'a', 'b'],
    a: 0,
    b: 0
  },
  b: 0
}

const output = sortKeysRecursive(object)

console.log(output)

// {
//   a: {
//     a: 0,
//     b: 0,
//     c: ['a', 'b', 'c']
//   },
//   b: 0,
//   c: 0
// };

```

## API

### sortKeysRecursive(input, [options])

#### input

*Required*<br>
Type: `array`|`object`

The collection to be sorted.

#### options

##### compareFunction

Type: `function`

[Compare function](https://github.com/sindresorhus/sort-keys#compare).

##### ignoreArrayAtKeys

Type: `array`

Don't sort the Array at the specified keys, if any.

##### ignoreObjectAtKeys

Type: `array`

Don't sort the Object at the specified keys, if any.

## Examples

### <code>ignoreArrayAtKeys</code> and <code>ignoreObjectAtKeys</code>

```js

const options = {
  ignoreArrayAtKeys: [ // Don't sort the Array at the specified keys, if any.
    'b'
  ],
  ignoreObjectAtKeys: [ // Don't sort the Object at the specified keys, if any.
    'a'
  ]
}

const input = {
  a: { // This Object will not be sorted.
    a: 'a',
    b: 'b',
    c: 'c',
    d: ['a', 'c', 'b']
  },
  b: ['a', 'c', 'b'], // This Array will not be sorted.
  d: ['a', 'c', 'b']
}

const output = sort(object, options)

console.log(output)

// {
//   a: {
//     a: 'a',
//     b: 'b',
//     c: 'c',
//     d: ['a', 'c', 'b']
//   },
//   b: ['a', 'c', 'b'],
//   d: ['a', 'b', 'c']
// }

```

### <code>compareFunction</code>

You can pass a custom sort function as <code>compareFunction</code>. This function is passed to Javascript <code>[sort()](https://developer.mozilla.org/en/docs/Web/JavaScript/Reference/Global_Objects/Array/sort)</code>, that sorts in alphabetical order by default (it sorts elements by converting them to strings and comparing strings in Unicode code point order). The custom function should return zero, a negative or positive value:

```js
var reverseAlphabeticalSort = function (a, b) {
  return a < b
}

var options = {
  compareFunction: reverseAlphabeticalSort
}

var object = {
  a: {
    a: 0,
    c: ['c', 'a', 'b'],
    b: 0
  },
  c: 0,
  b: 0
}

var output = sort(object, options)

console.log(output)

// {
//   c: 0,
//   b: 0,
//   a: {
//     c: ['c', 'b', 'a'],
//     b: 0,
//     a: 0
//   }
// }

```

## License

MIT © [Kiko Beats](http://www.kikobeats.com)
