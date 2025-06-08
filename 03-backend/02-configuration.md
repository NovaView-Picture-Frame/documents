## New Project

```bash
pnpm i -D typescript vite nexe concurrently wait-on koa @koa/router @types/koa @types/koa__router

pnpm approve-builds

pnpm tsc --init
```

## VS Code Settings

### .vscode/settings.json

```jsonc
{
    "typescript.tsdk": "node_modules/typescript/lib"
}

```

## Configurations

### package.json

```diff
+ 	"type": "module",
+ 	"scripts": {
+ 		"dev": "concurrently -k 'vite build --w' 'wait-on dist/index.js && node --watch $_'",
+ 		"build": "vite build && nexe -i dist/index.js -o dist/node --asset ~/.nexe/node-$(node -v)"
+ 	},
  	...
```

### tsconfig.json

```diff
      ...
-     "target": "es2016",
+     // "target": "esnext",
      ...
-     "module": "commonjs",
+     // "module": "esnext",
      ...
-     // "moduleResolution": "node10",
+     "moduleResolution": "bundler",
      ...
-     // "noEmit": true,
+     "noEmit": true,
      ...
-     // "noUnusedLocals": true,
-     // "noUnusedParameters": true,
-     // "exactOptionalPropertyTypes": true,
-     // "noImplicitReturns": true,
-     // "noFallthroughCasesInSwitch": true,
-     // "noUncheckedIndexedAccess": true,
-     // "noImplicitOverride": true,
-     // "noPropertyAccessFromIndexSignature": true,
+     "noUnusedLocals": true,
+     "noUnusedParameters": true,
+     "exactOptionalPropertyTypes": true,
+     "noImplicitReturns": true,
+     "noFallthroughCasesInSwitch": true,
+     "noUncheckedIndexedAccess": true,
+     "noImplicitOverride": true,
+     "noPropertyAccessFromIndexSignature": true,
      ...
```

### vite.config.ts

```typescript
import { defineConfig } from 'vite';
import { builtinModules } from 'module';

export default defineConfig({
    build: {
        lib: {
            entry: 'src/index.ts',
            formats: ['es'],
        },
        target: 'esnext',
        rollupOptions: {
            external: [
                ...builtinModules.flatMap(module =>
                    [module, `node:${module}`]
                ),
            ]
        }
    },
})

```

### .gitignore

```glob
.DS_Store
node_modules
dist

```
