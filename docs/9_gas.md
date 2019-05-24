---
id: gas
title: Gas_rate API
sidebar_label: Bytom.Gas.API
---

## gas-rate

Quary gas rate.

#### Parameters

none

#### Returns

- `Integer` - *gas_rate*, gas rate.

#### Example
```js
const keyPromise = client.status.gasRate()
var sync = keyPromise.then((res) => console.log(res)) 
```
```js
$ node test.js
//response
{ 
    gas_rate: 200 
}
```