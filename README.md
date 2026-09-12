# AI-Loop Template

Claude Code のようなAIエージェントが、人間の監督のもとで継続的に開発サイクルを回すための
リポジトリテンプレートです。「知識」「タスク」「実装」「検証」を明確に分離し、エージェントが
迷わず次のアクションを選べる構造を提供します。

## コンセプト

このテンプレートは以下の領域で構成されています。

| 領域 | ディレクトリ | 役割 |
|---|---|---|
| **STOCK** | `doc/` | プロジェクト全体の設計資料（ルール・意思決定record） |
| **AI** | `gen-ai/` | エージェントの動作に関する定義（ループ・スキル・モデル選定） |
| **FLOW** | `flow/` | 今どのタスクに取り組んでいるかという動的なコンテキスト |
| **EXECUTION** | `src/` | 実際のプロダクトコード |
| **LOOP** | `loop/` | 実装後の検証とそのフィードバック |
| **DATA** | `data-models/` | プロジェクトで扱うデータモデルの定義 |

タスクは `flow/` → `src/` → `loop/` の順で流れ、`doc/`・`gen-ai/`・`data-models/` は
その全工程を通じて参照される土台という位置づけです。

## ディレクトリ構成

```
.
├── doc/                    # STOCK: 設計資料
│   ├── rules/              #   エージェントへの指示・運用ルール
│   └── adr/                #   Architecture Decision Record（意思決定の記録）
├── gen-ai/                 # AI: エージェントの動作定義
│   ├── loops/              #   検証/フィードバックループの定義
│   ├── skills/             #   再利用可能な作業手順（スキル）の定義
│   └── model-roles/        #   タスク種別ごとのモデル選定方針
├── flow/                   # FLOW: 動的なタスクコンテキスト
│   ├── tasks/              #   タスクファイル（task-template.md を複製して使う）
│   └── context/            #   タスクに紐づく補足コンテキスト
├── src/                    # EXECUTION: プロダクトコード
├── loop/                   # LOOP: 検証とフィードバック
│   ├── scripts/            #   検証・テストスクリプト
│   └── feedback/           #   検証結果・CIログの記録
├── data-models/            # DATA: データモデル定義
│   ├── master/             #   マスタデータのモデル定義
│   ├── transaction/        #   トランザクションデータのモデル定義
│   ├── system/             #   システム内部データのモデル定義
│   └── overviews.md        #   データモデル全体の概要
└── .github/workflows/
    └── ai-validation.yml   # CI: 上記構造とタスクファイルの整合性を検証
```

## 使い方

1. `flow/tasks/task-template.md` をコピーして `flow/tasks/TASK-XXX-<slug>.md` を作成し、
   Goal・Acceptance Criteria・Steps を埋める。
2. 関連する定義があれば `gen-ai/{loops,skills,model-roles}/` を確認し、
   なければ追記する。重要な設計判断は `doc/adr/` にADRを残す。
3. `src/` に実装する。
4. `loop/scripts/` の検証を実行し、結果を `loop/feedback/` に記録する。
5. ブランチを push し、`ai-validation.yml` がグリーンであることを確認する。
6. タスクファイルの `Status` を `done` に更新する。

詳細な運用ルールは [`doc/rules/claudecode_instructions.md`](doc/rules/claudecode_instructions.md)
を参照してください。

## CI

`.github/workflows/ai-validation.yml` は以下を検証します。

- `doc/{rules,adr}`、`gen-ai/{loops,skills,model-roles}`、`flow/tasks`、`loop/feedback`、
  `data-models` が存在すること
- `flow/tasks/*.md`（テンプレート自身を除く）が `# Task:` 見出しと `## Goal` セクションを
  持つこと
