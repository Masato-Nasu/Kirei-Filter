# kirei-filter

画像を入れると、AI が内容を見て補正方針を提案する PWA 試作です。

- 顔 / 食事 / デザイン / プロダクト / 室内 / その他 を自動判定
- Before / After 表示
- PWA 対応
- 初回アクセス時のみキーワード認証
- 認証は Cloudflare Pages Functions 側でも確認

## 動作構成

- Frontend: HTML / CSS / JavaScript
- Backend: Cloudflare Pages Functions
- AI: OpenAI API

## フォルダ構成

```text
kirei-filter/
├─ index.html
├─ style.css
├─ app.js
├─ manifest.webmanifest
├─ sw.js
├─ icons/
│  ├─ icon-192.png
│  └─ icon-512.png
└─ functions/
   └─ api/
      ├─ analyze.js
      ├─ auth.js
      ├─ auth-status.js
      └─ logout.js
```

## Cloudflare に設定する値

Cloudflare Pages の **Settings → Variables and Secrets** に追加してください。

### Secrets

- `OPENAI_API_KEY` = OpenAI API キー
- `ACCESS_KEYWORD` = 初回認証に使うキーワード

### Variables

- `OPENAI_MODEL` = `gpt-4.1-mini`

## デプロイ

Cloudflare Pages へ直接デプロイする場合:

```powershell
npx.cmd wrangler pages deploy . --project-name ai-kirei-filter
```

## GitHub に上げるとき

この ZIP を解凍し、`kirei-filter` フォルダの中身をそのままリポジトリに入れてください。

例:

```text
your-repo/
├─ index.html
├─ style.css
├─ app.js
├─ manifest.webmanifest
├─ sw.js
├─ icons/
└─ functions/
```

Cloudflare Pages を GitHub 連携で使う場合も、そのまま利用できます。

## 注意

- `OPENAI_API_KEY` は **Secret** にしてください
- `ACCESS_KEYWORD` も **Secret** にしてください
- PWA はキャッシュが残ることがあるため、反映確認時は再読み込みやシークレットモード確認が安全です

## ライセンス

試作用
