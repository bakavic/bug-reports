# Bug Report

This reproduces bug for "caret(`^version`) clobbers tilde(`~version`) in generated `yarn.lock`".

## Steps to reproduce

1. Remove `yarn.lock` to ensure fresh creation of lockfile
2. Run `yarn install` to generate lock file - rename to `yarn.lock.bak` for later comparison
3. Run `bun install --yarn` to generate `yarn.lock` from `bun.lockb`
4. Compare `yarn.lock` and `yarn.lock.bak`

## Missing dependency for `type-check@~0.4.0`

`yarn.lock.bak` from Yarn:
```
type-check@^0.4.0, type-check@~0.4.0:
  version "0.4.0"
[...]
```

`yarn.lock` from Bun:
```
type-check@^0.4.0:
  version "0.4.0"
[...]
```
