# file2bin — Agent Instructions

Single-file HTML5 app (`file2bin.html`). No build step. All HTML, CSS, and JS live in one file.

## Stack
- Vanilla JS (ES2020+), no frameworks
- Web Crypto API (AES-256-GCM + PBKDF2) for encryption
- Geist font via Google Fonts
- Max width 600px, mobile-first

## Design Tokens

```css
--bg: #ffffff;
--bg-subtle: #f7f7f5;      /* card headers, input backgrounds */
--bg-hover: #f1f1ef;
--border: #e8e8e6;
--border-focus: #b8b8b4;
--text: #1a1a1a;
--text-2: #787774;         /* labels, descriptions */
--text-3: #b0b0ab;         /* placeholders, muted */
--accent: #2383e2;         /* links, focus ring */
--accent-bg: #eef5fd;
--accent-border: #c5ddf7;
--green: #0f7b6c;
--green-bg: #eefaf7;
--red: #e03e3e;
--red-bg: #fdf2f2;
--radius: 8px;
--radius-sm: 6px;
```

```css
font-family: 'Geist', -apple-system, BlinkMacSystemFont, sans-serif;
/* monospace for hex/code */
font-family: 'SF Mono', 'Fira Code', monospace;
```

Font weights: 400 body · 500 buttons/titles · 600 page title  
Font sizes: 30px page title · 14px body · 12px labels · 11px badges

## Component Patterns

**Page header**: breadcrumb (12px, `--text-3`, format `工具 / 页面名`) → emoji icon (40×40) → title (30px, 600) → desc (14px, `--text-2`)

**Tabs**: outer `background: --bg-subtle; border: 1px solid --border; border-radius: --radius; padding: 3px`. Active tab: `background: --bg; box-shadow: 0 1px 3px rgba(0,0,0,0.08), 0 0 0 1px --border`. Tab has 13×13 icon + label, `gap: 6px`.

**Dropzone**: `border: 1.5px dashed --border; border-radius: --radius; padding: 36px 24px`. Hover/drag: `border-color: --accent; background: --accent-bg`. Inner: 36×36 icon container → title → subtitle.

**Result card**: `border: 1px solid --border; border-radius: --radius; overflow: hidden`. Header: `padding: 10px 14px; background: --bg-subtle; border-bottom: 1px solid --border` (icon+label left, badge right). Body: `padding: 14px`.

**Meta list** (key/value rows): `border: 1px solid --border; border-radius: 6px; overflow: hidden`. Each row: `padding: 8px 12px; border-bottom: 1px solid --border`. Key: `12px, --text-3, width: 80px`. Value: `13px, --text`.

**Badge**: `font-size: 11px; font-weight: 500; border-radius: 4px; padding: 1px 7px`.

**Primary button**: `background: --text (#1a1a1a); color: #fff; border-radius: --radius-sm; padding: 8px 16px; font-size: 13px; font-weight: 500`. Hover: `opacity: 0.85`. Disabled: `opacity: 0.3`. No shadow, no gradient.

**Status callout**: `padding: 9px 12px; border-radius: --radius-sm; font-size: 13px; display: flex; gap: 8px`. Success: `--green-bg` bg + `1px solid #b8ede5` border. Error: `--red-bg` + `1px solid #f5c5c5`. Left: 14×14 SVG icon.

**Callout block**: `padding: 12px 14px; background: --bg-subtle; border: 1px solid --border; border-radius: --radius`. Emoji left, title (13px, 500) + body (12px, `--text-2`) right.

**Toggle**: button `font-size: 13px; font-weight: 500; color: --text-2; gap: 6px`. Open: arrow SVG rotates 90°. Content: `padding: 12px 0 4px 22px`.

## SVG Icons
- Sizes: 13×13 inline · 14×14 status · 18×18 upload area
- `stroke-width: 1.4` (large icons: 1.2)
- `stroke-linecap: round; stroke-linejoin: round; color: currentColor`

## Spacing
- Page padding: `24px` (mobile: `16px`), page top: `64px`
- Between sections: `28px`, component padding: `14px`, small elements: `8–10px`
- Divider: `height: 1px; background: --border; margin: 28px 0`

## Animation
```css
@keyframes fadeIn { from { opacity: 0; transform: translateY(4px); } to { opacity: 1; transform: translateY(0); } }
animation: fadeIn 0.15s ease;
transition: all 0.12s;
```
Max 150ms. No spring, no bounce, no decorative effects.

## Mobile
```css
@media (max-width: 480px) { .page { padding: 40px 16px 80px; } .page-title { font-size: 24px; } }
```

## Don'ts
- No `linear-gradient` backgrounds
- No `box-shadow` larger than `0 2px 8px`
- No `border-radius` > 8px
- No colored buttons — primary button is always `#1a1a1a`
- No decorative animations (particles, shimmer, bounce)
- No emoji icons in place of SVGs (except page header icon)
- No fixed heights that truncate content on mobile

## Copy Style
- Short and direct: buttons ≤ 6 chars, descriptions ≤ 2 lines
- No exclamation marks
- Verbs first: "下载文件" not "点击下载文件"
- Lowercase English tech terms: `.bin`, `hex`, `aes-256-gcm`
- Empty state placeholder: `—` (em dash), not "暂无" or "loading"
