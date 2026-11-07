# IGCSE Boards: deploy and update guide

Static site: `index.html`, `manifest.webmanifest`, `sw.js` and three icons. No server, no build step.

## Deploy free (Cloudflare Pages)
1. Make a free Cloudflare account, then Workers & Pages, Create, Pages, Upload assets.
2. Drag this whole folder in and deploy. You get `https://<name>.pages.dev`.
3. For automatic updates, put this folder in a GitHub repo and use Connect to Git instead. Every push deploys.

GitHub Pages also works: push the folder to a public repo, Settings, Pages, deploy from the main branch.

## Rules that keep users' data safe when you update
- Pick your final address FIRST. Browser data belongs to the address (origin). A new domain starts empty for everyone.
- Never rename the storage key `ig3` and never delete fields. Only add new ones with defaults, and bump the `S.v<4` check in `migrate()` when a change needs converting old data.
- Keep editing the same `index.html`, then redeploy. Users keep their data, and `sw.js` fetches the newest version when they are online.
- Keep telling users to use Export backup. Safari can clear a website's storage after 7 days of Safari use without visiting it, unless the site is added to the Home Screen.
