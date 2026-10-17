# md-to-x-article-skill

Converts Markdown long-form content into a polished X Article publishing draft: edited Markdown + copy-ready rich-text HTML preview.

Based on [shaom/md-to-x-article-skill](https://github.com/shaom/md-to-x-article-skill) (open Agent Skills format), plus session-tested notes from real publishing runs:

- Don't paste raw Markdown into the X editor (`![alt](path)` renders as literal text). Open the HTML preview in a browser, select all, copy into the X Article editor — headings/bold/lists carry over as rich text.
- Images in the HTML preview must be base64-embedded, or they break when the file is opened standalone.
- Videos/GIFs stay as insertion markers; upload natively in the X editor.
- X article cover: 1600×900 (16:9), center-safe composition (feed previews crop tighter). Design separately from WeChat covers (900×500).
- Publishing requires an X Premium (or higher) subscription; X Articles support multiple inline videos.
