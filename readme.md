# @exhumer/import-jsx ![Build Status](https://github.com/eXhumer/import-jsx/workflows/test/badge.svg)

> Import and transpile JSX via [loader hooks](https://nodejs.org/dist/latest-v18.x/docs/api/esm.html#loaders). It doesn't transpile anything besides JSX and caches transpiled sources by default.

## Install

```console
npm install @exhumer/import-jsx
```

## Usage

> **Note**:
> `@exhumer/import-jsx` only works with ES modules.

```sh
node --loader=@exhumer/import-jsx react-example.js
```

**react-example.js**

```jsx
const HelloWorld = () => <h1>Hello world</h1>;
```

## Examples

### React

React is auto-detected by default and `react` will be auto-imported, if it's not already.

```jsx
const HelloWorld = () => <h1>Hello world</h1>;
```

### Preact

If an alternative library is used and exports `createElement`, like Preact, configure `@exhumer/import-jsx` to import it instead of React:

```jsx
/** @jsxImportSource preact */

const HelloWorld = () => <h1>Hello world</h1>;
```

### Any JSX pragma

For libraries not compatible with React's API, but which still support JSX, import it and configure `@exhumer/import-jsx` to use its pragma:

```jsx
/** @jsxRuntime classic */
/** @jsx h */
import h from 'vhtml';

const HelloWorld = () => <h1>Hello world</h1>;
```

### Disable cache

`@exhumer/import-jsx` caches transpiled sources by default, so that the same file is transpiled only once.
If that's not a desired behavior, turn off caching by setting `IMPORT_JSX_CACHE=0` or `IMPORT_JSX_CACHE=false` environment variable.

```console
IMPORT_JSX_CACHE=0 node --loader=@exhumer/import-jsx my-code.js
```
