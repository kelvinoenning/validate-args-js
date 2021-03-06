# Validate-args-js

Validate arguments for a Javascript.

[![Build Status](https://travis-ci.org/Adapcon/validate-args-js.svg?branch=master)](https://travis-ci.org/Adapcon/validate-args-js)

[![Coverage Status](https://coveralls.io/repos/github/Adapcon/validate-args-js/badge.svg?branch=master)](https://coveralls.io/github/Adapcon/validate-args-js?branch=master)

## Installation

```
npm install --save validate-args-js
```

## Usage

#### Import

``` js
const check = require('validate-args-js')
```

#### Simple
``` js
check.arg({ 
    arg: undefined, 
    err: 'err name' 
})

//Return -> throw new Error('err name')
```
``` js
check.arg({ 
    arg: undefined, 
    err: undefined 
})

//Return -> throw new Error('one argument has not been defined!')
```

#### Accept
``` js
check.arg({ 
    arg: undefined, 
    err: 'err name',
    accept: {
        options: [1,2,3],
        err: 'err accept name'
    }
})

//Return -> throw new Error('err name')
```
``` js
check.arg({ 
    arg: 4, 
    err: 'err name',
    accept: {
        options: [1,2,3],
        err: 'err accept name'
    }
})

//Return -> throw new Error('err accept name')
```
``` js
check.arg({ 
    arg: 4, 
    err: 'err name',
    accept: {
        options: [1,2,3],
        err: undefined
    }
})

//Return -> throw new Error('one argument has not been accepted!')
```

#### List
``` js
check.args([
    { 
        arg: 1, 
        err: 'err value',
        accept: {
            options: [1,2,3],
            err: 'err accept value'
        }
    },
    { 
        arg: 4, 
        err: 'err value 2',
        accept: {
            options: [1,2,3],
            err: 'err accept value 2'
        }
    }
])

//Return -> throw new Error('err accept value 2')
```

``` js
check.args([{ 
    arg: undefined, 
    err: 'err name',
    accept: {
        options: [1,2,3],
        err: 'err accept name'
    }
}])

//Return -> throw new Error('err name')
```