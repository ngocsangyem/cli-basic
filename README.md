# CLI

1. Create folder **src** in the root of project and place a file called **cli.js** into then add the code:

```javascript
export function cli(args) {
	console.log(args);
}
```

2. Create entry point. Create new directory **bin** in the root and a file called **create-project** into it.

```javascript
#!/usr/bin/env node

require = require('esm')(module /*, options*/);
require('../src/cli').cli(process.argv);
```

-   **_esm_** enables to use import in other folder. So we dont need to transpile Node.js version without using babel

3. In **package.json** the **_bin_** key have an object two key/value pair. Those define the CLI commands that your package manager will install. In our case we'll register the same script for two commands. Once using our own npm scope by using our username and once as the generic create-project command for convenience.

-   To test out script run: **sudo npm link**

4. In order to do recursive copying of the files we'll use a library called **_ncp_**

-   This library supports recursive copying cross-platform and even has a flag to force override existing files

5. Place logic code into **_main.js_**

6. Initialize git and install our dependencies

-   **_execa_** which allows us to easily run external commands like git
-   **_pkg-install_** to trigger either yarn install or npm install depending on what the user uses
-   **_listr_** which let's us specify a list of tasks and gives the user a neat progress overview

## Publish

Add a **_files_** key in your **package.json** to specify which files should be published.
