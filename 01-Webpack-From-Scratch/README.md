# Webpack From Scratch

npm allows us to run scripts that hoist the binary (.bin) node_modules package within its scope.

**package.json**
```javascript
"scripts": {
  "webpack": "webpack"
}

// Then to run it

yarn webpack
```

## Adding npm Scripts for Environment Builds

Webpack, by default doesn't require a config. Webpack looks for an entry property, in this case */src*.

### Mode

Using the `mode` property, we specify development or production. Setting up for dev:

**package.json**
```javascript
"scripts": {
  "dev": "npm run webpack -- --mode development",
  "prod": "npm run webpack -- --mode production"
}
```

**-- says pipe in the next arguments onto the original command.**

*-- --mode development*

Now we can compose, without rewriting everything.

## Setting Up Debugging

**package.json**
```javascript
"scripts": {
  "webpack": "webpack",
    "debug": "node --inspect --inspect-brk ./node_modules/webpack/bin/webpack.js",
  "dev": "npm run webpack -- --mode development",
  "prod": "npm run webpack -- --mode production",
  "dev:debug": "npm run debug -- --mode production",
  "prod:debug": "npm run debug -- --mode development"
}
```

## Running Webpack

**yarn prod**

By default, Webpack will bundle all of our files and put the output into the **/dist** folder.

## Adding Watch Mode

```javascript
"dev": "npm run webpack -- --mode development --watch",
```

We add watch mode using the **--watch** argument to whatever environment we want to watch.

## ES Module Syntax

**Named Exports:**
```javascript
export var top = "top";
export var bottom = "bottom";

//  OR

export {
  top,
  bottom
}
```

## Common JS Export and Import

**Default Exports**

```javascript
module.exports = function (name) {
  return `Button: ${name}`
}

// OR

function makeButton(buttonName) {
  return `Button: ${name}`
}

module.exports = makeButton;
```

**Named Exports**

```javascript
var red = "color: red;";
var blue = "color: blue;";

function makeColorStyle(color) {
  return `color: ${color}`
};

exports.red = red;
exports.blue = blue;
exports.makeColorStyle = makeColorStyle;
```

Importing  the function:

```javascript
import makeButton from "./button"
import {red, blue, makeColorStyle} from "./buttonStyles"
```

## Adding a Default Webpack Configuration

By default, when Webpack runs, all it's doing is a require() relative to the local path: webpack.config.js.

**webpack.config.js**
```javascript
module.exports = {
  mode: "none"
}
```

Webpack applies its' defaults after it requires the config.

The webpack.config.js file allows us to override the defaults.

