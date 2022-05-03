# Ramda Typed Any

## Table of Contents

1. [What is this?](#what-is-this?)
1. [Why would this be useful?](#why-would-this-be-useful?)
1. [How do I use this?](#how-do-i-use-this)

## What is this?

This is a fork of `@types/ramda` where all ramda functions have been replaced with the "AnyFn".
```
  export type AnyFn = (...args: any[]) => any;
```
## Why would this be useful?
Ramda is notoriously painful to use with typescript, mainly because each function has so many overloads that typescript doesn't account for.

**E.g.** The code below would throw a typescript error as typescript doesn't expect `inc` to work with string representations of numbers - even though it can!
```
inc('45') // output 46
```

The `AnyFn` turns each Ramda function into a typescript type that says "I'm a function that can take any number of parameters and return anything".

This prevents all clashes with typescript, while still providing helpful type function definitions.

## How do I use this?
1. In the `src` directory of your project, create a new folder called `types`.
2. Inside of `types`, create a new folder called `ramda`.
3. Copy and paste the above `index.d.ts` file into the `ramda` folder.
4. _Optional_ - If the types don't appear immediately, add the location of your new type folder, along with `"node_modules/@types"` to your `tsconfig.json`
```{
  "compilerOptions": {
    //...other properties
    "typeRoots": [
      "src/types",
      "node_modules/@types"
    ]
  }}
  ```

  ### End Result
  Your directory structure should look like this:
  ```
 .
├── src/
│   ├── types/
│   │   └── ramda/
│   │       └── index.d.ts
│   └── ...other files       
├── tsconfig.json
└── ...other files 
```