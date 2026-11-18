# Quartz v5

> “[One] who works with the door open gets all kinds of interruptions, but [they] also occasionally gets clues as to what the world is and what might be important.” — Richard Hamming

Quartz is a set of tools that helps you publish your [digital garden](https://jzhao.xyz/posts/networked-thought) and notes as a website for free.

🔗 Read the documentation and get started: https://quartz.jzhao.xyz/

[Join the Discord Community](https://discord.gg/cRFFHYye7t)

## Development container

Install Docker and the VS Code Dev Containers extension, then open this repository in VS Code
and run **Dev Containers: Reopen in Container**. The container provides Node.js 22 and Git,
and installs the locked npm dependencies and Quartz plugins automatically on creation.

Start the local preview from the container terminal:

```sh
node --no-deprecation quartz/bootstrap-cli.mjs build --serve
```

Open http://localhost:8080. Ports 8080 (preview) and 3001 (live reload) are forwarded to your
machine; keep local port 3001 available for live reload. To preview the documentation instead,
run `node --no-deprecation quartz/bootstrap-cli.mjs build --serve -d docs`.

These commands run the CLI directly from the checkout, avoiding npm's temporary `npx` cache.

## Publishing to GitHub Pages

The workflow in `.github/workflows/deploy.yaml`, **Deploy Quartz site to GitHub Pages**, runs
on pushes to the `v5` branch. It uses Node.js 24 on Ubuntu, installs dependencies with `npm ci`,
installs Quartz plugins, and builds the site with `npx quartz build`. The generated `public/`
directory is uploaded and deployed to the `github-pages` environment.

For repository setup, select **GitHub Actions** as the publishing source under
**Settings → Pages**. Ensure `.github/workflows/deploy.yaml` is committed and pushed to `v5`
so GitHub can run it.

To publish content:

1. Add or edit notes and assets in `content/`. This directory currently contains only a
   placeholder; add an `index.md` for the site's home page.
2. Preview the site locally using the development container command above.
3. Commit your changes and push to `v5`.
4. Follow **Deploy Quartz site to GitHub Pages** in the repository's **Actions** tab. Once the
   deployment succeeds, open the site URL shown by the deployment.

The Pages workflow builds `content/`, the CLI's default input directory. The `docs/` preview
command above is for the Quartz documentation. Local container development uses Node.js 22;
the Pages build uses Node.js 24.

## Sponsors

<p align="center">
  <a href="https://github.com/sponsors/jackyzha0">
    <img src="https://cdn.jsdelivr.net/gh/jackyzha0/jackyzha0/sponsorkit/sponsors.svg" />
  </a>
</p>
