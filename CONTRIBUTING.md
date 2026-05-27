# Contributing to Kleos

Thanks for helping make Kleos better. Here's how to contribute.

## Ways to Contribute

| Type | How |
|------|-----|
| **Bug reports** | Open an [Issue](https://github.com/Lubitzy/kleos/issues) with steps to reproduce |
| **Feature ideas** | Open an Issue with `[Feature]` prefix |
| **Code** | Fork → branch → PR |
| **Docs** | Fix typos, improve clarity, add examples |
| **Presets** | Share your automation commands in Discussions |

## Skill Development

Kleos follows the [Bankr SKILL.md format](https://docs.bankr.bot/skills/in-bankr/skill-format). Key rules:

- `SKILL.md` is the entry point — keep it concise
- Detailed workflows go in `references/` — loaded on demand by the agent
- Each reference file should be markdown, max 100KB
- Frontmatter requires `name` and `description` fields

## Adding Automation Presets

Presets live in `presets/`. Each file should contain:
1. Clear section headers
2. Copy-paste ready commands
3. Placeholders in `[brackets]` for user customization
4. Note about limits at the bottom

## PR Guidelines

1. Fork the repo
2. Create a feature branch (`feat/your-feature` or `fix/your-fix`)
3. Test your changes in Bankr if possible
4. Keep commits atomic and well-described
5. Open a PR with a clear description

## Questions?

Open a [Discussion](https://github.com/Lubitzy/kleos/discussions) or reach out via issues.
