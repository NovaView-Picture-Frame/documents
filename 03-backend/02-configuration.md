## New Project

```bash
pnpm i -D typescript rolldown-vite koa @koa/router

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

### tsconfig.json

```diff
      ...
-     "target": "es2016",
+     // "target": "ESNext",
      ...
-     "module": "commonjs",
+     // "module": "ESNext",
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

### package.json

```diff
+ 	"type": "module",
+ 	"main": "dist/main.js",
+ 	"scripts": {
+ 		"electron:dev": "vite build -w"
+ 	},
  	...
```

### .gitignore

```glob
.DS_Store
node_modules
dist

```

## Build

```bash
pnpm nexe -i src/index.ts -o dist/node --asset ~/.nexe/node-$(node -v)
```
