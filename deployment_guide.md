# recoco HP 公開・運用ガイド

ホームページの一般公開と、LINE・Instagramとの連携方法についての手順書です。

## 1. ホームページを一般公開する方法

現在、ホームページのファイルはあなたのパソコンの中（Dropbox内）にしかありません。
これを世界中の人が見られるようにするには、「サーバー」にアップロードする必要があります。
最も簡単で無料の方法として「Vercel（バーセル）」または「Netlify（ネットリファイ）」をおすすめします。

### おすすめ：Vercelを使う方法（一番簡単です）

1.  **Vercelのアカウント作成**: [https://vercel.com/](https://vercel.com/) にアクセスし、「Sign Up」からアカウントを作ります（GitHubアカウントがあれば連携、なければEmailで作成）。
2.  **CLIのインストール（またはドラッグ&ドロップ）**: 
    - 難しい操作が苦手な場合は、Vercelのダッシュボードにある「Add New Project」から、GitHub経由で公開するのが一般的です。
    - もしくは「Netlify Drop」([https://app.netlify.com/drop](https://app.netlify.com/drop)) なら、`Recoco_HP` フォルダごとブラウザにドラッグ＆ドロップするだけで公開できます。**こちらが一番簡単かもしれません。**

#### Netlify Dropの手順（推奨）
1.  [Netlify Drop](https://app.netlify.com/drop) にアクセスします。
2.  `Recoco_HP` フォルダを、画面の点線枠内にドラッグ＆ドロップします。
3.  数秒でアップロードが完了し、完了画面にURL（例: `random-name.netlify.app`）が表示されます。これで公開完了です！
4.  **独自ドメイン**（例: `recoco-nurse.com`）を使いたい場合は、Netlifyの管理画面からドメイン設定を行う必要があります（ドメインの購入等は別途必要です）。

## 2. LINE・Instagramと連携する方法

HP上のアイコンをクリックしたときに、それぞれのアプリやページが開くように設定します。

### ステップ1: URLを取得する

*   **Instagram**: 
    - 自分のプロフィールページのURLをコピーします。
    - 例: `https://www.instagram.com/recoco_nurse/`
*   **LINE公式アカウント**:
    - LINE Official Account Managerにログインします。
    - 「友だち追加ガイド」または「ホーム」から、友だち追加用のURLを取得します。
    - 例: `https://lin.ee/xxxxx`

### ステップ2: index.htmlを書き換える

`index.html` ファイルを開き、以下の部分（ファイルの下の方、195行目付近）を探して書き換えます。

**変更前:**
```html
<div class="sns-links">
    <a href="#" class="sns-icon">Instagram</a>
    <a href="#" class="sns-icon">LINE</a>
</div>
```

**変更後（例）:**
`href="#"` の `#` の部分を、ステップ1で取得したURLに置き換えます。

```html
<div class="sns-links">
    <a href="https://www.instagram.com/あなたのアカウントID/" class="sns-icon" target="_blank">Instagram</a>
    <a href="https://lin.ee/あなたのID" class="sns-icon" target="_blank">LINE</a>
</div>
```

*   `target="_blank"` を追加すると、クリックしたときに新しいタブで開くようになります（推奨）。

## 今後の更新について

写真や文章を変えたいときは、今回のように `index.html` や画像を直接編集し、再度Netlifyなどにドラッグ＆ドロップすれば更新されます。
