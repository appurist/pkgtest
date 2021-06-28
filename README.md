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

I have tried renaming both source files to have `.mjs` filenames, to avoid ambiguity, but `pkg` tries to load `main.js` 
regardless so with the current filename, it is clear the files it seeks do exist, and can be loaded by node.
However, it is unable to load any modules skipped by the bytecode "warning" above.

The problem appears to be related to dependent modules, in this case the simple import of `version.js`. If I remove that import from `main.js`, I no longer get the bytecode errors and the resulting executable runs fine.

