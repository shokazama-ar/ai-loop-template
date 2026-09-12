# Item: Retry Policy

## Summary
検証失敗時にどこまで自動でリトライしてよいかを定義する。

## Definition
- 同一原因での失敗が3回続いた場合、自動リトライを止める
- その場合は `flow/tasks/` の該当タスクを `blocked` にして人間に判断を仰ぐ

## Related
- `loop/feedback/`
