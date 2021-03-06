[![npm version](https://badge.fury.io/js/metalsmith-pandoc.svg)](https://badge.fury.io/js/metalsmith-pandoc) [![Build Status](https://travis-ci.org/arve0/metalsmith-pandoc.svg?branch=master)](https://travis-ci.org/arve0/metalsmith-pandoc)

# metalsmith-pandoc
Wrap around [pdc](https://github.com/pvorb/node-pdc), which lets you transform files with pandoc. For example from markdown to Word (docx). Pandoc needs to be [system installed](http://pandoc.org/installing.html).

## Install
```sh
npm install metalsmith-pandoc
```

## Usage
```js
pandoc = require('metalsmith-pandoc');

Metalsmith(__dirname)
.use(pandoc())
...
```

As default, plugin will use these settings:
```
options = {
  from: 'markdown',
  to:   'html5',
  args: [],
  opts: {},
  pattern: '**/*.md', // multimatch
  ext: '.html' // extension for output file
};
```

To override the defaults, pass an object to the plugin:
```
.use(pandoc({
  pattern: ['rsts/*.md', 'docs/**/*.md'],
  args: ['--columns=80'],
  from: 'markdown',
  to: 'rst',
  ext: '.rst'
}))
```
See [pdc](https://github.com/pvorb/node-pdc#api) and [pandoc](http://johnmacfarlane.net/pandoc/README.html) for more detailed description of options.


## Release
```sh
npm version major|minor|patch
npm publish
```

## Credit
Stole code from [metalsmith-markdown](https://github.com/segmentio/metalsmith-markdown).
