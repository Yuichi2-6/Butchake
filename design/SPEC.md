# Handoff: BUTCHAKE コーポレートサイト リデザイン

## Overview
株式会社BUTCHAKE（https://www.butchake.jp/ 、現行はWix製）のコーポレートサイトを、既存コンテンツそのままでデザインのみブラッシュアップした1ページ構成のリデザイン案。
和モダン（明朝体＋余白＋アースカラー）を基調に、ヒーロー／About／Services／CLUB BUTCHAKE／会社概要／フッターの6ブロックで構成している。

## About the Design Files
同梱の `BUTCHAKE Site.dc.html` は **HTMLで作られたデザインリファレンス（プロトタイプ）** であり、そのまま本番投入するコードではない。
想定される作業は、このHTMLが示す見た目・挙動を **対象コードベースの既存環境（Next.js / React / Astro / Vue など）の作法とライブラリで作り直すこと**。まだ環境が無い場合は、静的コーポレートサイトに適したフレームワーク（例: Next.js App Router + 静的書き出し、または Astro）を選定して実装する。
`support.js` はプレビュー用ランタイムなので移植不要。

## Fidelity
**High-fidelity（hifi）**。配色・タイポグラフィ・余白・ホバー状態まで確定値で指定してある。ピクセル単位で再現してよい。

## Screens / Views

サイトは単一ページ（1カラム縦積み）。全セクション共通で内側コンテナは `max-width: 1120px; margin: 0 auto; padding: 左右32px`。ベース行間 `line-height: 1.9`、本文フォント `'Noto Sans JP', sans-serif`、本文色 `#23211d`、ページ背景 `#f7f5f0`。

