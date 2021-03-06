# padded-blocks

Requires or disallows padding within blocks.

Some style guides require block statements to start and end with blank lines. The goal is
to improve readability by visually separating the block content and the surrounding code.

```js
if (a) {

    b();

}
```

Since it's good to have a consistent code style, you should either always write
padded blocks or never do it.

## Rule Details

This rule enforces consistent empty line padding within blocks.

## Options

This rule has two options, the first one can be a string option or an object option.
The second one is an object option, it can allow exceptions.

### First option

String option:

* `"always"` (default) requires empty lines at the beginning and ending of block statements, function bodies, class static blocks, classes, and `switch` statements.
* `"never"` disallows empty lines at the beginning and ending of block statements, function bodies, class static blocks, classes, and `switch` statements.
* `"loose"` applies the `always` rule if there is at least one empty (padding) line inside the block's body, and applies the `never` rule otherwise. Note that if the block contains other blocks, the empty lines in those blocks' bodies are not considered, only those for each block's own block level.

Object option:

* `"blocks"` require or disallow padding within block statements, function bodies, and class static blocks
* `"classes"` require or disallow padding within classes
* `"switches"` require or disallow padding within `switch` statements

### Second option

* `"allowSingleLineBlocks": true` allows single-line blocks
* `"noBottomPadding": true` prevents padding to be added to the bottom of blocks
* `"includeObjects": true` extends the scope of the rule to Objects (i.e.: ObjectPattern, ObjectExpression) - The original `padded-blocks` rule does not consider Object literals, however from styling perspective those may need the same handling as other `{...}` parts, so this option extends the check to cover those. Note that you may need to turn off or configure the `object-curly-newline` rule to avoid conflicts with this one.

### always

Examples of **incorrect** code for this rule with the default `"always"` option:

```js
/*eslint padded-blocks: ["error", "always"]*/

if (a) {
    b();
}

if (a) { b(); }

if (a)
{
    b();
}

if (a) {
    b();

}

if (a) {
    // comment
    b();

}

class C {
    static {
        a();
    }
}
```

Examples of **correct** code for this rule with the default `"always"` option:

```js
/*eslint padded-blocks: ["error", "always"]*/

if (a) {

    b();

}

if (a)
{

    b();

}

if (a) {

    // comment
    b();

}

class C {

    static {

        a();

    }

}
```

### never

Examples of **incorrect** code for this rule with the `"never"` option:

```js
/*eslint padded-blocks: ["error", "never"]*/

if (a) {

    b();

}

if (a)
{

    b();

}

if (a) {

    b();
}

if (a) {
    b();

}

class C {

    static {

        a();

    }

}
```

Examples of **correct** code for this rule with the `"never"` option:

```js
/*eslint padded-blocks: ["error", "never"]*/

if (a) {
    b();
}

if (a)
{
    b();
}

class C {
    static {
        a();
    }
}
```

### loose

Examples of **incorrect** code for this rule with the `"loose"` option:

```js
/*eslint padded-blocks: ["error", "loose"]*/

if (a) {
  b();
  
  c();
}

if (a) {
  
    b();
    
}

if (a) { b(); 
  
  c(); }

if (a)
{
  
    b();
    
}

if (a)
{
  b();

  c();
}

if (a) {
    b();

}

if (a) {
    // comment
    b();

}

class C {

  static {

    a();

  }

}

class C {
  static {
    a();
    b();
  }
}

class C {
  
  static {
    a();
    
    b();
  }
  
}
```

Examples of **correct** code for this rule with the `"loose"` option:

```js
/*eslint padded-blocks: ["error", "loose"]*/

if (a) {
  
  b();

  c();
  
}

if (a) {
    b();
}

if (a) { b(); }

if (a)
{
    b();
}

if (a)
{
  
  b();

  c();
  
}

if (a) {
    // comment
    b();
}

class C {
  static {
    a();
  }
}

class C {
  static {
    
    a();
    
    b();
    
  }
}
```

### blocks

Examples of **incorrect** code for this rule with the `{ "blocks": "always" }` option:

```js
/*eslint padded-blocks: ["error", { "blocks": "always" }]*/

if (a) {
    b();
}

if (a) { b(); }

if (a)
{
    b();
}

if (a) {

    b();
}

if (a) {
    b();

}

if (a) {
    // comment
    b();

}

class C {

    static {
        a();
    }

}
```

