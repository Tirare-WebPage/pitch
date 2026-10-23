# Tirare Pitch Website — GitHub Pages

This is a static website: HTML, CSS and JavaScript are all in `index.html`. There is no backend and no build step required. GitHub Pages can serve the site directly from a repository branch.

## Recommended deployment

Create a new public repository named `tirare-pitch` under the `Tirare-WebPage` account (or use another repo name you prefer). Upload the contents of this folder so that `index.html` is in the repository root. Under **Settings → Pages**, choose **Deploy from a branch**, select `main` and `/(root)`, then Save. GitHub Pages publishes static files committed to that branch. For an account/project repository, the URL will generally be `https://Tirare-WebPage.github.io/tirare-pitch/` (GitHub may normalize the case of the account name).

If you instead put this into the existing `Tirare-WebPage.github.io` repository, the URL can be `https://tirare-webpage.github.io/pitch/` only if the deployment publishes the `pitch/` folder as part of its built output. If the existing site uses an Actions build that deploys `dist/`, copy the pitch folder into the deployed output or use a separate repo to avoid interfering with the main site.

## Make videos appear for every visitor

Upload the public clips to `assets/media/` with these exact names:

- `worker.mp4`
- `existing-drivetrain.mp4`
- `mrii-installation.mp4`
- `mrii-oneway.mp4`

Those committed files are fetched automatically from relative paths by the website. Everyone visiting the deployed page can see them. The MRII mechanism video is embedded directly from YouTube: https://youtu.be/4IOVUIjke8k, so it does not need to be uploaded into `assets/media/`. It does require internet access and YouTube embedding must remain enabled for the video. The `Media` picker is an optional local override; any file selected through it is saved in that browser's IndexedDB, not uploaded to GitHub and not visible to other visitors.

Optional self-hosted CAD files can go in `assets/cad/` as `reality.glb`, `first-attempt.glb`, `constraint-collision.glb` and `current-platform.glb`. When those files exist, the page prefers them; otherwise it falls back to the current public GLBs in Tirare's existing repository.

## Asset size and public disclosure

GitHub Pages published sites must be under 1 GB. The GitHub browser uploader accepts files only up to 25 MiB each; regular Git can push individual files up to 100 MiB, while larger files require Git LFS. Git LFS itself cannot be used to serve files on GitHub Pages, so compress video or host very large public-safe clips on a video/CDN service. Keep files small enough that they load quickly in a live presentation.

Do not upload patent-sensitive animation unless counsel has cleared that exact edit for public release. Any committed file is public along with the page.

## External dependencies

The page loads Google Fonts, Google's `model-viewer` custom element from unpkg, and currently falls back to the four public CAD models from the existing Tirare repository. Those portions need internet access. The video assets placed in `assets/media/` are local to the deployed site and do not need a separate media server.

## Local-media picker

If you use the Media panel instead of committing files, the site stores selected files in IndexedDB, in the browser profile and site origin. It will usually survive refreshes on the same device and deployed URL, but browser storage is best-effort and can be cleared or evicted. It is not a publishing mechanism or a reliable way to share files with judges on other devices.
