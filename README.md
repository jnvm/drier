[![](https://img.shields.io/badge/SLOC-1-brightgreen.svg)](https://github.com/jnvm/drier/blob/master/drier.js#L1)
[![David](https://img.shields.io/david/jnvm/drier.svg?maxAge=360000)]()
# Drier

Does repetition in code bother you to what others call an unreasonable degree?

Is DRY (**D**on't **R**epeat **Y**ourself) such a governing rule when you write code that you regularly apply it to real life scenarios?

Do blocks of code with even this level of repetition offend you at a visceral level?

```javascript
let thing = operator('thing')
let aThing = operator('aThing')
let thisThing = operator('thisThing')
let thatThing = operator('thatThing')
let theOtherThing = operator('theOtherThing')
```

Be offended no more: just make it `drier`!

```javascript
let {thing, aThing, thisThing,
	thatThing, theOtherThing} = require('drier')(operator)
```

...and through the magic of [destructuring](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators/Destructuring_assignment) and [proxies](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Proxy/handler/get), never stutter variables in code again!

## How It Works

`drier` is a function which invokes its input function with a string of each variable name on the left of the destructuring assignment,
removing the need to repeat them, and maybe encouraging more meaningful names.

Or you could describe it as an iterator across variable names.

## More Examples
```javascript
const drier = require('./drier.js')
const dryquire = drier(require)
const {fs, crypto, util, http, os, repl, express, "package.json":{scripts}} = dryquire
const {sqlA, sqlB, sqlC, sqlD} = drier(s => fs.readFileSync(`${__dirname}/${s}.sql`))
```
----
#### see also
* [dryer vs drier](https://writingexplained.org/drier-vs-dryer-difference)
* [`new Proxy()`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Proxy)