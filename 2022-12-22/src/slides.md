---
theme: seriph
layout: cover
class: 'text-center justify-center'
---

<style>
  .slidev-layout.default p {
    line-height: 1.7;
  }
  .slidev-layout h1 {
    margin-bottom: 2rem!important;
  }
  .slidev-code-wrapper {
    height: 100%;
  }
  .slidev-code {
    height: 100%;
    overflow: auto;
  }
</style>

# Webサイト制作に特化したフレームワーク『Astro』

takeda.k

---
layout: default
class: text-25px leading-normal
---

# 前提

## Webサイト

<p class="text-18px">
  マーケティングサイト、企業のコーポレートサイト、ドキュメントサイト、ブログ、ポートフォリオなど
  <br />
  静的なコンテンツが多く、情報を提供することが目的のサイト
</p>


<div class="mt-40px" />

## Webアプリ
<p class="text-18px">
  TODOリスト、SNSなど
  <br />
  インタラクティブ（双方向）な機能によってサービスを提供するサイト
</p>

<div v-click class="mt-50px text-25px underline underline-offset-8">
  今回はWebサイトに焦点を当てた発表になります
</div>

---
layout: default
class: text-18px leading-normal
---

## Astroとは


AstroはWebサイト制作に特化したフレームワーク

> Astroは、コンテンツにフォーカスした高速なWebサイトを構築するためのオールインワンWebフレームワークです。

<p class="text-12px text-right">

