<!-- classes: title -->

# Chrome Dev Summit 2019
# @SanFrancisco
# Report

---

import yuta from '../images/yuta.jpg'

## Who?

<div class="m-8" />

### YutaSuzuki @TDD#Dev1

<img src={yuta} width={400} />

<div/>

- BigdataETL のバッチ
- Japan Digital Bank 構想の検証
- slack セキュリティ調査

---

## Chrome Dev Summit とは

<div/>

- Google が毎年開催している Web / Frontend Developer のためのグローバルカンファレンス
- Google I/O が全ジャンルであるのに対し、 CDS は Web に特化した内容
- Googler をはじめとして、グローバル企業のエンジニア達が講演する

---

## 復習: 現代のブラウザと Web 開発

- ブラウザ上では JavaScript という言語が動作する
- ブラウザが URL を解釈すること、もしくは JavaScript の処理がサーバと通信し、データを取得する
  - データが重いと遅くなり __UX を損なう__
- Chrome などは新しい機能を随時搭載していっているが、 Safari や IE11 は機能や __JSエンジンすら__ 古い
  - このため __複数ブラウザ対応__ が必要になる
  - 複数ブラウザ対応分、 JS コードが重く/遅くなり __UX を損なう__
- 新機能の中でも、 PC or Android + Chrome だけで物も多く、かつ実用的な段階である
  - ネイティブアプリのようにインストールすることができる (PWA - Progressive Web App)
  - Push Notification
  - バックグラウンドでの通信やキャッシュによる高速化 (Service Worker)

---

## Chrome Dev Summit 2019 傾向

<div/>

- ローディング関連の速度/ UX 向上についての話が多かった
  - webbundle(web ページをまるっと1つのバイナリにする技術)
  - Differencial Loading
- ブラウザに未実装である実験機能(OrignTrial)を用いた UX 向上についての話が多かった
  - SMS Reciever API
  - prefers-reduced-motion
- UX 向上のために Hacky なことをしなくて済む、 DX との両立の側面の話も多かった
  - Dynamic Import などのフレームワークによるサポートの充実
  - ビルド分割(Webpack)の成熟、フレームワークによるデフォルト最適化

---

## Day 1

<div class="m-8"/>

<div class="flex vh-80">
<div class="w-1/6" />
  <div class="items-center w-1/3 schedule-image day1-1">
  </div>
  <div class="w-1/3 schedule-image day1-2">
  </div>
<div class="w-1/6" />
</div>

---

## Day 2

<div class="m-8"/>

<div class="flex vh-80">
<div class="w-1/6" />
  <div class="w-1/3">
    <div class="h-full schedule-image day2-1"></div>
  </div>
  <div class="w-1/3 schedule-image day2-2">
  <day2-2/>
  </div>
<div class="w-1/6" />
</div>

---

## セッション紹介

---

## Keynote

<div/>

- OriginTrials な API をどんどん紹介していきます！
- Google は Next.js に貢献しています！ SQEX ではプロダクション利用されています！
- 将来的に速いサイトにはリワードを、遅いサイトには警告バッジを表示し、改善を促したい

---

## Protecting users on a thriving web

<div/>

- https everywhere が広まるにつれて偽サイトを見破るのが難しくなってきたが、それをブラウザでサポートするよ
  - HTTPS の緑色の表示や安全でないサイトとしての表示、認証局の表示等を試行錯誤している
  - 非 ASCII 文字を交えたフィッシングに対しては、 ASCII のみを解釈して「もしかして？」とサジェストされる
- サードパーティクッキーって本当にいいんだっけ？制限したときのデータを出したよ
  - ads 500サイトで52%低下、ニュースサイトでは62%低下
  - じゃあどうしようというのは目下の課題
    -　そもそも cookie が壊れてるよねという話も当然ある

---

## What's new in sign-up and sign-in

<div/>

- ブラウザの新しい機能を使って認証を楽にすると UX と安全性を両立できるよね
- SMS に届いた認証コードを取得する機能がブラウザに入るよ(最近のネイティブアプリには実装されている)
- WebAuthN による生体認証もできるよ
  - Yahoo!　JAPAN の対応事例は有名
- WebAuthN を使えば 2FA を毎回使わない方法もあるのではないか
  - フォールバック先としてのみ使う
  - 再設定のときのみ使う

---

## Adaptive Loading - Improving the user-experience for millions on low-end devices

<div/>

- ユーザには様々なデバイススペックやネットワーク環境がいるので、当然出し分けを考えるべき
  - 日本ではあまり体感する機会が少なかったが、最近では通信規制 128kbps の問題は大きい
  - 例えば低スペック端末では css アニメーションを間引く(reduce)など
  - フレームレートを下げるという力技も
- データセービングモードを取得する API (navigator.connective.dataSave)
  - ちゃんと意識して機能を振り分けると UX は当然よくなる
- 開発者に与えられる端末でしかテストしないと低スペック端末で動かなくなるので注意しよう
  - 低スペック端末で開発するとパフォーマンス上がる問題

---

## HTML isn't done!

<div/>

