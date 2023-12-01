# Nuxt tutorial

app.vueがデフォルトのエントリポイント

コンポーネント: `components/`
明示的にインポートしなくてもアプリケーション全体で自動的に使用できる。

ページ: `pages/`
app.vueなどのルートファイルから`NuxtPage`を使って表示できる。

``` vue
<NuxtLayout>
  <NuxtPage />
</NuxtLayout>
```

Layouts: `layouts/`
app.vueで`NuxtLayout`を定義しておく必要がある
`<slot />`を入れることによってコンテンツを表示するコンポネートを呼べる

``` vue
<template>
  <div>
    <AppHeader />
    <slot />
    <AppFooter />
  </div>
</template>
```

Asset: assets/
/font, /image, /stylesheet などのアセットを配置するフォルダ
assetsフォルダ内の画像を取得させるには以下のように記述する必要がある
`<img src="@/assets/image/small.png" alt="Discover Nuxt3" />`
グローバルスタイルの設定
nuxt.config.tsの下に追加
``` vue
module.exports = {
  css: [
    "@/assets/scss/main.css"
  ],
}
```
