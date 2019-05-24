---
id: mining
title: Mining API
sidebar_label: Bytom.Mining.API
---

## is-mining

Returns the mining status.

#### Parameters

none

#### Returns


- `Boolean` - *is_mining*, whether the node is mining.

#### Example
```js
const keyPromise = client.status.isMining()
var sync = keyPromise.then((res) => console.log(res)) 
```
```js
$node test.js
//response
{
  "is_mining": true
}
```

## set-mining

Start up node mining.

#### Parameters

- `Boolean` - *is_mining*, whether the node is mining.

#### Example
```js
const keyPromise = client.status.setMining({
    is_mining: true
})
var sync = keyPromise.then((res) => console.log(res)) 
```
```js
$node test.js
//response
//none
```