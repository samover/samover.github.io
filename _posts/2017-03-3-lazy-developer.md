---
layout: post
title: Becoming even more lazy as a developer
---

Confoo is a multi-tech conference hosted in Montreal, Canada, at the beginning of the (still) very
cold month of March. So after a comfortable intercontinental flight and checking in at my airBnB, I
walked to downtown Montreal and immersed myself into my first tech conference ever. As a classicist
recently turned developer I really looked forward to getting a taste of as many new technologies as
possible. But in the end, the stuff that stuck was about code quality: how to write better, i.e.
more testable, more readable and more maintainable code.

Developing in Node.js, or any other language for that matter, can lead to a lot of boilerplate code.
I live by the adage that a good developer is a lazy developer. That's why I would like to share some
ways in which to write less and cleaner code in Node.js both in application code as in unit testing.
This contribution is inspired by the awesome talks by Gleb Bahmutov (https://glebbahmutov.com) and Christopher Neugebauer (https://chris.neugebauer.id.au/);

# ES6 goodies

## Separate arguments

In ES5, we would write the following in order to access all arguments after `y`:

```javascript
function f(x, y) {
   var a = Array.prototype.slice.call(arguments, 2);
   // other code
};
```

In ES6, we can use the `rest` operator:

```javascript
function f(x, y, ...a) {
  // a is an array of arguments after "y"
};
```


## Computed Keys

Every javascript developer has written the following code:

```javascript
const foo = 'key';
const object = {};
object[foo] = 42;
```

But in ES6, we can use `computed keys`:

```javascript
const foo = 'key';
const object = {
  [foo]: 42
};
```

# Argument binding

Given this example of express code:

```javascript
app.get('/repos', passport.isAuthenticated, passport.isAuthorized, ctrl.getRepos);
app.get('/repos/:user/:name', passport.isAuthenticated, passport.isAuthorized, ctrl.getRepo);
app.get('/repos/view/:user/:name', passport.isAuthenticated, passport.isAuthorized, ctrl.viewFile);
```

Wouldn't it be awesome to be able to write just this?

```javascript
authGet('/repos', ctrl.getRepos);
```

In Javascript, we can easily bind arguments to a function using the `bind` function:

```javascript
const sum = (a, b) => a + b;
const add5 = sum.bind(null, 5)
add5(4) // 9
```

But in our example, we want to bind the second and third argument. This is not possible using
`bind`, but the npm module `spots` allows us to do just that:

```javascript
const S = require('spots');
const authGet = S(app.get, S, passport.isAuthenticated, passport.isAuthorized).bind(app);"
```

And now it is possible to define an authenticated route in a more readable and concise way:

```javascript
authGet('/repos', ctrl.getRepos);
```

# Property based testing

Good unit testing requires a lot of test cases. Let's take the `add` function we defined above.
There are a few cases we need to check in our tests:

```javascript
// Mocha using expect library
describe('add', () => {
  it('should work', () => {
    expect(add(1, 1).to.eql(2);
    expect(add(1, 3).to.eql(4);
    expect(add(0, 0).to.eql(0);
    expect(add(-1, 1).to.eql(0);
    expect(add(10, -1).to.eql(9);
  });
});
```

Using property testing and the excellent `jsverify` module (inspired by the `quickcheck` haskell
library: https://hackage.haskell.org/package/QuickCheck), we can avoid a lot of boilerplate. And as
a bonus, the module will by itself check a lot of edge cases:


```javascript
const jsc = require('jsverify');

const add = (a, b) => a + b;

describe('add', () => {
    it('does stuff', () => {
        expect(jsc.checkForall(jsc.integer, jsc.integer, (a, b) => a + b === add(a,b)));
      // output:
      // OK, passed 100 tests
      //  ✓ does stuff
    });
});
```

This is just the tip of the iceberg for property based testing. By writing general properties for
our scenario, `jsverify` generates by default 100 test cases checking most if not all edge cases. It
thus makes the hard job of thinking of all the edge cases when testing algorithms a breeze and as a consequence, this lazy developer can become even more lazy and concentrate on the fun parts of coding.
