# TypeScript Guide - TypeScript Setup and Configuration
Quick Links: [ReadMe](../README.md) | [Table of Contents](./docs/00-index.md)

---

## TypeScript Setup and Configuration

### Install the TypeScript Compiler

```sh
> npm install -g typescript
```

### The TypeScript Compiler

#### Transpile TypeScript into JavaScript

To transpile TypeScript code into JavaScript code use TypeScript Compiler command `tsc` and the name of the TypeScript file:

```sh
> tsc index.ts
```

#### Running the compiler in watch mode

```ts
> tsc index.ts --watch
```
or

```ts
> tsc index.ts -w
```

#### Compiling the entire project / multiple files

```ts
tsc --init
```

Initializes a TypeScript project and creates a tsconfig.json file.

### tsconfig Options

Take a look at the references section for a reference to the complete list of options.

#### Including and Excluding Files

you can add an `include` and `exclude` key in the config file which will include or exclude files. These options will be arrays of paths to files which you want to include / exclude.

If you add the `include` option, you MUST add all files you want to compile.

```json
  "exclude": [
    "analytics.ts", // exclude a single file
    "*.dev.ts", // exclude all files that have the .dev.ts ending
    "**/*.dev.ts" // any file in any folder with that pattern
    "node_modules" // do not need to do this, it is excluded by default
  ],
  "include": [
    "app.ts", // compile a single file
  ],
```

There is also a `files` options you can use instead of include but there you can only specify files and not whole folders.

#### Setting a Compilation Target

`target` tells TypeScript which version of JavaScipt you want to compile the code.

#### Module

> **[HOLD]**
#### Core Libs

TypeScript includes a default set of type definitions for built-in JS APIs (like Math), as well as type definitions for things found in browser environments (like document). TypeScript also includes APIs for newer JS features matching the target you specify; for example the definition for Map is available if target is ES6 or newer.

#### Source Maps

Source Maps are super useful for debugging.

Enables the generation of sourcemap files. These files allow debuggers and other tools to display the original TypeScript source code when actually working with the emitted JavaScript files.

#### rootDir and outDir

`rootDir` basically specifies the source folder for your project (i.e. `./src`)

`outDir` basically specifies a folder where the compiled files should be placed (i.e. `./dist`)


### References

 - [compiler options](https://www.typescriptlang.org/docs/handbook/compiler-options.html)
 - [tsconfig](https://www.typescriptlang.org/tsconfig)

 - [https://www.udemy.com/course/understanding-typescript](https://www.udemy.com/course/understanding-typescript)