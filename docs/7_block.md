---
id: block
title: Block API
sidebar_label: Bytom.Block.API
---

## get-block-count

Returns the current block height for blockchain.

#### Parameters

none

#### Returns

- `Integer` - *block_count*, recent block height of the blockchain.

#### Example
```js
const keyPromise = client.block.getBlockCount()
var sync = keyPromise.then((res) => console.log(res)) 
```
```js
$ node test.js
//response
{ block_count: 217520 }
```

## get-block-hash

Returns the current block hash for blockchain.

#### Parameters

none

#### Returns

- `String` - *block_hash*, recent block hash of the blockchain.

#### Example
```js
const keyPromise = client.block.getBlockHash()
var sync = keyPromise.then((res) => console.log(res)) 
```
```js
$ node test.js
//response
$ node test.js
{ 
    block_hash:'c4f5e0214f5f46f2de4022dfca4976c4c4d0078eb0f434f83ffdd8999648e4df' 
}
```

## get-block

Returns the detail block by block height or block hash.

#### Parameters

`Object`: block_height | block_hash

Optional:

- `String` - *block_hash*, hash of block.
- `Integer` - *block_height*, height of block.

#### Returns

`Object`:

- `String` - *hash*, hash of block.

- `Integer` - *size*, size of block.

- `Integer` - *version*, version of block.

- `Integer` - *height*, height of block.

- `String` - *previous_block_hash*, previous block hash.

- `Integer` - *timestamp*, timestamp of block.

- `Integer` - *nonce*, nonce value.

- `Integer` - *bits*, bits of difficulty.

- `String` - *difficulty*, difficulty value(String type).

- `String` - *transaction_merkle_root*, merkle root of transaction.

- `String` - *transaction_status_hash*, merkle root of transaction status.

- `Array of Object`- * transactions*, transaction object:

  - `String` - *id*, transaction id, hash of the transaction.

  - `Integer` - *version*, version of transaction.

  - `Integer` - *size*, size of transaction.

  - `Integer` - *time_range*, the unix timestamp for when the requst was responsed.

  - `Boolean` - *status_fail*, whether the state of the request has failed.

  - `String` - *mux_id*, the previous transaction mux id(source id of utxo).

  - `Array of Object`- *inputs*, object of inputs for the transaction.

    - `String` - *type*, the type of input action, available option include: 'spend', 'issue', 'coinbase'.
    - `String` - *asset_id*, asset id.
    - `String` - *asset_alias*, name of asset.
    - `Object` - *asset_definition*, definition of asset(json object).
    - `Integer` - *amount*, amount of asset.
    - `Object` - *issuance_program*, issuance program, it only exist when type is 'issue'.
    - `Object` - *control_program*, control program of account, it only exist when type is 'spend'.
    - `String` - *address*, address of account, it only exist when type is 'spend'.
    - `String` - *spent_output_id*, the front of outputID to be spent in this input, it only exist when type is 'spend'.
    - `String` - *account_id*, account id.
    - `String` - *account_alias*, name of account.
    - `Object` - *arbitrary*, arbitrary infomation can be set by miner, it only exist when type is 'coinbase'.

  - `Array of Object` - *outputs* , object of outputs for the transaction.

    - `String` - *type*, the type of output action, available option include: 'retire', 'control'.
    - `String` - *id*, outputid related to utxo.
    - `Integer` - *position*, position of outputs.
    - `String` - *asset_id*, asset id.
    - `String` - *asset_alias*, name of asset.
    - `Object` - *asset_definition*, definition of asset(json object).
    - `Integer` - *amount*, amount of asset.
    - `String` - *account_id*, account id.
    - `String` - *account_alias*, name of account.
    - `Object` - *control_program*, control program of account.
    - `String` - *address*, address of account.

#### Example

get specified block information by block_hash or block_height, if both exists, the block result is querying by hash.

