## New Project

## VS Code Settings

### > TypeScript: Select TypeScript Version...
`Use Workspace Version`

## Configurations

```bash
pnpm i -D typescript rolldown-vite concurrently wait-on @types/node

pnpm tsc --init
```

### .gitignore

```glob

node_modules
dist

```

### package.json

```diff
+ 	"type": "module",
+ 	"scripts": {
+ 		"dev:node": "wait-on dist/index.js && node --watch $_ ",
+ 		"dev": "concurrently -k 'vite build -w' 'npm:dev:node'",,
+ 		"build": "vite build"
+ 	},
  	...
```

### tsconfig.json

```diff
-     "module": "nodenext",
+     "module": "esnext",
+     "moduleResolution": "bundler",
      "target": "esnext",
-     "types": [],
+     // "types": [],
      ...
+     "noEmit": true,
-     "sourceMap": true,
-     "declaration": true,
-     "declarationMap": true,
+     // "sourceMap": true,
+     // "declaration": true,
+     // "declarationMap": true,
      ...
-     // "noImplicitReturns": true,
-     // "noImplicitOverride": true,
-     // "noUnusedLocals": true,
-     // "noUnusedParameters": true,
-     // "noFallthroughCasesInSwitch": true,
-     // "noPropertyAccessFromIndexSignature": true,
+     "noImplicitReturns": true,
+     "noImplicitOverride": true,
+     "noUnusedLocals": true,
+     "noUnusedParameters": true,
+     "noFallthroughCasesInSwitch": true,
+     "noPropertyAccessFromIndexSignature": true,
      ...
-     "jsx": "react-jsx",
+     // "jsx": "react-jsx",
```

### vite.config.ts

```typescript
import { defineConfig } from 'rolldown-vite'

export default defineConfig({
    ssr: {
        noExternal: true,
    },
    build: {
        ssr: 'src/index.ts',
        target: 'esnext',
        minify: true,
    },
    esbuild: {
        legalComments: 'none',
    },
})

```

### src/index.ts

```typescript
console.log("Hello, World!");

```