- Form しんどくてみんな再発明してたのでちゃんとスタイリングなどできるように最近がんばってるのでもうちょっと待ってね
  - DatePicker とか Select とか
- 当然、 SPA でもそうでなくても Form Control 使うのは UX / a11y 的に前提っぽい

---

## Advancing the web framework ecosystem

<div/>

- Web フレームワークである Angular はビルドや配信周りでの UX サポートを DX と共に両立している
  - v8 からの Differencial Loading や Dynamic Import
  - ビルドや chunk の分割までデフォルトである程度チューニングされている
  - (Ivy (次世代テンプレートエンジン)の型チェックすごいので v9 みなさん触って欲しい)
- React を単体で使っているページの課題解決のために、 Google は Next.js に貢献している
  - 現状普通に React を使っているページでは Cascading Data Fetch が起きているものが多い
  - ビルドまわりの最適化もフレームワークに組み込む
- @babel/preset-modules と Differencial Loading の合わせ技でバンドルを最適化
  - 現状は IE11 対応のために最新ブラウザでは不要なコードが大量に増えている箇所がある
  - type=module を使って出し分ける前提でビルドターゲットを分けることで回避

---

## 私見

---

## UX の義務意識

<div/>

- 海外では多様な状態の人が Web を通じて情報を取得できるようにする「アクセシビリティ」が重視
  - 対応不備には罰則がある地域も
  - 色覚障害向けのコントラストカラーの設定など (最近は OS レベルでダークカラーやハイライトカラーを指定できる)
  - 音声読み上げ向けに、機械にもわかりやすい html 実装
- 金融商品を扱うところでは誤解を誘導する UX をすると金融庁から怒られるらしい
  - 注文後ボタンが変わらないのでもう一度押したら二重注文になるなど
  - または説明と違う UX であるなど
- 公共性の高いサービスの UX も義務化されるのではないか
  - とはいえ直感的ならともかく、数値指標で UX を測るのは難しい
  - 離脱率ノルマとか？

---

## 現実

<div/>

- 日本では UX を本当に追求しているサービスやその話題が少ないこと
  - SEO のための速度向上すら後回しになりがち
  - UX が悪くても独占状態なので許されてしまいがち
- UX 以前に DX の話ばかりになっているように感じる
  - Vuex は Global 変数でしょ？とか
  - 海外の人に聞いたら Atomic Design なんて全然知らないなど

---

## 現実として存在する、わかりやすい課題

<div/>

- もっとも身近なのが、月末にギガが減るユーザ
  - 月末に JS 読み込みエラーのログがある
  - 読み込みが遅いと崩れて表示されたり、ちゃんと進んでいるのか不安だったり
  - 同じボタンをなんども押すなど
- IE 対応により最新ブラウザでも JS ロードが遅い
  - polyfill 全部入りで最新ブラウザ

---

import reduxDdd from '../images/redux-ddd.png'

## 日本のフロントエンドで人気の話題

<img src={reduxDdd} width={800} />

#### 私たちはなぜ SPA で開発するのか / Takuma HANATANI

---

## 本質に向き合えていますか？

<div/>

- UX を提供するためのフロントエンドをしていますか？
  - 初期ロードや画面遷移は十分に速いか？
  - ユーザの利用シーン/スペックを前提としているか？
- DX だけを追求して UX を犠牲にしていないか？
  - 雑に非同期取得を実装してガクッとなるやつ
  - アニメーションをちゃんとやれないでガクッとなるやつ

---

## これから UX にどう向き合うか

---

## ケーススタディ: 銀行の Web の UX

<div/>

- 寡占かつ生活必需サービスなので UX が悪くても使わざるを得ない
  - 遅い、わかりにくい、必要ないものが多い
- UX が悪いしわ寄せをユーザが被っている
  - Web での送金の仕方が分からないため物理 ATM に行くなど

---

## 求められる UX

<div/>

- 簡単な認証
  - パスワードや二要素認証がわかりにくい
  - 例えば SMS のマジックリンクを使うなど
- わかりやすいデザイン
  - 銀行カラーを出しすぎておりナビゲーションに色を活用できていない
  - 統計によると 40 人に 1 人は色弱である。想定した色使いをできているか？
- 速さ
  - 最近は `ギガが無くなる` ケースが多いが、 128kbps での利用を想定できているか？
  - 月末は銀行を利用したいタイミングとギガが無くなるケースが被りがち、無視できない

---

## 問題点を細分化するための分析

<div/>

- Largest Contentful Paint(First Meaningful Paint) の測定
- JavaScript や画像のタイムアウトエラーの測定
- CDN やキャッシュの設定 etc...

<div class="m-8" />

### フロントエンドだけの問題ではない

---

## 数値分析を元に、現在の課題を解決する適切な手法/ UX を

---

## まとめ

<div/>

- 独占状態/生活必需であれば UX が悪いままでも人は使い続けるが、そこに甘んじていいのか？
- 利益とは別に UX を向上させるインセンティブ設計を行う必要があるフェーズではないだろうか
- バックエンドやビジネス要件含めて UX は作られる。フロント開発者以外も課題意識を
