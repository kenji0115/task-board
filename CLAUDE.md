# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Git運用ルール

- コードに変更を加えた場合は、その都度コミットを作成し、GitHubのリモートリポジトリへプッシュすること。
- コミットメッセージは変更内容が分かるように簡潔に記述する。
- プッシュ先のリモート/ブランチが未設定の場合は、ユーザーに確認の上で設定する。

## デプロイ先

https://kenji0115.github.io/task-board/

- `main`ブランチへのpushで`.github/workflows/deploy.yml`が自動実行され、GitHub Pagesへデプロイされる。
- Viteの`base`は`/task-board/`に設定済み(リポジトリ名と一致させること)。

## 技術スタック

- React 19 + Vite(JavaScript / JSX、TypeScriptは未使用)
- スタイリングはプレーンCSS(`App.css` / `index.css`)。CSS Modulesやライブラリは未使用
- Lint: ESLint(`npm run lint`)
- 状態管理は`useState`/`useEffect`のみ(外部の状態管理ライブラリは未使用)
- データ永続化は`localStorage`(キー: `task-board-tasks`)

## コンポーネントの命名規約

- コンポーネントファイルは`src/components/`配下にPascalCase(例: `TaskForm.jsx`)で配置し、ファイル名・コンポーネント名・デフォルトエクスポート名を一致させる
- コンポーネントは`function ComponentName(props) { ... }`の関数宣言で記述し、propsはその場で分割代入する
- イベントハンドラをpropsとして渡す場合は`on`プレフィックス(`onAddTask`, `onToggle`, `onDelete`など)を使う
- CSSクラス名はkebab-case(例: `task-item`, `add-button`, `empty-message`)とし、状態を表す場合は`completed`のような修飾クラスを併用する
