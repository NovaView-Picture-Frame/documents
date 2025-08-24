## Copy Native Dependencies

### package.json

```diff
  	"scripts": {
+ 		"postinstall": "$npm_execpath rebuild sharp",
```

```bash
pnpm i -D node-addon-api node-gyp sharp vite-plugin-static-copy

pnpm approve-builds

rm -rf node_modules

pnpm i
```

### src/index.ts

```diff
- console.log("Hello, World!");
+ import sharp from 'sharp';
+ 
+ console.log(sharp);

```

### vite.config.ts

```diff
  import { defineConfig } from 'rolldown-vite'
+ import { viteStaticCopy } from 'vite-plugin-static-copy'
      ...
      esbuild: {
          legalComments: 'none',
      },
+     plugins: [
+         viteStaticCopy({
+             targets: [
+               {
+                   src: 'node_modules/sharp/src/build/Release/sharp-*.node',
+                   dest: 'node_modules/@img',
+                   rename: (name, _ext, _path) => `${name}/sharp.node`,
+               },
+             ],
+         }),
+     ],
```
