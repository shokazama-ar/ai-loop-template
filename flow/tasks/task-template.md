# Task: <タスク名>

## Metadata
- **ID**: TASK-000
- **Status**: `todo` | `in-progress` | `done` | `blocked`
- **Priority**: `low` | `medium` | `high`
- **Created**: YYYY-MM-DD
- **Updated**: YYYY-MM-DD

## Goal
<!-- このタスクで達成したいことを1〜3文で記述する -->

## Background
<!-- なぜこのタスクが必要か。関連ADRや過去の決定があればリンクする -->
- Related ADR: `knowledge/adr/YYYY-MM-DD-<title>.md` (任意)

## Related Definitions
<!-- このタスクが依存する knowledge/defines/ 配下の定義があれば記載する -->
- Loop: `knowledge/defines/loop/<file>.md` (任意)
- Skill: `knowledge/defines/skill/<file>.md` (任意)
- Model: `knowledge/defines/model/<file>.md` (任意)

## Acceptance Criteria
<!-- 完了条件を箇条書きで。CI green が必須条件 -->
- [ ] CI (`ai-validation.yml`) がグリーンになること
- [ ] `loop/feedback/` にエラーログがないこと
- [ ]

## Scope
<!-- 変更対象のファイル・ディレクトリを明示する -->
- `src/`

## Out of Scope
<!-- このタスクでは扱わないことを明記する -->
-

## Steps
<!-- 実装手順の概要。Claude Code が読んで迷わないように書く -->
1.
2.
3.

## Notes
<!-- 制約・落とし穴・参考情報など -->
