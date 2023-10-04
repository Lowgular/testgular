---
sidebar_position: 1
---

# Testgular Intro

Let's discover **Testgular in less than 5 minutes**.

## Getting Started

Get started by **creating a new project**.

### What you'll need

- [Node.js](https://nodejs.org/en/download/) version 16.14 or above:
  - When installing Node.js, you are recommended to check all checkboxes related to dependencies.

## Installation

You can install testgular using the following command:

```bash
npm install @lowgular/testgular
```

You can type this command into Command Prompt, Powershell, Terminal, or any other integrated terminal of your code editor.

The command also installs all necessary dependencies you need to run Testgular.

## TS Setup

Underneath the Testgular is using playwright which by default does not support the Typescript decorators and if we wanna write our tests just like in Angular, we must have this feature enabled.

In order to do so, make sure to check where in your typescript configuration file is the `outputDir` folder.

Here is an example of simplified `tsconfig.spec.ts` file:

```
{
  "extends": "./tsconfig.json",
  "compilerOptions": {
    "outDir": "./RELATIVE_PATH_TO_DIR_FOLDER",
    "emitDecoratorMetadata": true,
    "experimentalDecorators": true,
    "types": [
      "node",
    ]
  },
  "include": [
    "src/**/*.spec.ts",
    "src/**/*.d.ts"
  ]
}
```

Replace `RELATIVE_PATH_TO_DIR_FOLDER` with your path.

Now we need to be able to run our tests using this configuration. In order to do so, let's add a few things to the `package.json` file:

```
{
  "name": "testgular-showcases",
  "version": "0.0.1",
  "license": "MIT",
  "scripts": {
    "pretest": "tsc --incremental -p ./tsconfig.spec.json",
    "test": "playwright test -c ./RELATIVE_PATH_TO_DIR_FOLDER/src"
  },
  "dependencies": {
    "@lowgular/testgular": "^0.0.2",
    "tslib": "^2.3.0"
  },
}
```

This allows us to build typescript app using custom config and then run playwright test on these files