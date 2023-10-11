# ESLint Config Test

Demonstrates an issue I am encountering in VS Code with regard to the newer ESLint flat config format when using the ESLint extension.

### Setup

Run `npm i` to install the dependencies.

There are two ESLint config files in the repository: `.eslint.config.js.example` and `.eslintrc.js.example`. To test, begin by renaming `.eslint.config.js.example` to `.eslint.config.js`.

### Expected output

At this point, I would expect to see the file `index.js` be highlighted in red in VS Code, and opening the file would show a red underline to indicate a mising semicolon on line 1.

I also expect that running the `npm run lint` will report the error of the missing semicolon.

### Actual Output

On my machine, running `npm run lint` gives teh following output, which is correct.

```
> lint
> eslint .


/Users/jamie.law/Documents/eslint-config-test/index.js
  1:15  error  Missing semicolon  semi

✖ 1 problem (1 error, 0 warnings)
  1 error and 0 warnings potentially fixable with the `--fix` option.
```

However, I do not see `index.js` being highlighted in red, nor the red underline where the missing semicolon is.

### Workaround (Not a solution)

Rename `.eslint.config.js` back to `.eslint.config.js.example` and rename `.eslintrc.js.example` to `.eslintrc.js` to enable the old stlye of config file.

### Attempted workarounds

I have tried adding `{ "eslint.experimental.useFlatConfig": true }` to `.vscode/settings.json`.

### System info

#### VS Code

Version: 1.83.0 (Universal)
Commit: e7e037083ff4455cf320e344325dacb480062c3c
Date: 2023-10-03T16:13:15.449Z
Electron: 25.8.4
ElectronBuildId: 24154031
Chromium: 114.0.5735.289
Node.js: 18.15.0
V8: 11.4.183.29-electron.0
OS: Darwin arm64 22.1.0

#### ESLint Extension

Name: ESLint
Id: dbaeumer.vscode-eslint
Description: Integrates ESLint JavaScript into VS Code.
Version: 2.4.2
Publisher: Microsoft
VS Marketplace Link: https://marketplace.visualstudio.com/items?itemName=dbaeumer.vscode-eslint