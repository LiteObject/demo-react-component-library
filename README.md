# React Component

## Initialize project

    npm init -y

## Install dev dependencies

    npm i -D @types/node @types/react @types/react-dom react react-dom typescript source-map-loader

## Add TypeScript config

    npx tsc --init

---

## Unit Test using Jest

### Install necessary packages

    npm i jest @types/jest ts-jest typescript -D

-   Install jest framework (jest)
-   Install the types for jest (@types/jest)
-   Install the TypeScript preprocessor for jest (ts-jest) which allows jest to transpile TypeScript on the fly and have source-map support built in.
-   Install the TypeScript compiler ('typescript') which is prerequisite for 'ts-jest'.
-   Save all of these to your dev dependencies (testing is almost always a npm dev-dependency)

### Update `tsconfig.json`

You may need to include `@types/jest` in the `types` as shown below.

```json
"compilerOptions": {
    ...,
    "types": ["...", "@types/jest"],
    ....
},
```

### Configure Jest

Either run `jest --init` which creates a `jest.config.js` file with default configuration or manually add the following `jest.config.js` file to the root of your project:

```JavaScript
module.exports = {
  "roots": [
    "<rootDir>/src"
  ],
  "testMatch": [
    "**/__tests__/**/*.+(ts|tsx|js)",
    "**/?(*.)+(spec|test).+(ts|tsx|js)"
  ],
  "transform": {
    "^.+\\.(ts|tsx)$": "ts-jest"
  },
}
```

> If your `package.json` file contains `"type": "module"`, which causes Node to assume modules are in ES6 format, you can convert the above to es6 format by replacing the top line to export default

-   We always recommend having all TypeScript files in a `src` folder in your project. We assume this is true and specify this using the roots option.
-   The `testMatch` config is a glob pattern matcher for discovering .test / .spec files in ts / tsx / js format.
-   The `transform` config just tells jest to use `ts-jest` for ts / tsx files.

### Run tests

Run `npx jest` or `npm test` from your project root and jest will execute any tests you have.

```shell
 PASS  src/foo/foo.test.ts
  √ basic (4 ms)
  √ basic again

Test Suites: 1 passed, 1 total
Tests:       2 passed, 2 total
Snapshots:   0 total
Time:        2.959 s, estimated 3 s
Ran all test suites.
```

---
