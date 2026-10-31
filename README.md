# Tessa Alexanian's personal website

Hosted at [tessa.fyi](https://tessa.fyi). Built with [Jekyll](https://jekyllrb.com/) and deployed to GitHub Pages by
`.github/workflows/jekyll.yml` on every push to `main`. No JavaScript framework, no node_modules.

## Preview locally

```sh
bundle install
bundle exec jekyll serve   # http://localhost:4000
```

## How it fits together

- `_includes/head.html` builds every page's `<head>` (title, description, social cards, favicons, CSS, fonts) from front matter.
- `_includes/nav.html` is the link bar at the top; pick links with `nav: [home, about, zachary-jacobi]`.
- `_layouts/article.html` is for long-form pages written in Markdown (essays, the Zachary Jacobi pages).
- Files with no front matter (e.g. `projects/east-bay-biosecurity/`, `book.html`) are copied as-is, so archived sites keep
  their own HTML and CSS.
- `foo.md` builds to `foo.html`, which GitHub Pages serves at `/foo`.

## Adding an essay

Create `words/my-essay.md`:

```markdown
---
layout: article
title: My Essay
description: One sentence for search results and link previews.
image: /img/words/my-essay/cover.jpg     # optional, for link previews
nav: [home, about]
dateline: October 2026                    # optional, shown under the title
intro: "*Originally published in [Somewhere](https://example.com).*"   # optional
main_col: col-sm-8                        # optional, default col-sm-7
---

Body text in Markdown.

![Alt text](/img/words/my-essay/photo.jpg){: .img-fluid}

A caption under the photo.
{: .caption}
```

### Images beside the text

Put `<!-- side -->` on its own line: everything after it goes in a right-hand column (set its classes with `side_col`,
default `col-sm-5 text-center`). Put `<!-- row -->` on its own line to start a new row, e.g. one per section, each with
its own `<!-- side -->` image. See `zachary-jacobi/elephant-aversary.md` for an example.
