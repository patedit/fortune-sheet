### How to first install
1. Fork and clone the original repository
2. Install dependencies `yarn`
2. Update packages/react/packages.json to point to local @fortune-sheet/core
```
"@fortune-sheet/core": "file:../core",
```
3. Update both @fortune-sheet/core/packages.json and fortune-sheet/react/packages.json version to something different so is easier to know which version we are picking each time. Eg:
```json
{
    "version": "0.19.2999"
}
```
4. Create a link in `@fortune-sheet/core` (we might need to build first, I forgot)
```shell
cd packages/core && sudo npm link
```
5. Build the project `yarn build`
6. Create a link in `@fortune-sheet/react`
```shell
cd packages/react && sudo npm link
```
7. Open your project `package.json` and update your dependency
```json
"dependencies" :{
    "@fortune-sheet/react": "file:/usr/local/lib/node_modules/@fortune-sheet/react",
}
```
8. Link library `pnpm link @fortune-sheet/react`
8. Re-install package
```shell
pnpm install @fortune-sheet/react
```

### How to make changes
1. Make the changes you want on /react or /core
2. Build library `yarn build`
3. Update project dependency `pnpm install @fortune-sheet/react`
4. Restart project

You can also run `make update-fortune-sheet` if you are on Lymon


### How to publish
Make sure you are logged in `npm whoami`

1. Build `yarn build`
2. `yarn lerna publish`

It might error on formula-parser but we can dismiss for now. Check on NPM registry that new version is uploaded.