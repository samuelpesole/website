# samuel-pesole site

Personal site + academic blog built with [Hugo](https://gohugo.io) and the [Blowfish](https://blowfish.page) theme. English is the main language; every page has an Italian translation (`*.it.md`).

## Write a new post

```bash
hugo new content posts/my-post/index.md        # English
cp content/posts/my-post/index.md content/posts/my-post/index.it.md   # then translate
hugo new content --kind paper posts/my-paper/index.md   # post about a paper (template)
```

Set `draft: false` when ready. Preview locally with `hugo server -D` → http://localhost:1313

## Publish

Push to `main`: the GitHub Action in `.github/workflows/deploy.yml` builds and deploys to GitHub Pages
(repo Settings → Pages → Source: **GitHub Actions**).

## Things to set before going live

- `config/_default/hugo.toml` → `baseURL`
- `config/_default/params.toml` → `contact.formspreeId` (free form at formspree.io)
- `config/_default/languages.*.toml` → uncomment the GitHub link