[Astroを選ぶ理由](https://docs.astro.build/ja/concepts/why-astro/)より引用
</p>

<img src="https://raw.githubusercontent.com/withastro/astro/main/assets/social/banner-minimal.png" width="">



---
layout: default
class: text-25px leading-normal
---

# Astroの特徴 １

- サーバーファースト
  <p class="text-16px">
  
  AstroはReactのようなSPAではなくHTMLをサーバーサイドでレンダリングするMPA（マルチページアプリケーション）を採用している（Wordpressなどと同じアプローチ）  
  SPAと比較した場合、初期表示が速くSEOにも強い（ただしページ遷移はSPAほど速くない）  
  MPAをHTML、CSS、JavaScript（TypeScript）のみで実現できる

  </p>
- デフォルトで高速
  <p class="text-16px">

    Astroはビルド時にJavaScriptを排除することで、クライアントサイドで実行されるJavaScriptをほぼ0にする。  
    Reactなどを使っていてクライアントサイドでのJavaScriptの実行が必要な時はJavaScriptを読み込み実行するタイミングを明示的に指定することができる（[Astro Islands](https://docs.astro.build/en/concepts/islands/)）

    [高速であることが売上やコンバージョン率の向上につながる。](https://docs.astro.build/ja/concepts/why-astro/#%E3%83%87%E3%83%95%E3%82%A9%E3%83%AB%E3%83%88%E3%81%A7%E9%AB%98%E9%80%9F)

  </p>

---
layout: default
class: text-25px leading-normal
---

# Astroの特徴 2

- 簡単に使える
  <p class="text-16px">

    基本的なHTML, CSS, JavaScriptが書ければすぐに使える。  
    部分的にReactやVueなどのUIライブラリを使用することも可能。  
    Reactなどと同じくコンポーネント指向な開発ができるため従来の開発環境（Gulp, Webpackなど）と比べても開発者体験が良い。

  </p>
- 充実した機能と柔軟性（integrations）
  <p class="text-16px">

    [integrations](https://astro.build/integrations/)というwordpressでいうプラグインのような機能が100以上用意されている。<br />
    [サイトマップ](https://docs.astro.build/en/guides/integrations-guide/sitemap/)、[SEO](https://github.com/jonasmerlin/astro-seo#readme)、[robots-txt](https://github.com/alextim/astro-lib/tree/main/packages/astro-robots-txt#readme)などWebサイト制作で欠かせないものから[画像最適化](https://docs.astro.build/en/guides/integrations-guide/image/)のためのプラグインなども存在している。
  </p>

---
layout: default
class: text-25px leading-normal
---

# Astroの特徴 3
-  場所を選ばない
<p class="text-16px">

  エッジ環境含め場所を選ばずどこでもデプロイできる
  <br />
  また、主要なデプロイサービスであれば
  [integrationとデプロイガイド](https://docs.astro.build/ja/guides/deploy/)
  が用意されており簡単にデプロイできる。
</p>

<img src="/deploy_service.png" width="400">

---
layout: default
class: text-20px leading-normal
---

# Astroのデメリット

- MPAなのでSPAのようなページ遷移はできない
- イベントリスナーを登録（ボタンをクリックした時の動作など）する時は命令的に記述する必要がある。宣言的に記述したい場合はReactやVueなどを使用する。

<div>

```js
  // 命令的
  const handleClick = () => {
    // クリックした時の処理
  }
  const btn = document.getElementById('hoge')
  btn.addEventListener('click', handleClick)
```
</div>

<div>

```jsx
  // 宣言的
  const handleClick = () => {
    // クリックした時の処理
  }

  <button onClick={handleClick}>
    ボタン
  </button>
```
</div>

---
layout: cover
class: text-center justify-center
---

# 実際に使ってみる

---
layout: default
class: text-16px leading-normal
---

# プロジェクトの作成
以下のコマンドでプロジェクトを作成

<div>

```bash
yarn create astro
```
</div>

対話形式でいくつか質問されるので適当に答える（recommendedになっているものを選べばOK）
<img src="/astro-init.png" class="h-300px rounded block mt-20px" />

---
layout: default
class: text-16px leading-normal
---

# ディレクトリ構成

<div>

```bash
├── README.md
├── astro.config.mjs
├── package.json
├── public
│   └── favicon.svg
├── src
│   ├── components
│   │   └── Card.astro
│   ├── env.d.ts
│   ├── layouts
│   │   └── Layout.astro
│   └── pages
│       └── index.astro
├── tsconfig.json
└── yarn.lock
```
</div>

<div class="mt-30px" />
基本的にはNext.jsなどと同じでsrcの中で作業する。<br />
Integrationsなどの設定はastro.config.mjsに記述する。

---
layout: default
class: text-16px leading-normal
---

## コンポーネント

<div class="mt-20px relative h-300px">

```tsx
// src/components/Card.astro
---
// コンポーネントスクリプト (JavaScript / TypeScript)
export interface Props {
  title: string
  body: string
  href: string
}

const { href, title, body } = Astro.props
---

<!-- コンポーネントテンプレート (HTML + JS Expressions) -->
<li class="link-card">
  <a href={href}>
    <h2>
      {title}
      <span>&rarr;</span>
    </h2>
    <p>
      {body}
    </p>
  </a>
</li>
<style>
  .link-card {
    list-style: none;
    display: flex;
    padding: 0.15rem;
    background-color: white;
    background-image: var(--accent-gradient);
    background-size: 400%;
    border-radius: 0.5rem;
    background-position: 100%;
    transition: background-position 0.6s cubic-bezier(0.22, 1, 0.36, 1);
    box-shadow: 0 4px 6px -1px rgba(0, 0, 0, 0.1),
      0 2px 4px -2px rgba(0, 0, 0, 0.1);
  }

  .link-card > a {
    width: 100%;
    text-decoration: none;
    line-height: 1.4;
    padding: 1rem 1.3rem;
    border-radius: 0.35rem;
    color: #111;
    background-color: white;
    opacity: 0.8;
  }
  h2 {
    margin: 0;
    font-size: 1.25rem;
    transition: color 0.6s cubic-bezier(0.22, 1, 0.36, 1);
  }
  p {
    margin-top: 0.5rem;
    margin-bottom: 0;
    color: #444;
  }
  .link-card:is(:hover, :focus-within) {
    background-position: 0;
  }
  .link-card:is(:hover, :focus-within) h2 {
    color: rgb(var(--accent));
  }
</style>

```

</div>

<p class="mt-20px">

コンポーネントはUIを再利用可能な部品に分割したもの
<br />
Astroコンポーネントは、**コンポーネントスクリプト**と**コンポーネントテンプレート**の2つで構成される
<br />
親コンポーネントからのpropsは**Astro.props**というグローバル変数から取得する
<br />
コンポーネントスクリプトの変数は中括弧{}で囲うことでコンポーネントテンプレートで使用できる

</p>

---
layout: default
class: text-16px leading-normal
---

## レイアウト

<div class="mt-20px relative h-300px">

```tsx
// src/layouts/Layout.astro
---
export interface Props {
  title: string
}

const { title } = Astro.props
---

<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="UTF-8" />
    <meta name="viewport" content="width=device-width" />
    <link rel="icon" type="image/svg+xml" href="/favicon.svg" />
    <meta name="generator" content={Astro.generator} />
    <title>{title}</title>
  </head>
  <body>
    <slot />
  </body>
</html>
<style is:global>
  :root {
    --accent: 124, 58, 237;
    --accent-gradient: linear-gradient(
      45deg,
      rgb(var(--accent)),
      #da62c4 30%,
      white 60%
    );
  }
  html {
    font-family: system-ui, sans-serif;
    background-color: #f6f6f6;
  }
  code {
    font-family: Menlo, Monaco, Lucida Console, Liberation Mono,
      DejaVu Sans Mono, Bitstream Vera Sans Mono, Courier New, monospace;
  }
</style>

```
</div>

<p class="mt-20px">

各ページの共通のタグで構成されたコンポーネント
<br />
ヘッダーやフッターなども入れることが多い
<br />
[slot](https://docs.astro.build/ja/core-concepts/astro-components/#%E3%82%B9%E3%83%AD%E3%83%83%E3%83%88)の中に各ページから受け取ったコンテンツが入る
<br />
styleタグに[is:global](https://docs.astro.build/ja/guides/styling/#%E3%82%B0%E3%83%AD%E3%83%BC%E3%83%90%E3%83%AB%E3%82%B9%E3%82%BF%E3%82%A4%E3%83%AB)をつけるとグローバルに適用される
</p>


---
layout: default
class: text-16px leading-normal
---

## ページ

<div class="mt-20px relative h-300px">

```tsx
// src/pages/index.astro
---
import Layout from '@/layouts/Layout.astro'
import Card from '@/components/Card.astro'
---

<Layout title="Welcome to Astro.">
  <main>
    <h1>Welcome to <span class="text-gradient">Astro</span></h1>
    <p class="instructions">
      To get started, open the directory <code>src/pages</code> in your project.<br
      />
      <strong>Code Challenge:</strong> Tweak the "Welcome to Astro" message above.
    </p>
    <ul role="list" class="link-card-grid">
      <Card
        href="https://docs.astro.build/"
        title="Documentation"
        body="Learn how Astro works and explore the official API docs."
      />
      <Card
        href="https://astro.build/integrations/"
        title="Integrations"
        body="Supercharge your project with new frameworks and libraries."
      />
      <Card
        href="https://astro.build/themes/"
        title="Themes"
        body="Explore a galaxy of community-built starter themes."
      />
      <Card
        href="https://astro.build/chat/"
        title="Community"
        body="Come say hi to our amazing Discord community. ❤️"
      />
    </ul>
  </main>
</Layout>

<style>
  main {
    margin: auto;
    padding: 1.5rem;
    max-width: 60ch;
  }
  h1 {
    font-size: 3rem;
    font-weight: 800;
    margin: 0;
  }
  .text-gradient {
    background-image: var(--accent-gradient);
    -webkit-background-clip: text;
    -webkit-text-fill-color: transparent;
    background-size: 400%;
    background-position: 0%;
  }
  .instructions {
    line-height: 1.6;
    margin: 1rem 0;
    border: 1px solid rgba(var(--accent), 25%);
    background-color: white;
    padding: 1rem;
    border-radius: 0.4rem;
  }
  .instructions code {
    font-size: 0.875em;
    font-weight: bold;
    background: rgba(var(--accent), 12%);
    color: rgb(var(--accent));
    border-radius: 4px;
    padding: 0.3em 0.45em;
  }
  .instructions strong {
    color: rgb(var(--accent));
  }
  .link-card-grid {
    display: grid;
    grid-template-columns: repeat(auto-fit, minmax(24ch, 1fr));
    gap: 1rem;
    padding: 0;
  }
</style>

```
</div>

<p class="mt-20px">

pages以下に作成したディレクトリやファイルに基づいてURLが決まる（ファイルベースルーティング）
<br />
Layoutコンポーネントをimportし全体をラップする
<br />
[動的なページ](https://docs.astro.build/ja/core-concepts/routing/#%E5%8B%95%E7%9A%84%E3%83%AB%E3%83%BC%E3%83%86%E3%82%A3%E3%83%B3%E3%82%B0)の場合はファイル名に角括弧[]をつける（例：[id].astro）
</p>

---
layout: cover
class: text-center justify-center
---

# AstroにReactを導入してみる

---
layout: default
class: text-16px leading-normal
---

## 1. Integrationの追加と設定

astro addコマンドを使うことで依存関係のインストールから設定ファイルの記述まで一括で行える
<div class="mt-20px relative">

```bash
yarn astro add react
```

<img src="/add_react.png" width="600" class="block mt-20px">

</div>

---
layout: default
class: text-16px leading-normal
---

## 2. Reactコンポーネント作成

<div class="mt-20px relative h-400px">

```tsx
// src/components/Menu.tsx
import { useState } from 'react'

export const Menu = () => {
  const [isOpen, setIsOpen] = useState(false)

  const handleClick = () => {
    setIsOpen((prev) => !prev)
  }

  return (
    <div className="relative">
      <button onClick={handleClick}>
        Menu
      </button>
      {isOpen && (
        <ul className="border absolute left-[-80px] top-[40px] bg-gray-300 rounded-lg flex flex-col items-center justify-center w-[200px] min-h-[150px]">
          <li>
            <a href="/" className="text-white font-bold">
              Home
            </a>
          </li>
        </ul>
      )}
    </div>
  )
}
```

</div>

---
layout: default
class: text-16px leading-normal
---

## 3. 作成したReactコンポーネントをAstroコンポーネントで呼び出す

<p>

インタラクティブなReactコンポーネントはクライアントサイドでのJavaScriptの実行が必要になるためclient:*ディレクティブをつける必要がある。  
*の部分に記述する値によってどのタイミングでコンポーネントを読み込むかを指定できる。  
[利用可能なディレクティブの一覧](https://docs.astro.build/ja/reference/directives-reference/#client-directives)

</p>

<div class="mt-20px relative h-250px">

```tsx {3,19}
// src/layouts/Layout.astro
---
import { Menu } from '@/components/Menu'

export interface Props {
  title: string
}

const { title } = Astro.props
---

<!DOCTYPE html>
<html lang="en">
  <head>
    ・・・
  </head>
  <body>
    <header class="mx-auto max-w-screen-sm mt-8">
      <Menu client:load />
    </header>
    <main class="mx-auto max-w-screen-sm py-16">
      <slot />
    </main>
  </body>
</html>

```

</div>

---
layout: default
class: text-16px leading-normal
---

## デモサイト

Astro × microCMS  

[https://astro-microcms.pages.dev/](https://astro-microcms.pages.dev/)  

ソースコード  

[https://github.com/nado1001/astro-microcms](https://github.com/nado1001/astro-microcms)  

---
class: common text-20px leading-normal gap-2
---

# まとめ


- AstroはWebサイト制作に特化したフレームワーク  
- ビルド時にできる限りJavaScriptを排除することで初期表示を高速化
- ReactなどのUIライブラリを部分的に利用できコンポーネント指向な開発が可能

<div v-click class="mt-30px font-bold">
   Webサイトを作る際はぜひAstroを検討してみてください！
</div>

---
layout: center
---

# ご静聴ありがとうございました！