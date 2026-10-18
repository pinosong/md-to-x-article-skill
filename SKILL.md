---
name: md-to-x-article-skill
description: Convert Markdown long-form content into a polished X Article publishing draft. Use when a user asks to convert, adapt, format, or optimize Markdown for X Articles, including producing a copy-ready rich-text HTML version and an edited Markdown version.
---

# Convert Markdown to X Article

Convert the supplied Markdown into an X Article draft that is accurate, readable on mobile, and easy to paste into the X Article editor.

## Core Rules

- Preserve the author's meaning, factual claims, numbers, links, and overall position.
- Improve structure and presentation without silently rewriting substantive content.
- Use plain, professional language. Avoid promotional exaggeration and unnecessary jargon.
- Do not claim that X supports direct Markdown import. Treat HTML as a copy-ready rich-text source, not an upload format.
- X Articles can contain images, video, GIFs, embedded X posts, and links. Preserve every meaningful media item and its intended position.
- Do not imply that copying HTML will upload or embed media into X. Tell the user to add media natively in the X Article editor.
- Prefer short paragraphs, clear headings, lists, bold emphasis, quotations, and links.
- Do not use Markdown tables in the final publishing draft. Convert each table row into a concise bullet with a bold label.
- Remove obvious placeholders, empty sections, repeated separators, and drafting notes.
- Flag uncertain facts or broken links instead of inventing corrections.

## Workflow

1. Read the complete source before editing.
2. Identify the title, opening, section hierarchy, tables, links, placeholders, ending, and all rich media.
3. Create a media inventory in source order:
   - Images and screenshots
   - Charts and diagrams
   - Video and GIF files or links
   - X post URLs intended for embedding
   - Captions, credits, source links, and alt text
4. Create a specific title that accurately communicates the article's subject and value.
5. Add or refine a brief opening that explains why the subject matters. Do not add unsupported claims.
6. Normalize the hierarchy:
   - Use one article title.
   - Use section headings for major ideas.
   - Use subheadings only where they improve navigation.
   - Fix incorrect or inconsistent numbering.
7. Improve mobile readability:
   - Keep one main idea per paragraph.
   - Break up dense passages.
   - Use bullets or numbered lists for parallel items and procedures.
   - Bold only the most important phrases.
8. Convert tables to lists using this pattern:

   `- **Label**: explanation`

9. Process rich media using the rules below.
10. Preserve quotations as blockquotes and preserve valid source links.
11. Strengthen the ending with a concise summary. Remove empty recommendation or resource sections.
12. Perform the validation checklist before delivery.

## Rich Media Rules

### Images, Screenshots, Charts, and Diagrams

- Preserve each meaningful image at the closest relevant paragraph.
- Preserve useful alt text. Improve vague alt text such as `image` only when the image content is known.
- Preserve captions, credits, and source links separately from alt text.
- Verify that local image files exist when filesystem access is available.
- Keep remote image URLs for reference, but do not rely on hotlinked images for final publication.
- In the HTML preview, render accessible images with `img`, `alt`, and optional `figcaption`.
- In the Markdown output, preserve standard image syntax.
- Recommend one strong, relevant header image when the source has a suitable candidate. Do not invent or generate one unless requested.

### Video and GIFs

- Preserve the original URL or file reference and its intended position.
- Add a clear insertion marker in both outputs, such as:

  `[Insert video in X editor: product demonstration — source: ./demo.mp4]`

- Do not convert a video or GIF into an autoplaying HTML embed.
- Recommend native upload in the X Article editor.

### X Posts

- Detect `x.com` and `twitter.com` status URLs.
- Preserve the URL and mark it for native post embedding in the X Article editor.
- Do not replace an X post with an unsupported iframe or copied screenshot unless the user requests it.

### Missing or Inaccessible Media

- Never silently remove missing media.
- Keep an insertion marker that includes the original path or URL.
- Report missing, inaccessible, or unsupported items in the delivery summary.

### Media Density

- Use media to explain, demonstrate, or provide evidence.
- Avoid placing multiple decorative images together without a clear purpose.
- Keep captions concise and ensure each visual is understandable in context.

## Required Outputs

Unless the user requests another format, create both files in the current workspace:

- `x-article-ready.md`: edited, readable Markdown for review and future revisions.
- `x-article-ready.html`: a clean rich-text page that the user can open in a browser and copy into the X Article editor.

The HTML version must:

- Use semantic elements such as `article`, `h1`, `h2`, `h3`, `p`, `strong`, `em`, `blockquote`, `ul`, `ol`, `li`, and `a`.
- Use `figure`, `img`, and `figcaption` for images when applicable.
- Include UTF-8 and responsive viewport metadata.
- Use simple inline CSS for comfortable browser review.
- Avoid JavaScript, external dependencies, tracking, and decorative elements that will not survive copying.
- Display cleanly on desktop and mobile.
- Show visible insertion markers for video, GIF, missing media, and native X post embeds.

If the environment cannot create files, return the polished draft directly and explain the limitation briefly.

## Validation Checklist

Before delivering, verify:

- The title appears once.
- Heading levels are consistent.
- No placeholders or empty sections remain.
- No Markdown tables or separator-only lines remain.
- Lists are complete and correctly ordered.
- Bold and italic markers are balanced.
- Links are preserved and not malformed.
- All rich media appears in the media inventory and remains in the correct article position.
- Image alt text, captions, credits, and source links are preserved where available.
- Local media paths exist, or missing items are clearly reported.
- Video, GIF, and X post insertion markers are present where native editor actions are required.
- Quotes are clearly distinguished.
- No substantive claim, number, or conclusion was accidentally changed.
- The article ends deliberately rather than fading into an empty section.
- The HTML opens successfully and contains the same article content as the Markdown version.

