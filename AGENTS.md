# mobile-html-card-image-skill — Agent Instructions

This skill activates when the user wants a mobile-friendly HTML/CSS card, poster, long image, quote card, poem poster, study note image, or any visual card exported from HTML to PNG.

## Purpose

Design polished mobile-first long-form image cards and export them through CodeShack HTML to Image Converter:

https://codeshack.io/html-to-image-converter/

The final output should be a high-resolution PNG downloaded locally and displayed in chat with Markdown local media syntax.

## Activation Keywords

Activate for requests containing concepts like:

- HTML card
- HTML to image
- long image
- mobile poster
- phone screen card
- quote card
- poem poster
- typography card
- study note image
- 小红书卡片
- 长图海报
- 手机长图
- 文字卡片
- 诗歌海报
- 把内容做成图片

## Core Rules

- Default to mobile long-image design, not desktop banner design.
- Use CSS width around 720px–900px; recommended default 780px.
- Use auto height for long content.
- Use Scale 4 for final export clarity.
- Use readable Chinese typography: body text usually 26px–34px CSS pixels, line-height 1.75–2.05.
- Avoid tiny text and wide layouts.
- Do not use Markdown tables for user-facing output.
- Do not silently replace the user's content.
- If the user provides colors, use them deliberately and completely when feasible.
- Use a two-stage workflow: preview first, final download only after user confirmation.
- During refinement, update the online iframe preview and show the Playwright browser tab/state to the user instead of downloading every iteration.

## Website Automation Summary

The workflow has two stages.

### Stage 1: Preview / Refinement

1. Open `https://codeshack.io/html-to-image-converter/`.
2. Wait for CodeMirror and controls.
3. Set HTML/CSS with:

```js
const cms = document.querySelectorAll('.CodeMirror');
cms[0].CodeMirror.setValue(html);
cms[1].CodeMirror.setValue(css);
```

4. Set preview controls:

```js
document.getElementById('canvas-width').value = 'auto';
document.getElementById('canvas-height').value = 'auto';
document.getElementById('filename').value = filename;
const scale = document.getElementById('scale');
scale.value = '4';
scale.dispatchEvent(new Event('input', { bubbles: true }));
```

5. Show the current Playwright browser tab or preview state to the user. Do not download yet. Ask whether the user wants refinement or final export.

### Stage 2: Final Export

Only after the user confirms the preview, generate PNG with the page library:

```js
const iframe = document.getElementById('render-target');
const node = iframe.contentDocument.documentElement;
const dataUrl = await htmlToImage.toPng(node, {
  pixelRatio: 4,
  backgroundColor: 'transparent',
  width: node.scrollWidth,
  height: node.scrollHeight
});
```

6. Create a temporary `<a download>` link and click it if the native download button is unreliable.
7. Confirm saved path in `/storage/emulated/0/Download/`.
8. Display with:

```markdown
![description](file:///storage/emulated/0/Download/filename.png)
```

See `SKILL.md` for the full workflow and detailed failure handling.