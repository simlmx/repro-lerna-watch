# Minimal package that reproduces a bug with `lerna watch`


# Environment

Operating System: Arch Linux
Kernel: Linux 6.7.4-arch1-1
`pnpm`: `8.15.1`


## Steps to reproduce

### Install the dependencies

`pnpm i`

### Start `lerna watch`

`pnpm exec lerna watch -- echo \$LERNA_PACKAGE_NAME \$LERNA_FILE_CHANGES`

### Look at the logs of `nx`

`tail -f node_modules/.cache/nx/d/daemon.log`

### Edit a file

Edit `packages/a/package.json` with VIM


When we edit `a/package.json`, `nx` sees it, but it doesn't get to `lerna`. Sometimes it works once or twice!
