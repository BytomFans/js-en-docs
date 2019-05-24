---
id: work
title: Work API
sidebar_label: Bytom.Work.API
---

## get-work

Get the proof of work.

#### Parameters

none

#### Returns

`Object`:

- `Object` - *block_header*, raw block header.
- `Object` - *seed*, seed.


#### Example
```js
const keyPromise = client.status.getWork()
var sync = keyPromise.then((res) => console.log(res)) 
```
```js
$node test.js
//response
{ 
    block_header:
   "0101eaa30d17c54a9dfc1c0b0d1722ee1592d96ff64d1ea1be6ae03fbe80ef63e05e58725add8ee1e50540b93d691e5ec99698ecfcd3e0ad8c2196429f24708f0663730d1d387f31e11dafc9c377e5192668bc0a367e4a4764f11e7c725ecced1d7b6a492974fab1b6d5bc00b9fb8981808080801c",
  seed:
   "c4addf810420a1ba2ef646e68d8be89b636c26a48eeb386c10bf20dec4d37dcc" 
}
```


## submit-work

Submit the proof of work.

#### Parameters

- `Object` - *block_header*, raw block header.

#### Returns

true if success.

#### Example
```js
const keyPromise = client.status.submitWork({
    block_header: "0101870103f2c7495164c8f3af43697e81faa21dcb2d60aa5e10ce4f233491e62420742fbeadfcd50540bef2670a5fade2e58ad4955e2375a04ad1e4cb9c104faddab43f4a79e35be253c9c377e5192668bc0a367e4a4764f11e7c725ecced1d7b6a492974fab1b6d5bc00ffffff838080808020"
})
var sync = keyPromise.then((res) => console.log(res)) 
```
```js
$node test.js
//response
true / error
```