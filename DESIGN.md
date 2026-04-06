# Design System — file2bin Style

> Notion 风格。干净、克制、功能优先。适合工具类单页应用。

---

## 设计原则

- **内容优先**：无装饰性元素，所有视觉服务于功能
- **克制留白**：用间距而非边框来划分区域
- **一致性**：组件语言统一，不混用风格
- **移动友好**：默认为移动端设计，桌面端自然扩展

---

## 颜色

```css
--bg: #ffffff;
--bg-subtle: #f7f7f5;      /* 次级背景，用于卡片头、输入框背景 */
--bg-hover: #f1f1ef;       /* hover 状态背景 */
--border: #e8e8e6;         /* 通用边框 */
--border-focus: #b8b8b4;   /* focus / 强调边框 */
--text: #1a1a1a;           /* 主文字 */
--text-2: #787774;         /* 次级文字，说明、label */
--text-3: #b0b0ab;         /* 占位、弱提示 */
--accent: #2383e2;         /* 品牌蓝，链接、focus ring */
--accent-bg: #eef5fd;
--accent-border: #c5ddf7;
--green: #0f7b6c;          /* 成功状态 */
--green-bg: #eefaf7;
--red: #e03e3e;            /* 错误状态 */
--red-bg: #fdf2f2;
```

---

## 字体

```css
font-family: 'Geist', -apple-system, BlinkMacSystemFont, sans-serif;
/* Geist 是 Vercel 出品，与 Notion 气质接近 */
/* Fallback 保证无网络环境下系统字体风格一致 */

/* 代码 / Hex 内容使用等宽字体 */
font-family: 'SF Mono', 'Fira Code', monospace;
```

字重规范：
- 页面标题：`font-weight: 600`
- 组件标题、按钮：`font-weight: 500`
- 正文、说明：`font-weight: 400`

字号规范：
- 页面大标题：`30px`
- 正文：`14px`
- 次级说明、label：`12px`
- 微标注（badge、hex label）：`11px`

---

## 圆角

```css
--radius: 8px;     /* 卡片、输入区、按钮 */
--radius-sm: 6px;  /* 小组件、badge、状态条 */
```

---

## 间距节奏

- 页面左右内边距：`24px`（移动端 `16px`）
- 页面顶部：`64px`
- 区块之间：`28px`
- 组件内部 padding：`14px`
- 小元素内部：`8–10px`

---

## 组件规范

### 页面头部

```
breadcrumb（面包屑）     ← 12px，text-3 颜色
page-icon（emoji）       ← 40×40，28px 字号
page-title               ← 30px，font-weight 600
page-desc                ← 14px，text-2 颜色
```

面包屑格式：`工具 / 页面名`，用 `/` 分隔，颜色用 `text-3`。

---

### Tabs（分段控制器）

```css
/* 外层容器 */
background: var(--bg-subtle);
border: 1px solid var(--border);
border-radius: var(--radius);
padding: 3px;

/* 激活 tab */
background: var(--bg);
box-shadow: 0 1px 3px rgba(0,0,0,0.08), 0 0 0 1px var(--border);
```

Tab 内包含小图标 + 文字，图标 `13×13`，`gap: 6px`。

---

### 上传区（Dropzone）

```css
border: 1.5px dashed var(--border);
border-radius: var(--radius);
padding: 36px 24px;
background: var(--bg);

/* hover / drag-over */
border-color: var(--accent);
background: var(--accent-bg);
```

内部结构：图标容器（`36×36`，圆角 8px，浅灰背景）→ 标题 → 副说明文字。

---

### 结果卡片

```css
border: 1px solid var(--border);
border-radius: var(--radius);
overflow: hidden;

/* 卡片头 */
padding: 10px 14px;
background: var(--bg-subtle);
border-bottom: 1px solid var(--border);
/* 左侧：图标 + 标签文字；右侧：状态 badge */

/* 卡片体 */
padding: 14px;
```

---

### 数据行列表（Meta List）

Notion database 风格，key/value 水平排列：

```css
border: 1px solid var(--border);
border-radius: 6px;
overflow: hidden;

/* 每行 */
display: flex;
padding: 8px 12px;
border-bottom: 1px solid var(--border);

/* key */
font-size: 12px; color: var(--text-3); width: 80px; flex-shrink: 0;

/* value */
font-size: 13px; color: var(--text);
```

---

### Badge（状态标签）

```css
font-size: 11px; font-weight: 500;
border-radius: 4px;
padding: 1px 7px;
/* 成功 */
color: var(--green); background: var(--green-bg); border: 1px solid #b8ede5;
```

---

### 按钮

主按钮（实心黑）：

