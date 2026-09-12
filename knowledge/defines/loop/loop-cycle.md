# Define: Loop Cycle

## Summary
`loop/` が担う検証フィードバックサイクルの定義。タスクが「done」と呼べる条件と、
失敗時にどこまでリトライしてよいかを定める。

## Definition

1. 実装（`src/` への変更）が完了したら、`loop/scripts/` にある検証スクリプトを実行する。
   スクリプトが存在しない場合は、プロジェクトのテスト・lintコマンドをそのまま使う。
2. 検証結果（成功・失敗いずれも）は `loop/feedback/<TASK-ID>-<YYYYMMDD>.md` に記録する。
   失敗した場合はエラーメッセージの要点と、次に試す対処を書く。
3. CI (`.github/workflows/ai-validation.yml`) が失敗した場合は、まず
   `loop/feedback/` に既知の原因が記録されていないか確認してから修正に着手する。
4. 同じ原因での失敗が3回続いた場合は、自動でリトライを続けず `flow/tasks/` の該当タスクを
   `blocked` にして人間に判断を仰ぐ。
5. タスクが「done」と呼べるのは、CIがグリーンかつ `loop/feedback/` に未解決のエラーが
   残っていない状態のみ。

## Example

```
loop/feedback/TASK-012-20250110.md
---
## Result: FAILED
- Command: npm test
- Error: TypeError in src/foo.ts:42
- Next action: 型定義の不整合を修正して再実行する
```

## Related
- `knowledge/rules/claudecode_instructions.md`（LOOPセクション）
- `loop/scripts/`
