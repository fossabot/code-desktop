# Strawbees CODE Desktop app

This app is intended to a version of [Strawbees CODE](https://code.strawbees.com) that can be used offline.

We provide installers for Windows 7, 8.1, and 10, a dmg for MacOS above High Sierra and a zip for Ubuntu 18.04LTS.

The app is written using [NWJS](https://nwjs.io/) and uses [Strawbees Desktop Packager](https://github.com/strawbees/desktop-packager) to bundle, package, sign and deploy the final app.

## Download for your platform

Check [releases](https://github.com/strawbees/code-desktop/releases) for the latest version.

## Running from source

To run the app from the source code, the npm dependencies must be installed both on the root of this repository and on the `src` folder. This process is automated by the `postinstall` script.

The last step is to move which UI the app should load and it can be done with `npm run move-ui-stage` or `npm run move-ui-production`.

Finally run `npm start` to run the app.

```bash
npm install
npm run move-ui-stage
npm start
```

To run a local version of the ui, first follow the instructions to setup [`code-ui`](https://github.com/strawbees/code-ui) and build locally. Then "link" it by runing `npm link` at the root of **`code-ui`**.

After that, run the following commands on the root of **`code-desktop`** repository:

```bash
npm install
npm link @strawbees/code-ui
npm run move-ui-develop
npm start
```

## Building

Make sure you have removed the folders `node_modules` and `src/node_modules` and install the dependencies again but specifying the environment you are building for:

```bash
npm install --only=production
npm run move-ui-production
NODE_ENV=production npm run build
```

**Note**: Bump version on `src/package.json`.

## Signing and Deploying

### OSX

```bash
# Clean up files
rm -rf node_modules
rm -rf src/node_modules
rm -rf src/ui
# Install and build
npm install --only=production
npm run move-ui-production
NODE_ENV=production npm run bundle
NODE_ENV=production npm run package
```

TODO
