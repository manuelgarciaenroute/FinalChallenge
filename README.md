# Coding Assistants Website Automation

## What it does
This project automates how website change requests are executed for the Coding Assistants site in `src/` by using a repeatable Git workflow: create a feature branch from `main`, apply edits to HTML/CSS/JS files, stage and commit with a descriptive message, record the same message in `README.md` under an incremented version entry, and open a pull request that waits for manual approval.

## What work-role task it solves
As a software engineer maintaining a small marketing website, the real recurring problem is handling frequent content/design updates without losing traceability. This automation solves the operational task of turning ad-hoc requests into controlled, reviewable change sets so every update has a branch, commit record, version note, and PR.

## Why it needs a coding assistant
A coding assistant is useful because the workflow is procedural and easy to do inconsistently under time pressure. For example, it can consistently generate a branch name like `feature/update-home-hero`, apply changes across multiple files (`src/html/index.html`, `src/css/styles.css`, `src/js/main.js`), write a commit message that actually explains what changed, increment versions predictably (`v1.0`, `v1.1`, `v1.2`), and prepare a PR that is explicitly marked for manual approval.

## How to set it up
### Prerequisites
- Git installed and repository initialized.
- GitHub CLI (`gh`) installed and authenticated (`gh auth login`) if you want automated PR creation.
- Existing website files under `src/`.
- Skill file available at `skills/website-change-gitflow/SKILL.md`.

### Installation steps
1. Clone the repository and enter the project directory.
2. Confirm the skill exists at `skills/website-change-gitflow/SKILL.md`.
3. Ensure `main` is available locally and remotely.
4. If using PR automation, run `gh auth status` to verify authentication.

## How to use it
1. Provide a website requirement (for example: "Update the clients page with two new client cards").
2. Create a branch from `main` named `feature/<keyword>`.
3. Apply required edits under `src/`.
4. Stage the changes with `git add src README.md`.
5. Write a descriptive commit message for the requirement.
6. Append the same commit message under `## Version History` in this file using the next version (`1.0`, then `+0.1` each commit).
7. Commit changes using the same message content.
8. Push the branch and create a PR targeting `main`.
9. Leave the PR pending manual approval (do not merge automatically).

## Example output
```text
Branch created: feature/update-clients-page
Files changed:
- src/html/clients.html
- src/css/styles.css
- README.md

Commit: 3f8a21c
Message:
feat: add two enterprise client cards to clients page

- Added Helios Systems and Northwind Robotics cards
- Adjusted clients grid spacing for better mobile layout

Version entry added: v1.0
Pull request: https://github.com/example-org/coding-assistants/pull/14
Status: Awaiting manual approval
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
