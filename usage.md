# How to Use This Class Block Template

This template is designed to help you quickly scaffold and organize class blocks for your course or workshop.

## Structure

- **readme.md**: Main overview for the block. Update the placeholders `[theme]`, `[block_name]`, `[block_type]` and fill in each section.
- **content/**: Place your main content files here. Use `content_template.md` as a starting point.
- **slides/**: This folder is preconfigured as a [Slidev](https://github.com/gu-ma/slidev-template) project (added as a git submodule).

  - After cloning this repository, run: `git submodule update --init --recursive` to initialize the Slidev template.
  - To update the Slidev template to the latest version, run: `git submodule update --remote slides`
  - To customize your slides, edit the files directly in `slides/`.

- **resources/**: Add any additional resources (links, PDFs, datasets, etc.) here.
- **samples/**: Add sample code, exercises, or solutions here.

## Getting Started

1. Duplicate this template folder for each new block.
2. Update `readme.md` with your block's details.
3. Add your content and slides using the provided templates.
4. Place any supporting resources or samples in their respective folders.

## Tips

- Keep file and folder names descriptive.
- Remove unused template files as needed.
- Add more sections or templates to fit your teaching style.

---

For questions or suggestions, open an issue or contact the maintainer.

## Deploying to GitHub Pages

This template is configured to publish:
- the root site with Jekyll (from the repository root), and
- the Slidev presentation at the sub-path `/slides`.

Reference: https://sli.dev/guide/hosting#github-pages

How it works:
- A GitHub Actions workflow at `.github/workflows/deploy.yml`:
  - Builds the Jekyll site into `_site/`
  - Builds Slidev into `_site/slides` with the proper base path
  - Uploads `_site` as the Pages artifact and deploys it
- The Slidev build base is computed automatically:
  - For a user/org pages repository named `<user>.github.io`: base is `/slides/`
  - For a project repository: base is `/<repo>/slides/`
  - Note: Slidev’s `--base` must start and end with a slash

Requirements:
1. In GitHub → Settings → Pages, set Source to “GitHub Actions”.
2. Ensure the `slides` submodule is initialized after cloning:
   ```bash
   git submodule update --init --recursive
   ```
3. Push to the default branch to trigger the workflow.

URLs after deployment:
- Root site: `https://<user>.github.io/<repo>/` (or `https://<user>.github.io/` for user/org pages)
- Slides: `https://<user>.github.io/<repo>/slides/` (or `https://<user>.github.io/slides/` for user/org pages)

Favicon for Slidev:
- The Slidev template exposes static files from `slides/public`. To ensure the favicon works on GitHub Pages, set the frontmatter favicon to the `.ico` in `slides/public/favicons/`:
  ```yaml
  ---
  favicon: ./favicons/favicon.ico
  ---
  ```
  The file is already present at `slides/public/favicons/favicon.ico`.

Notes:
- Deep-link refreshes in SPAs on Pages can 404 with history mode. If needed, set `routerMode: hash` in the Slidev frontmatter to avoid that.
- The workflow checks out submodules so CI will build `slides` correctly.
