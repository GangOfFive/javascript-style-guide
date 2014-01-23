# JavaScript Style Guide for *Gang of Five*

Based on [Google's](http://google-styleguide.googlecode.com/svn/trunk/javascriptguide.xml)
and [Airbnb's](https://github.com/airbnb/javascript/) excellent JavaScript style guides.

## Naming Conventions
 - JavaScript files should be named like this:
   - `elephant.js`
   - `favorite-movies.js`
 - Be descriptive with your naming.

    ~~~
    // bad
    function q() {
        // ...stuff...
    }

    // good
    function query() {
        // ..stuff..
    }
    ~~~

 - Use `camelCase` when naming objects, functions, and instances.

    ~~~
    // bad
    var OBJEcttsssss = {};
    var this_is_my_object = {};
    function c() {};
    var u = new user({
        name: 'Bob Parr'
    });

    // good
    var thisIsMyObject = {};
    function thisIsMyFunction() {};
    var user = new User({
        name: 'Bob Parr'
    });
    ~~~

 - Use `PascalCase` when naming constructors or classes.

    ~~~
    // bad
    function user(options) {
        this.name = options.name;
    }

    var bad = new user({
        name: 'nope'
    });

    // good
    function User(options) {
        this.name = options.name;
    }

    var good = new User({
        name: 'yup'
    });
    ~~~

 - Use a leading underscore _ when naming private properties.

    ~~~
    // bad
    this.__firstName__ = 'Panda';
    this.firstName_ = 'Panda';

    // good
    this._firstName = 'Panda';
    ~~~

 - Use `NAMES_LIKE_THIS` for constants.
 - Prefix jQuery object variables with a `$`.

    ~~~
    // bad
    var sidebar = $('.sidebar');

    // good
    var $sidebar = $('.sidebar');
    ~~~

## var
 - Always declare with var to avoid accidentally polluting the global scope.

    ~~~
    // bad
    pet = 'dog';

    // good
    var pet = 'dog';
    ~~~

 - Use one var declaration for multiple variables and declare each
   variable on a newline.

    ~~~
    // bad
    var items = getItems();
    var pet = 'dog';
    var special = false;

    // good
    var items = getItems(),
        pet = 'dog',
        special = false;
    ~~~

- Declare unassigned variables last. This is helpful when later on you might
  need to assign a variable depending on one of the previous assigned variables.

    ~~~
    // bad
    var i, length, special,
        items = getItems(),
        pet = 'dog';

    // bad
    var i, items = getItems(),
        special,
        pet = 'dog',
        length;

    // good
    var items = getItems(),
        pet = 'dog',
        special,
        length,
        i;
    ~~~

## Objects
 - Use the literal syntax for object creation:

    ~~~
    // bad
    var item = new Object();

    // good
    var item = {};
    ~~~

## Arrays
 - Use the literal syntax for array creation:

    ~~~
    // bad
    var items = new Array();

    // good
    var items = [];
    ~~~

 - Always use normal `for` loops when using arrays, do not use `for-in` loops.

    ~~~
    // bad
    var i;
    for (i in arr) {
        console.log(arr[i]);
    }
    // good
    var i,
        l = arr.length;

    for (i = 0; i < l; i++) {
        console.log(arr[i]);
    }
    ~~~

## Strings
 - Use single quotes for strings

    ~~~
    // good
    var color = 'red';

    // bad
    var color = "red";
    ~~~

- Strings longer than 80 characters should be written across
  multiple lines using string concatenation.

## Functions
 - Function expressions

    ~~~
    // anonymous function expression
    var anonymous = function() {
        return true;
    };

    // named function expression
    var named = function named() {
        return true;
    };

    // immediately-invoked function expression (IIFE)
    (function() {
        console.log('Hello');
    })();
    ~~~

 - Never declare a function in a non-function block (if, while, etc).
   Assign the function to a variable instead.

    ~~~
    // bad
    if (currentUser) {
        function test() {
            console.log('No');
        }
    }

    // good
    var test;
    if (currentUser) {
        test = function test() {
            console.log('Yes');
        };
    }
    ~~~

 - Nested functions can be very useful, for example in the creation of continuations and
   for the task of hiding helper functions. Feel free to use them.

 - Never name a parameter `arguments`, this will take precedence over
   the `arguments`object that is given to every function scope.

    ~~~
    // bad
    function nope(name, options, arguments) {
        // ...stuff...
    }

    // good
    function yup(name, options, args) {
        // ...stuff...
    }
    ~~~

## Properties
 - Use dot notation when accessing properties.

    ~~~
    // bad
    console.log(user['name']);
    // good
    console.log(user.name);
    ~~~

 - Use subscript notation `[]` when accessing properties with a variable.

    ~~~
    var attr = 'name';
    console.log(user[attr]);
    ~~~

## Modifying prototypes of builtin objects
 - Avoid modifying builtins like `Object.prototype` and `Array.prototype`.

## Conditional Expressions & Equality
 - Use `===` and `!==` over `==` and `!=`.
 - Use shortcuts.

    ~~~
    // bad
    if (name !== '') {
        // ...stuff...
    }

    // good
    if (name) {
        // ...stuff...
    }

    // bad
    if (collection.length > 0) {
        // ...stuff...
    }

    // good
    if (collection.length) {
        // ...stuff...
    }
    ~~~


## Code Formatting
 - Soft line length limit: 80.
 - Hard line length limit: 120.

### Array and Objects initializers
 - Single-line array and object initializers are allowed when they fit on a line.

    ~~~
    var arr = [1, 2, 3];  // No space after [ or before ].
    var obj = {a: 1, b: 2, c: 3};  // No space after { or before }.
    ~~~

### Function arguments
 - When possible, all function arguments should be listed on the same line. If
doing so would exceed the 80-column limit, the arguments must be line-wrapped
in a readable way. Both of the examples below are acceptable:

    ~~~
    // Four-space, wrap at 80.  Works with very long function names, survives
    // renaming without reindenting, low on space.
    var doThingThatIsVeryDifficultToExplain = function(
        veryDescriptiveArgumentNumberOne,
        veryDescriptiveArgumentTwo,
        tableModelEventHandlerProxy,
        artichokeDescriptorAdapterIterator) {
      // ...
    };
    // Parenthesis-aligned, one argument per line.  Emphasizes each
    // individual argument.
    function bar(veryDescriptiveArgumentNumberOne,
                 veryDescriptiveArgumentTwo,
                 tableModelEventHandlerProxy,
                 artichokeDescriptorAdapterIterator) {
      // ...
    }
    ~~~

### Blocks
 - Use braces with all multi-line blocks.

    ~~~
    // bad
    if (test)
        return false;

    // good
    if (test) return false;

    // good
    if (test) {
        return false;
    }

    // bad
    function() { return false; }

    // good
    function() {
        return false;
    }
    ~~~

### Whitespace
 - Use soft tabs set to 4 spaces

    ~~~
        // bad
        function() {
        ∙∙var name;
        }

        // bad
        function() {
        ∙var name;
        }

        // good
        function() {
        ∙∙∙∙var name;
        }
    ~~~

 - Place 1 space before the leading brace.

    ~~~
    // bad
    function test(){
        console.log('test');
    }

    // good
    function test() {
        console.log('test');
    }

    // bad
    dog.set('attr',{
        age: '1 year',
        breed: 'Schnauzer'
    });

    // good
    dog.set('attr', {
        age: '1 year',
        breed: 'Schnauzer'
    });
    ~~~

 - Set off operators with spaces.
    ~~~
    // bad
    var x=y+5;

    // good
    var x = y + 5;
    ~~~

 - Place an empty newline at the end of the file.

### Commas
 - Leading commas: **No**.

    ~~~
    // bad
    var one
      , two
      , three;

    // good
    var one,
        two,
        three;
    ~~~

 - Additional trailing comma: **No**.

    ~~~
    // bad
    var names = [
        'Jeff',
        'Sam',
        'Fred',
    ];

    // good
    var names = [
        'Jeff',
        'Sam',
        'Fred'
    ];
    ~~~

### Semicolons
  - **Yes**. Relying on implicit insertion can cause subtle, hard to debug problems.
    Don't do it. You're better than that.

    ~~~
    // bad
    (function() {
        var name = 'Skywalker'
        return name
    })()

    // good
    (function() {
        var name = 'Skywalker';
        return name;
    })();
    ~~~

### Comments
 - Use `/** ... */` for multiline comments. Include a description, specify
   types and values for all parameters and return values.

    ~~~
    // bad
    // make() returns a new element
    // based on the passed in tag name
    //
    // @param {string} tag
    // @return {Element} element
    function make(tag) {
        // ...stuff...
        return element;
    }

    // good
    /**
     * make() returns a new element
     * based on the passed in tag name
     *
     * @param {string} tag
     * @return {Element} element
     */
    function make(tag) {
        // ...stuff...
        return element;
    }
    ~~~

 - Use // for single line comments. Place single line comments on a newline
   above the subject of the comment. Put an empty line before the comment.

    ~~~
    // bad
    var active = true;  // is current tab

    // good
    // is current tab
    var active = true;

    // bad
    function getType() {
        console.log('fetching type...');
        // set the default type to 'no type'
        var type = this._type || 'no type';

        return type;
    }

    // good
    function getType() {
        console.log('fetching type...');

        // set the default type to 'no type'
        var type = this._type || 'no type';

        return type;
    }
    ~~~

 - Prefixing your comments with `FIXME` or `TODO` helps other developers quickly
   understand if you're pointing out a problem that needs to be revisited, or if
   you're suggesting a solution to the problem that needs to be implemented. These
   are different than regular comments because they are actionable. The actions
   are `FIXME -- need to figure this out` or `TODO -- need to implement`.

#### Types and Tags
 - It is only mandatory to add JSDoc comments to functions and constructors.

 - For types and tags please refer to:
   - [JSDoc Tag Reference](http://google-styleguide.googlecode.com/svn/trunk/javascriptguide.xml#JSDoc_Tag_Reference)
   - [JavaScript Types](http://google-styleguide.googlecode.com/svn/trunk/javascriptguide.xml#JsTypes)

 - We will make use of the following tags:
   - @const
   - @constructor
   - @enum
   - @fileoverview
   - @param
   - @return

## Parting Words

(taken from the Google JavaScript style guide)

*BE CONSISTENT.*

If you're editing code, take a few minutes to look at the code around you and
determine its style. If they use spaces around all their arithmetic operators,
you should too. If their comments have little boxes of hash marks around them,
make your comments have little boxes of hash marks around them too.

The point of having style guidelines is to have a common vocabulary of coding
so people can concentrate on what you're saying rather than on how you're
saying it. We present global style rules here so people know the vocabulary,
but local style is also important. If code you add to a file looks drastically
different from the existing code around it, it throws readers out of their
rhythm when they go to read it. Avoid this.
