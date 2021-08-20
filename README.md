# tme

tme is a testing app that can test nodejs and web applications.
I wrote this app by following [this](https://www.udemy.com/course/javascript-beginners-complete-tutorial/) tutorial by Stephen Grider.

## Requirements

- Node version 14.x and above
- npm version 6.x and above

## Installation

1. clone this repo.
2. go to the tme directory.
3. install dependencies using npm.

```npm
    npm install
```

4. link this repo to your local computer using npm so you can access tme everywhere on your terminal.

```npm
    npm link
```

## Usage

The test files that you make should follow this pattern :

```js
    *.test.js
```

Inside those test file you can use _it_ and _beforeEach_ function to define you tests.

### it

The _it_ function is the core part of this testing app. It accepts two arguments, a description of the test that will be shown on terminal and a callback function that is your actual test!

```js
it("DESCRIPTION", testFunction);
```

### beforeEach

This pre-defined function accepts just a callback function that will execute before each test that was defined by _it_.

```js
beforeEach(callbackFunction);
```

But before defining your test with _it_ and _beforeEach_, you must to add some other code to your \*.test.js files in order to work correctly and that depends on which platform your app is written in.

## Nodejs

If you are testing a node application, do these instructions :

1. require in each function that you want to test.

```js
const { foo } = require("../index");
```

2. require [assert](https://nodejs.org/dist/latest-v14.x/docs/api/assert.html#assert_assert) that is a pre-defined nodejs module.

```js
const assert = require("assert");
```

3. define your test using _it_ and _beforeEach_
4. at the end of each test, use assert module to check what the test return and what do you expect it to return.

## Web Apps

1. require [assert](https://nodejs.org/dist/latest-v14.x/docs/api/assert.html#assert_assert) that is a pre-defined nodejs module.

```js
const assert = require("assert");
```

2. use async key word for _it_ callback function.
3. at each test you should first render your main html file to the app.

```js
const dom = await render("index.html");
```

4. also if you want to dispatch action to dom then test something with it, use this syntax in your callback function : (For more information see [jsdom](https://github.com/jsdom/jsdom) documentation)

```js
dom.window.document
  .querySelector("form")
  .dispatchEvent(new dom.window.Event("submit"));
```

## Caution

Please take note that this app will run every thing that is writen in those \*.test.js files. If there is some bad code that mess with your system via nodejs, it can cause many problems as jsdom [says](https://github.com/jsdom/jsdom#executing-scripts).

So just test and run test files that you wrote yourself. In that case there is absolutely nothing to be worry about.

## Examples

You can find some examples by looking at tests in 'sampleNodeProject' and 'sampleWebProject' directories in this repo.
