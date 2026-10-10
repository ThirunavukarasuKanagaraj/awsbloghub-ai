# AWSBlogHub AI

Open-source AI and cloud developer platform (early stage). This repository is the project home and contains the landing page for AWSBlogHub AI.

## Project status

AWSBlogHub AI is at a very early stage. This is what exists today:

- This public repository.
- A responsive landing page in [`site/`](site/), built with plain HTML and CSS. No build step, no backend and no JavaScript.
- A GitHub Actions workflow that deploys the page to GitHub Pages.

AI-powered tools, a hosted service and integrations with AWS services are **planned, not implemented**. The landing page and this README describe them as planned and should be kept that way until they exist.

## Repository layout

```
.
├── .github/workflows/pages.yml   Deploys ./site to GitHub Pages
├── site/
│   ├── index.html                Landing page
│   ├── 404.html                  Not-found page
│   ├── robots.txt
│   ├── sitemap.xml
│   └── assets/
│       ├── styles.css
│       └── favicon.svg
├── .gitignore
└── README.md
```

## Preview locally

The site is static, so any file server works. From the repository root:

```bash
cd site
python3 -m http.server 8000
```

Then open <http://localhost:8000>. If you prefer Node.js:

```bash
npx serve site
```

## Deploy to GitHub Pages

Deployment uses GitHub Actions, so no `gh-pages` branch is needed.

1. Push the repository to GitHub (the `main` branch).
2. Open **Settings → Pages** in the repository.
3. Under **Build and deployment**, set **Source** to **GitHub Actions**.
4. Push to `main`, or open **Actions → Deploy to GitHub Pages → Run workflow**.
5. When the workflow succeeds, the site is available at
   `https://thirunavukarasukanagaraj.github.io/awsbloghub-ai/`.

If the workflow fails with a "Pages not enabled" or "not found" error, step 3 has not been done yet.

### Custom domain (optional)

A custom domain needs DNS changes at your domain registrar, so it is not configured here.

1. In **Settings → Pages → Custom domain**, enter your domain and save.
2. At your DNS provider, add the records GitHub lists in its
   [custom domain documentation](https://docs.github.com/en/pages/configuring-a-custom-domain-for-your-github-pages-site).
   In short: a `CNAME` record from `www` to `thirunavukarasukanagaraj.github.io`, and for an apex domain the `A` (and optionally `AAAA`) records GitHub publishes there.
3. Wait for DNS to propagate, then enable **Enforce HTTPS**.
4. Update the absolute URLs that point at the default address:
   `<link rel="canonical">`, the `og:url` tag and the JSON-LD block in `site/index.html`, plus `site/robots.txt` and `site/sitemap.xml`.
5. In `site/404.html`, change the `/awsbloghub-ai/` link to `/`, because a custom domain serves the site from the root.

Renaming the repository also changes the Pages URL, so the same URLs need updating.

## Security

The landing page is fully static. It contains no API keys, tokens or environment variables, and it must never be given any. The `.gitignore` excludes common secret files such as `.env`, but never commit credentials in the first place. If you add a backend later, keep secrets on the server side or in GitHub Actions secrets.

## Contributing

Ideas, questions and pull requests are welcome while the project takes shape.

- Open an [issue](https://github.com/ThirunavukarasuKanagaraj/awsbloghub-ai/issues) to suggest an idea or report a problem.
- For a change to the landing page, edit the files in `site/` and open a pull request. Preview it locally first.
- Please do not describe features as available until they are implemented.

## License

No license has been chosen yet. One will be added alongside the contribution guidelines. Until then, all rights are reserved by the author.

## Disclaimer

AWSBlogHub AI is an independent project. It is not affiliated with, endorsed by or sponsored by Amazon Web Services. AWS and related names are trademarks of Amazon.com, Inc. or its affiliates.