```js
const keyPromise = client.block.getBlock({
    block_height: 217521, 
    block_hash: 'c4f5e0214f5f46f2de4022dfca4976c4c4d0078eb0f434f83ffdd8999648e4df'
})
var sync = keyPromise.then((res) => console.log(res)) 
```
```js
$ node test.js
//response
{ 
  hash:'c4f5e0214f5f46f2de4022dfca4976c4c4d0078eb0f434f83ffdd8999648e4df',
  size: 416,
  version: 1,
  height: 217521,
  previous_block_hash:
   '36b6b386ab8a0d31e50f63cd4cc7d1a856c37772e199b4490c58939ceb66d9cf',
  timestamp: 1555574169,
  nonce: 936937894344669600,
  bits: 2017612633064242700,
  difficulty: '31878122073',
  transaction_merkle_root:
   '47091250d24330e5b7d5964579600accd792821ae9051a8d10dffe5cc693c290',
  transaction_status_hash:
   'c9c377e5192668bc0a367e4a4764f11e7c725ecced1d7b6a492974fab1b6d5bc',
  transactions:
   [ { id:
        'cc074284c301a97d0c73f1c3081768b9b0ce1e872c99a0c497ef632dc7a47646',
       version: 1,
       size: 82,
       time_range: 0,
       inputs: [Array],
       outputs: [Array],
       status_fail: false,
       mux_id:
        '001f63a7e82991a574c5bdcd09f8cac4a75cd100b3d4b82cb2d87341df66e3b8' } ] 
}
```

## get-block-header

Returns the detail block header by block height or block hash.

#### Parameters

`Object`: block_height | block_hash

Optional:

- `String` - *block_hash*, hash of block.
- `Integer` - *block_height*, height of block.

#### Returns

- `Object` - *block_header*, header of block.
- `Integer` - *reward*, reward.

#### Example
```js
const keyPromise = client.block.getBlockHeader({
    block_height: 217521, 
    block_hash: 'c4f5e0214f5f46f2de4022dfca4976c4c4d0078eb0f434f83ffdd8999648e4df'
})
var sync = keyPromise.then((res) => console.log(res)) 
```
```js
$ node test.js
//response
{
    block_header:
   '0101b1a30d36b6b386ab8a0d31e50f63cd4cc7d1a856c37772e199b4490c58939ceb66d9cf99
dbe0e5054047091250d24330e5b7d5964579600accd792821ae9051a8d10dffe5cc693c290c9c377
e5192668bc0a367e4a4764f11e7c725ecced1d7b6a492974fab1b6d5bc85f39088d081ab800db9fb
8981808080801c',
  reward: 41250000000 
}

```

## get-difficulty

Returns the block difficulty by block height or block hash.

#### Parameters

- `String` - *block_hash*, hash of block.
- `Integer` - *block_height*, height of block.

#### Returns

- `Integer` - *bits*, bits of block.
- `String` - *difficulty*, difficulty of block.
- `String` - *hash*, block hash.
- `Integer` - *height*, block height.

#### Example

Get difficulty for specified block hash / height.
```js
const keyPromise = client.block.getDifficulty({
    block_height: 217521, 
    block_hash: 'c4f5e0214f5f46f2de4022dfca4976c4c4d0078eb0f434f83ffdd8999648e4df'
})
var sync = keyPromise.then((res) => console.log(res)) 
```
```js
$ node test.js
//response
{ 
   hash:
   'c4f5e0214f5f46f2de4022dfca4976c4c4d0078eb0f434f83ffdd8999648e4df',
  height: 217521,
  bits: 2017612633064242700,
  difficulty: '31878122073' 
}
```

## get-hash-rate

Returns the block hash rate by block height or block hash, it returns the current block hash rate when request is empty.

#### Parameters

- `String` - *block_hash*, hash of block.
- `Integer` - *block_height*, height of block.

#### Returns

- `Integer` - *hash_rate*, difficulty of block.
- `String` - *hash*, block hash.
- `Integer` - *height*, block height.

#### Example

Get hash rate for specified block hash / height.

```js
const keyPromise = client.block.getHashRate({
    block_height: 217521, 
    block_hash: 'c4f5e0214f5f46f2de4022dfca4976c4c4d0078eb0f434f83ffdd8999648e4df'
})
var sync = keyPromise.then((res) => console.log(res)) 
```
```js
$ node test.js
//response
{ 
  hash:
   'c4f5e0214f5f46f2de4022dfca4976c4c4d0078eb0f434f83ffdd8999648e4df',
  height: 217521,
  hash_rate: 203045363 
}


```

