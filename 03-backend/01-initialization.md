## Build

```bash
mkdir ~/.nexe && cd $_

export PYTHON=$(which python3)

export MAKEFLAGS="-j<JOBS>"
# Set the number of parallel jobs (no more than the number of logical CPU cores).
# Ensure at least 2 GB (LLVM) or 2.5 GB (GCC) of RAM is available per job.

echo 'console.log("hello")' | pnpm dlx nexe --build --verbose

mv $(node -v | cut -c2-)/out/Release/node node-$(node -v)

rm -rf .nexe $(node -v | cut -c2-)
```

## Clean Cache

```bash
rm -rf ~/.nexe
```
