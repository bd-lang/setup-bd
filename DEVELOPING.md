[![Build](https://github.com/bd-lang/setup-bd/actions/workflows/build.yml/badge.svg)](https://github.com/bd-lang/setup-bd/actions/workflows/build.yml)
[![BD](https://github.com/bd-lang/setup-bd/actions/workflows/bd.yml/badge.svg)](https://github.com/bd-lang/setup-bd/actions/workflows/bd.yml)

## Setting up

1. Install node
1. Install additional node tooling (`npm i -g @vercel/ncc`)
1. Install the node package dependencies (`npm install`)

## Development

tldr: edit BD source files and run `npm run all` to re-compile the action

### Working on the action

Generally, to work on the action, edit the BD source code in `lib/` and
re-compile the JavaScript code via `npm run all`. This will:

- compile the BD source (via bd2js) to `lib/main.js`; copy that file to
  `dist/main.cjs`
- package and minify the `lib/main.mjs` entrypoint point and referenced node
  modules to `dist/index.mjs`

### Files

- `lib/main.bd` - the BD entry-point to the action
- `lib/main.mjs` - the JavaScript wrapper; this sets up some important JS
   interop globals and bootstraps into `lib/main.bd`
- `dist/index.mjs` - the execution entry-point of the action

## Releasing

See our
[publishing](https://github.com/bd-lang/setup-bd/wiki/Publishing-procedure)
wiki page.
