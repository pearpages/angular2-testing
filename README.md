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

## Load tests with SystemJS

Our test environment lacks support for module loading. Apparently we can't simply load our application and test scripts like we do with 3rd party JavaScript libraries.

We add module loading support in four steps:

1. add the SystemJS module management library
2. configure SystemJS to look for JavaScript files by default
3. import our test files
4. tell Jasmine to run the imported tests

```html
<body>
  <!-- #1. add the system.js library -->
  <script src="../node_modules/systemjs/dist/system.src.js"></script>

  <script>
    // #2. Configure systemjs to use the .js extension
    //     for imports from the app folder
    System.config({
      packages: {
        'app': {defaultExtension: 'js'}
      }
    });

    // #3. Import the spec file explicitly
    System.import('app/hero.spec')

      // #4. wait for all imports to load ...
      //     then re-execute `window.onload` which
      //     triggers the Jasmine test-runner start
      //     or explain what went wrong.
      .then(window.onload)
      .catch(console.error.bind(console));
  </script>
</body>
```

