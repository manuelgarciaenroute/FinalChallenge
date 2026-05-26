---
name: website-change-gitflow
description: Implement requested website changes for the project under src and its subdirectories using a strict Git flow. Use when the user asks to modify the website: create a new branch from main named feature/<requirement-keyword>, apply file changes, stage and commit with a descriptive message, append the same commit message to README.md under an incremented version header (starting at 1.0 and increasing by 0.1 each commit), then open a pull request for manual approval.
---

# Website Change Git Flow

Execute these steps whenever the user requests a change to the website in `src/`.

## Scope Rules

- Work only inside the project folder and `src/` subtree unless the workflow requires updating `README.md`.
- Do not rewrite unrelated files.
- Keep changes minimal and directly tied to the requirement.

## Step-by-Step Workflow

1. Sync with `main` and create branch
- Ensure current branch is `main`.
- Pull latest `main` if remote is configured.
- Derive a short, lowercase keyword from the requirement.
- Create branch `feature/<keyword>` from `main`.

Suggested commands:
```bash
git checkout main
git pull --ff-only origin main   # skip if no remote
git checkout -b feature/<keyword>
```

2. Implement the website requirement
- Edit existing files in `src/` or add new files under `src/` as needed.
- Prefer preserving current page structure unless requirement asks otherwise.

3. Stage all related changes
```bash
git add src README.md
```
If additional related files were changed, stage them explicitly.

4. Create descriptive commit message
- Use imperative voice.
- Summarize what changed and where.
- Keep first line concise; optional body for details.

Format:
```text
<type>: <summary of website change>

- <important change 1>
- <important change 2>
```

5. Update `README.md` version history
- Locate or create section `## Version History`.
- Determine latest version number in that section.
- If no version exists, use `1.0`.
- Otherwise increment by `0.1` (one decimal place).
- Add a new entry with header `### v<version>` and paste the exact commit message text below it.

Example:
```markdown
## Version History

### v1.0
feat: update homepage hero copy

- Refine headline and CTA text
```

6. Commit
- Stage again after README update.
- Commit using the same message appended to README.

```bash
git add src README.md
git commit -m "<same summary line>" -m "<same bullet details if present>"
```

7. Open pull request for manual approval
- Push branch and open PR targeting `main`.
- Do not merge the PR automatically.
- State clearly that manual approval is required.

```bash
git push -u origin feature/<keyword>
gh pr create --base main --head feature/<keyword> --title "<summary line>" --body "Manual approval required.\n\n<commit message body>"
```

If `gh` is unavailable, provide push instructions and PR URL template for manual creation.

## Output Template

After execution, report:
- Branch created
- Files changed
- Commit hash and message
- New README version added
- PR link and note: "Awaiting manual approval"

## Guardrails

- Never merge the PR automatically.
- Never skip README version update.
- Keep version increments exactly `+0.1`.
- Use the same commit message in git commit and README version entry.
