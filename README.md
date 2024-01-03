This repository is to demonstrate the different behavior of `npm i --production` vs `bun i --production` using workspaces. 

`app1` has a `devDependency` on `@playwright/test`. The expected behavior is that when we do `--production`, that `@playwright/test` is not being installed. 

This works correctly in both bun and npm when no workspaces are involved.

However, when we use workspaces, bun is installing the app1 devDependencies, regardless of `--production` flag or not.

To reproduce this behavior, clone the repository and run from the root:

1. `npm i --production`
2. Check the `node_modules` folder in the root, it should have an empty `@playwright` folder. ✔️
3. Delete the node_modules folder (`rm -rf node_modules`)
4. `bun i --production`
5. Check the `node_modules` folder in the root. We expect an empty `@playwright` folder but you will find it having full contents
