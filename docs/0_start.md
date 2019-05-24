---
id: start
title: quick start
sidebar_label: SDK环境配置
---
## Download bytom-js-sdk

 Below we provide two ways to install and use this sdk.Note that the bytom-js-sdk requires node.js and npm.

### Install with Npm

To install the SDK with Node, you will need to be using  [Node](https://nodejs.org/en/download/) 
Then, create a `package.json` file in the project root directory，run:

```bash
npm init
```

Run `install bytom-sdk` to download the SDK and set up the autoloader.

```bash
npm install bytom-sdk
```

And then require it from your project.

```js
var require = require('bytom-sdk')
```

### Install with Git

You can clone down this SDK using your favorite Github client, or via the terminal.

```bash
git clone https://github.com/lxlxw/bytom-php-sdk.git
```

## Usage 

### Usage examples

Here's how to send a message using the SDK:

```js
//Require the SDK
const bytom = require('bytom-sdk')
const url = 'http://localhost:9888'

// Local node, default url is `127.0.0.1:9888`
const accessToken = ''

//Instantiate the SDK Client
const client = new bytom.Client(url, accessToken)

//Now, request bytom api.
const keyPromise = client.keys.create({ 
    alias:'alice', 
    password: '123456'
   })
```

Returns:

```json
{
  "alias": "alice",
  "xpub": "a7dae957c2d35b42efe7e6871cf5a75ebd2a0d0e51caffe767db42d3e6d69dbe211d1ca492ecf05908fe6fa625ad61b3253375ea744c9442dd5551613ba50aea",
  "file": "/Path/To/Library/Bytom/keystore/UTC--2018-04-22T06-30-27.609315219Z--0e34293c-8856-4f5f-b934-37456a3820fa"
}
```

### All usage examples

You find more detailed documentation at [API doc](http://localhost:3000/docs/key)

## Support and Feedback

If you find a bug, please submit the issue in Github directly.
[bytom-node-sdk Issues](https://github.com/Bytom/bytom-node-sdk/issues)

## Contact

- Email：[x@xwlin.com](mailto:x@xwlin.com)


