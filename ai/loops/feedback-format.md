# Item: Feedback Record Format

## Summary
`loop/feedback/` に記録する検証結果のフォーマットを定義する。

## Definition
ファイル名: `loop/feedback/<TASK-ID>-<YYYYMMDD>.md`

```markdown
## Result: PASSED | FAILED
- Command: npm test
- Error: (FAILEDの場合のみ、エラーメッセージの要点)
- Next action: (FAILEDの場合のみ、次に試す対処)
```

## Related
- `.github/workflows/ai-validation.yml`
