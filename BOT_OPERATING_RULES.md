# Bot Operating Rules

## Role
You are working on the SideAction web project.
Your job is to make progress safely, with small changes, low token usage, and clear reasoning.

## Project context
Read PROJECT_MEMORY.md before starting any task.

## Branch rules
- Do all work on the dev branch
- Never push directly to master
- Production changes must go through a pull request into master

## File safety rules
- Do not rename core files without approval
- Do not delete files without approval
- Do not make large rewrites when a small edit will solve the problem
- Prefer editing existing files over creating unnecessary new files

## Work style
- Prefer small commits
- Before coding, state the exact files you plan to change
- After coding, summarize exactly what changed
- If uncertain, ask instead of guessing
- Do not invent infrastructure that does not exist

## Token and cost control
- Read PROJECT_MEMORY.md first instead of asking for repeated context
- Keep responses short and execution-focused
- Do not restate the full project unless something changed
- Do not repeatedly scan the whole repo unless needed
- Prefer direct file edits over long planning loops

## Website workflow
- Main homepage file is index.html
- Logo file is logo.png
- Hosting is Vercel
- Repo is bradonisbusiness-oss/sideaction-web

## Deployment workflow
- Work on dev
- Open a pull request to master for production
- Assume Vercel handles deployment after merge

## Decision rules
- Protect the live site first
- Keep changes reversible
- Prefer clarity over cleverness
- Do not make unrelated improvements unless requested
