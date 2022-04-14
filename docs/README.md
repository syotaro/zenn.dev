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

* [📝 記事一覧](https://zenn.dev/shotaro)
* [📘 zenn CLI Guide](https://zenn.dev/zenn/articles/zenn-cli-guide)
* [トピック検索](https://zenn.dev/search)

```sh
# CLIをアップデートする。リポジトリ上のトップで下記を実行
% npm install zenn-cli@latest
```

```jsonc
// keybindings.json
{
  "key": "shift+alt+cmd+c",
  "command": "markdown.extension.editing.toggleCodeBlock",
  "when": "editorLangId == 'markdown'"
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