Examples of **correct** code for this rule with the `{ "blocks": "always" }` option:

```js
/*eslint padded-blocks: ["error", { "blocks": "always" }]*/

if (a) {

    b();

}

if (a)
{

    b();

}

if (a) {

    // comment
    b();

}

class C {

    static {

        a();

    }

}

class D {
    static {

        a();

    }

}
```

Examples of **incorrect** code for this rule with the `{ "blocks": "never" }` option:

```js
/*eslint padded-blocks: ["error", { "blocks": "never" }]*/

if (a) {

    b();

}

if (a)
{

    b();

}

if (a) {

    b();
}

if (a) {
    b();

}

class C {
    static {

        a();

    }
}
```

Examples of **correct** code for this rule with the `{ "blocks": "never" }` option:

```js
/*eslint padded-blocks: ["error", { "blocks": "never" }]*/

if (a) {
    b();
}

if (a)
{
    b();
}

class C {
    static {
        a();
    }
}

class D {

    static {
        a();
    }

}
```

### classes

Examples of **incorrect** code for this rule with the `{ "classes": "always" }` option:

```js
/*eslint padded-blocks: ["error", { "classes": "always" }]*/

class  A {
    constructor(){
    }
}
```

Examples of **correct** code for this rule with the `{ "classes": "always" }` option:

```js
/*eslint padded-blocks: ["error", { "classes": "always" }]*/

class  A {

    constructor(){
    }

}
```

Examples of **incorrect** code for this rule with the `{ "classes": "never" }` option:

```js
/*eslint padded-blocks: ["error", { "classes": "never" }]*/

class  A {

    constructor(){
    }

}
```

Examples of **correct** code for this rule with the `{ "classes": "never" }` option:

```js
/*eslint padded-blocks: ["error", { "classes": "never" }]*/

class  A {
    constructor(){
    }
}
```

### switches

Examples of **incorrect** code for this rule with the `{ "switches": "always" }` option:

```js
/*eslint padded-blocks: ["error", { "switches": "always" }]*/

switch (a) {
    case 0: foo();
}
```

Examples of **correct** code for this rule with the `{ "switches": "always" }` option:

```js
/*eslint padded-blocks: ["error", { "switches": "always" }]*/

switch (a) {

    case 0: foo();

}

if (a) {
    b();
}
```

Examples of **incorrect** code for this rule with the `{ "switches": "never" }` option:

```js
/*eslint padded-blocks: ["error", { "switches": "never" }]*/

switch (a) {

    case 0: foo();

}
```

Examples of **correct** code for this rule with the `{ "switches": "never" }` option:

```js
/*eslint padded-blocks: ["error", { "switches": "never" }]*/

switch (a) {
    case 0: foo();
}

if (a) {

    b();

}
```

### always + allowSingleLineBlocks

Examples of **incorrect** code for this rule with the `"always", {"allowSingleLineBlocks": true}` options:

```js
/*eslint padded-blocks: ["error", "always", { allowSingleLineBlocks: true }]*/

if (a) {
    b();
}

if (a) {

    b();
}

if (a) {
    b();

}
```

Examples of **correct** code for this rule with the `"always", {"allowSingleLineBlocks": true}` options:

```js
/*eslint padded-blocks: ["error", "always", { allowSingleLineBlocks: true }]*/

if (a) { b(); }

if (a) {

    b();

}
```

### always + noBottomPadding

Examples of **incorrect** code for this rule with the `"always", {"noBottomPadding": true}` options:

```js
/*eslint padded-blocks: ["error", "always", { noBottomPadding: true }]*/

if (a) {
    b();
}

if (a) {

    b();
    
}

if (a) {
    b();

}
```

Examples of **correct** code for this rule with the `"always", {"noBottomPadding": true}` options:

```js
/*eslint padded-blocks: ["error", "always", { noBottomPadding: true }]*/

if (a) {

    b();
}
```

## When Not To Use It

You can turn this rule off if you are not concerned with the consistency of padding within blocks.

## Original rule

This rule is based on the `padded-blocks` rule in the ESLint package. See the original documentation here:
 * https://eslint.org/docs/rules/padded-blocks
 * https://github.com/eslint/eslint/blob/main/docs/src/rules/padded-blocks.md
