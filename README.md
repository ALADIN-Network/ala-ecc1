[![NPM](https://img.shields.io/npm/v/alaexplorerjs-ecc-v1.6.1.svg)](https://www.npmjs.org/package/alaexplorerjs-ecc-v1.6.1)
[![Build Status](https://travis-ci.org/ALAIO/alaexplorerjs-ecc-v1.6.1.svg?branch=master)](https://travis-ci.org/ALAIO/alaexplorerjs-ecc-v1.6.1)

# Elliptic curve cryptography functions (ECC)

Private Key, Public Key, Signature, AES, Encryption / Decryption

# Import

```js
import ecc from 'alaexplorerjs-ecc-v1.6.1'
// or
const ecc = require('alaexplorerjs-ecc-v1.6.1')
```

# Common API

<!-- Generated by documentation.js. Update this documentation by updating the source code. -->

## wif

[Wallet Import Format](https://en.bitcoin.it/wiki/Wallet_import_format)

Type: [string](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/String)

## ecc

### randomKey

**Parameters**

-   `cpuEntropyBits` **[number](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Number)** gather additional entropy
    from a CPU mining algorithm.  Set to 0 for testing. (optional, default `128`)

**Examples**

```javascript
ecc.randomKey()
```

Returns **[wif](#wif)** 

### seedPrivate

**Parameters**

-   `seed` **[string](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/String)** any length string.  This is private.  The same
    seed produces the same private key every time.  At least 128 random
    bits should be used to produce a good private key.

**Examples**

```javascript
ecc.seedPrivate('secret') === wif
```

Returns **[wif](#wif)** 

### privateToPublic

**Parameters**

-   `wif` **[wif](#wif)** 

**Examples**

```javascript
ecc.privateToPublic(wif) === pubkey
```

Returns **[pubkey](#pubkey)** 

### isValidPublic

**Parameters**

-   `pubkey` **[pubkey](#pubkey)** like ALAKey..

**Examples**

```javascript
ecc.isValidPublic(pubkey) === true
```

Returns **[boolean](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Boolean)** valid

### isValidPrivate

**Parameters**

-   `wif` **[wif](#wif)** 

**Examples**

```javascript
ecc.isValidPrivate(wif) === true
```

Returns **[boolean](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Boolean)** valid

### sign

Create a signature using data or a hash.

**Parameters**

-   `data` **([string](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/String) \| [Buffer](https://nodejs.org/api/buffer.html))** 
-   `privateKey` **([wif](#wif) | PrivateKey)** 
-   `hashData` **[boolean](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Boolean)** sha256 hash data before signing (optional, default `true`)

**Examples**

```javascript
ecc.sign('I am alive', wif)
```

Returns **[string](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/String)** hex signature

### verify

Verify signed data.

**Parameters**

-   `signature` **([string](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/String) \| [Buffer](https://nodejs.org/api/buffer.html))** buffer or hex string
-   `data` **([string](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/String) \| [Buffer](https://nodejs.org/api/buffer.html))** 
-   `pubkey` **([pubkey](#pubkey) | PublicKey)** 
-   `hashData` **[boolean](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Boolean)** sha256 hash data before verify (optional, default `true`)

**Examples**

```javascript
ecc.verify(signature, 'I am alive', pubkey) === true
```

Returns **[boolean](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Boolean)** 

### recover

Recover the public key used to create the signature.

**Parameters**

-   `signature` **[String](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/String)** (hex, etc..)
-   `data` **([String](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/String) \| [Buffer](https://nodejs.org/api/buffer.html))** 
-   `hashData` **[boolean](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Boolean)** sha256 hash data before recover (optional, default `true`)

**Examples**

```javascript
ecc.recover(signature, 'I am alive') === pubkey
```

Returns **[pubkey](#pubkey)** 

### sha256

**Parameters**

-   `data` **([string](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/String) \| [Buffer](https://nodejs.org/api/buffer.html))** 
-   `encoding` **[string](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/String)** 'hex', 'binary' or 'base64' (optional, default `'hex'`)

**Examples**

```javascript
ecc.sha256('hashme') === '02208b..'
```

Returns **([string](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/String) \| [Buffer](https://nodejs.org/api/buffer.html))** Buffer when encoding is null, or string

## pubkey

ALAKey..

Type: [string](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/String)

# Usage (Object API)

```js
let {PrivateKey, PublicKey, Signature, Aes, key_utils, config} = require('alaexplorerjs-ecc-v1.6.1')

// Create a new random private key
privateWif = PrivateKey.randomKey().toWif()


// Convert to a public key
pubkey = PrivateKey.fromWif(privateWif).toPublic().toString()
```

-   [PrivateKey](./src/key_private.js)
-   [PublicKey](./src/key_public.js)
-   [Signature](./src/signature.js)
-   [Aes](./src/aes.js)
-   [key_utils](./src/key_utils.js)
-   [config](./src/config.js)

# Browser

```bash
git clone https://github.com/ALADIN-Network/alaexplorerjs-ecc-v1.6.1.git
cd alaexplorerjs-ecc-v1.6.1
npm install
npm run build
# builds: ./dist/alaexplorerjs-ecc-v1.6.1.js
# Verify release hash
```

```html
<script src=alaexplorerjs-ecc-v1.6.1.js></script>
```

```js
var ecc = alaexplorerjs_ecc
var privateWif = ecc.randomKey()
var pubkey = ecc.privateToPublic(privateWif)
console.log(pubkey)
```

# Configure

```js
const {config} = require('alaexplorerjs-ecc-v1.6.1')

// Change the public key address prefix
// config.address_prefix = 'XXX'
```

See [Config](./src/config.js)