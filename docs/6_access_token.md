---
id: access_token
title: Access_token API
sidebar_label: Bytom.Access_token.API
---

## create-access-token

Create access token, it provides basic access authentication for HTTP protocol, returns token contain username and password, they are separated by a colon.

#### Parameters

- `String` - *id*, token ID.

optional:

- `String` - *type*, type of token.

#### Returns

- `String` - *token*, access token, authentication username and password are separated by a colon.
- `String` - *id*, token ID.
- `String` - *type*, type of token.
- `Object` - *created_at*, time to create token.

#### Example
```js
const keyPromise = client.accessTokens.create({
    id:'token1'
})
var sync = keyPromise.then((res) => console.log(res)) 
```
```js
$ node test.js
//response
{ id: 'token1',
  token:
   'token1:d15b6975281ba2f9201976b1f7c8f2b3d4c2bf3d9589f14e2c56882d32f5dd83',
  created_at: '2019-04-18T15:39:26.3583019+08:00' }
```

## list-access-tokens

Returns the list of all available access tokens.

#### Parameters

none

#### Returns

- `Array of Object`, access token array.
  - `Object`:
    - `String` - *token*, access token.
    - `String` - *id*, token ID.
    - `String` - *type*, type of token. 
    - `Object` - *created_at*, time to create token.

#### Example

list all the available access tokens.

```js
const keyPromise = client.accessTokens.listAll()
var sync = keyPromise.then((res) => console.log(res)) 
```
```js
$ node test.js
//response
[
  {
    "token": "token1:1fee70f537128a201338bd5f25a3adbf33dad02eae4f4c9ac43f336a069df8f3",
    "id": "token1",
    "created_at": "2018-03-20T18:56:01.043919771+08:00"
  },
  {
    "token": "alice:78598c6d9fb9e3258d01f78005d4e5725ad0d45e20af90a30b577b407d4a2edd",
    "id": "alice",
    "created_at": "2018-03-20T18:56:01.043919771+08:00"
  }
]
```

## delete-access-token

Delete existed access token.

#### Parameters

`Object`:

- `String` - *id*, token ID.

#### Returns

none if the access token is deleted successfully.

#### Example

delete access token.
```js
const keyPromise = client.accessTokens.delete({
   id:'token1'
})
var sync = keyPromise.then((res) => console.log(res)) 
```
```js
$ node test.js
//response
//none
```


## check-access-token

Check access token is valid.

#### Parameters

`Object`:

- `String` - *id*, token ID.
- `String` - *secret*, secret of token, the second part of the colon division for token.

#### Returns

none if the access token is checked valid.

#### Example

check whether the access token is vaild or not.
```js
const keyPromise = client.accessTokens.check({
     id:'token1',
    secret: '1fee70f537128a201338bd5f25a3adbf33dad02eae4f4c9ac43f336a069df8f3'
})
var sync = keyPromise.then((res) => console.log(res)) 
```
```js
// Result
//none
```