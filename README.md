# pkgtest
### Example project showing pkg failure

This project runs fine with Node (14 or 16) but fails to build with `pkg`.

### Node
Try `yarn start` or `yarn dev` to launch:
`node main.mjs`

### Pkg
Try `yarn build` to launch:
`pkg main.mjs -t latest -o pkgtest`

or `yarn build14` to launch:
`pkg main.mjs -t node14 -o pkgtest`

or `yarn build16` to launch:
`pkg main.mjs -t node14 -o pkgtest`

Node (14 and 16) have no trouble running the simple project (hello world + version number) but `pkg` produces:
```
> Warning Failed to make bytecode node16-x64 for file /snapshot/pkgtest/main.mjs`
> Warning Failed to make bytecode node16-x64 for file /snapshot/pkgtest/version.mjs
```
And the resulting executable does not start, it `cannot find module main.js` (which is the wrong name).
