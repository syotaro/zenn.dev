---
title: "Googleドライブ・ドキュメントのURL操作Tips"
emoji: "🕌"
type: "tech" # tech: 技術記事 / idea: アイデア
topics: [googledrive, google, gas]
published: true
---

- [1. よく使う](#1.-%E3%82%88%E3%81%8F%E4%BD%BF%E3%81%86)
  - [1.1. 読み取り専用モード](#1.1.-%E8%AA%AD%E3%81%BF%E5%8F%96%E3%82%8A%E5%B0%82%E7%94%A8%E3%83%A2%E3%83%BC%E3%83%89)
  - [1.2. 実ファイル（pngやcsv）としてURL参照可能に](#1.2.-%E5%AE%9F%E3%83%95%E3%82%A1%E3%82%A4%E3%83%AB%EF%BC%88png%E3%82%84csv%EF%BC%89%E3%81%A8%E3%81%97%E3%81%A6url%E5%8F%82%E7%85%A7%E5%8F%AF%E8%83%BD%E3%81%AB)
- [2. 稀に使う](#2.-%E7%A8%80%E3%81%AB%E4%BD%BF%E3%81%86)
  - [2.1. Webビューアーをスキップ（直接ダウンロードリンク）](#2.1.-web%E3%83%93%E3%83%A5%E3%83%BC%E3%82%A2%E3%83%BC%E3%82%92%E3%82%B9%E3%82%AD%E3%83%83%E3%83%97%EF%BC%88%E7%9B%B4%E6%8E%A5%E3%83%80%E3%82%A6%E3%83%B3%E3%83%AD%E3%83%BC%E3%83%89%E3%83%AA%E3%83%B3%E3%82%AF%EF%BC%89)
  - [2.2. コピーして自分のものにする](#2.2.-%E3%82%B3%E3%83%94%E3%83%BC%E3%81%97%E3%81%A6%E8%87%AA%E5%88%86%E3%81%AE%E3%82%82%E3%81%AE%E3%81%AB%E3%81%99%E3%82%8B)
  - [2.3. テンプレート共有を目的としたプレビューモード](#2.3.-%E3%83%86%E3%83%B3%E3%83%97%E3%83%AC%E3%83%BC%E3%83%88%E5%85%B1%E6%9C%89%E3%82%92%E7%9B%AE%E7%9A%84%E3%81%A8%E3%81%97%E3%81%9F%E3%83%97%E3%83%AC%E3%83%93%E3%83%A5%E3%83%BC%E3%83%A2%E3%83%BC%E3%83%89)
  - [2.4. コピーするときにユーザーを招待する](#2.4.-%E3%82%B3%E3%83%94%E3%83%BC%E3%81%99%E3%82%8B%E3%81%A8%E3%81%8D%E3%81%AB%E3%83%A6%E3%83%BC%E3%82%B6%E3%83%BC%E3%82%92%E6%8B%9B%E5%BE%85%E3%81%99%E3%82%8B)
  - [2.5. 任意のDriveフォルダーに、ドキュメントを新規作成](#2.5.-%E4%BB%BB%E6%84%8F%E3%81%AEdrive%E3%83%95%E3%82%A9%E3%83%AB%E3%83%80%E3%83%BC%E3%81%AB%E3%80%81%E3%83%89%E3%82%AD%E3%83%A5%E3%83%A1%E3%83%B3%E3%83%88%E3%82%92%E6%96%B0%E8%A6%8F%E4%BD%9C%E6%88%90)
- [3. ほとんど使わない](#3.-%E3%81%BB%E3%81%A8%E3%82%93%E3%81%A9%E4%BD%BF%E3%82%8F%E3%81%AA%E3%81%84)
  - [3.1. プレゼンター表示モードに](#3.1.-%E3%83%97%E3%83%AC%E3%82%BC%E3%83%B3%E3%82%BF%E3%83%BC%E8%A1%A8%E7%A4%BA%E3%83%A2%E3%83%BC%E3%83%89%E3%81%AB)
  - [3.2. Webページに埋め込む](#3.2.-web%E3%83%9A%E3%83%BC%E3%82%B8%E3%81%AB%E5%9F%8B%E3%82%81%E8%BE%BC%E3%82%80)
  - [3.3. ユニバーサルファイルビューアー](#3.3.-%E3%83%A6%E3%83%8B%E3%83%90%E3%83%BC%E3%82%B5%E3%83%AB%E3%83%95%E3%82%A1%E3%82%A4%E3%83%AB%E3%83%93%E3%83%A5%E3%83%BC%E3%82%A2%E3%83%BC)
- [4. まとめ](#4.-%E3%81%BE%E3%81%A8%E3%82%81)

前提：Googleドライブ内のすべてのドキュメントは、開くとだいたい以下のようなURLで、編集状態になっている。

`https://docs.google.com/document/d/FILE_ID/edit`

URLを書き換えると、便利な挙動をさせることができる。

## 1. よく使う

### 1.1. 読み取り専用モード

- `https://docs.google.com/document/d/FILE_ID/`**edit**
  ↓
- `https://docs.google.com/document/d/FILE_ID/`**preview**
  へ変更する

### 1.2. 実ファイル（pngやcsv）としてURL参照可能に

以下のフォーマットで、ファイルとして、直接ダウンロードが可能
markdown等からも参照できて便利

- googleドキュメント
  - `https://docs.google.com/document/d/FILE_ID/`**export?format=pdf**
  - `https://docs.google.com/document/d/FILE_ID/`**export?format=doc**
- googleスライド
  - `https://docs.google.com/presentation/d/FILE_ID/`**export/pdf**
  - `https://docs.google.com/presentation/d/FILE_ID/`**export/pptx**
- googleシート
  - `https://docs.google.com/spreadsheets/d/FILE_ID/`**export?format=xlsx**
  - `https://docs.google.com/spreadsheets/d/FILE_ID/`**export?format=pdf**
  - `https://docs.google.com/spreadsheets/d/FILE_ID/`**export?format=csv**
- Google描画
  - `https://docs.google.com/drawings/d/FILE_ID/`**export/svg**
  - `https://docs.google.com/drawings/d/FILE_ID/`**export/pdf**
  - `https://docs.google.com/drawings/d/FILE_ID/`**export/jpg**

googleスライドは、ページ単位でも可能

- スライドのページをexport
  - `https://docs.google.com/presentation/d/FILE_ID/`**export/png?pageid=PAGE_ID**
  - `https://docs.google.com/presentation/d/FILE_ID/`**export/jpg?pageid=PAGE_ID**
  - `https://docs.google.com/presentation/d/FILE_ID/`**export/svg?pageid=PAGE_ID**

---

## 2. 稀に使う

### 2.1. Webビューアーをスキップ（直接ダウンロードリンク）

- 通常共有リンク
  - `https://drive.google.com/open?id=FILE_ID`
- 直接DL
  - `https://drive.google.com/uc?export=download&id=FILE_ID`
  - `https://drive.google.com/uc?id=FILE_ID`
- Googleドライブのウェブビューアーでファイルを開く
  - `https://drive.google.com/file/d/FILE_ID/view`

### 2.2. コピーして自分のものにする

- Original Link:
  - `https://docs.google.com/document/d/FILE_ID/`**edit**
- Copy Link:
  - `https://docs.google.com/document/d/FILE_ID/`**copy**

パラメーターとして、以下が設定可能

- **?copyComments=true**
  - コピーしたドキュメントに元のドキュメントのコメントを含める場合
- **?includeResolvedCommentsOnCopy=false**
  - 解決されたコメントのコピーをスキップ
- **?copyCollaborators=false**
  - コピーされたドキュメントを元の共同編集者と共有しない

Googleフォームにも使用できるが、フォームの所有者がフォームへのアクセスを許可した場合にのみ、フォームは別のユーザーのGoogleアカウントにコピーされ流。

### 2.3. テンプレート共有を目的としたプレビューモード

`/copy`と似ているが、 `/template/preview`とすることで、テンプレートリンクになる（プレビューリンクとコピーの作成リンクの組み合わせ）
この時、**テンプレートを使用**ボタンも表示されます（このボタンをクリックすると、元のドキュメントのコピーが作成されます。そのコピーは、操作したユーザー所有になり、Googleドライブに配置されます）

このモードは、**コピーを作成**ボタンをクリックするのとは異なり、Googleドライブへコピーする前に、内容を見ることができます。
また、新しくコピーされたドキュメントのファイル名に「コピー」とつきません。

### 2.4. コピーするときにユーザーを招待する

ドキュメントをコピーしたGoogleユーザーは、ドキュメントをコピーした直後に特定のGoogleアカウントとドキュメントを共有するように求められます。

- `https://docs.google.com/document/d/FILE_ID/copy?userstoinvite=EMAIL_ADDRESS`

### 2.5. 任意のDriveフォルダーに、ドキュメントを新規作成

- `https://docs.google.com/document/create?usp=drive_web&folder=FOLDER_ID&authuser=0`

---

## 3. ほとんど使わない

### 3.1. プレゼンター表示モードに

- `https://docs.google.com/presentation/d/FILE_ID/`**present?slide=id.p21**
- `https://docs.google.com/presentation/d/FILE_ID/`**preview?rm=minimal**
- `https://docs.google.com/presentation/d/15CK...x4F8/`**preview?rm=full**

### 3.2. Webページに埋め込む

```html
<iframe src="https://docs.google.com/document/d/FILE_ID/preview" height="600px" width=“800px" allowfullscreen >
</iframe>
```

Googleのブランディングとプレーヤーコントロールを削除する場合、`rm=minimal`を、iframeリンクに追加します（rmとは、レンダリングモードのこと）

さらに、下記のように記載すれば、レスポンシブに表示させることもできます。

```html
<style>
  .responsive-google-slides {
    position: relative;
    padding-bottom: 56.25%;
    /* 16:9 Ratio */
    height: 0;
    overflow: hidden;
  }

  .responsive-google-slides iframe {
    border: 0;
    position: absolute;
    top: 0;
    left: 0;
    width: 100% !important;
    height: 100% !important;
  }
</style>

<div class="responsive-google-slides">
  <iframe
    src="https://docs.google.com/presentation/d/e/FILE_ID/embed?start=false&loop=false&delayms=3000&rm=minimal"
  ></iframe>
</div>
```

### 3.3. ユニバーサルファイルビューアー

- `https://docs.google.com/viewer?url=`**https://example.pdf**

## 4. まとめ

googleが、これらURLによる挙動をあまりオープンにしていないが、便利なものばかりなので、覚えておくと得
