---
id: asset
title: Asset API
sidebar_label: Bytom.Asset.API
---

## create-asset

Create asset definition, it prepares for the issuance of asset.

#### Parameters

- `Array of String` - *root_xpubs*, xpub array.
- `String` - *alias*, name of the asset.
- `Integer` - *quorum*, the default value is `1`, threshold of keys that must sign a transaction to spend asset units controlled by the account.

Optional

- `Object` - *definition*, definition of asset.
- `String` -  *issuance_program*, user-defined contract program.

#### Returns

- `String` - *id*, asset id.
- `String` - *alias*, name of the asset.
- `String` - *issuance_program*, control program of the issuance of asset.
- `Array of Object` - *keys*, information of asset pubkey.
- `String` - *definition*, definition of asset.
- `Integer` - *quorum*, threshold of keys that must sign a transaction to spend asset units controlled by the account.

#### Example

```js
const definition = {
    name: "GOLD",
    symbol: "GOLD",
    decimals: 8,
    description: {}
  }  
const keyPromise = client.assets.create({
    alias: 'GOLD',
    definition,
    root_xpubs: ['f6a16704f745a168642712060e6c5a69866147e21ec2447ae628f87d756bb68cc9b91405ad0a95f004090e864fde472f62ba97053ea109837bc89d63a64040d5'],
    quorum: 1
    })
var sync = keyPromise.then((res) => console.log(res)) 
```

```json
$ node test.js
//response
{ id:
   '57ba2e10543e35f682d4e47729da3c6da0372a94b4c6d04fe59bd389e2e68edc',
  alias: 'GOLD',
  issuance_program:
   'ae203fdd51e7622fc776b1841a0f45d6f82b65401bee9e2845ada193f94c3cda3e975151ad',
  keys:
   [ { root_xpub:
        'f6a16704f745a168642712060e6c5a69866147e21ec2447ae628f87d756bb68cc9b9140
5ad0a95f004090e864fde472f62ba97053ea109837bc89d63a64040d5',
       asset_pubkey:
        '3fdd51e7622fc776b1841a0f45d6f82b65401bee9e2845ada193f94c3cda3e97cb881ca
aeec8c45b65abd8ff38623f1ec7e5fdca9eec7fd96c6c28cdf9d676d1',
       asset_derivation_path: [Array] } ],
  quorum: 1,
  definition:
   { decimals: 8, description: {}, name: 'GOLD', symbol: 'GOLD' } }

```

## get-asset

Query detail asset by asset ID.

#### Parameters

- `String` - *id*, id of asset.

#### Returns

- `String` - *id*, asset id.
- `String` - *alias*, name of the asset.
- `String` - *issuance_program*, control program of the issuance of asset.
- `Integer` - *key_index*, index of key for xpub.
- `Integer` - *quorum*, threshold of keys that must sign a transaction to spend asset units controlled by the account.
- `Array of Object` - *xpubs*, pubkey array.
- `String` - *type*, type of asset.
- `Integer` - *vm_version*, version of VM.
- `String` - *raw_definition_byte*, byte of asset definition.
- `Object` - *definition*, description of asset.

#### Example
```js
const keyPromise = client.assets.list({
    id:'57ba2e10543e35f682d4e47729da3c6da0372a94b4c6d04fe59bd389e2e68edc'
    })
var sync = keyPromise.then((res) => console.log(res)) 
```

```json
// Result
{
  "alias": "SILVER",
  "definition": null,
  "id": "57ba2e10543e35f682d4e47729da3c6da0372a94b4c6d04fe59bd389e2e68edc",
  "issue_program": "ae2029cd61d9ef31d40af7541f9a50831d6317fdb0870249d0564fcfa9a8f843589c5151ad",
  "key_index": 1,
  "quorum": 1,
  "raw_definition_byte": "",
  "type": "asset",
  "vm_version": 1,
  "xpubs": [
    "34b16ee500615cd325f8b84099f83c1ebecaca67977c5dc9b71ae32ceaf18207f996b0a9725b901d3792689b2babcb60febe3b81a684d9b56b65f67f307d453d"
  ]
}
```

