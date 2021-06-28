# pkgtest
### Example project showing pkg failure

This project runs fine with Node (14 or 16) but fails to build with `pkg`.

### Node
Try `yarn start` or `yarn dev` to launch:
`node main.mjs`

### Pkg
Try `yarn build` to launch:
`node pkg main.mjs -t latest`

or `yarn build14` to launch:
`node pkg main.mjs -t node14`

or `yarn build16` to launch:
`node pkg main.mjs -t node16`

Node (14 and 16) have no trouble running the simple project (hello world + version number) but `pkg` produces:
```
> Warning Failed to make bytecode node16-x64 for file /snapshot/pkgtest/main.mjs`
> Warning Failed to make bytecode node16-x64 for file /snapshot/pkgtest/version.mjs
```
