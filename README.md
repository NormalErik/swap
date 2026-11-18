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
npx quartz build --serve
```

Open http://localhost:8080. Ports 8080 (preview) and 3001 (live reload) are forwarded to your
machine; keep local port 3001 available for live reload. To preview the documentation instead,
run `npm run docs`.

## Sponsors

<p align="center">
  <a href="https://github.com/sponsors/jackyzha0">
    <img src="https://cdn.jsdelivr.net/gh/jackyzha0/jackyzha0/sponsorkit/sponsors.svg" />
  </a>
</p>