## list-assets

Returns the list of all available assets.

#### Parameters

none

#### Returns

- `Array of Object`, asset array.
  - `String` - *id*, asset id.
  - `String` - *alias*, name of the asset.
  - `String` - *issuance_program*, control program of the issuance of asset.
  - `Integer` - *key_index*, index of key for xpub.
  - `Integer` - *quorum*, threshold of keys that must sign a transaction to spend asset units controlled by the account.
  - `Array of Object` - *xpubs*, pubkey array.
  - `String` - *type*, type of asset.
  - `Integer` - *vm_version*, version of VM.
  - `String` - *raw_definition_byte*, byte of asset definition.
  - `Object` - *definition*, description of asset.

#### Example

```js
const keyPromise = client.assets.listAll()
var sync = keyPromise.then((res) => console.log(res)) 
```

```json
// Result
[
  {
    "alias": "BTM",
    "definition": {
      "decimals": 8,
      "description": "Bytom Official Issue",
      "name": "BTM",
      "symbol": "BTM"
    },
    "id": "ffffffffffffffffffffffffffffffffffffffffffffffffffffffffffffffff",
    "issue_program": "",
    "key_index": 0,
    "quorum": 0,
    "raw_definition_byte": "7b0a202022646563696d616c73223a20382c0a2020226465736372697074696f6e223a20224279746f6d204f6666696369616c204973737565222c0a2020226e616d65223a202262746d222c0a20202273796d626f6c223a202262746d220a7d",
    "type": "internal",
    "vm_version": 1,
    "xpubs": null
  },
  {
    "alias": "SILVER",
    "definition": null,
    "id": "50ec80b6bc48073f6aa8fa045131a71213c33f3681203b15ddc2e4b81f1f4730",
    "issue_program": "ae2029cd61d9ef31d40af7541f9a50831d6317fdb0870249d0564fcfa9a8f843589c5151ad",
    "key_index": 1,
    "quorum": 1,
    "raw_definition_byte": "",
    "type": "asset",
    "vm_version": 1,
    "xpubs": [
      "34b16ee500615cd325f8b84099f83c1ebecaca67977c5dc9b71ae32ceaf18207f996b0a9725b901d3792689b2babcb60febe3b81a684d9b56b65f67f307d453d"
    ]
  }
]
```

## update-asset-alias

Update asset alias by assetID.

#### Parameters

- `String` - *id*, id of asset.
- `String` - *alias*, new alias of asset.

#### Returns

none if the asset alias is updated success.

#### Example

```js
const keyPromise = client.assets.updateAlias({
    id:'57ba2e10543e35f682d4e47729da3c6da0372a94b4c6d04fe59bd389e2e68edc',
    alias:'NEW_GOLD'
    })
var sync = keyPromise.then((res) => console.log(res)) const keyPromise =
```

```json
$ node test.js
//response
//none
```

## list-balances

Returns the list of all available account balances.

#### Parameters

none

#### Returns

- `Array of Object`
    - `String` - *account_id*, account id.
    - `String` - *account_alias*, name of account.
    - `String` - *asset_id*, asset id.
    - `String` - *asset_alias*, name of asset.
    - `Integer` - *amount*, specified asset balance of account.

#### Example

list all the available account balances.

```js
const keyPromise = client.balances.listAll()
var sync = keyPromise.then((res) => console.log(res)) 
```

```js
$ node test.js
//response
[
    {
      "account_alias": "default",
      "account_id": "0BDQ9AP100A02",
      "amount": 35508000000000,
      "asset_alias": "BTM",
      "asset_id": "ffffffffffffffffffffffffffffffffffffffffffffffffffffffffffffffff"
    },
    {
      "account_alias": "alice",
      "account_id": "0BDQARM800A04",
      "amount": 60000000000,
      "asset_alias": "BTM",
      "asset_id": "ffffffffffffffffffffffffffffffffffffffffffffffffffffffffffffffff"
    }
]
```

