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
.DS_Store
node_modules
dist

```

### package.json

```diff
+ 	"type": "module",
+ 	"scripts": {
+ 		"dev": "concurrently -k 'vite build -w' 'wait-on dist/index.js && node --watch $_'",
+ 		"build": "vite build"
+ 	},
  	...
```

### tsconfig.json

```diff
      ...
-     // "lib": ["esnext"],
+     "lib": ["esnext"],
      ...
-     // Style Options
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
})

```

### src/index.ts

```typescript
console.log("Hello, World!");

```
