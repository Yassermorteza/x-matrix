# matrix  [![Build Status](https://travis-ci.org/Yassermorteza/x-matrix.svg?branch=master)](https://travis-ci.org/Yassermorteza/x-matrix)

# x-mocha-intro

This exercise is aimed to introduce unit testing with [mocha](https://mochajs.org/) and the [require](http://devdocs.io/node~6_lts/modules#modules_module_require_id) function from Node.js.

__Note:__ at the end of __every steps__, build your code, make a commit (with the step's name) and push to to the working branch (will be named `feat-test`).

## Steps

### Preparation

If you have doubt about the following tasks, refer to the [x-loader-simulation](https://github.com/zeropaper/x-loader-simulation) exercise.

- Create a git branch called `feat-test` (`git checkout -b feat-test`).
- Create a file called `.gitignore` in which you will add a line with `node_modules` (this will prevent your `node_modules` to be added to git)
- Create a `src` folder and move your `index.js` and `index.html` in it.
- In the repository of your [x-array-matrix](https://github.com/zeropaper/x-array-matrix) exercise, create a `package.json` (with the right `npm` command).
  Answer `mocha` when you will be asked for a "test command" by the wizard.
- Make sure that your project is "private".
- Install the following development dependencies
  - mkdirp
  - cp
  - browserify
  - uglify-js
  - jshint
  - [mocha](https://www.npmjs.com/package/mocha)
  - [expect.js](https://www.npmjs.com/package/expect.js)
- In your `package.json` create the following `script` entries:
  - `prebuild` which:
    - uses `jshint` to lint the `src/*.js` files
    - creates a `docs` folder
    - then copy the `src/index.html` into it
  - `build`: which compiles the `src/index.js` into `docs/bundle.js` with `browserify`
  - `postbuild`: which will minify the `docs/bundle.js`
- Modify your `src/index.html` to load `bundle.js` instead of `index.js`

### Refactoring

Refactoring is an operation in which the some code is changed without changing its functionnalities.

For each functions (except `renderTableDom` if you have it) in your `src/index.js`, create a file named after the function and use `require` to load the file.
Example with the `createMatrix` function, you will create a file called `create-matrix.js` (in the `src` folder) in which you will have:

````js
module.exports = function createMatrix(rowsCount, columnsCount) {
  /*... */
};
````
(the `module.exports` make it possible for other files to "require" the function)

and in your `src/index.js` you will have

````js
var createMatrix = require('./create-matrix'); // you don't need the '.js' here
````
In the end, you should have 8 files for your functions in your `src` folder (and your `index.js`).

### Writing tests
