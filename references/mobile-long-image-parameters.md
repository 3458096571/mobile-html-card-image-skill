# Mobile Long Image Design Parameters

This reference defines the default parameters for mobile-first HTML image cards exported through CodeShack HTML to Image Converter.

## Why Scale 4 Matters

Long mobile images are often zoomed, compressed by chat apps, or viewed on high-density screens. If the HTML is exported at Scale 1 or 2, Chinese text in long cards becomes fuzzy after sharing or phone viewing.

Scale 4 means:

- CSS width 780px becomes approximately 3120px output width.
- CSS height 3000px becomes approximately 12000px output height.
- Text edges stay crisp on modern phones.
- The file is larger and generation is slower, but quality is much better.

## Recommended Widths

Use one of these based on purpose:

- 720px: compact quote card, fast export, lightweight.
- 780px: default mobile long card, best balance.
- 840px: richer poster with more ornament and margins.
- 900px: dense infographic or poem poster, still phone-friendly after scaling.

Avoid widths above 1000px unless user explicitly asks for a desktop poster.

## Recommended Font Sizes

Chinese mobile long images:

- Tiny label: 18px–22px.
- Metadata / eyebrow text: 20px–26px.
- Body text: 28px–34px.
- Poem body: 27px–32px.
- Notes / annotations: 24px–28px.
- Subtitle: 32px–44px.
- Main title: 56px–88px.

For dense long poems, do not shrink below 25px unless absolutely necessary.

## Recommended Line Heights

- Prose body: 1.75–1.95.
- Poetry: 1.9–2.15.
- Short quote: 1.45–1.65.
- Notes: 1.65–1.85.

## Export Parameters

Website controls:

- Width: `auto`
- Height: `auto`
- Scale: `4`
- Filename: descriptive PNG name

htmlToImage parameters:

```js
{
  pixelRatio: 4,
  backgroundColor: 'transparent',
  width: node.scrollWidth,
  height: node.scrollHeight
}
```

## Time Estimates

After workflow is known:

- Simple quote card: 3–5 minutes.
- Normal text card: 5–8 minutes.
- Poem / aesthetic long poster: 8–15 minutes.
- Very long article / dense infographic: 12–25 minutes.

Actual browser operation after HTML/CSS is ready:

- Page open/load: 10–25 seconds.
- Code injection: 3–10 seconds.
- Preview update: 5–20 seconds.
- Scale 4 generation: 15–90 seconds.
- Download + media display: 10–30 seconds.

So the repeated mechanical website part is usually about 1–3 minutes. The design writing part is the main variable.

## Practical Workflow Optimization

To reduce time:

1. Draft HTML/CSS locally in one pass.
2. Inject once.
3. Preview and inspect only key dimensions/text.
4. Adjust CSS if cropped or too wide.
5. Export Scale 4.
6. If export fails, simplify heavy effects before lowering scale.

## Visual Style Defaults

For elegant mobile long cards:

- Use layered backgrounds.
- Use a clear title block.
- Use generous spacing.
- Use subtle dividers.
- Use controlled accent colors.
- Keep shadows soft; avoid huge blur on very long images.
- Prefer CSS gradients and pseudo-elements over external images.
- Use semantic HTML for easier styling.

## Final Checklist

Before final export:

- HTML content matches user-provided content.
- No accidental invented replacement text.
- CSS width is mobile-appropriate.
- Online iframe preview has been shown to the user.
- User has confirmed the preview or explicitly asked to download/export.

Before final response:

- Scale is 4.
- Height is auto.
- File downloaded successfully.
- Local media Markdown path uses `file:///`.