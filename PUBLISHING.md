# Publishing

The profile uses native GitHub Markdown and one Bomberman animation. Publish the contents of this folder to the public repository `Abhi-eversor/Abhi-eversor`, with `README.md` at the repository root.

All four project links were checked on 15 October 2026. NutritionScanner, Yukti, Provlepsi-AI and Before-the-Library are public. Provlepsi-AI now contains its project source, so its pending-upload note has been removed.

## First upload from the prepared local folder

The local package is already a Git repository on `main`, with no commits and no remote configured at verification. Use the existing folder; there is no need to run `git init` again.

1. Sign in to GitHub as `Abhi-eversor` and open [New repository](https://github.com/new).
2. Set the repository name to **Abhi-eversor** and visibility to **Public**. Leave the starter README, .gitignore and license options off, then create the empty repository. GitHub displays the root README on your profile when the public repository name matches your username; see [profile requirements](https://docs.github.com/en/account-and-profile/how-tos/profile-customization/managing-your-profile-readme).
3. Open PowerShell and run:

   ```powershell
   Set-Location -LiteralPath 'C:\Users\abhia\Desktop\New folder (2)\github_readme\profile-package\Abhi-eversor'
   git status --short
   git add -- README.md PUBLISHING.md .gitignore .github/workflows/bomberman.yml assets
   git commit -m "Add GitHub profile"
   git remote add origin https://github.com/Abhi-eversor/Abhi-eversor.git
   git push -u origin main
   ```

   Only this package folder belongs in the repository. Its root should contain `README.md`, `PUBLISHING.md`, `.gitignore`, `.github/` and `assets/`. Do not upload the enclosing workspace or `profile-review/`. If using the ZIP, extract it and publish the contents of its `Abhi-eversor` folder, not the ZIP or an extra enclosing folder.

4. Complete GitHub's sign-in if prompted. If Git asks for a commit identity, set `git config user.name "Abhishek Aryan"` and `git config user.email "YOUR_GITHUB_NOREPLY_ADDRESS"` in this folder, replacing the placeholder with the no-reply address shown in your GitHub account's **Settings > Emails**, then repeat the commit and subsequent commands. Do not invent an email address or put it in the README.
5. In the uploaded repository, open **Settings > Actions > General**. Ensure the action policy permits `actions/checkout` and `abozanona/pacman-contribution-graph` (for example, **Allow all actions and reusable workflows**), then save. The workflow already declares `contents: write`. If the repository's **Workflow permissions** setting prevents its asset commit, enable **Read and write permissions** and save. No approval-to-create-pull-requests setting is needed. See [Actions settings](https://docs.github.com/en/repositories/managing-your-repositorys-settings-and-features/enabling-features-for-your-repository/managing-github-actions-settings-for-a-repository).
6. Open **Actions > Refresh Bomberman > Run workflow**, select `main`, and run it. Wait for a green result and check the automatic asset-update commit. This workflow runs on a schedule or manual request; the first push does not itself trigger generation. If the generated files are unchanged, no new commit is needed.
7. Open [your GitHub profile](https://github.com/Abhi-eversor). Check the four project links, both contact buttons and Bomberman. The daily refresh is configured for **03:17 Asia/Kolkata**; it is not a live update after every contribution.

If you have already created or populated the remote repository, inspect it before these first-upload commands. Do not force-push over an existing history. If `origin` already exists, check `git remote -v` rather than adding it again.

## Later edits

Before editing locally, pull the automatic Bomberman updates, then commit and push your changes:

```powershell
git pull --ff-only
# Edit README.md, then:
git add -- README.md
git commit -m "Update GitHub profile"
git push
```

## Bomberman updates

[bomberman.yml](.github/workflows/bomberman.yml) runs daily at **03:17 Asia/Kolkata** and can also be run manually. It uses the original JavaScript action from [abozanona/pacman-contribution-graph](https://github.com/abozanona/pacman-contribution-graph), pinned to revision `7332e1de7903ab780c3692a4127a59cc13872daa` (package 5.3.2).

The built-in `GITHUB_TOKEN` fetches the contribution calendar; no personal token is required. The action generates the upstream GitHub light and dark themes. Both outputs are checked before replacing the stored SVGs, so a failed generation keeps the previous images. The commit step includes only those two asset paths. Branch protection must allow this update route.

The README displays animated SVG images. JavaScript runs in Actions, not in the profile page. Gameplay does not add contributions or represent a contribution total. The initial files were generated locally from the public contribution calendar; later runs use GitHub's authenticated calendar API.

The upstream action makes best-effort requests to its analytics and game-stat service. Its source code is not included in this package. No upstream license is assumed.

Scheduling uses GitHub's documented [timezone support](https://docs.github.com/en/actions/reference/workflows-and-actions/workflow-syntax#onschedule). Scheduled runs can be delayed or disabled after extended repository inactivity. The first hosted run verifies permissions and automation; local preview checks do not establish a hosted run.
