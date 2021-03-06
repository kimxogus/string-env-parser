# inject-env
> Inject environment variables to string

[![npm version](https://img.shields.io/npm/v/inject-env.svg)](https://npmjs.org/package/inject-env)
[![npm downloads](https://img.shields.io/npm/dm/inject-env.svg)](https://npmjs.org/package/inject-env)


[![Build Status](https://travis-ci.org/kimxogus/inject-env.svg?branch=master)](https://travis-ci.org/kimxogus/inject-env)

## Installation
- npm
```bash
npm install inject-env
```

- yarn
```bash
yarn add inject-env
```

## Usage
```js
import injectEnv from 'inject-env'

const bashProfilePath = injectEnv('${HOME}/.bash_profile');   // /your/home/.bash_profile

const apiURL = injectEnv('${HTTP_PROXY}/api');                // http://proxy.url/api

// Without default value
injectEnv('${NODE_ENV}');             // undefined

// With default value
injectEnv('${NODE_ENV:-development}')  // development

// With default value
injectEnv('${NODE_ENV-development}')   // development if unset

// With substitution value
injectEnv('${NODE_ENV:+development}')  // development if value set

// With substitution value
injectEnv('${NODE_ENV+development}')   // development if set

// Does not work without '{' and '}' characters!
injectEnv('$NODE_ENV');               // $NODE_ENV

injectEnv(['${NODE_ENV}', '${PWD}'])  // [undefined, '/your/pwd']

injectEnv({a: '${NODE_ENV}', b: '${PWD}'}) // {a: undefined, b: '/your/pwd'}
```
