# Item: Role-to-Model Mapping

## Summary
タスクの性質に応じて、どのクラスのモデルを使うべきかを定義する。

## Definition
| タスクの性質 | 推奨モデル | 理由 |
|---|---|---|
| 設計判断・複雑なリファクタリング・ADR作成 | Opus系 | 深い推論と広い文脈把握が必要 |
| 通常の実装・バグ修正・レビュー | Sonnet系 | 精度とコストのバランスが良く、日常タスクの既定値 |
| 定型チェック・フォーマット検証・単純な確認 | Haiku系 | 低コストで高速、単純作業に十分 |

迷ったらSonnet系を既定値とする。

## Related
- `gen-ai/model-roles/escalation-policy.md`
