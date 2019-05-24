---
id: decode_program
title: Decode_program API
sidebar_label: Bytom.Decode_program.API
---

## decode-program

Decode program. 

#### Parameters

- `String` - *program*, program for account.

#### Returns

`Object`:

- `String` - *instructions*, instructions and data for program.

#### Example
```js
const keyPromise = client.status.decodeProgram({
    program:'0014a86c83ee12e6d790fb388345cc2e2b87056a0773'
})
var sync = keyPromise.then((res) => console.log(res)) 
```
```js
$ node test.js
//response
{ instructions:
   'DUP \nHASH160 \nDATA_20 a86c83ee12e6d790fb388345cc2e2b87056a0773\nEQUALVERIF
Y \nTXSIGHASH \nSWAP \nCHECKSIG \n' }

```

