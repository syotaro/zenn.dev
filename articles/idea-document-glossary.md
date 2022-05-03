---
title: "技術用語の解釈メモ"
emoji: "🗂"
type: "idea" # tech: 技術記事 / idea: アイデア
topics: [document]
published: true
---

## 概要

よく目にするが、メモっておかないと、ずれそうな用語をメモっておく

なぜか？

- チーム開発、プロジェクト活動する時、認識ずれを予防できるかどうかは大きな要素。
- 自分のプロジェクトでは、この用語をこういうふうに解釈してますよ、と先にポンと出せたら、認識ずれはだいぶ予防できる。認識すり合わせのスピードを上げられある。
- 各ステークホルダー（ユーザー、PO、デザイナー、エンジニア、マーケター、営業）に作成した用語集のレビューを定期的に行なってもらう

---

- [概要](#%E6%A6%82%E8%A6%81)
- [base16（HEX）とbase64](#base16%EF%BC%88hex%EF%BC%89%E3%81%A8base64)
- [hashと暗号化](#hash%E3%81%A8%E6%9A%97%E5%8F%B7%E5%8C%96)
- [slug（スラッグ）](#slug%EF%BC%88%E3%82%B9%E3%83%A9%E3%83%83%E3%82%B0%EF%BC%89)
- [Lint（Linter）とFormatter](#lint%EF%BC%88linter%EF%BC%89%E3%81%A8formatter)
- [IntelliSense](#intellisense)
- [JSONC](#jsonc)
- [TL;DR（Too Long; Didn't Read.）](#tl%3Bdr%EF%BC%88too-long%3B-didn%27t-read.%EF%BC%89)
- [Vercel](#vercel)
- [ビジネスロジック](#%E3%83%93%E3%82%B8%E3%83%8D%E3%82%B9%E3%83%AD%E3%82%B8%E3%83%83%E3%82%AF)

---

## base16（HEX）とbase64

16進数は、base16なのだが、IT界隈は、HEXと大文字表すことがよくある。
6（Hexa）と10の進数（decimal）でHexadeciminal。

64進数は、base64。画像を文字列で表すときなんかに使われる。

```sh
# base16 (hex)のサンプル
8D756736520697320617765736F6D6521205C6F2F
# base64のサンプル
## A～Zと、a～zと、0～9と記号(+,/) の64文字、 とパディング（余った部分を詰める）のための記号として'='
vbWF3ZXNv3ZXbWU3ZXhIFxvXhIFxvDFxvxvxvLw==
```

たとえば、zenn.devの記事slugについて、特に指定しない場合、「107c4fc35748ce」のような形になるが、これは0〜fまでの16進数でHEX。zennのslugの生成には、https://apidock.com/ruby/SecureRandom/hex/class のような[hexな組み込み関数を使っているとのこと](https://zenn.dev/link/comments/d279423c231152)

[multibase](https://github.com/multiformats/multibase)という、テキストに表示されるベースエンコード（base32、base36、base64、base58など）バイナリのエンコードを明確にするためのプロトコルもある。

## hashと暗号化

hashは一方向。暗号化は、双方向（データを元に戻すことが可能）
各々、たくさんのアルゴリズムがある。

https://qiita.com/KEINOS/items/c92268386d265042ea16

代表的なアルゴリズム

- sha3-512: 128桁のハッシュ。強度が高く、互換性も高い。
- MD5: 32桁のハッシュ値
- crc32: 8桁のハッシュ値。データの誤りを検査等でよく利用される。

hash化する際、ソルト（salt = 塩）と組み合わせることが多い。
ソルトは、パスワードをハッシュ化して保存するときに登場し、ハッシュ値から元のパスワードを推測しにくくするのが目的の文字列。

## slug（スラッグ）

URLなどで、ユニークなIDのような使い方をする文字列。重複しないことが重要。

https://zenn.dev/zenn/articles/what-is-slug

## Lint（Linter）とFormatter

- Linter
  - 静的解析。バグの温床となりうるようなコードを検知して知らせてくれたり、可能であれば自動で修正してくれたりする。代表ツールはESLint。
- Formatter
  - コードを、任意のフォーマットに自動整形したり、使い方が誤っているときにアラートを出したりしてくれる。代表ツールはPrettier。

複数メンバーでこのルールを共有していると、各個人の癖に左右されず、品質を一定に保てる（精神衛生上良い）

## IntelliSense

オートコンプリート、オートコレクトなどの入力支援、操作性向上のための機能の総称

## JSONC

JSONには、本来コメントを書けないし、あと、[末尾のカンマ](https://developer.mozilla.org/ja/docs/Web/JavaScript/Reference/Trailing_commas)（[ケツカンマ](https://developer.mozilla.org/ja/docs/Web/JavaScript/Reference/Trailing_commas)も許容していない。
JSONCはその辺が柔軟

settings.jsonも正確にはJSONCとのこと。
JSONも、JSONCも、拡張子が同じなのに、どこで判別しているのかはよくわからない。
https://github.com/microsoft/node-jsonc-parser

## TL;DR（Too Long; Didn't Read.）

要約のこと。良く、ブログ記事の先頭に記載してある。
「長すぎる。読んでない。」という意味の英略語から転じて、「長すぎるという方のための要約」という意味でも用いられる（インターネットスラング）の1つ。

## Vercel

https://vercel.com/

- NextJSの開発元が提供
- 最近勢いのあるホスティングサービス
- 開発初期はVercelで、その後CloudRunなどに移行している人をよく見かける（zenn.devも）
- 静的サイトのホスティングだけではなくNode.jsアプリも動かせる（Serverless Functions）
- 料金について　https://zenn.dev/lollipop_onl/articles/eoz-vercel-pricing-2020

## ビジネスロジック

![ビジネスロジック](https://docs.google.com/presentation/d/1xUiInh4ojOV_S6gfSNkTa_aoejGfMUsTHsfAJbqa9iY/export/svg?pageid=g126badcf7d4_0_10)

ビジネスロジックは、アプリケーションを、分解する観点の1つ。
そのシステムにおける、システム固有の処理を行う部分。ビジネスロジックを分離することで、別のシステムに流用できる部分を特定するのが楽になったり、影響範囲を限定できたりする。

ビジネスロジックを理解するためには、その境界である、プレゼンテーション層や、データ層を理解する必要がある（ごっちゃにならないように）

- **プレゼンテーション層**
  - そのアプリケーションとユーザや外部システムとのやりとりを担当する層
  - たとえば、古典的なMVCフレームワークによるWebアプリと同様の処理をAPIやCLIアプリケーションとして提供するとき、プレゼンテーション層以外が使い回せるような構造になっていると理想的。
- **データ層**
  - データ層の役割は、ファイルやDBに対してデータを読み書きすること。
  - ビジネスロジックをデータ層と切り離すことで、保存先がファイルなのかRDBなのかを気にかけず、ビジネスロジックを記述できる
  - データ層は、保存先の媒体によらず同じインタフェースをビジネスロジック層に対して提供し、保存先が変わってもデータ層だけ直せばいいというのが理想的