## list-unspent-outputs

Returns the sub list of all available unspent outputs for all accounts in your wallet.

#### Parameters

- `String` - *id* , id of unspent output.

#### Returns

- `Array of Object`, unspent output array.
    - `String` - *account_id*, account id.
    - `String` - *account_alias*, name of account.
    - `String` - *asset_id*, asset id.
    - `String` - *asset_alias*, name of asset.
    - `Integer` - *amount*, specified asset balance of account.
    - `String` - *address*, address of account.
    - `Boolean` - *change*, whether the account address is change.
    - `String` - *id*, unspent output id.
    - `String` - *program*, program of account.
    - `String` - *control_program_index*, index of program.
    - `String` - *source_id*, source unspent output id.
    - `String` - *source_pos*, position of source unspent output id in block.
    - `String` - *valid_height*, valid height.

#### Example

list all the available unspent outputs:
```js
const keyPromise = client.unspentOutputs.listAll()
var sync = keyPromise.then((res) => console.log(res)) 
```

```json
$ node test.js
//response
[
  {
    "account_alias": "alice",
    "account_id": "0BKBR6VR00A06",
    "address": "bm1qv3htuvug7qdv46ywcvvzytrwrsyg0swltfa0dm",
    "amount": 2000,
    "asset_alias": "GOLD",
    "asset_id": "1883cce6aab82cf9af8cd085a3115dd4a92cdb8e6a9152acd73d7ae4adb9030a",
    "change": false,
    "control_program_index": 2,
    "id": "58f29f0f85f7bd2a91088bcbe536dee41cd0642dfb1480d3a88589bdbfd642d9",
    "program": "0014646ebe3388f01acae88ec318222c6e1c0887c1df",
    "source_id": "5988c1630c1f325e69bb92cb4b19af14286aa107311bc64b8f1a54629a33e0f4",
    "source_pos": 2,
    "valid_height": 0
  },
  {
    "account_alias": "default",
    "account_id": "0BKBR2D2G0A02",
    "address": "bm1qx7ylnhszg24995d5e0nftu9e87kt9vnxcn633r",
    "amount": 624000000000,
    "asset_alias": "BTM",
    "asset_id": "ffffffffffffffffffffffffffffffffffffffffffffffffffffffffffffffff",
    "change": false,
    "control_program_index": 12,
    "id": "5af9d3c9b69470983377c1fc0c9125c4ac3bfd32c8d505f2a6042aade8503bc9",
    "program": "00143789f9de0242aa52d1b4cbe695f0b93facb2b266",
    "source_id": "233d1dd49e591980f98e11f333c6c28a867e78448e272011f045131df5aa260b",
    "source_pos": 0,
    "valid_height": 12
  }
]
```
list the unspent output matching the given id:
```js
const keyPromise = client.unspentOutputs.list({
    id:'58f29f0f85f7bd2a91088bcbe536dee41cd0642dfb1480d3a88589bdbfd642d9'
})
var sync = keyPromise.then((res) => console.log(res)) 
```
```json
$ node test.js
//response
{
  "account_alias": "alice",
  "account_id": "0BKBR6VR00A06",
  "address": "bm1qv3htuvug7qdv46ywcvvzytrwrsyg0swltfa0dm",
  "amount": 2000,
  "asset_alias": "GOLD",
  "asset_id": "1883cce6aab82cf9af8cd085a3115dd4a92cdb8e6a9152acd73d7ae4adb9030a",
  "change": false,
  "control_program_index": 2,
  "id": "58f29f0f85f7bd2a91088bcbe536dee41cd0642dfb1480d3a88589bdbfd642d9",
  "program": "0014646ebe3388f01acae88ec318222c6e1c0887c1df",
  "source_id": "5988c1630c1f325e69bb92cb4b19af14286aa107311bc64b8f1a54629a33e0f4",
  "source_pos": 2,
  "valid_height": 0
}
```