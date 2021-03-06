# Metarhia script loader, node.js vm wrapper

[![CI Status](https://github.com/metarhia/metavm/workflows/Testing%20CI/badge.svg)](https://github.com/metarhia/metavm/actions?query=workflow%3A%22Testing+CI%22+branch%3Amaster)
[![NPM Version](https://badge.fury.io/js/metavm.svg)](https://badge.fury.io/js/metavm)
[![NPM Downloads/Month](https://img.shields.io/npm/dm/metavm.svg)](https://www.npmjs.com/package/metavm)
[![NPM Downloads](https://img.shields.io/npm/dt/metavm.svg)](https://www.npmjs.com/package/metavm)

## Create script from string

Script contains object expression. You can use it for configs, network packets,
serialization format, etc.
```js
const metavm = require('metavm');

const src = `({ field: 'value' });`;
const ms = metavm.createScript('Example', src);
console.log(ms);

// Output:
//   MetaScript {
//     name: 'Example',
//     script: Script {},
//     context: {},
//     exports: { field: 'value' }
//   }
```

Script contains function expression. You can use it for api endpoints, domain
logic stored in files or database, etc.
```js
const metavm = require('metavm');

const src = `(a, b) => a + b;`;
const ms = metavm.createScript('Example', src);
console.log(ms);

// Output:
//   MetaScript {
//     name: 'Example',
//     script: Script {},
//     context: {},
//     exports: [Function]
//   }
```

## Read script from file

```js
const metavm = require('.');

(async () => {
  const ms = await metavm.readScript('./test/examples/simple.js');
  console.log(ms);
})();

// Output:
//   MetaScript {
//     name: 'simple',
//     script: Script {},
//     context: {},
//     exports: { field: 'value', add: [Function: add], sub: [Function: sub] }
//   }
```