### 1. Header（sticky）
- **Purpose**: 常時表示のグローバルナビ。
- **Layout**: `position: sticky; top: 0; z-index: 20`。背景 `rgba(247,245,240,0.92)` + `backdrop-filter: blur(10px)`、下境界 `1px solid rgba(35,33,29,0.1)`。内側は `padding: 18px 32px` の flex（`justify-content: space-between; gap: 24px; align-items: center`）。
- **Components**:
  - ロゴ（`#top` へのリンク、縦積み flex, gap 2px）
    - "BUTCHAKE" — Cormorant Garamond / 26px / letter-spacing .22em / `#1f3a34` / line-height 1
    - "ぶっちゃけ" — 10px / letter-spacing .3em / `rgba(35,33,29,0.5)`
  - ナビ（flex, gap 32px, 13px, letter-spacing .08em）: `About Us`(#about) / `CLUB BUTCHAKE`(#club) / `Services`(#services)
    - ※現行Wixサイトにある「求人サイト」リンクは本デザインでは**意図的に削除済み**。復活させないこと。
  - CTA「会社概要」(#company) — `padding: 10px 20px`、背景 `#1f3a34`、文字 `#f7f5f0`、`border-radius: 2px`、letter-spacing .12em、hover: 背景 `#9c4221`

### 2. Hero（id="top"）
- **Purpose**: 事業の一言メッセージと主要導線。
- **Layout**: `padding: 96px 32px 88px`、grid `1.05fr 0.95fr` / gap 64px / align-items center。
- **Components**:
  - Eyebrow: "RESTAURANT × PRIMARY INDUSTRY" — 12px / letter-spacing .34em / `#9c4221` / margin-bottom 28px
  - H1: 「飲食店が利益を出す<br>仕組みを、**ぶっちゃける。**」 — Zen Old Mincho 600 / 52px / line-height 1.5 / letter-spacing .04em / `#1f3a34`。「ぶっちゃける。」のみ `#9c4221`
  - リード: 「BUTCHAKEは千代田区の飲食店向けの求人サービスを提供する企業です。また農業・漁業などの一次産業と飲食店も繋ぎます。」 — 16px / max-width 30em / `rgba(35,33,29,0.78)`
  - ボタン2つ（flex, gap 16px, wrap, いずれも 15px 30px / 13px / letter-spacing .14em / radius 2px）
    - Primary「事業概要を見る」(#services) 背景 `#1f3a34` 文字 `#f7f5f0`、hover 背景 `#9c4221`
    - Ghost「CLUB BUTCHAKE」(#club) 枠 `1px solid rgba(31,58,52,0.35)` 文字 `#1f3a34`、hover 枠 `#1f3a34` / 背景 `rgba(31,58,52,0.05)`
  - 右カラム: 画像 `height: 440px; object-fit: cover; filter: saturate(0.92)`。背後にオフセット枠 `position:absolute; inset: 24px -24px -24px 24px; border: 1px solid rgba(31,58,52,0.25)`（画像は `position: relative` で前面）

### 3. About（id="about"）
- **Purpose**: 社名の由来を伝える。
- **Layout**: セクション背景 `#efece4`、上境界 `1px solid rgba(35,33,29,0.1)`、`padding: 88px 32px`、grid `0.85fr 1.15fr` / gap 64px。左に画像（`height: 380px; object-fit: cover`）、右にテキスト。
- **Components**:
  - Eyebrow "ABOUT US" — 11px / .34em / `#9c4221`
  - H2「BUTCHAKE-ぶっちゃけの由来」 — Zen Old Mincho 600 / 32px / .06em / `#1f3a34` / margin-bottom 32px
  - 本文2段落 — 15.5px / `rgba(35,33,29,0.82)` / 段落間 22px
    1. 「BUTCHAKE（ぶっちゃけ）は、「ぶっちゃける」を由来としています。その意味は、本音や自分が知っていて相手が知らないであろう事実を包み隠さずにハッキリと言うことを指します。」
    2. 「飲食店が利益を出すために必要な仕組みやノウハウを包み隠さずにお伝えし、成長をしていただきたい、と言う思いを社名に込めました。」

### 4. Services（id="services"）
- **Purpose**: 5つの提供サービスの一覧。
- **Layout**: `padding: 96px 32px`。見出しブロックの下に grid `1.1fr 0.9fr` / gap 56px / align-items start。左がリスト、右が画像（`min-height: 380px; height: 100%; object-fit: cover`）。
- **Components**:
  - Eyebrow "SERVICES"、H2「事業概要」、説明文「BUTCHAKE（ぶっちゃけ）は、飲食店に対して、以下をサービスとして準備しています。」（15.5px / `rgba(35,33,29,0.75)` / 下 48px）
  - リスト: 親を `display: grid; gap: 1px; background: rgba(35,33,29,0.12)` にして1pxの区切り線を作る hairline テクニック。各行は `background: #f7f5f0; padding: 26px 28px` の flex（gap 22px / align-items baseline）、hover で `background: #ffffff`
    - 連番: Cormorant Garamond / 20px / `#9c4221` / min-width 30px（01〜05のゼロ埋め）
    - ラベル: 16px / letter-spacing .02em
  - 項目（順序どおり）:
    1. 単日だけでも勤務できるアルバイトの手配
    2. お土産用商品の開発支援
    3. 通販用商品の開発支援
    4. シェア農場・シェア漁場の管理・運営
    5. 農業や漁業などの一次産業とのマッチング

### 5. CLUB BUTCHAKE（id="club"、ダークセクション）
- **Purpose**: 招待制コミュニティの説明と会の案内。
- **Layout**: 背景 `#1f3a34` / 文字 `#f2efe7`、`padding: 96px 32px`、grid `1fr 1fr` / gap 64px。右に画像（`height: 480px; object-fit: cover`）。
- **Components**:
  - Eyebrow "CLUB BUTCHAKE" — 11px / .34em / `#d9a189`
  - H2「招待制のコミュニティ」 — Zen Old Mincho 600 / 32px / `#f7f5f0`
  - リード「CLUB BUTCHAKEは千代田区でシェア農場や漁場に興味のある方向けのコミュニティになります。以下が参加条件になります。」 — 15.5px / `rgba(247,245,240,0.82)`
  - 参加条件リスト（list-style none / grid gap 12px、行頭に `◆`（`#d9a189`）、本文 `rgba(247,245,240,0.92)` 15.5px）
    - 千代田区にお勤めの方 / 千代田区にお住まいの方 / シェア農場や漁場に興味のある方
  - 区切り `border-top: 1px solid rgba(247,245,240,0.2); padding-top: 26px`
  - 「各会のご案内」ラベル — 12px / .24em / `#d9a189`
  - 会リンクカード（→ https://www.butchake.jp/club-butchake01）: flex space-between / `padding: 18px 22px` / 背景 `rgba(247,245,240,0.07)` / 枠 `1px solid rgba(247,245,240,0.16)` / 15px、hover 背景 `rgba(247,245,240,0.13)`。テキスト「【受付完了】 2023年5月19日（金）鯛しゃぶの会@夢心邸」、右端に `→`（`#d9a189`）
  - 補足「会についてご質問がある場合は、[お問合せフォーム]よりご連絡ください。」 — 13.5px / `rgba(247,245,240,0.7)`、リンクは `#d9a189` + 下線 `1px solid rgba(217,161,137,0.5)`

### 6. Company（id="company"）
- **Purpose**: 会社概要テーブル。
- **Layout**: `padding: 96px 32px`。Eyebrow "COMPANY" + H2「会社概要」（下 48px）。`<dl>` を grid `160px 1fr`、上境界 `1px solid rgba(35,33,29,0.15)`。各セル `padding: 22px 0`、下境界 `1px solid rgba(35,33,29,0.1)`。dt は 13px / .16em / `rgba(35,33,29,0.55)`、dd は 16px。
- **内容**: 法人名=株式会社BUTCHAKE / 所在地=東京都千代田区麹町3丁目4番1号 夢心邸 内 / 代表者=須田樹一郎 / 設立=2022年6月

### 7. Footer
- 背景 `#efece4`、上境界 `1px solid rgba(35,33,29,0.12)`、`padding: 56px 32px`、flex space-between / align-items flex-end / gap 40px / wrap。
- 左: "BUTCHAKE"（Cormorant Garamond 24px / .22em / `#1f3a34`）＋「株式会社BUTCHAKE / 東京都千代田区麹町3丁目4番1号 夢心邸 内」（12.5px / `rgba(35,33,29,0.6)`）
- 右: Facebook / Twitter / Instagram（flex gap 24px / 12.5px / .08em / `rgba(35,33,29,0.7)`）
  - ⚠ 現行サイトのSNSリンクはWix公式アカウント（`ja-jp.facebook.com/WixJapan` 等）のままになっている。実装時は BUTCHAKE の実アカウントURLに差し替えるか、無ければ削除すること。

## Interactions & Behavior
- ナビ・ヒーローCTAはページ内アンカー。`html { scroll-behavior: smooth }` によるスムーススクロール。
- ヘッダーは sticky + backdrop blur。
- ホバー状態は上記各コンポーネント記載のとおり。グローバルなリンク色は `a { color: #1f3a34 }` / `a:hover { color: #9c4221 }`、`text-decoration: none`。
- ローディング／エラー／フォーム状態は無し（問合せは外部フォームへのリンク）。
- **レスポンシブは未設計**。実装時に追加すること。推奨: 900px 以下で全 grid を1カラム化、ヒーロー H1 を 32〜36px、ヘッダーのナビをハンバーガー化、左右 padding を 20px。

## State Management
クライアント状態なし。Services の5項目のみデータ配列（`{ no, label }`）としてループ描画している。静的レンダリングで完結する。

## Design Tokens
**Colors**
- Ink（本文）: `#23211d` / 透過版 `rgba(35,33,29,.82) .78 .75 .7 .6 .55`、境界 `rgba(35,33,29,.15) .12 .1`
- Primary（深緑）: `#1f3a34`、透過境界 `rgba(31,58,52,.35) .25`、hover 背景 `rgba(31,58,52,.05)`
- Accent（テラコッタ）: `#9c4221`
- Accent on dark: `#d9a189`
- Base BG: `#f7f5f0` / Alt BG: `#efece4` / Dark BG: `#1f3a34`
- On dark text: `#f2efe7`, `#f7f5f0`, `rgba(247,245,240,.92) .82 .7`、境界 `rgba(247,245,240,.2) .16`、面 `rgba(247,245,240,.07) .13`

**Typography**
- 見出し（和文）: Zen Old Mincho 600 — H1 52px/1.5/.04em、H2 32px/.06em
- 本文: Noto Sans JP 400 — 16px / 15.5px / 13.5px / 12.5px、line-height 1.9
- 欧文ロゴ・番号: Cormorant Garamond — 26px（ロゴ）/ 24px（footer）/ 20px（番号）、letter-spacing .22em
- Eyebrow: 11–12px / letter-spacing .34em / uppercase 相当
- Google Fonts: `Zen Old Mincho:wght@400;600;700`, `Noto Sans JP:wght@400;500;700`, `Cormorant Garamond:wght@400;600`

**Spacing**: セクション縦 96px（About のみ 88px）、コンテナ左右 32px、grid gap 64px / 56px、見出し下 48px / 32px、段落間 22px
**Radius**: 2px（ボタンのみ）。それ以外は角丸なし
**Shadow**: なし（境界線と面の明度差のみで構成）
**Max width**: 1120px

## Assets
現状は現行Wixサイトの静的画像を直リンクしている（`static.wixstatic.com`）。**本番実装では必ず自社ホスティングの画像に差し替えること。**
1. ヒーロー: `f930c1_8a53e74eb9ff4dae94a79544aa7796ff~mv2.jpg`（960×740 で取得、表示 440px高）
2. About: `f930c1_f55a89421ec945acb4664d5beffd7ada~mv2.jpg`（P028440214、822×648、表示 380px高）
3. Services: `f930c1_5e18f701726a4b938ca76a032858cca9~mv2.jpg`（23900956、850×566）
4. CLUB: `f930c1_75932dbcf747453eb78950192de9b1f2~mv2.jpg`（図1、910×638、表示 480px高）
アイコン類は不使用（`◆` `→` はテキスト文字）。ロゴは画像ではなくテキスト組版。

## Files
- `BUTCHAKE Site.dc.html` — デザイン本体（ブラウザで直接開ける）
- `support.js` — プレビュー用ランタイム（移植不要）
