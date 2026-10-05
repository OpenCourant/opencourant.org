# opencourant.org

Homepage for [OpenCourant](https://github.com/OpenCourant/OpenCourant), the community
continuation of OpenRadioss.

Built with [Hugo](https://gohugo.io/) (no external theme; layouts and CSS live
in this repo).

## Local development

```sh
hugo server
```

Then open http://localhost:1313/.

## Adding a news post

```sh
hugo new content news/my-post-title.md
```

Edit the file in `content/news/`, set `draft = false` (or remove it), and
commit.

## The downloads page

`/downloads/` is generated at **build time** from the
[GitHub Releases API](https://docs.github.com/en/rest/releases/releases), so
the published HTML contains the real download links, sizes, SHA-256 digests and
download counts. The site ships no client-side JavaScript for this.

| Piece | Where |
| --- | --- |
| Platform matrix | `[[params.downloads.platforms]]` in `hugo.toml` |
| API fetch and normalisation | `layouts/partials/github-releases.html` |
| Page template | `layouts/downloads.html` |
| Static prose | `content/downloads.md` |

Each platform entry reserves a card. The card fills in automatically as soon as
a release publishes an asset whose file name matches the entry's `asset`, and
otherwise renders as "not yet available" with its `reason`. **When the delivery
pipeline starts shipping `OpenCourant_win64.zip` or `OpenCourant_linuxa64.zip`
again, those cards light up with no change to this site.** Adding a brand-new
platform is one more block in `hugo.toml`.

If the API call fails, the build still succeeds: it logs a `WARN` and the page
renders a notice pointing at GitHub rather than showing stale or empty data.

### Keeping it current

Because the data is baked in at build time, the site must rebuild to show a new
release. `.github/workflows/deploy.yml` runs daily at 06:17 UTC for this. To
publish a new release immediately, trigger the workflow by hand:
**Actions → Deploy to GitHub Pages → Run workflow**.

Note that GitHub disables scheduled workflows on public repositories after 60
days with no commits; the manual trigger is the way back.

### Rate limits

CI passes the job's `GITHUB_TOKEN` as `HUGO_GITHUB_TOKEN`, which raises the API
limit from 60 requests/hour per IP (shared across all GitHub-hosted runners) to
5,000/hour. Local development works unauthenticated, but you can export a
personal access token the same way if you hit the limit:

```sh
HUGO_GITHUB_TOKEN=ghp_... hugo server
```

The `HUGO_` prefix is required — it matches Hugo's default
`security.funcs.getenv` allowlist.

Responses are cached on disk for 15 minutes (`[caches.getresource]` in
`hugo.toml`); Hugo's default is to cache forever, which would pin local builds
to the first response. Use `hugo --ignoreCache` to force a refetch.

## Deployment

Pushes to `main` are built and deployed to GitHub Pages by
`.github/workflows/deploy.yml`, as is the daily scheduled run described above.

For the custom domain, set `opencourant.org` under
**Settings → Pages → Custom domain** in the GitHub repository (this manages
DNS verification and the CNAME automatically with the Actions-based flow).

## Contact

- Chat: [#opencourant on the Rocky Linux Mattermost](https://chat.rockylinux.org/rocky-linux/channels/opencourant)
- Email: [hello@opencourant.org](mailto:hello@opencourant.org)
