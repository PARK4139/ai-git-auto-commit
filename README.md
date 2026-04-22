# ai-git-auto-commit

AI-powered git commit & push automation using Gemini CLI.

> ⚠️ This tool performs real `git push`. Always review changes before confirming.

---

## Overview

This tool automates the following workflow:

1. `git add -A`
2. Collect staged diff
3. Generate commit message via Gemini CLI
4. Ask for user confirmation
5. `git commit`
6. `git push`

The goal is to reduce friction while preserving safety via explicit confirmation.

---

## Features

- Stages all changes automatically
- Generates detailed commit messages from staged diff
- Uses Gemini CLI (`npx @google/gemini-cli`)
- Explicit confirmation before commit & push
- Pushes current branch to remote (`origin`)
- Minimal setup, no global AI dependency required

---

## ⚠️ Safety & Risks

This tool performs **real git operations**, including:

- `git add -A`
- `git commit`
- `git push`

### Risks

- Unintended files may be committed
- Sensitive data may be included
- Wrong branch may be pushed
- AI-generated commit message may be inaccurate

### You MUST

- Review commit message before confirming
- Be aware of current branch
- Avoid running on `main` unless intended
- Use `.gitignore` properly

---

## Dependency: Gemini CLI (Required)

This tool **depends on Gemini CLI via `npx`**.

It will NOT work without it.

### Required command

```bash
npx @google/gemini-cli --version
```

### Requirements

- Node.js installed
- `npx` available in PATH
- Internet access (for first run)

---

## Requirements

- Git
- Python (`py` or `python`)
- Node.js + `npx`

---

## Installation

### 1. Copy files into your repository

your-project/
├── run_ai_git_push.bat
├── ensure_repo_pushed_by_ai_agent_commit_message.py
├── src/
├── README.md

---

## Usage

### 1. Make changes

Modify your code as usual.

---

### 2. Run the script

```bat
run_ai_git_push.bat
```

---

### 3. Internal flow

The script performs:

1. Validate git repository
2. Run `git add -A`
3. Collect staged diff
4. Send diff to Gemini CLI
5. Generate commit message
6. Display commit message
7. Ask for confirmation
8. If confirmed:
   - `git commit`
   - `git push origin <current-branch>`

---

### 4. Confirmation step

You will see:

Proceed with git commit and git push? [y/N]:

- `y` → commit + push
- others → cancel

---

## Example Workflow

(edit code)
↓
run_ai_git_push.bat
↓
(diff 분석)
↓
AI commit message 생성
↓
[확인]
↓
git commit
↓
git push

---

## Recommended Usage Pattern

```bash
git checkout -b feature/my-change
```

Then:

```bat
run_ai_git_push.bat
```

---

## Optional: Alias

### Windows (cmd)

```bat
doskey agp=run_ai_git_push.bat
```

Then:

agp

---

## Limitations

- Depends on external AI (Gemini CLI)
- No offline support
- Always stages ALL changes (`git add -A`)
- No partial staging support
- Commit quality depends on diff clarity

---

## Design Principles

- Minimal automation (not full autonomy)
- Explicit human confirmation
- No hidden background execution
- Fail fast on errors
- Keep workflow predictable and reproducible

---

## Recommended Future Improvements

- Dry-run mode (preview only)
- Partial staging support
- Branch protection check
- Commit message validation rules
- Multi-provider AI support (Gemini / OpenAI / local)

---

## License

MIT (recommended)
