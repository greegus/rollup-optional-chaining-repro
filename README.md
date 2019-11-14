```
yarn
yarn rollup -c
```

Uncomment the `"target": "esnext"` line in `tsconfig.json` to show the error:

```
index.ts: (3:57)
[!] Error: Unexpected token (Note that you need plugins to import files that are not JavaScript)
index.ts (3:57)
1: import React from 'react'
2: 
3: const a: { b?: string } = {}
                               ^
4: 
5: export default () => <span>{a?.b}</span>
Error: Unexpected token (Note that you need plugins to import files that are not JavaScript)
    at error (/Users/bchinn/Desktop/rollup-example/node_modules/rollup/dist/rollup.js:5351:30)
    at Module.error (/Users/bchinn/Desktop/rollup-example/node_modules/rollup/dist/rollup.js:9643:9)
    at tryParse (/Users/bchinn/Desktop/rollup-example/node_modules/rollup/dist/rollup.js:9552:16)
    at Module.setSource (/Users/bchinn/Desktop/rollup-example/node_modules/rollup/dist/rollup.js:9868:33)
    at /Users/bchinn/Desktop/rollup-example/node_modules/rollup/dist/rollup.js:12148:20
    at async Promise.all (index 0)
    at async Promise.all (index 0)
    at async Promise.all (index 0)
```

Seems to be a `rollup-plugin-typescript2` bug because with `"target": "esnext"`
uncommented, `yarn tsc --noEmit` still works (e.g. Typescript parses it fine).
