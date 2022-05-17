---
title: "リポジトリ内のコード品質を一定に保つ為の仕組み化"
emoji: "✨"
type: "idea" # tech: 技術記事 / idea: アイデア
topics: [git, vscode, github, code]
published: true
---

aa

- [1. 初めに](#1.-%E5%88%9D%E3%82%81%E3%81%AB)
  - [1.1. 目的](#1.1.-%E7%9B%AE%E7%9A%84)
  - [1.2. 前提方針](#1.2.-%E5%89%8D%E6%8F%90%E6%96%B9%E9%87%9D)
- [2. GitHub関連](#2.-github%E9%96%A2%E9%80%A3)
- [3. Git関連](#3.-git%E9%96%A2%E9%80%A3)
- [4. VS Code固有設定](#4.-vs-code%E5%9B%BA%E6%9C%89%E8%A8%AD%E5%AE%9A)
- [5. コーディングルール](#5.-%E3%82%B3%E3%83%BC%E3%83%87%E3%82%A3%E3%83%B3%E3%82%B0%E3%83%AB%E3%83%BC%E3%83%AB)
- [6. 静的エラーチェック（Linter）](#6.-%E9%9D%99%E7%9A%84%E3%82%A8%E3%83%A9%E3%83%BC%E3%83%81%E3%82%A7%E3%83%83%E3%82%AF%EF%BC%88linter%EF%BC%89)
- [7. コード整形（Formatter）](#7.-%E3%82%B3%E3%83%BC%E3%83%89%E6%95%B4%E5%BD%A2%EF%BC%88formatter%EF%BC%89)
- [8. デバッガー(Debugger)](#8.-%E3%83%87%E3%83%90%E3%83%83%E3%82%AC%E3%83%BC%28debugger%29)

## 1. 初めに

### 1.1. 目的

- コードの品質を一定に保つ為の、非属人的な仕組み化を決める。
- 世の中の標準にできる限り合わせ、後から加わる開発者が理解しやすくする。

### 1.2. 前提方針

- リポジトリには「チームの利益になるものだけを入れる」（個人のための設定は入れない）
- 他の開発者（チームメンバー）の開発体験を損なわないように注意することが重要。
  - ※windowsとmac、両方でも動くことを意識する
  - ※エディターは、基本はvscodeとするが、他のエディターでも動くことをできるだけ意識
- 前提として、リポジトリ自体の
  - 参考資料： [GitHubセキュリティ Organization運用のベストプラクティス](https://zenn.dev/tmknom/books/github-organization-security/viewer/introduction),

## 2. GitHub関連

- `/docs/README.md`
  - GitHubで、リポジトリTOPの下に出てくる解説文
  - 各種ルールのハブ的な案内など。実装者が最初に見る文章
- `/docs/CONTRIBUTING.md`
  - IssueやPR作成、ブランチの命名規則やコード規約等についてガイドライン
  - 参考記事： <https://github.blog/2016-02-17-issue-and-pull-request-templates/>
  - PR時に、一応リンクが出てくる
  - コード規約としては、もっともベンチマークとする、オープンな規約を最初に定めると良い
    - 例：[GoogleJavaScriptスタイルガイド](https://google.github.io/styleguide/jsguide.html)
  - リポジトリ内の、ファイルやフォルダーの構成概要
  - マージまたはクローズして不要になったリモートブランチは、削除するかどうか
  - コメントルール
    - その処理を入れた意図は？
    - 関数の処理概要、用途は？
    - パラメーターがある場合、パラメーターの意味するところは？
- `/docs/PULL_REQUEST_TEMPLATE.md`
  - プルリクエスト時に、自動で説明欄に挿入されるテンプレート
- `/docs/ISSUE_TEMPLATE.md`
  - Issueを新規作成時に、自動で説明欄に挿入されるテンプレート。
- `.github/CODEOWNERS`
  - 特定のディレクトリやファイルを編集したPRを作成した時、自動でその編集箇所のOwnerに対してレビューリクエストを送信するための機能
    - 参考：[GitHub で Code Owners を会社として活用する](https://zenn.dev/matken/articles/github-codeowners)
    - [コードオーナーについて - GitHub Docs](https://docs.github.com/ja/repositories/managing-your-repositorys-settings-and-features/customizing-your-repository/about-code-owners#codeowners-file-location)

## 3. Git関連

- `/.gitattributes`
  - 指定したファイル名のパターンに合致するファイルに対し、特定の属性を与える
- `/.gitignore`
  - commit対象に含めないファイルを定義。[github公認テンプレート](https://github.com/github/gitignore)

## 4. VS Code固有設定

- `/*.code-workspace`
  - ワークスペース設定。ここからエディター起動。
- `/.vscode/extensions.json`
  - 推奨拡張機能を記述
- `/.vscode/settings.json`
  - 使用するlinterやformatterの設定など
    - 設定例（フォーマッタの、下記を有効にするかどうか）
      - ファイル保存時の自動フォーマット有無
      - ペーストした文字の自動フォーマット有無
      - 文字入力行の自動フォーマット有無
      - デフォルトフォーマッターの指定
      - ファイル保存時のフォーマッターの指定
  - UI関連の設定や、lint/formatを自動実行するタイミングの設定などは人によって好みが別れるので共有すべきではない
  - 文字コードやインデント関連の設定は`settings.json`に書くよりEditorConfig設定 (`.editorconfig`) に書いた方が良い。EditorConfigであれば各種エディター用のプラグインが出ているので違うエディターを使っている人とも設定を共有することもできる。
- `/.vscode/**.code-snippets`
  - ユーザースニペットを共有
- `.vscode/tasks.json`
  - タスクの記述
- `vscode/launch.json`
  - デバッグ設定

## 5. コーディングルール

- [EditorConfig](https://marketplace.visualstudio.com/items?itemName=EditorConfig.EditorConfig)（.editorconfig）
  - タブインデントや文字コード、改行コードなどのコーディングスタイルに関するエディターの設定を、異なるエディター間で共有するための規格

## 6. 静的エラーチェック（Linter）

- EditorConfigと比べて細かい指定ができ、if文の括弧の前後に空白を入れるかや改行位置の指定などの定義が可能。指定したフォーマットから外れていれば、警告やエラーを出します（また、後述のコードフォーマッター機能も含む場合も多い）
- 代表ツール
  - ESLint（/.eslintrc.json）
  - Husky（.husky/）
    - Gitのコミットコマンドの実行を検知して、コミットが実際に行われる前にLintによるコードチェックやテストを走らせ、コードに誤りがないか確認する
  - [テキスト校正くん](https://marketplace.visualstudio.com/items?itemName=ICS.japanese-proofreading)
    - 日本語文法チェック

## 7. コード整形（Formatter）

- 代表ツール
  - [Prettier](https://marketplace.visualstudio.com/items?itemName=esbenp.prettier-vscode)（.prettierrc.json）
- 定義したフォーマットに自動的に整形。Linterと役割は重複する所があるが、柔軟性がより高い。（行単位に設定された最大文字数に対し、適切な改行処理を行う、など）
- 特徴として、設定可能な項目数が極端に少なく強制度が高い整形処理を行う。採用に際しては、それまで持っていたコードスタイルに対する細かなこだわりを捨てることを要求される。それゆえに開発者間でコードスタイルの定義に迷う余地がなく、共通のスタイルで統一されたソースコードが維持されるというメリットもある。

## 8. デバッガー(Debugger)

- ブレークポイントを設定してコールスタックを確認したり、ステップ実行や変数のウォッチなど。vscodeに標準で用意されている。
