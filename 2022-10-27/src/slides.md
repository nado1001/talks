---
theme: seriph
layout: cover
class: 'text-center justify-center'
---

<style>
  .slidev-layout.default p {
    line-height: 1.5;
  }
</style>

# 心理的安全性を保つためのコードレビュー文化を育てたい

takeda.k

---
layout: default
class: text-25px leading-normal
---

# 心理的安全性とは何か

<div class='mt-8' v-click="1">
  対人関係においてリスクある行動を取ったときの結果に対する個人の認知の仕方
</div>

<div class="mt-40px" />

<ul v-click="2" class="mt-30px">
  <li>安心して発言・行動できる環境</li>
  <li class="mt-30px">チーム内での居心地の良さ</li>
</ul>

---
layout: default
class: text-25px leading-normal
---

## 効果的なチームに必要な要素

<div class="flex gap-20px">

  <div>
    <p class="">Googleのリサーチチーム（re:Work）による調査の結果、心理的安全性はパフォーマンスの高いチームを構築するために最も重要な要素であると結論づけている</p>
  </div>

  <img src="/psychological-safety.png" class="h-90 rounded" />
</div>

<div class="mt-40px" />

> https://rework.withgoogle.com/jp/guides/understanding-team-effectiveness

---
layout: default
class: text-25px leading-normal
---

## コードレビューでも心理的安全性を保ちたい

<div class="mt-40px" />

コードレビューでは

<div class="mt-30px">
  ・ githubを用いたテキストベースのコミュニケーションであること
</div>

<div class="mt-30px -indent-30px pl-[30px]">
  ・ 基本的には相手の考えていることとは違う意見を伝える（相手のコードを指摘する）こと
</div>

<div class="mt-30px">
  の2点から心理的安全が損なわれてしまう傾向がある
</div>

---
layout: default
class: text-25px leading-normal
---

## コードレビューにおける心理的安全性

<div v-click="1" class="mt-30px -indent-30px pl-[30px]">
  ・ 技術レベルに関係なく誰もがレビューに参加できる環境（チーム全員が発言しやすい環境）
</div>

<div v-click="2" class="mt-30px">
  ・ レビュアーが相手と相手のコードを尊重してレビューできていること
</div>

<div v-click="3" class="mt-30px -indent-30px pl-[30px]">
  ・ レビュイーがレビュアーの指摘に対して不健全な感情を抱かないこと<br/>これによってレビュアーが意見しやすい環境になっていること
</div>

<div v-click="4" class="mt-30px">
  これら踏まえてコードレビューにおいても心理的安全性を保つための具体的な取り組みをいくつか提案します。
</div>

---
layout: cover
class: text-center justify-center
---

# 具体的な取り組み

---
layout: default
class: text-16px leading-normal
---

## 相手の心理的安全に配慮する

<div class="mt-30px" />

<div v-click="1">
  <p class="text-25px">・相手のコードを尊重したレビューを書く</p>
  相手のコードを頭ごなしに否定しない<br />
  悪い点だけでなくそのコードの中にある良い点も合わせて書く等...

  ```ts
  例： この部分の処理はこのように書くとコードの記述量が減って良いかもしれないです。とはいえ、〇〇さんの書き方の方が可読性は高いと思います。
  ```
</div>

<div class="mt-30px" />

<div v-click="2">
  <p class="text-25px">・感嘆符（！）や絵文字<twemoji-star-struck />を使う</p>
  <p class="">テキストベースのコミュニケーションでは感情が伝わりにくく、相手の受け取り方によってはネガティブな印象を与えてしまう可能性がある</p>
  <p class="">感嘆符や絵文字はテキストにおいて感情を表現するためのツール</p>
  <p class="text-13px">※感嘆符や絵文字でのコミュニケーションが合わない人もいるため、その場合は相手にネガティブな印象を与えそうな表現がないか確認する</p>

  LGTMする際に[LGTMOON](https://lgtmoon.herokuapp.com/)などの画像を使うのもおすすめ（私はapproveする際によく使っています）
</div>

---
layout: default
class: text-16px leading-normal
---

## 誰でもレビューに参加できる環境を作る

<div class="mt-30px" />

<div v-click="1">
  <p class="text-25px">・レビュイーに対しての質問OK</p>
  コードの指摘だけでなくわからない箇所や難しい処理があればレビュイーに対して質問する  

  ```ts
  例： 
  ここの処理ってこういう解釈であってますか？

  これってどういうライブラリなんですか？
  ```
</div>

<div class="mt-40px" />

<div v-click="2">
  <p class="text-25px">・感想を言うだけでもOK</p>
  指摘するところがなければコードの良い箇所に対する感想を言うという形でレビューに参加するのもOK<br />
  ポジティブな感想をもらえることでレビュイーのモチベーションの向上にもつながる


  ```ts
  例：
  この書き方良いですね！参考にさせていただきます。

  このライブラリの導入goodです👍
  ```
</div>

---
layout: default
class: text-16px leading-normal
---

## レビュアーのコメントにラベルをつける

<div class="flex justify-between mt-40px gap-20px" v-click="1">
  <div>
    <p>レビューアー側のコメントの重み付け</p>
    <p>コメントにラベルをつけることでレビュアーの意図を正しく<br />伝えられる</p>
    <p>レビュアーとレビュイーの対等な関係づくりに寄与する</p>
  </div>

  <img src="/review-label.png" class="h-200px rounded" />
</div>


<div class="mt-20px" />

<div v-click="2">

  ```ts
  例：
  [MUST]
  データがない時の処理がないので追加お願いします！

  [IMO]
  ここの変数名は〇〇ではなく××でも良いかなと思いました🤔

  [NITS]
  ここは変数に格納せずそのまま書いてしまっても良いかもなと思いました🤔
  ```

</div>

---
layout: default
class: text-16px leading-normal
---

## コードレビューのアンチパターン

<div class="mt-30px" />

1. コメントが怖い
2. 理由がない
3. 誹謗中傷
4. 大量コメント
5. 長大な議論

参考記事  
https://blog.toshimaru.net/hrt-review/

---
class: common text-20px leading-normal gap-2
---

# まとめ

<div class="mt-30px" />

- 心理的安全性は安心して発言・行動できる環境のこと
- コードレビューでは相手の考えていることとは違う意見を伝えるため心理的安全が損なわれやすい傾向がある
- レビュアーは相手のコードを尊重する・感嘆符や絵文字を使うなどの工夫で相手の心理的安全に配慮すると良い
- レビューではコードの指摘だけでなく質問や感想を言うだけでもok
- レビューの内容に応じてラベルで重み付けをすることでレビュアーの意図を正しく伝えることができる
- 心理的安全性が保たれることでチームのパフォーマンス向上にもつながる
  <br />→ 幸せになれる<twemoji-party-popper />

---
layout: center
---

# ご静聴ありがとうございました！