<h1 align="center">Astrohelm default workspace</h1>

<h2 align="center">Installation guide 🚀</h2>

### First step: workspace installation

You can use this repository as template - otherwise install it manually:

```bash
  # Download repository
  git clone https://github.com/astrohelm/node-workspace
  rm -rf ./path/to/workspace/.git ./path/to/workspace/package-lock.json
  cd ./path/to/workspace/
  # Update node.js (optional)
  nvm install latest
  nvm use latest
  # Update and install dependencies
  ncu -u
  npm i
```

### Second step: Package personalization

Update package json:

- Replace all fields with prefix <code>your-</code>
- Update engines, if current is out of date
- Remove browser field & dist folder, if you don't support it

```js
// package.json
{
  "license": "MIT",
  "version": "0.0.1",
  "type": "commonjs",
  "name": "your-package-name",
  "homepage": "https://astrohelm.ru",
  "description": "your-package-description",
  "author": "your-name <your-mail>",
  "keywords": ["your-keyword #1", "your-keyword #n"],

  "main": "index.js",
  "types": "types/index.d.ts",
  "packageManager": "npm@9.6.4",
  "readmeFilename": "README.md",
  "engines": { "node": ">= 18" },
  "browser": {},
  "files": ["/dist", "/lib", "/types"],

  "scripts": {
    "test": "node --test && tsc",
    "dev": "node index.js",
    "prettier:fix": "prettier --write \"**/*.{js,ts,json,html,cjs,md,yaml}\"",
    "eslint:fix": "eslint --fix \"**/*.{js,ts}\""
  },

  "repository": { "type": "git", "url": "git+https://github.com/astrohelm/your-package-name.git" },
  "bugs": { "url": "https://github.com/astrohelm/your-package-name/issues", "email": "your-mail" },

  "devDependencies": {
    "@types/node": "^18.15.10",
    "eslint": "^8.40.0",
    "eslint-config-astrohelm": "^1.0.0",
    "eslint-config-prettier": "^8.8.0",
    "eslint-plugin-prettier": "^4.2.1",
    "prettier": "^2.8.8",
    "typescript": "^5.0.2"
  }
}
```

### Third step: About files

Go to CHANGELOG.md and update it for your package. _WARNING !_ Don't forget about date (xxxx-xx-xx).

```md
<!-- CHANGELOG.md -->

# Changelog

## [Unreleased][unreleased]

## [0.0.1][] - xxxx-xx-xx

- Stable release version
- Repository created

[unreleased]: https://github.com/astrohelm/your-package-name/compare/v0.0.1...HEAD
[0.0.1]: https://github.com/astrohelm/your-package-name/releases/tag/v0.0.1
```

Update AUTHORS

```md
 <!-- AUTHORS -->

your-name <your-mail>
```

### Almost last step: Update README.md

Replace your README.md with next information and change Your-package-name to actual.

```md
<!-- README.md -->
<h1 align="center">Your-package-name v0.0.1</h1>

<h2 align="center">Initial release 🚀</h2>

<h2 align="center">Copyright & contributors</h2>

<p align="center">
Copyright © 2023 <a href="https://github.com/astrohelm/Your-package-name/graphs/contributors">Astrohelm contributors</a>.
This repository is <a href="./LICENSE">MIT licensed</a>.<br/>
And it is part of <a href="https://github.com/astrohelm">Astrohelm ecosystem</a>.
</p>
```

### Last step: Save results

_WARNING !_ Update this file before moving throw this step.

Create a new package in [organization][https://github.com/astrohelm/] repository. Use next commands
to save you package.

```bash
git init
git remote add origin your-package-location
# Start from here, if you used template
git branch -M main # if your default branch is not main
git commit -am "Repository init"
git tag v0.0.1
git push origin main
git push origin v0.0.1
git checkout -b dev
git push origin dev
```

Return to your organization repository and do:

- Add keywords
- Update description
- Draft release with `v0.0.1` tag and `v0.0.1` as a title and updated README file as description.

> If you want to create library you could publish it to npm with `npm publish` command.

Congratulations, package initialized 🚀

## About files & structure

This workspace have commonjs in use by default. You can switch it in package.json if you want.

- `dist` directory used for fronted package analog. You can use it if your package is
  multi-platform, [readme](./dist/README.md).
- `eslint` astrohelm eslint rules
- `types` .d.ts library types exports
- `CHANGELOG.md` in use for project history documentation
- `Makefile` ultimate commands shortcuts creator
- `tests` here you can put all test coverage of your package
- `.github` github ci pipeline by default
- `lib` folder should contain all you library logic,**_WARNING !_** Remove if you not writing
  library. Replace with **src** folder.

<h2 align="center">Copyright & contributors</h2>

<p align="center">
Copyright © 2023 <a href="https://github.com/astrohelm/node-workspace/graphs/contributors">Astrohelm contributors</a>.
This workspace is <a href="./LICENSE">MIT licensed</a>.<br/>
And it is part of <a href="https://github.com/astrohelm">Astrohelm ecosystem</a>.
</p>
