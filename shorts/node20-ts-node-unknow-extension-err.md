## Issue

```
ts-node --esm
```

return error
```
$ yarn ts-node example.ts
TypeError [ERR_UNKNOWN_FILE_EXTENSION]: Unknown file extension ".ts" for /Users/taynguyen/Projects/example/example.ts
    at new NodeError (node:internal/errors:399:5)
    at Object.getFileProtocolModuleFormat [as file:] (node:internal/modules/esm/get_format:99:9)
    at defaultGetFormat (node:internal/modules/esm/get_format:139:38)
    at defaultLoad (node:internal/modules/esm/load:83:20)
    at nextLoad (node:internal/modules/esm/hooks:781:28)
    at load (/Users/taynguyen/.npm/_npx/1bf7c3c15bf47d04/node_modules/ts-node/dist/child/child-loader.js:19:122)
    at nextLoad (node:internal/modules/esm/hooks:781:28)
    at Hooks.load (node:internal/modules/esm/hooks:381:26)
    at handleMessage (node:internal/modules/esm/worker:153:24)
    at checkForMessages (node:internal/modules/esm/worker:102:28) {
  code: 'ERR_UNKNOWN_FILE_EXTENSION'
}
```

## Root cause:
Node 20


https://github.com/TypeStrong/ts-node/issues/1997
