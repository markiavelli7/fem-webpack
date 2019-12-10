# Webpack 4 Fundamentals

## Why Webpack?

Webpack is a module bundler. It lets us write any module format (mixed!) and compiles them for the browser.

Supports static async bundling.

The most performant way to ship JavaScript today.


## Configuring Webpack

### Webpack Config

```javascript
module.exports = {
  entry: {
    vendor: './src/vendor.ts',
    main: './src/main.browser.ts'
  },
  output: {
    path: 'dist/',
    filename: '[name].bundle.js'
  }
}
```

### Webpack CLI

```bash
$> webpack <entry.js> <result.js> --colors --progress

$> webpack-dev-server --port=9000
```

### Node API

```javascript
var webpack = require('webpack')

// returns a Compiler instance
webpack({
  // configuration object here!
}, function(err, stats) {
  // ...
  // compilerCallback
  console.error(err);
})
```