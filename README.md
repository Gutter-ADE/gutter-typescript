# TypeScript and JavaScript for Gutter

Adds hover docs and go to definition for `.ts`, `.tsx`, `.mts`, `.cts`, `.js`, `.jsx`, `.mjs`, and `.cjs` through [typescript-language-server](https://github.com/typescript-language-server/typescript-language-server). Coloring stays Gutter's own.

## Install

Needs Node.js (Gutter doesn't install it).

- **Browse:** Settings > Extensions > Browse, find this extension, and choose Install. After the confirmation, `npm ci --ignore-scripts` installs the pinned server (`server/package-lock.json`) once.
- **By name:** Settings > Extensions > Install from npm…, then the package name.
- **Development folder:** Settings > Extensions > Add development folder… and pick this folder, then choose **Install server** on its row.

A repository's own `typescript` package is preferred when it has one; otherwise the pinned TypeScript 6 installed beside the server is used.

## Use a server already installed

Under this extension's row in Settings, set **typescript-language-server script** to the server's `cli.mjs` (for a global install, `<npm root -g>/typescript-language-server/lib/cli.mjs`), and **Node.js** to the `node` you want.

## Check it

From a checkout of Gutter:

```sh
npm run check-extension -- path/to/gutter-typescript
```

It validates `gutter-extension.json` and the npm install step (the server's `package.json` and lockfile), and checks what `npm pack` would publish. Coloring is Gutter's own, so `samples/` is there to open in Gutter and try hover and go to definition, not to check a grammar.

## Updating the server

Change the versions in `server/package.json`, run `npm install --package-lock-only` in `server/`, and bump `version` in both `package.json` and `gutter-extension.json`. Installed copies reinstall the server when they update, because its lockfile changed.

## Publishing

`package.json` uses the placeholder scope `@your-scope`. Swap in your own, add a `repository` field pointing at this repository's remote, keep `version` the same in `package.json` and `gutter-extension.json`, check it as above, and run `npm publish --access public` from this folder.
