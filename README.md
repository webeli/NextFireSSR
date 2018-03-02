# SSR with Next.js and Firebase Hosting / Cloud Functions

## Important!

This example uses `firebase-tools` as a devDependency which is run from the `node_modules/.bin/` folder via `yarn`. Yarn will run scripts from either the `package.json` or binary scripts from `node_modules/.bin/`. `npm run` does not check the `.bin` folder for executables, so if you use `npm` you will either have to change the scripts to explicitly run the `firebase` binary from `node_modules/.bin/` or install `firebase-tools` globally and remove it from the devDeps list.

## Installation

```bash
yarn install
```

## Login to Firebase CLI

This is used as a dev-dependency instead of a global install. I've found this to be a much nicer dev experience.

```bash
yarn fblogin
```

## Next.js Development

Standard Next.js development with Hot-module Reloading etc

```bash
yarn dev
```

## Local Testing

Unfortunately I have been unable to get any combination of

```bash
firebase serve --only functions,hosting
```

to work as expected. [This issue is where solutions are being explored](https://github.com/firebase/firebase-tools/issues/535) and they will be shared here and on the [Next.js repo's similar issue](https://github.com/zeit/next.js/issues/3167) when discovered.

In the meantime you'll just have to do a full deployment and test online. The new project structure of v2.0.0 and partial deployments reduces the deployment time significantly so this is not too bad. I'm continually looking into a solution to this.

## Deploy to Firebase

You will need to connect the project to your Firebase project. Edit the name in .firebaserc or run `firebase init` and choose not to override any files.

### Deploy Hosting resources and the rewrite Cloud Function

```bash
yarn deploy-app
```

### Deploy functions not used for the SSR

Deploy all functions specified in the function group. Edit this script to add more function groups. - see [Partial deploys docs](https://firebase.google.com/docs/cli/#partial_deploys) for how to use function groups.

```bash
yarn deploy-funcs
```

### Deploy everything to Firebase

```bash
yarn deploy-all
```

## Clean `dist` Folder

```bash
yarn clean
```
