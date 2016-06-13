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
  },
  "files": ["src/**/*.ts"]
}
```

## Compile and Run

Compile in the terminal window using the npm script command

```bash
tsc
```

Every test file should have at least one describe that identifies the file holding the test(s).

## Debug the test

Open the browser’s “Developer Tools” (F12 or Ctrl-Shift-I).

- Pick the “sources” section
- Open the 1st.spec.ts test file (Ctrl-P, then start typing the name of the file).
- Set a breakpoint on the second line of the failing test

