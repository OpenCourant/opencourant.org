# opencourant.org

Homepage for [OpenCourant](https://github.com/OpenCourant/OpenCourant), the community
continuation of OpenRadioss, a project of the
[Rocky Enterprise Software Foundation](https://resf.org/).

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

## Deployment

Pushes to `main` are built and deployed to GitHub Pages by
`.github/workflows/deploy.yml`.

For the custom domain, set `opencourant.org` under
**Settings → Pages → Custom domain** in the GitHub repository (this manages
DNS verification and the CNAME automatically with the Actions-based flow).

## Contact

- Chat: [#opencourant on the Rocky Linux Mattermost](https://chat.rockylinux.org/rocky-linux/channels/opencourant)
- Email: [hello@opencourant.org](mailto:hello@opencourant.org)
