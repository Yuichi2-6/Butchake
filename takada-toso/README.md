# 高田塗装（デモサイト）

インベストデザイン株式会社主催のセミナーで「Claude Codeによるコーポレートサイト制作」の事例として使用するダミー企業サイトです。実在の企業・人物とは関係ありません。

このリポジトリでは `takada-toso/` を独立したAstroプロジェクトとして、ルートの `BUTCHAKE` サイトとは別管理にしています（1つのリポジトリで複数の企業サイトをClaude Codeが管理できることを示すデモ構成）。

## セットアップ

```
cd takada-toso
npm install
npm run dev      # http://localhost:4321
npm run build    # dist/ に静的書き出し
npm run preview  # ビルド結果をローカル確認
```

## 構成

- `src/pages/index.astro` — トップページ
- `src/components/` — Header / Hero / Strengths / Services / Works / Flow / Company / Contact / Footer
- `public/images/` — プレースホルダーSVG画像（実写真差し替え可）
