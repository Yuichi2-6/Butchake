# Butchake

株式会社BUTCHAKE コーポレートサイト。

## リポジトリ構成

- `design/` — Claude Design が生成したデザインリファレンス。**このフォルダはデザイン側が更新する権限を持つ。実装側は編集しない。**
  - `BUTCHAKE Site.dc.html` — デザイン本体（ブラウザで直接開ける）
  - `SPEC.md` — 色・タイポ・余白・文言・画像の確定値をまとめた実装仕様書
  - `support.js` — プレビュー用ランタイム（移植不要）
- `src/` — 実装コード（Astro）
- `public/images/` — 差し替え可能な画像（現状はプレースホルダーSVG）

## 実装状況

Astro（静的書き出し）で `design/SPEC.md` の仕様どおりに実装済み。

```
npm install
npm run dev      # http://localhost:4321
npm run build    # dist/ に静的書き出し
npm run preview  # ビルド結果をローカル確認
```

### 対応済み
1. **レスポンシブ** — 900px以下で全gridを1カラム化、ヘッダーはハンバーガーメニュー化、左右paddingを20pxに縮小。
2. **画像の自社ホスティング化** — `static.wixstatic.com` への直リンクは廃止。ただし実際の商用写真は未入手のため、`public/images/*.svg` に配色トーンを合わせたプレースホルダー画像を配置している。**実写真が用意でき次第、同じファイル名（`hero.svg` `about.svg` `services.svg` `club.svg`）を差し替えるか、`src/components/*.astro` の `<img src>` を変更すること。**
3. **SNSリンク** — Wix公式アカウントへのリンクは削除済み（BUTCHAKEの実アカウントが判明したらフッターに追加する）。

## 更新フロー

```
Claude Design ──> design/ を更新 ──> push
                                      │
                                      ▼
Claude Code ──> pull ──> src/ を実装 ──> push
```

デザイン変更時は `design/` の差分を見て `src/` に反映する。
