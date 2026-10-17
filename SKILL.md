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
