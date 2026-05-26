# Coding Assistants Website Automation

## What it does
This project maintains the **Coding Assistants** website in `src/` and automates how website change requests are delivered: create a feature branch from `main`, implement the requested HTML/CSS/JS updates, record the same descriptive commit message in `README.md` version history, include `Codex_Log.txt` updates in the same commit, and create a pull request for manual approval.

## What work-role task it solves
As a software engineer maintaining a marketing and portfolio website, the recurring operational issue is shipping frequent copy/design/content updates without losing process discipline. This setup turns ad-hoc requests into a predictable workflow with branch isolation, clear commit history, documented release notes, and reviewable pull requests.

## Why it needs a coding assistant
A coding assistant helps enforce consistency across repetitive but failure-prone steps. For example, it can update multiple pages consistently when navigation changes, keep version history increments exact (`+0.1`), ensure `Codex_Log.txt` is committed with website updates, and apply a relevant PR title/body format so reviewers immediately understand the requirement and scope.

## Current website structure
- `src/html/index.html` - Home
- `src/html/about.html` - About
- `src/html/clients.html` - Clients
- `src/html/projects.html` - Projects
- `src/html/your-lucky-number.html` - Lucky number generator page
- `src/html/contact.html` - Contact form
- `src/css/styles.css` - Shared styling
- `src/js/main.js` - Shared client-side behavior

## Project automation components
- `skills/website-change-gitflow/SKILL.md`  
  Skill that defines the branch -> change -> stage -> version -> commit -> PR process.
- `.github/workflows/auto-pr-on-feature-push.yml`  
  GitHub Actions workflow that, on push to non-`main` branches, creates a PR to `main` if missing and updates existing PR descriptions with the latest pushed commits/files.
- `Codex_Log.txt`  
  Prompt/result log that is required to be included in commits when using `website-change-gitflow`.

## How to set it up
### Prerequisites
- Git installed
- GitHub repository with `main` branch and `origin` remote configured
- Website files under `src/`
- Skill file at `skills/website-change-gitflow/SKILL.md`
- Optional: GitHub CLI (`gh`) installed and authenticated (`gh auth login`) for local PR creation/verification commands

### Installation steps
1. Clone the repository and open the project folder.
2. Confirm these files exist:
   - `skills/website-change-gitflow/SKILL.md`
   - `.github/workflows/auto-pr-on-feature-push.yml`
3. Verify remote and branch baseline:
   - `git remote -v`
   - `git checkout main`
   - `git pull --ff-only origin main`

## How it works
1. Provide a website requirement.
2. Create a feature branch from `main`: `feature/<keyword>`.
3. Implement updates under `src/`.
4. Write a descriptive commit message.
5. Append the exact same commit message under `## Version History` using the next version (`1.0`, then `+0.1` each commit).
6. Append the prompt/result entry to `Codex_Log.txt`.
7. Stage required files:
   - `git add src README.md Codex_Log.txt`
8. Commit using the same message text added to `README.md`.
9. Push the branch to `origin`.
10. Open/verify PR to `main` with a relevant title and leave it pending manual approval.

## How to use it
1. Provide a website requirement to codex asking it to do something to the website using the website-change-gitflow skill. 
2. A series of authorizations will be asked by codex to approve (mostly git commands and file edits).
3. Check in the github webiste a PR will be created with all of the relevant title, changes and description.
4. If all of the changes are ok someone must manually approve the PR in github.

## Example output
```text
Branch created: feature/projects-page
Files changed:
- src/html/projects.html
- src/html/index.html
- src/html/about.html
- src/html/clients.html
- src/html/contact.html
- src/html/your-lucky-number.html
- README.md
- Codex_Log.txt

Commit: e97aa5d
Message:
feat: add projects page with famous website-inspired portfolio

- Add new Projects page showcasing Coding Assistants work inspired by major web platforms
- Add Projects navigation link across all existing website pages

Version entry added: v1.4
PR title: feat: add projects page with famous website-inspired portfolio
PR status: Awaiting manual approval
```

## Version History

### v1.0
feat: add lucky number page and navigation link

- Add a new "Your Lucky Number" page that displays a random number on each page load
- Update shared navigation across all pages and extend JavaScript to render the lucky number

### v1.1
fix: remove literal `r`n text from website navigation

- Replace accidental escaped newline text in navigation markup across all main pages
- Restore clean nav link rendering for Home, About, Clients, Your Lucky Number, and Contact

### v1.2
style: set website buttons to blue primary color

- Update shared button color tokens to a blue primary palette
- Ensure button text and hover state use accessible blue-themed styling

### v1.3
style: change website background to light yellow-to-purple gradient

- Update global page background to a gradient from light yellow to light purple
- Keep the existing layout and component styling while refreshing overall page ambiance

### v1.4
feat: add projects page with famous website-inspired portfolio

- Add new Projects page showcasing Coding Assistants work inspired by major web platforms
- Add Projects navigation link across all existing website pages

### v1.5
feat: add two new projects to projects page portfolio

- Add CodeHarbor (GitHub-inspired) project entry to the Projects page
- Add TuneFlow (Spotify-inspired) project entry to the Projects page
