---
title: "[公式]ついにプルリクエスト統合も実現した、GitHub Desktop3.0"
emoji: "🙆"
type: "tech" # tech: 技術記事 / idea: アイデア
topics: [github, git, githubdesktop, githubactions]
published: true
---

- [1. GitHubDesktopとは](#1.-githubdesktop%E3%81%A8%E3%81%AF)
- [2. プルリクエストの統合](#2.-%E3%83%97%E3%83%AB%E3%83%AA%E3%82%AF%E3%82%A8%E3%82%B9%E3%83%88%E3%81%AE%E7%B5%B1%E5%90%88)
  - [2.1. GitHub Actions結果の受信と再実行](#2.1.-github-actions%E7%B5%90%E6%9E%9C%E3%81%AE%E5%8F%97%E4%BF%A1%E3%81%A8%E5%86%8D%E5%AE%9F%E8%A1%8C)
  - [2.2. レビューコメントを受信](#2.2.-%E3%83%AC%E3%83%93%E3%83%A5%E3%83%BC%E3%82%B3%E3%83%A1%E3%83%B3%E3%83%88%E3%82%92%E5%8F%97%E4%BF%A1)
- [3. チェリーピッキング（コミットを別ブランチにコピー）](#3.-%E3%83%81%E3%82%A7%E3%83%AA%E3%83%BC%E3%83%94%E3%83%83%E3%82%AD%E3%83%B3%E3%82%B0%EF%BC%88%E3%82%B3%E3%83%9F%E3%83%83%E3%83%88%E3%82%92%E5%88%A5%E3%83%96%E3%83%A9%E3%83%B3%E3%83%81%E3%81%AB%E3%82%B3%E3%83%94%E3%83%BC%EF%BC%89)
- [4. スカッシュ（コミットをまとめる、並べ替え）](#4.-%E3%82%B9%E3%82%AB%E3%83%83%E3%82%B7%E3%83%A5%EF%BC%88%E3%82%B3%E3%83%9F%E3%83%83%E3%83%88%E3%82%92%E3%81%BE%E3%81%A8%E3%82%81%E3%82%8B%E3%80%81%E4%B8%A6%E3%81%B9%E6%9B%BF%E3%81%88%EF%BC%89)
- [5. 画像のDIFF](#5.-%E7%94%BB%E5%83%8F%E3%81%AEdiff)
- [6. Webとの統合](#6.-web%E3%81%A8%E3%81%AE%E7%B5%B1%E5%90%88)
- [7. VScodeとの連携](#7.-vscode%E3%81%A8%E3%81%AE%E9%80%A3%E6%90%BA)
- [8. スマホ用の公式ツール](#8.-%E3%82%B9%E3%83%9E%E3%83%9B%E7%94%A8%E3%81%AE%E5%85%AC%E5%BC%8F%E3%83%84%E3%83%BC%E3%83%AB)
- [9. まとめ](#9.-%E3%81%BE%E3%81%A8%E3%82%81)

![GitHubDesktop 3.0](https://github.blog/wp-content/uploads/2022/04/github-desktop-hero.png?resize=2400%2C1260)

## 1. GitHubDesktopとは

GitHubの公式ツール。オープンソースで、[頻繁な改善](https://desktop.github.com/release-notes/)が行われている（TypeScriptとReactを使用した、Electronベースのアプリ）

他のGitクライアントに比べると、機能は少ないが、公式であるからこその強みとなる要素も持ち合わせている

また、2022年4月26日には、バージョン3.0が公開され、待望のプルリクエスト統合が実現しました。

https://desktop.github.com/

## 2. プルリクエストの統合

### 2.1. GitHub Actions結果の受信と再実行

![PR](/images/tech-github-desktop/1.gif)

プルリクエスト時にGitHubActionの結果通知をリアルタイムに受信し、実行結果のステータスを確認できます。

また、失敗したジョブまたは単一のジョブのみを再実行させることも可能です。
プルリクエスト中に、チェックに失敗した時などに、システム通知を受信することもできます。
![PRのテスト結果通知](/images/tech-github-desktop/2022-04-29-1201.png)

チーム開発の場合、チェック失敗への対応スピードは生産性に直結します。他のメンバーの手を止めてしまう前に、素早く気づき、対処することは重要です。
slackを経由して通知をすることも可能ですが、初回の設定が面倒なのと、**自分に関係ない通知が多くなって他のメンバーのノイズにり、結果、誰も見なくなったりします。**
GitHubDesktopなら、ダイレクトに自分に関係のある通知だけを受け取ることもでき、便利です。

https://github.blog/2022-04-26-github-desktop-3-0-brings-better-integration-for-your-pull-requests/

### 2.2. レビューコメントを受信

PRのチェックをクリア後、マージする前に、チームメンバーからコメントや変更リクエスト、承認を貰った時、その内容も通知されます。各レビュアーが、GitHub上でコメントした後、slackで改めてメンションをつけて連絡する、といった手間から解放されます。

![コメント通知](/images/tech-github-desktop/2022-04-29-1211.png)

## 3. チェリーピッキング（コミットを別ブランチにコピー）

![alt](/images/tech-github-desktop/3.gif)

チェリーピッキング（摘み取り。あるブランチから別のブランチにコミットをコピーする）を、ドラッグ＆ドロップで直感的に実行できます（複数のコミットを持って行きたい時は、Shiftキーを押しながら）

利用シーンとしては、新しい機能の開発中に、mainブランチの既存のバグを発見した時、修正コミットのみをhot-fixブランチに適応したい時、など。

https://github.blog/2021-03-30-github-desktop-now-supports-cherry-picking/

## 4. スカッシュ（コミットをまとめる、並べ替え）

![スカッシュ](/images/tech-github-desktop/2.gif)

コミットが細かすぎたり、コミットの順序にストーリー性がないと、他のチームメンバーの理解を妨げる可能性があります。PRをレビューしてもらう前に、スカッシュを活用して分かりやすくすることはマナーです。

## 5. 画像のDIFF

![画像のDIFF](/images/tech-github-desktop/4.gif)

これは、web上でも普通にできるのですが、一応紹介。画像の変化がわかりやすい、特有のDIFF方法が提供される。なお、SVGはWeb上であれば、画像（blob）としてプレビューや差分比較できるが、ローカルだとテキストファイルとしてのみ認識されているっぽくプレビューされません。

## 6. Webとの統合

![Webとの統合](/images/tech-github-desktop/5.gif)

GitHubのWeb上に、「Open with GitHub Desktop」ボタンが用意されています。ちょっとローカルのエディターで見たい、という時に便利

## 7. VScodeとの連携

vscodeから、GitHubDesktopを呼び出す拡張があります。

https://marketplace.visualstudio.com/items?itemName=wraith13.open-in-github-desktop
![alt](/images/tech-github-desktop/2022-04-29-0114.png)

## 8. スマホ用の公式ツール

iOS/Android用の公式ツールもあります。
https://github.co.jp/mobile.html

通知トリガーだけでなく、通知時間なども、リポジトリ単位で細かく設定できるところがポイントです。

![GitHubモバイルアプリ](/images/tech-github-desktop/2022-04-29-1247.png)

## 9. まとめ

Gitクライアントといえば、CLIや、VScode標準の機能、[Sourcetree](https://www.sourcetreeapp.com/)や[GitKraken](https://www.gitkraken.com/)を利用している人も多いかと思いますが、公式ツールもかなりオススメですよという内容でした。
公式としても、シンプルさを大方針として掲げているようで、初心者や非エンジニア（デザイナーなど）もとっつきやすそう。プロジェクトチーム全員で活用できると、コミュニケーションロスが減り、生産性もかなり上がると思います。
