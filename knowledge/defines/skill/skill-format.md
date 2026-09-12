# Define: Skill Definition Format

## Summary
このプロジェクトで繰り返し使う定型作業（例: デプロイ手順、DBマイグレーション手順、
特定フレームワークでのコンポーネント追加手順）を「スキル」として文書化する際のフォーマット。
エージェントが毎回ゼロから手順を推測しないようにするための定義。

## Definition

1つのスキルは `knowledge/defines/skill/<skill-name>.md` として1ファイルにまとめ、
以下のセクションを含める。

- **Name**: スキル名（ファイル名と一致させる）
- **When to use**: どんな状況・タスクでこのスキルを使うべきか
- **Preconditions**: 実行前に満たすべき条件（環境変数、依存パッケージなど）
- **Steps**: 具体的な手順（コマンド込み）
- **Verification**: 成功したことをどう確認するか

## Example

```markdown
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
```

## Related
- `knowledge/rules/claudecode_instructions.md`
- `flow/tasks/task-template.md`（`Related Definitions` セクション）
