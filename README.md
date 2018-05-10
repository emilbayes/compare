# `correct-compare`

![100-correct](https://img.shields.io/badge/Correct%20-100%25-brightgreen.svg?style=flat)

> Compare primitives the right way (using `<`, `>` and `==`)

This module does the right thing with numbers and ascii strings.
Normally `String.prototype.localeCompare` is recommended for strings,
but that can have nasty side effects on some machines, eg.

```js
'cu'.localeCompare('cs', 'hu')
```

Compare the above in stock node (which doesn't come with `Intl`) and
a browser of your choice (which most likely has `Intl` support).

## Usage

```js
var compare = require('correct-compare')
[1, 2, 10].sort() // [1, 10, 2]
[1, 2, 10].sort(compare) // [1, 2, 10]

// Below is sorted correctly according to Hungarian, but runtimes without Intl
// support will reorder them
['cu', 'cs'].sort((a, b) => a.localeCompare(b, 'hu'))
['cu', 'cs'].sort(compare) // This will always sort the same
```

## API

### `compare(a, b)`

Standard `Array.prototype.sort(cmp)` function signature. If `a > b` return `1`,
if `a < b` return `-1`, otherwise return `0`

## Install

```sh
npm install correct-compare
```

## License

[ISC](LICENSE)
