## Terminology

IDE = integrated development environment

visual studio
webstorm

GIT = version control system

GitHub !== GIT

http://localhost

npm i === npm install

## Modules

default imports / exports

named imports / exports

```js
export function doSomething() {}

//export { doSomething };

import { doSomething } from './sample.js';
```

## Methods vs Functions

Methods are the same as functions, but are functions that belong to an object

## Running applications in different modes

Production - For end-users
Development - For developers
Test - For testing

## Removing files from GIT after they are committed

```bash
git rm --cached .env.development
git rm --cached -r ./node_modules
```

.gitignore all node_modules folders
**/node_modules
