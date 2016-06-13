## Setup

```bash
# Official packaging of Jasmine's core files for use by Node.js projects
npm install jasmine-core --save-dev --save-exact
```

## Prepare for TypeScript

We need to compile our TypeScript test files as we do our TypeScript application files.

We first have to tell the compiler how to compile our TypeScript files with a **tsconfig.json**.

```json
{
  "compilerOptions": {
    "target": "es5",
    "module": "system",
    "moduleResolution": "node",
    "sourceMap": true,
    "emitDecoratorMetadata": true,
    "experimentalDecorators": true,
    "removeComments": false,
    "noImplicitAny": true,
    "suppressImplicitAnyIndexErrors": true
  }
}
```

## Compile and Run

Compile in the terminal window using the npm script command

```bash
npm run tsc
```