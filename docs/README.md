<p align="center">
  <img src="https://zenn.dev/images/logo.png" alt="zenn.dev"></a>
</p>

<h3 align="center"><a href="https://zenn.dev/shotaro">zenn.dev</a>の記事管理</h3>

<div align="center">

[![Status](https://img.shields.io/badge/status-active-success.svg)](https://github.com/syotaro/zenn.dev/)
[![GitHub Issues](https://img.shields.io/github/issues/syotaro/zenn.dev.svg)](https://github.com/syotaro/zenn.dev/issues)
[![GitHub Pull Requests](https://img.shields.io/github/issues-pr/syotaro/zenn.dev.svg)](https://github.com/syotaro/zenn.dev/pulls)

</div>

---

- [📝 記事一覧](https://zenn.dev/shotaro)
- [📘 zenn CLI Guide](https://zenn.dev/zenn/articles/zenn-cli-guide)
- [🔍 トピック検索](https://zenn.dev/search)

- フォーマッタ：prettier & EditorConfig
- Linter ：markdownlint & テキスト校正くん

```sh
# リポジトリ直下に移動
% cd <repo>
# zenn-CLIをアップデートする。
% npm install zenn-cli@latest
# Prettierのバグ対応（Markdown文書中内の漢字仮名と英数字の間に半角スペースが挿入されないようにする）
% npm install -D prettier
% npm install -D prettier-plugin-md-nocjsp
# TextLintに必要なものをinstall
% npm install textlint \
              textlint-rule-preset-ja-spacing \
              textlint-rule-preset-ja-technical-writing \
              @proofdict/textlint-rule-proofdict \
```

```jsonc
// keybindings.json
{
  "key": "shift+alt+cmd+c",
  "command": "markdown.extension.editing.toggleCodeBlock",
  "when": "editorTextFocus && editorLangId == 'markdown'"
}
{
  "key": "shift+cmd+8",
  "command": "markdown.extension.editing.toggleList",
  "when": "editorLangId == 'markdown'"
}
{
  "key": "shift+cmd+c",
  "command": "markdown.extension.editing.toggleCodeSpan",
  "when": "editorLangId == 'markdown'"
}
```

# フォルダー構成

- articles : zenn.devの記事
- books: zenn.devの本
- draft: 下書き
- note.com: note.comへ投稿する記事
