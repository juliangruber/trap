# trap

trap is simply the most dead-simple test framework you can pick up. It builds and simplifies
the already simple structure of of `node-tap` or `tape`, but is extensible like `mocha`.

## What do I need to know?

Two things: `test`, and `t.cb`. It's really that simple. You can use the assertion framework
you already know. By default trap uses the standard node assertion library. To run the tests in
single file, just `node` the file.

### `test`

Like tap, we make new test blocks with the `test` function.

```javascript
var test = require('trap').test;

test('This is a test block!', function (t) {
  t.test('This is a child test block!', function (t) {
    // continue to your heart's content.
  });
});
```

### `t.cb`

Unlike tap, you don't need to figure out when your async tests are done runnning, nor
do you need to count how many assertions you have and plan them. Instead, simply register
all of your callbacks with `t.cb`.

```javascript
var test = require('trap').test;

test('Async stuff', function (t) {
  setTimeout(t.cb(function() {
    t.ok(true, 'This is still part of the "Async stuff" test!');
  }), 100);
});
```

### Assertions

To get the maximum prettiness and documentation of trap, customize
`config.createAssertionWrapper` to wrap your favorite assertion library. Otherwise
you can just throw exceptions like you normally do, and those will be interpreted as
assertion failures. Hopefully soon we can get plugins for all the major assertion
libraries so this will be even easier.

## Examples

Check out the examples folder.