## Delivery

Briefly state:

- Which files were created.
- The main structural changes made.
- That the HTML version should be opened in a browser and copied into the X Article editor.
- Which images, videos, GIFs, and X posts must be uploaded or embedded natively in X.
- Any factual, link, or formatting issues that still require human review.

## 本地实测补充（2026-10-17，DeepSeek 1017 文章转 X 实测）
- 不要直接粘 Markdown 进 X 编辑器：实测 `![alt](路径)` 原样显示为文本，X 不解析。正确流：打开 x-article-ready.html → 全选复制 → 粘进 X 文章编辑器，标题/加粗/列表以富文本带过去。
- HTML 预览里的图片必须 base64 内嵌：相对路径引用在用户单开文件时必裂图。视频不内嵌，留虚线插入标记，用户在编辑器手动上传。
- X 文章封面 1600×900（16:9），feed 预览裁得更紧，关键内容居中；跟微信封面（900×500，订阅列表缩略图）流量逻辑不同，要区分设计。中文标题照旧 PIL 精确排。
- 发布需要 Premium 及以上订阅；X Articles 支持正文任意位置内嵌多个视频。

## X Article Markdown Paste 插件实测（2026-10-18）
- 插件只处理：图片、表格（转高清图）、代码块、封面、推文嵌入。**不支持视频**——视频位用引用块标记（如 `> 【手动上传视频】xxx.mp4`），用户在编辑器手动上传后删标记。
- 封面规则：默认取正文第一张图当封面，必须用 frontmatter 覆盖：`cover: ./cover.png`（同理 `title:` 覆盖首个 H1）。
- 本地图片需把文件夹拖进浏览器授权一次（File System Access API），之后相对路径自动解析；引用一律用相对路径 `./xxx.png`，绝对路径会被拒。
- 文章简介栏插件不填，留 HTML 注释提醒用户手动填。

## 标准交付流程（2026-10-18 定版，用户确认）
以后每篇 X 文章交付两件套：
1. `{slug}_x_article.md`：frontmatter（`title:` / `cover: ./cover.png`，注意冒号后空格）+ H1 标题 + 正文；图片用相对路径 `![说明](./xxx.png)`；视频用英文标记行 `> VIDEO-UPLOAD: xxx.mp4 (plugin cannot upload video; upload manually in X editor, then delete this line)`（中文括号在写入时可能丢失，用英文标记最稳）。
2. `{slug}_x_media.zip`：封面图 + 正文图片 + 视频，全放包里，用户解压到同一文件夹再授权给插件。
用户侧操作：解压 zip → MD 与素材同目录 → 文件夹拖进浏览器给插件授权 → 粘贴/拖 MD 进 X 编辑器 → 图片封面自动就绪 → 按 VIDEO-UPLOAD 标记手动传视频 → 填简介 → 发布。
已知限制：插件图片走 X 媒体管道自动上传；视频直引会上传超时，必须手动传。

## 封面尺寸规格（2026-10-18 核实修正）
- 微信公众号头条封面：900x383（2.35:1），多个 2026 年来源确认；900x500 是 2019 年老规格，用它会被裁掉上下。PIL 精确排中文。
- X Articles 封面：宽高比 5:2（用户 2026-10-18 查 X 官网确认）。例：1500x600 / 1600x640。中文标题 PIL 精确排，关键内容居中（feed 预览会裁）。此前误用的 1600x900（16:9）作废。

## 封面设计原则（2026-10-18 双平台调研定版）
账号选定风格：Swiss minimal（纸面底 + 巨型数字 + 红色点缀），双平台统一用此风格出封面。

### 微信（900x383，2.35:1）
1. 一封面只讲一件事，6-10 个大字，缩略图一眼可读。
2. 封面和标题互补，不说同一句话（标题说结果/提问，封面给场景/答案）。
3. 核心信息放中央安全区，四角留白。
4. 高对比是硬要求（本账号用浅色纸面 + 深色大字 + 红色点缀）。
5. 版式固定，形成账号辨识度；读者 0.3 秒认出。
6. 大字报路线最适合知识干货，信息直给优先。
7. 无自动 A/B 测试就人工测：3 标题 x 3 封面，发核心读者群看点击意愿再定。
8. 分场景检查：订阅号列表缩略图效果、朋友圈分享（近 1:1 裁切）、搜一搜摘要（第二钩子）。
- 基准线：头条打开率 2%-5%，低于 2% 先修封面标题。
- 号外体只留给真正的大新闻，不滥用。
- 封面不放品牌名和日期（用户要求）。
- PIL 自排不算 AI 生成，无需标注。

### X Articles（5:2，官网确认）
1. 实证优先：放一个图表/基准数字 + 一句话结论，装饰性视觉无用。
2. 封面文字 <=5 词，绝不重复文章标题。
3. 中央安全区：关键内容放中间 60-70%，feed 预览裁得更紧。
4. 在深色时间线里用亮色块打出边缘感（本账号纸面浅色天然满足）。
5. 元素约 3 个：主体 + 一个语境元素 + 短文字。
6. 固定模板，双平台与微信统一为 Swiss 风格。
7. 封面目标是激发回复/转发，不只是点击。
8. frontmatter 指定封面：`cover: ./cover.png`（否则插件默认取正文第一张图）。
