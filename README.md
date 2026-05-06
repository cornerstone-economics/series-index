# series-index

Source for [papers.c-economics.com](https://papers.c-economics.com), the public-facing index of the Cornerstone Economics Working Paper Series.

## What this is

A small Quarto website that lists published working papers, links to their PDFs and DOIs, and explains the series. The site is built on every push to `main` and deployed to GitHub Pages. The custom domain is set via `CNAME` and a DNS record on `c-economics.com`.

## Adding a paper

When a new working paper is released, edit `papers.json` and add an entry in the same shape as the existing entries. The site will rebuild and the new paper will appear within a few minutes. Sort order is automatic by paper ID.

```json
{
  "id": "WP-2026-02",
  "date": "Month YYYY",
  "title": "Title sentence-case.",
  "authors": ["Author One", "Author Two"],
  "abstract": "One paragraph, three to five sentences.",
  "jel": ["O10", "F60"],
  "doi": "10.5281/zenodo.XXXXXXX",
  "pdf": "https://github.com/cornerstone-economics/wp-2026-02-shortname/releases/latest/download/paper.pdf",
  "repo": "https://github.com/cornerstone-economics/wp-2026-02-shortname",
  "status": "published"
}
```

Set `doi` and `pdf` to `null` while a paper is in production. The card shows `DOI pending` and `PDF pending` until they are populated.

## Local preview

```bash
quarto preview
```

You need Quarto 1.5 or later. No R is required for the index site itself.

## Deployment

GitHub Pages is set to deploy from GitHub Actions, branch `main`. The `CNAME` file in this repo claims the `papers.c-economics.com` domain. The DNS side requires four `A` records on the apex (or one `CNAME` if `papers` is a subdomain) pointing to GitHub Pages. See `docs/dns-cname-setup.md` if present, or follow [GitHub's documentation](https://docs.github.com/en/pages/configuring-a-custom-domain-for-your-github-pages-site).
