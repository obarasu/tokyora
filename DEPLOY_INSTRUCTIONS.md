# Tokyora - Cloudflare Pages デプロイ手順

## 前提条件
- ✅ GitHubリポジトリ作成済み: https://github.com/obarasu/tokyora
- ✅ ドメイン取得済み: tokyora.com (Cloudflare Registrar)
- ⏳ Cloudflare Pagesデプロイ（これから）

---

## Cloudflare Pages デプロイ手順

### 1. Cloudflare Dashboardにログイン
https://dash.cloudflare.com/

### 2. Workers & Pages → Create application

### 3. "Pages" タブ → "Connect to Git"

### 4. GitHubアカウント接続
- "Connect GitHub" ボタンをクリック
- GitHubで認証
- リポジトリアクセス許可（`obarasu/tokyora` を選択）

### 5. プロジェクト設定
- **Project name:** `tokyora`
- **Production branch:** `main`
- **Build settings:**
  - Framework preset: `Astro`
  - Build command: `npm run build`
  - Build output directory: `dist`

### 6. 環境変数（不要）
この時点では環境変数は不要です。

### 7. "Save and Deploy" をクリック

---

## デプロイ後

### 初回デプロイ（自動）
- 約2-3分でビルド完了
- Cloudflareが自動的にURLを生成: `tokyora.pages.dev`

### カスタムドメイン接続

デプロイ完了後：

1. **Custom domains** タブに移動
2. **"Set up a custom domain"** をクリック
3. ドメインを入力: `tokyora.com`
4. Cloudflareが自動的にDNS設定を検出（同じアカウントなので）
5. **"Activate domain"** をクリック
6. SSL証明書が自動発行される（数分）

### wwwサブドメインも追加（推奨）

1. 同じく **"Set up a custom domain"**
2. `www.tokyora.com` を入力
3. Activate

これで `tokyora.com` と `www.tokyora.com` 両方でアクセス可能になります。

---

## 確認

### サイトが表示されるか確認
- https://tokyora.pages.dev （Cloudflare自動URL）
- https://tokyora.com （カスタムドメイン）

### 記事が表示されるか確認
- Tokyo's Shiny Buildings
- Tokyo Matcha Ice Cream
- Cool Japan Failed
- Ginza Novo Failed

---

## 今後の更新方法

**自動デプロイ設定済み！**

1. 記事を追加・編集
2. `git add -A && git commit -m "記事追加"`
3. `git push`
4. Cloudflareが自動的にビルド＆デプロイ（2-3分）

手動操作は不要です🎉

---

## トラブルシューティング

### ビルドエラーが出た場合
Cloudflare Pagesの "Deployments" タブでログを確認。

### ドメイン接続がうまくいかない場合
- DNS設定を確認（Cloudflare DNS）
- SSL証明書の発行を待つ（最大15分）

### 画像が表示されない場合
- Astroのビルド設定を確認
- 画像パスが正しいか確認

---

**所要時間:** 約10分（ビルド時間含む）
**難易度:** 簡単（全部ボタンクリックだけ）
