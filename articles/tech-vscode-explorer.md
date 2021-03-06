---
title: "VSCodeで、エクスプローラに表示されるアルファベット（A, M, U, D, C, R, S）と数字の意味"
emoji: "👌"
type: "tech" # tech: 技術記事 / idea: アイデア
topics: [vscode]
published: true
---

![画像の説明文](/images/tech-vscode-explorer/2022-04-20-1101.png)

## アルファベットの意味

Gitにおけるファイルの状態を表す

| アルファベット | 単語      | 意味                         |
| -------------- | --------- | ---------------------------- |
| A              | added     | 新規追加                     |
| M              | modified  | 変更あり                     |
| U              | untracked | gitが未追跡(新規作成、add前) |
| D              | deleted   | 削除済み                     |
| C              | conflict  | コンフリクト発生中           |
| R              | renamed   | ファイル名変更済み           |
| S              | submodule | サブモジュール               |

## アルファベットの左側に表示される数字

ファイルで発生している問題やエラーの数を表す

- HTMLファルであれば、タグが間違ってたり、終端タグのみ書かれているといった場合
- Markdownであれば、Lintでエラーを検出した場合など
