<h1 align="center"><img alt="openapi-client-axios" src="https://github.com/anttiviljami/openapi-client-axios/raw/master/header.png?raw=true" style="max-width:50rem"></h1>

[![CI](https://github.com/anttiviljami/openapi-client-axios/workflows/CI/badge.svg)](https://github.com/anttiviljami/openapi-client-axios/actions?query=workflow%3ACI)
[![npm version](https://img.shields.io/npm/v/openapi-client-axios.svg)](https://www.npmjs.com/package/openapi-client-axios)
[![npm downloads](https://img.shields.io/npm/dw/openapi-client-axios)](https://www.npmjs.com/package/openapi-client-axios)
[![bundle size](https://img.shields.io/bundlephobia/minzip/openapi-client-axios?label=gzip%20bundle)](https://bundlephobia.com/package/openapi-client-axios)
[![License](http://img.shields.io/:license-mit-blue.svg)](https://github.com/anttiviljami/openapi-client-axios/blob/master/LICENSE)
[![Buy me a coffee](https://img.shields.io/badge/donate-buy%20me%20a%20coffee-orange)](https://buymeacoff.ee/anttiviljami)

<p align="center">JavaScript client library for consuming OpenAPI-enabled APIs with <a href="https://github.com/axios/axios" target="_blank">axios</a>. Types included.</p>

## Features

- [x] Create API clients from [OpenAPI v3 definitions](https://github.com/OAI/OpenAPI-Specification)
- [x] Client is configured in runtime. **No generated code!**
- [x] Generate TypeScript definitions (.d.ts) for your APIs with full IntelliSense support
- [x] Easy to use API to call API operations using JavaScript methods
  - `client.getPet(1)`
  - `client.searchPets()`
  - `client.searchPets({ ids: [1, 2, 3] })`
  - `client.updatePet(1, payload)`
- [x] Built on top of the robust [axios](https://github.com/axios/axios) JavaScript library
- [x] Isomorphic, works both in browser and Node.js

## Documentation

**New!** OpenAPI Client Axios documentation is now found on [openapistack.co](https://openapistack.co)

https://openapistack.co/docs/openapi-client-axios/intro

## Quick Start

```
npm install --save axios openapi-client-axios
```

```
yarn add axios openapi-client-axios
```

With promises / CommonJS syntax:

```javascript
const OpenAPIClientAxios = require('openapi-client-axios').default;

const api = new OpenAPIClientAxios({ definition: 'https://example.com/api/openapi.json' });
api.init()
  .then(client => client.getPetById(1))
  .then(res => console.log('Here is pet id:1 from the api', res.data));
```

With async-await / ES6 syntax:

```javascript
import OpenAPIClientAxios from 'openapi-client-axios';

const api = new OpenAPIClientAxios({ definition: 'https://example.com/api/openapi.json' });
api.init();

async function createPet() {
  const client = await api.getClient();
  const res = await client.createPet(null, { name: 'Garfield' });
  console.log('Pet created', res.data);
}
```

## Type safe clients

![TypeScript IntelliSense](https://github.com/anttiviljami/openapi-client-axios/blob/master/packages/typegen/intellisense.gif)

`openapi-client-axios` comes with a tool called `typegen` to generate typescript type files (.d.ts) for
OpenAPIClient instances using an OpenAPI definition file.

```
npx openapi-client-axios-typegen ./openapi.yaml > src/types/openapi.d.ts
```

The output file exports a type `Client`, which can directly be used with instances created with `OpenAPIClientAxios`.

```typescript
import { Client as PetStoreClient } from './openapi.d.ts';

const client = await api.getClient<PetStoreClient>();
```

## Contributing

OpenAPI Client Axios is Free and Open Source Software. Issues and pull requests are more than welcome!
