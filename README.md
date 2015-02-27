# broccoli-pegjs

Forked from [broccoli-pegjs](https://github.com/ghempton/broccoli-pegjs).

A [PEG.js](http://pegjs.org/) filter for [Broccoli](http://broccolijs.com/) that
uses [pegjs-import](https://github.com/casetext/pegjs-import).

## Installation

```bash
npm install --save-dev broccoli-pegjs-import
```

## Usage

```js
var peg = require('pegjs-import');
var pegBuilder = require('broccoli-pegjs-import');
tree = pegBuilder(tree, {
  peg: peg
});
```

## Options

* `wrapper` - Wrap the generated parser in any code you want:

```
tree = pegBuilder(tree, {
  wrapper: function (src, parser) {
    return 'var Parser = ' + parser + ";\nvar parse = Parser.parse, SyntaxError = Parser.SyntaxError;\nexport {SyntaxError, parse};\nexport default parse;";
  }
});
```

* `peg` - Provide an alternative peg instance.

```
tree = pegBuilder(tree, {
  peg: require('pegjs-import')
});
```
