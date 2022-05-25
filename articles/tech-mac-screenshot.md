---
title: "macのスクリーンショット周りの調整"
emoji: "🙌"
type: "tech" # tech: 技術記事 / idea: アイデア
topics: [macOS, スクリーンショット]
published: true
---

## やったこと

`cmd + shift + 5`で実行するスクリーンショットの体験をよくするため、設定を行う

```sh
## スクリーンショットに関するすべての設定を確認
% defaults read com.apple.screencapture

##  ファイル名を、デフォルト（スクリーンショット yyyy-mm-dd hhmmss.png）から変更
% defaults write com.apple.screencapture name ""

## ファイルの保存先（デフォルト）
% defaults write com.apple.screencapture location ~/Desktop

## ファイル形式（デフォルト）
% defaults write com.apple.screencapture type png

## 部分スクリーンショットでの陰影をなくす
% defaults write com.apple.screencapture disable-shadow -bool true
```

Command + Shift + 5をした後、範囲選択をした直後、Enterを押すとフローティングサムネール。
フローティングサムネールを右クリックすると、メニューが選べる。

直接クリップボードにコピーしたい場合は、Enterではなく、Command + Cを押す
