<img src="https://user-images.githubusercontent.com/4631227/191834116-59cf590e-25cc-4956-ae5c-812ea464f324.png" height="100" />

[GitHub](https://github.com/LedgerHQ/ledger-live/),
[Ledger Devs Discord](https://developers.ledger.com/discord-pro),
[Developer Portal](https://developers.ledger.com/)

## @ledgerhq/hw-app-trx

Ledger Hardware Wallet TRX JavaScript bindings.

***

## Are you adding Ledger support to your software wallet?

You may be using this package to communicate with the TRX Nano App.

For a smooth and quick integration:

*   See the developers’ documentation on the [Developer Portal](https://developers.ledger.com/docs/transport/overview/) and
*   Go on [Discord](https://developers.ledger.com/discord-pro/) to chat with developer support and the developer community.

***

## API

<!-- Generated by documentation.js. Update this documentation by updating the source code. -->

#### Table of Contents

*   [Trx](#trx)
    *   [Parameters](#parameters)
    *   [Examples](#examples)
    *   [getAddress](#getaddress)
        *   [Parameters](#parameters-1)
        *   [Examples](#examples-1)
    *   [signTransaction](#signtransaction)
        *   [Parameters](#parameters-2)
        *   [Examples](#examples-2)
    *   [signTransactionHash](#signtransactionhash)
        *   [Parameters](#parameters-3)
        *   [Examples](#examples-3)
    *   [getAppConfiguration](#getappconfiguration)
        *   [Examples](#examples-4)
    *   [signPersonalMessage](#signpersonalmessage)
        *   [Parameters](#parameters-4)
        *   [Examples](#examples-5)
    *   [getECDHPairKey](#getecdhpairkey)
        *   [Parameters](#parameters-5)
        *   [Examples](#examples-6)

### Trx

Tron API

#### Parameters

*   `transport` **Transport** 
*   `scrambleKey`   (optional, default `"TRX"`)

#### Examples

```javascript
import Trx from "@ledgerhq/hw-app-trx";
const trx = new Trx(transport)
```

#### getAddress

get Tron address for a given BIP 32 path.

##### Parameters

*   `path` **[string](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/String)** a path in BIP 32 format
*   `boolDisplay` **[boolean](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/Boolean)?** 

##### Examples

```javascript
const address = await tron.getAddress("44'/195'/0'/0/0").then(o => o.address)
```

Returns **[Promise](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/Promise)<{publicKey: [string](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/String), address: [string](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/String)}>** an object with a publicKey and address

#### signTransaction

sign a Tron transaction with a given BIP 32 path and Token Names

##### Parameters

*   `path` **[string](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/String)** a path in BIP 32 format
*   `rawTxHex` **[string](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/String)** a raw transaction hex string
*   `tokenSignatures` **[Array](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/Array)<[string](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/String)>** Tokens Signatures array

##### Examples

```javascript
const signature = await tron.signTransaction("44'/195'/0'/0/0", "0a02f5942208704dda506d59dceb40f0f4978f802e5a69080112650a2d747970652e676f6f676c65617069732e636f6d2f70726f746f636f6c2e5472616e73666572436f6e747261637412340a1541978dbd103cfe59c35e753d09dd44ae1ae64621c7121541e2ae49db6a70b9b4757d2137a43b69b24a445780188ef8b5ba0470cbb5948f802e", [], 105);
```

Returns **[Promise](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/Promise)<[string](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/String)>** a signature as hex string

#### signTransactionHash

sign a Tron transaction hash with a given BIP 32 path

##### Parameters

*   `path` **[string](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/String)** a path in BIP 32 format
*   `rawTxHashHex` **[string](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/String)** 
*   `rawTxHex`  a raw transaction hex string

##### Examples

```javascript
const signature = await tron.signTransactionHash("44'/195'/0'/0/0", "25b18a55f86afb10e7aca38d0073d04c80397c6636069193953fdefaea0b8369");
```

Returns **[Promise](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/Promise)<[string](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/String)>** a signature as hex string

#### getAppConfiguration

get the version of the Tron app installed on the hardware device

##### Examples

```javascript
const result = await tron.getAppConfiguration();
{
  "version": "0.1.5",
  "versionN": "105".
  "allowData": false,
  "allowContract": false,
  "truncateAddress": false,
  "signByHash": false
}
```

Returns **[Promise](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/Promise)<{allowContract: [boolean](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/Boolean), truncateAddress: [boolean](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/Boolean), allowData: [boolean](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/Boolean), signByHash: [boolean](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/Boolean), version: [string](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/String), versionN: [number](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/Number)}>** an object with a version

#### signPersonalMessage

sign a Tron Message with a given BIP 32 path

##### Parameters

*   `path` **[string](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/String)** a path in BIP 32 format
*   `messageHex` **[string](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/String)** 
*   `message`  hex string to sign

##### Examples

```javascript
const signature = await tron.signPersonalMessage("44'/195'/0'/0/0", "43727970746f436861696e2d54726f6e5352204c6564676572205472616e73616374696f6e73205465737473");
```

Returns **[Promise](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/Promise)<[string](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/String)>** a signature as hex string

#### getECDHPairKey

get Tron address for a given BIP 32 path.

##### Parameters

*   `path` **[string](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/String)** a path in BIP 32 format
*   `publicKey` **[string](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/String)** address public key to generate pair key

##### Examples

```javascript
const signature = await tron.getECDHPairKey("44'/195'/0'/0/0", "04ff21f8e64d3a3c0198edfbb7afdc79be959432e92e2f8a1984bb436a414b8edcec0345aad0c1bf7da04fd036dd7f9f617e30669224283d950fab9dd84831dc83");
```

Returns **[Promise](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/Promise)<[string](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/String)>** shared key hex string,