```css
background: var(--text);  /* #1a1a1a */
color: #fff;
border: none;
border-radius: var(--radius-sm);
padding: 8px 16px;
font-size: 13px; font-weight: 500;
/* hover */
opacity: 0.85;
```

无描边、无阴影、无渐变。disabled 时 `opacity: 0.3`。

---

### 状态提示

```css
display: flex; align-items: center; gap: 8px;
padding: 9px 12px;
border-radius: var(--radius-sm);
font-size: 13px;

/* 成功 */
background: var(--green-bg);
border: 1px solid #b8ede5;
color: var(--green);

/* 错误 */
background: var(--red-bg);
border: 1px solid #f5c5c5;
color: var(--red);
```

左侧配 14×14 的 SVG 图标（圆圈 + 勾 / 叉）。

---

### Callout 块

```css
display: flex; gap: 10px;
padding: 12px 14px;
background: var(--bg-subtle);
border: 1px solid var(--border);
border-radius: var(--radius);
```

左侧 emoji 图标，右侧标题（13px，500）+ 正文（12px，text-2）。

---

### Toggle 折叠块

```css
/* 按钮 */
display: flex; align-items: center; gap: 6px;
font-size: 13px; font-weight: 500; color: var(--text-2);
/* hover */ color: var(--text);

/* 箭头图标旋转 */
.open svg { transform: rotate(90deg); transition: 0.15s; }

/* 内容区 */
padding: 12px 0 4px 22px;
```

---

### SVG 图标规范

- 尺寸统一：`13×13`（行内）、`14×14`（状态图标）、`18×18`（上传区）
- `stroke-width: 1.4`（大图标用 `1.2`）
- `stroke-linecap: round; stroke-linejoin: round`
- 颜色继承 `currentColor`，方便主题切换

---

## 动画

```css
/* 面板切换、卡片出现 */
@keyframes fadeIn {
  from { opacity: 0; transform: translateY(4px); }
  to   { opacity: 1; transform: translateY(0); }
}
animation: fadeIn 0.15s ease;

/* hover 过渡 */
transition: all 0.12s;
```

原则：动画时长短（≤150ms），无弹簧、无复杂缓动，感觉快而不是炫。

---

## 移动端适配

```css
@media (max-width: 480px) {
  .page { padding: 40px 16px 80px; }
  .page-title { font-size: 24px; }
}
```

最大宽度 `600px`，居中，左右 `24px` padding，天然适配移动端。

---

## Divider 分割线

```css
height: 1px;
background: var(--border);  /* #e8e8e6 */
margin: 28px 0;
```

用于分隔页面头部与主体内容、底部说明区块等。不使用有颜色或有厚度的分割线。

---

## 文案风格

- **短而直接**：按钮文字 ≤ 6 个字，说明文字 ≤ 2 行
- **无感叹号**：不用"！"制造紧迫感
- **动词开头**：按钮用动词，如"下载文件"而非"点击下载文件"
- **小写英文**：英文单词、技术术语统一小写（`.bin`、`hex`），专有名词除外
- **占位符用 `—`**：数据未加载时显示破折号，不用"暂无"或"loading"

---

## 禁止事项（Don'ts）

以下是明确不符合该设计风格的做法，Agent 生成代码时应避免：

- ❌ 渐变背景（`background: linear-gradient(...)`）
- ❌ 大阴影（`box-shadow` 超过 `0 2px 8px`）
- ❌ 圆角超过 `8px`
- ❌ 彩色按钮（主按钮只用纯黑 `#1a1a1a`）
- ❌ 装饰性动画（粒子、扫光、弹跳等）
- ❌ 超过 2 种字体混用
- ❌ 图标使用 emoji 替代 SVG（页面 icon 除外）
- ❌ 所有文字加粗或全部大写（仅 label 用 uppercase）
- ❌ 固定高度导致移动端截断内容

---

## 页面 HTML 骨架模板

Agent 创建新页面时可直接参考此结构：

```html
<!DOCTYPE html>
<html lang="zh">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>页面标题</title>
  <link href="https://fonts.googleapis.com/css2?family=Geist:wght@300;400;500;600&display=swap" rel="stylesheet">
  <style>
    /* 引入 CSS 变量 + 全局 reset */
    /* 参考本文件中的颜色、字体、圆角、间距规范 */
  </style>
</head>
<body>
<div class="page">

  <header>
    <div class="breadcrumb">工具 / 页面名</div>
    <div class="page-icon">🗄️</div>
    <div class="page-title">标题</div>
    <div class="page-desc">一句话说明功能。</div>
  </header>

  <div class="divider"></div>

  <!-- 主体内容：Tabs / 表单 / 卡片 等 -->

  <!-- 底部：Callout 说明 + Toggle 折叠块 -->

</div>
</body>
</html>
```
