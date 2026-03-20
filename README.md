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
# 1. Add marketplace
/plugin marketplace add jsyang-dev/code-quest

# 2. Install plugin
/plugin install code-quest@jsyang-dev-code-quest
```

## Usage

```
/code-quest <repo-url> --lang <language> --framework <framework> --task "<task>" [--locale <locale>]
```

### Parameters

| Parameter | Required | Description |
|-----------|----------|-------------|
| `<repo-url>` | ✅ | GitHub repo URL or `owner/repo` |
| `--lang` | ✅ | Programming language (e.g., `kotlin`, `typescript`, `python`, `go`) |
| `--framework` | ✅ | Framework (e.g., `spring-boot`, `nestjs`, `fastapi`, `gin`) |
| `--task` | ✅ | Learning task description |
| `--locale` | ➖ | Content language. Default: `ko` |

### Locale options

| Locale | Language |
|--------|----------|
| `ko` (default) | Korean — 한국어 |
| `en` | English |
| `ja` | Japanese — 日本語 |
| `zh` | Chinese — 中文 |
| any | Any language name (e.g., `--locale Spanish`) |

Locale affects: README, GitHub Issues, PR template, AI review language.

### Examples

```bash
# Korean (default) — Kotlin + Spring Boot
/code-quest https://github.com/user/board-api --lang kotlin --framework spring-boot --task "게시판 CRUD API 구현"

# English — TypeScript + NestJS
/code-quest user/my-repo --lang typescript --framework nestjs --task "Build a TODO REST API" --locale en

# Japanese — Go + Gin
/code-quest user/my-repo --lang go --framework gin --task "REST APIを作成する" --locale ja
```

## Learning Workflow

```
Issue -> Branch -> Implement -> PR (Closes #N) -> AI Review -> Fix -> Re-review -> Merge -> Next Level
```

## Requirements

- GitHub CLI (`gh`) installed and authenticated
- API key for one of the supported AI providers (set as a repo secret)

## AI Provider Support

Code Quest auto-detects which provider to use based on the available secret.

| Provider | Secret Name | Default Model |
|----------|-------------|---------------|
| Anthropic Claude (recommended) | `ANTHROPIC_API_KEY` | `claude-sonnet-4-20250514` |
| OpenAI GPT | `OPENAI_API_KEY` | `gpt-4o` |
| Google Gemini | `GEMINI_API_KEY` | `gemini-2.0-flash` |

### Optional repo variables

| Variable | Description |
|----------|-------------|
| `AI_PROVIDER` | Force a provider: `anthropic`, `openai`, `gemini` |
| `REVIEW_MODEL` | Override the default model |
| `REVIEW_LANG` | AI review response language (default: matches `--locale`) |

## Cost

- ~$0.01-0.05 per PR review (varies by provider)
- Use `gemini-2.0-flash` for lowest cost (~$0.005-0.02)

## License

MIT
