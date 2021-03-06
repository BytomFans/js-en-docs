---
id: message
title: Message API
sidebar_label: Bytom.Message.API
---

## sign-message

Sign a message with the key password(decode encrypted private key) of an address.

#### Parameters

- `String` - *address*, address for account.
- `String` - *message*, message for signature by address xpub.
- `String` - *password*, password of account.

#### Returns

- `String` - *derived_xpub*, derived xpub.
- `String` - *signature*, signature of message.

#### Example
```js
const keyPromise = client.status.signMessage({
    address:'bm1qkr80p0d7v4guvtan0xf4j0c7cnvq2yukd43ynj', 
    message:'this is a test message', 
    password:'123456'
})
var sync = keyPromise.then((res) => console.log(res)) 
```
```js
$node test.js
//response
{
  "signature": "74da3d6572233736e3a439166719244dab57dd0047f8751b1efa2da26eeab251d915c1211dcad77e8b013267b86d96e91ae67ff0be520ef4ec326e911410b609",
  "derived_xpub": "6ff8c3d1321ce39a3c3550f57ba70b67dcbcef821e9b85f6150edb7f2f3f91009e67f3075e6e76ed5f657ee4b1a5f4749b7a8c74c8e7e6a1b0e5918ebd5df4d0"
}
```

##  verify-message

Verify a signed message with derived pubkey of the address.

#### Parameters


- `String` - *address*, address for account.
- `String` - *derived_xpub*, derived xpub.
- `String` - *message*, message for signature by derived_xpub.
- `String` - *signature*, signature for message.

#### Returns

`Object`:

- `Boolean` - *result*, verify result.

#### Example
```js
const keyPromise = client.status.verifyMessage({
    address:'bm1qx2qgvvjz734ur8x5lpfdtlau74aaa5djs0a5jn', 
    derived_xpub:'6ff8c3d1321ce39a3c3550f57ba70b67dcbcef821e9b85f6150edb7f2f3f91009e67f3075e6e76ed5f657ee4b1a5f4749b7a8c74c8e7e6a1b0e5918ebd5df4d0', 
    message:'this is a test message', 
    signature:'74da3d6572233736e3a439166719244dab57dd0047f8751b1efa2da26eeab251d915c1211dcad77e8b013267b86d96e91ae67ff0be520ef4ec326e911410b609'
})
var sync = keyPromise.then((res) => console.log(res)) 
```
```js
$node test.js
//response
{
  "result": true
}
```