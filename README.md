# pkgtest
### Example project showing pkg failure

This project runs fine with Node (14 or 16) but fails to build with `pkg`.

### Node
Try `yarn start` or `yarn dev` to launch:
`node main.js`

This works, and produces:
```
$ node main.js
Hello World 1.0.0
```

### Pkg
Try `yarn build` to launch:
`pkg main.js -t latest -o pkgtest`

or `yarn build14` to launch:
`pkg main.js -t node14 -o pkgtest`

or `yarn build16` to launch:
`pkg main.js -t node14 -o pkgtest`

Node (14 and 16) have no trouble running the simple project (hello world + version number) but `pkg` produces:
```
> Warning Failed to make bytecode node16-x64 for file /snapshot/pkgtest/main.js`
> Warning Failed to make bytecode node16-x64 for file /snapshot/pkgtest/version.js
```
And the resulting executable does not start, it reports:
```
Error: Cannot find module '/snapshot/pkgtest/main.js'
```
