# Prevents some module import (require) 

## Rule Details

This rule allows you to forbid some module import and to suggest some alternative.

### Example:
Let's consider we have this configuration in `.eslintrc`:

```json
{
  "plugins": ["deprecate"],
  "rules": {
    "deprecate/import": ["error",
      {"name": "legacyModule", "use": "newModule"}
    ]
  }
}
```

### The following patterns are considered as errors:

```js
// any function call with name legacyFunc
import a from 'legacyModule';
const a = require('legacyModule');
```

## Options
You can just pass deprecated modules names as strings:

```js
"deprecate/import": [ 2, "<mod name1>", "<mod name2>"]
```

If you want more control over displayed errors (suggest alternative module import e.t.c)
you can pass objects instead of just modules names:

```js
"deprecate/import": [ 2, 
    {"name": "<import name>", "use": "<suggested alternative>"}, ... ]
```

## When Not To Use It

When you don't want to forbid some modules usage in your codebase.