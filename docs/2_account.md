---
id: account
title: Account API
sidebar_label: Bytom.Account.API
---



## creat-account

Create account to manage addresses. single sign account contain only one root_xpubs and quorum; however multi sign account contain many number of root_xpubs and quorum, quorum is the number of verify signature, the range is [1, len(root_xpubs)].

#### Parameters

- `Array of Sring` -  *root_xpubs*, pubkey array.

- `String` - *alias*, name of the account.

- `Integer` - *quorum*, the default value is `1`, threshold of keys that must sign a transaction to spend asset units controlled by the account.

Optional:

- `String` - *access_token*, if optional when creating account locally. However, if you want to create account remotely, it's indispensable.

#### Returns

-  `String` - *id*, account id.

-  `String` - *alias*, name of account.

-  `Integer` - *key_index*, key index of account.

-  `Integer` - *quorum*, threshold of keys that must sign a transaction to spend asset units controlled by the account.

-  `Array of Object` -  *xpubs*, pubkey array.

#### Example
```js
const accountPromise = keyPromise.then(key => {
client.accounts.create({
    alias: 'alice', 
    root_xpubs: [key.xpub], 
    quorum: 1 
})
})
var sync = accountPromise.then((res) => console.log(res)) 
```

```js
$ node test.js
//response
{
  "alias": "alice",
  "id": "08FO663C00A02",
  "key_index": 1,
  "quorum": 1,
  "xpubs": [
    "2d6c07cb1ff7800b0793e300cd62b6ec5c0943d308799427615be451ef09c0304bee5dd492c6b13aaa854d303dc4f1dcb229f9578786e19c52d860803efa3b9a"
  ]
}
```

## list-accounts

Returns the list of all available accounts.

#### Parameters
none
#### Returns
- `Array of Object`, account array.
  - `String` - *id*, account id.
  - `String` - *alias*, name of account.
  - `Integer` - *key_index*, key index of account.
  - `Integer` - quorum,  threshold of keys that must sign a transaction to spend asset units controlled by the account.
  - `Array of Object` - xpubs, pubkey array.
#### Example

```js
const keyPromise = client.accounts.listAll()
var sync = keyPromise.then((res) => console.log(res))
```

```json
$ node test.js
//response
[
  {
    "alias": "alice",
    "id": "086KQD75G0A02",
    "key_index": 1,
    "quorum": 1,
    "xpubs": [
      "180aab8bf247932a7cf68da5cc9a873266279155097612f1e5fdda4add88d5e91e2e7ce5b736f3ac933824cdee9effcf1531b90dfcb388e5cc306d14e9a2c85e"
    ]
  },
  {
    "alias": "bob",
    "id": "086KQO67G0A04",
    "key_index": 2,
    "quorum": 1,
    "xpubs": [
      "180aab8bf247932a7cf68da5cc9a873266279155097612f1e5fdda4add88d5e91e2e7ce5b736f3ac933824cdee9effcf1531b90dfcb388e5cc306d14e9a2c85e"
    ]
  }
]
```

## update-account-alias

Update alias for the existed account.

#### Parameters

- `String` - *account_id*, account_id
- `String` - *account_alias*, account_alias 
- `String` - *new_alias*, new alias of account.
#### Returns
none if the account alias is updated successfully.
#### Example
```js
const keyPromise = client.accounts.updateAlias({
    account_id:'0RADLP61G0A02',
    account_alias:'account',
    new_alias:'account123'
})
var sync = keyPromise.then((res) => console.log(res)) 
```

```json
$ node test.js
//response
//none
```

## delete-account

Delete existed account, please make sure that there is no balance in the related addresses.

#### Parameters
- `String` - *account-info*, account_alias | account_id
#### Returns
none if the account is deleted successfully.
#### Example
```js
const keyPromise = client.accounts.delete({account_id:'0RADP6RBG0A04'})
var sync = keyPromise.then((res) => console.log(res)) 
```
```json
$ node test.js
//response
//none
```
## create-account-receiver
create address and control program, the address and control program is are one to one relationship. in build-transaction API, receiver is address when action type is control_address, and receiver is control program when action type is control_program, they are the same result.
#### Parameters
`Object`: *account_alias | account_id*
Optional:

- `String` - *account_alias*, alias of account.
- `String` - *account_id*, id of account.
#### Returns
- `String` - *address*, address of account.
- `String` - *control_program*, control program of account.
#### Example
```js
const keyPromise = client.accounts.createReceiver({
    account_alias:'account',
    account_id:'0RADLP61G0A02'
})
var sync = keyPromise.then((res) => console.log(res)) 
```
```json
$ node test.js
//response
{ 
  control_program: '0014b0cef0bdbe6551c62fb37993593f1ec4d8051396',
  address: 'bm1qkr80p0d7v4guvtan0xf4j0c7cnvq2yukd43ynj' 
}
```

## list-addresses

Returns the sub list of all available addresses by account.

#### Parameters

- `String` - *account_alias*, alias of account.
- `String` - *account_id*, id of account.

#### Returns

  - `String` - *account_alias*, alias of account.
  - `String` - *account_id*, id of account.
  - `String` - *address*, address of account.
  - `Boolean` - *change*, whether the account address is change.

####  Example

```js
const keyPromise = client.accounts.listAddresses({
    account_alias:'alice',
    account_id:'086KQD75G0A02'
})
var sync = keyPromise.then((res) => console.log(res)) 
```
```json
$ node test.js
//response
[
  {
    "account_alias": "alice",
    "account_id": "086KQD75G0A02",
    "address": "bm1qcn9lf7nxhswratvmg6d78nq7r7yupm36qgsv55",
    "change": false
  },
  {
    "account_alias": "alice",
    "account_id": "086KQD75G0A02",
    "address": "bm1qew4h5uvt5ssrtg2alms0j77r94c30m78ucrcxy",
    "change": false
  },
  {
    "account_alias": "alice",
    "account_id": "086KQD75G0A02",
    "address": "bm1qgnp4lte7wge0rsekevjlrdh39vkzz0c2alheue",
    "change": false
  }
]
```

## validate-address

Verify the address is valid, and judge the address is own.

#### Parameters

- `String` - *address*, address of account.

####　Returns

- `Boolean` - *vaild*, whether the account address is valid.

- `Boolean` - *is_local*, whether the account address is local.

#### Example

```js
const keyPromise = client.accounts.validateAddresses({
    address: 'bm1qkr80p0d7v4guvtan0xf4j0c7cnvq2yukd43ynj'
})
var sync = keyPromise.then((res) => console.log(res)) 
```

```json
$ node test.js
// response
{
   "vaild": true,
   "is_local": true,
}
```