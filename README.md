# Code Quest

> Transform any GitHub repo into an AI-mentored learning environment with Claude Code.

## What it does

Code Quest is a Claude Code plugin that sets up a GitHub repository as a structured developer learning environment:

1. **Feature Decomposition** - Breaks your learning task into 5-10 progressive GitHub Issues
2. **GitHub Actions Workflow** - Installs an AI code review workflow that runs on every PR
3. **Templates** - Adds Issue and PR templates for a consistent learning workflow

The developer writes all the code. Code Quest provides structure and AI feedback.

## Install

```bash
/install jsyang-dev/code-quest
```

## Usage

```
/code-quest <repo-url> --lang <language> --framework <framework> --task "<task description>"
```

### Examples

```bash
# Kotlin + Spring Boot board API
/code-quest https://github.com/user/board-api --lang kotlin --framework spring-boot --task "Build a board CRUD API"

# TypeScript + NestJS TODO API
/code-quest user/my-repo --lang typescript --framework nestjs --task "Build a TODO REST API"
```

## Learning Workflow

```
Issue -> Branch -> Implement -> PR (Closes #N) -> AI Review -> Fix -> Re-review -> Merge -> Next Level
```

## Requirements

- GitHub CLI (`gh`) installed and authenticated
- Anthropic API key (set as `ANTHROPIC_API_KEY` repo secret)

## Cost

- ~$0.01-0.05 per PR review (claude-sonnet-4-20250514)
- Configurable via `CLAUDE_MODEL` repo variable

## License

MIT
