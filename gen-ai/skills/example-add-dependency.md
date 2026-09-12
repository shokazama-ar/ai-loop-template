# Skill: add-npm-dependency

## When to use
新しいnpmパッケージを追加する必要がある場合。

## Preconditions
- `package.json` が存在する

## Steps
1. `npm install <package>` を実行する
2. `package.json` と `package-lock.json` の差分を確認する

## Verification
- `npm run build` が成功する
