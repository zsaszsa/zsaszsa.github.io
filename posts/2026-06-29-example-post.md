---
title: Example post and formatting reference
date: 2026-06-29
summary: A reference post showing how code, images and video render. Kept hidden from the index.
status: hidden
---

This post is `status: hidden`, so it does **not** appear on the news index, but
its page is still built so you can preview it directly. Use it as a cheat sheet,
then delete `posts/2026-06-29-example-post.md` when you no longer need it.

## Headings, lists and text

Write normal Markdown. You get **bold**, *italic*, [links](https://www.misp-project.org/),
`inline code`, and:

- bullet lists
- with multiple items

1. and numbered
2. lists too

> Block quotes render as a callout-style indent.

## Code snippets

Fenced code blocks are syntax-highlighted at build time (no JavaScript needed).
Add the language after the opening fence:

```python
from pymisp import PyMISP

misp = PyMISP("https://misp.example.com", "API_KEY", ssl=True)
events = misp.search(tags=['zsazsa:type="pir"'], pythonify=True)
for event in events:
    print(event.info)
```

```bash
source venv/bin/activate
python build_blog.py
```

## Images

Put image files in `assets/img/blog/` and reference them with a normal
root-relative path — the build fixes the path for the post page automatically:

```markdown
![Alt text describing the image](assets/img/blog/my-screenshot.png)
```

## Video

Markdown lets you drop raw HTML straight in. For a YouTube or Vimeo clip, paste
the embed iframe:

```html
<div class="video-embed">
  <iframe src="https://www.youtube.com/embed/VIDEO_ID" title="Demo"
          allowfullscreen></iframe>
</div>
```

For a self-hosted file (keep large videos out of git — prefer an embed or
git-lfs), use a `<video>` tag pointing at `assets/img/blog/`:

```html
<video controls width="100%" src="assets/img/blog/demo.mp4"></video>
```
