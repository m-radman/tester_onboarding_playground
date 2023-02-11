# Part 3: Typescript Intro

## GitHub Repo → [`typescript-playground`](https://github.com/ivaaaa/typescript-playground)

### Reading list

- 5min read [https://www.typescriptlang.org/docs/handbook/typescript-in-5-minutes.html](https://www.typescriptlang.org/docs/handbook/typescript-in-5-minutes.html) to get an idea what TS is

    - 📌 instructions on how to setup / install → 5 min read [https://www.typescriptlang.org/docs/handbook/typescript-tooling-in-5-minutes.html](https://www.typescriptlang.org/docs/handbook/typescript-tooling-in-5-minutes.html)

    - 📌 tsconfig.json reference [https://www.typescriptlang.org/docs/handbook/tsconfig-json.html](https://www.typescriptlang.org/docs/handbook/tsconfig-json.html)

    - 📌 typescript compiler `tsc` CLI → docs here [https://www.typescriptlang.org/docs/handbook/compiler-options.html](https://www.typescriptlang.org/docs/handbook/compiler-options.html)

    - 📌 EcmaScript browser compatibility matrix [https://kangax.github.io/compat-table/es6/](https://kangax.github.io/compat-table/es6/)

## Three ways to run same program

### One: Run Javascript with node

```bash
node milos.js
```

- run `.js` on `node`**is equal to**
- compile (transpile) `.ts` to `.js` with `tsc` (`tsc` typescript compiler)
- run `.js` on `node`
:point_down:

### Two: Compile Typescript to Javascript then Run Javascript with node

```bash
npm install -g typescript
tsc iva.ts
node iva.js
```

- compile (transpile) `.ts` to `.js` with `tsc` (`tsc` typescript compiler)
- run `.js` on `node` **is equal to**
- run `.ts` in `ts-node` (`ts-node` being node env that transpiles ts to js in runtime / on the fly, during program’s execution) :point_down:

### Three: Run Typescript with ts-node

```bash
npm install -g ts-node
ts-node iva.ts
```

## What is REPL (Read Evaluate Print Loop) ?

- 📌 `node` is _JavaScript REPL_ → [https://nodejs.dev/en/learn/how-to-use-the-nodejs-repl/](https://nodejs.dev/en/learn/how-to-use-the-nodejs-repl/)
… same way `ts-node` is TypeScript REPL

- 📌 `ts-node` is _TypeScript REPL_ for node.js → see here https://github.com/TypeStrong/ts-node


---
:point_left: [go back to main page](../README.md)