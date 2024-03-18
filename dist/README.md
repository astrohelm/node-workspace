# How to setup workspace with builder

> [!TIP]
>
> In this example we will create workspace for frontend / backend library;
> This library would be accessible from any browser & nodejs.


## Install rollup:

Also we install here dependency for rollup that will transliterate our commonjs modules to esm.


```bash
  npm i -D rollup @rollup/plugin-commonjs
```

## Creating gateway file:

> [!IMPORTANT]
>
> Before we will create our config - i want to create special file for exports regulation.
> You can skip this step and fill input with your **entry point** javascript file.

```js
// ./dist/exports.js
'use strict';

const exp = {
  module1: require('./path/to/module1.js'),
  module2: require('./path/to/module2.js'),
}

module.exports = exp;
module.exports.default = exp; // For default export
```

## Writing rollup configuration:

> [!IMPORTANT]
>
> Use you own rollup configuration, this configuration should be only your entry point configuration.
> This configuration used to create cross-platform **(browser / nodejs)** libraries.

```js
// ./dist/rollup.config.js
'use strict';

module.exports = {
  input: ['./dist/exports.js'], // Our entry point
  output: {
    file: './dist/index.js',
    format: 'es',
  },
  plugins: [[require('@rollup/plugin-commonjs')()]],
};
```

## Finish moves:

> [!IMPORTANT]
>
> Add build script to your **package.json** file and enjoy.

```json
{
  // package.json
  // ...
  "scripts": {
    "build": "rollup -c ./dist/rollup.config.js",
    //...
  }
}
```

### Result / Testing

> [!IMPORTANT]
>
> If you done all correctly - all should be working.
> You can test it with next bash script:

```bash
  npm run build
  # Check ./dist folder for results
  ls ./dist
  # You will see index.js
  cat ./dist/index.js
  # Your code
  # ...
  # export { exports as default, module1, module2 }
```

### Optional

> [!IMPORTANT]
>
> If you do all steps with me and want browser support -
> You can add browser exports to your **package.json**.

```json
{
  // package.json
  // ...
  "browser": {
    "./index.js": "./dist/index.js",
    //...
  }
}
```
