# mobile-html-card-image-skill

A reusable skill for designing mobile-first HTML/CSS cards and long images, then exporting them as high-resolution PNG files through CodeShack HTML to Image Converter.

## What It Does

When the user asks for a card, poster, long image, poem image, quote card, study note image, or HTML-to-image output, this skill:

1. Designs mobile-friendly HTML/CSS.
2. Opens `https://codeshack.io/html-to-image-converter/`.
3. Injects HTML/CSS into CodeMirror correctly.
4. Shows the online iframe preview in the Playwright browser tab first, without downloading.
5. Lets the user request refinements while staying in preview mode.
6. After user confirmation, sets export controls to auto width/height and Scale 4.
7. Generates a high-resolution PNG.
8. Downloads it to local storage.
9. Displays it in chat with `file:///` Markdown media syntax.

## Recommended Invocation

```text
/mobile-html-card-image 把这段文字做成手机长图卡片：……
/mobile-html-card-image 用雪山配色做一张诗歌长图：……
/mobile-html-card-image 设计一张小红书风格学习笔记卡片，内容是……
```

## Key Defaults

- CSS width: 780px by default.
- Export scale: 4.
- Height: auto.
- Format: PNG.
- Output path: usually `/storage/emulated/0/Download/<filename>.png`.

## Time Estimate

- Simple card: 3–5 minutes.
- Medium long card: 5–8 minutes.
- Complex poem/poster: 8–15 minutes.
- Very long article/infographic: 12–25 minutes.

The website automation portion alone usually takes 1–3 minutes once HTML/CSS is ready.

## Files

- `SKILL.md`: full skill definition and workflow.
- `AGENTS.md`: companion activation instructions.
- `references/mobile-long-image-parameters.md`: mobile design and export parameter reference.