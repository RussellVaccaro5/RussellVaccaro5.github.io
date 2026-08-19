# Repository operating guide

## Project purpose

- `russvaccaro.com` is Russell Vaccaro's personal publishing and professional-presence site.
- It holds concise notes about what Russell is reading, writing, learning, and developing opinions about, especially technical go-to-market, startups, performance, and deliberate practice.
- Keep interactive tools, experiments, browser applications, and software projects in the separate Lab site unless the owner explicitly asks to put one here.

## Architecture

- This is a deliberately small static site built by GitHub Pages with Jekyll and the Minima theme.
- The `github-pages` gem supplies the GitHub Pages-compatible dependency set. Jekyll Feed and SEO Tag are enabled in `_config.yml`.
- There are no repository-owned layouts, includes, assets, CSS, JavaScript, or Actions workflows. Pages use Minima's `page` layout; do not assume theme internals are locally editable.
- Prefer Markdown, standard Jekyll features, existing Minima configuration, and only minimal HTML/CSS when a requested result requires it.
- Do not introduce a JavaScript framework, component library, database, server infrastructure, client state management, or extra build tooling for ordinary site work. Simplicity is a feature.

## Repository map

- `_config.yml`: canonical URL, site metadata, plugins, writing permalink pattern, and Minima header navigation.
- `index.md`: home page at `/`.
- `about.md`, `reading.md`, `writing.md`: primary pages at `/about/`, `/reading/`, and `/writing/`.
- `writing.md`: Liquid-generated list of posts, newest first according to Jekyll's `site.posts` ordering.
- `404.md`: custom `/404.html` page.
- `_posts/`: create this directory when publishing the first article; it does not currently exist.
- `Gemfile`: GitHub Pages dependency declaration.
- `CNAME`: GitHub Pages custom-domain record.

## Content and publishing

- Root pages are Markdown files with YAML front matter. Existing pages use `layout: page`, `title`, and an explicit `permalink`; some also provide `description`.
- Add articles as `_posts/YYYY-MM-DD-title.md` with valid front matter, including a real owner-supplied title and date. The configured post URL is `/writing/:title/`.
- `writing.md` already discovers `site.posts`; do not maintain a second manual post index.
- Header navigation is deliberately ordered as About, Reading Log, Writing through `header_pages` in `_config.yml`. The home page is reached through the Minima site title rather than a separate header entry.
- Use Jekyll's `relative_url` filter for internal links, following `writing.md`, `reading.md`, and `404.md`.
- Preserve the lightweight Markdown structure and the existing direct, first-person voice. Reading entries should follow the commented templates in `reading.md` when the owner supplies the facts.

## Content integrity

- Never invent or infer personal experiences, opinions, employment history, accomplishments, projects, reading history, book ratings, biographical details, published writing, credentials, recommendations presented as real, or dates/events attributed to Russell.
- If required facts were not supplied, leave existing content unchanged, ask the owner, or use unmistakably labeled placeholder/example content when the task allows it.
- When editing prose, preserve the owner's meaning and plainspoken voice; do not turn it into generic marketing copy or add unsupported claims.

## Design and implementation preferences

- Preserve Minima's restrained default presentation and the site's current text-first design unless a task explicitly requests a visual change.
- Extend existing Markdown, front-matter, and Liquid patterns before adding custom files. Add the smallest amount of HTML or CSS needed rather than importing an unrelated design system.
- Keep changes narrowly scoped. Avoid opportunistic rewrites, dependency additions, new automation, or abstractions that a small static site does not need.

## Site invariants and owner decisions

- Do not casually change `CNAME` (`russvaccaro.com`) or `_config.yml`'s canonical `url` (`https://russvaccaro.com`); domain changes require owner confirmation.
- Treat `/`, `/about/`, `/reading/`, `/writing/`, `/404.html`, and the `/writing/:title/` post pattern as published URLs. Confirm before moving them or changing permalink behavior.
- Confirm with the owner before changing header navigation, public contact details, site identity/metadata, publishing paths, or the boundary between this site and the Lab.
- Do not commit generated `_site/` output, Jekyll caches, Bundler install directories, or other paths already covered by `.gitignore`.

## Local development

Install Ruby and Bundler, then run:

```sh
bundle install
bundle exec jekyll serve
```

Preview at <http://localhost:4000>. For a non-serving validation build, run:

```sh
bundle exec jekyll build
```

## Definition of done

- Review the diff for factual accuracy, scope, front-matter validity, and accidental changes to site invariants.
- Run `bundle exec jekyll build` after content, configuration, dependency, template, or styling changes.
- For visible changes, inspect the relevant generated page in the local preview; check affected internal links and navigation.
- Ensure no generated files are staged and no personal claims were added without owner-supplied support.
