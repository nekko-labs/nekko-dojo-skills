# Nekko Dojo Skills 🐱⛩️

A public **Agent Skills hub** by [Nekko Labs](https://nekkolabs.com) — a place to
find, share, and install [Claude Agent Skills](https://agentskills.io). Browse
the catalog with votes and details at **[nekkolabs.com/dojo/skills](https://nekkolabs.com/dojo/skills)**.

This repository is also a **Claude Code plugin marketplace**, so you can install
skills directly into your agent and get updates pulled in automatically.

## Trust tiers

| Tier | What it is | How to treat it |
|---|---|---|
| 🟣 **Nekko official** | Built and reviewed by Nekko Labs | Safe to install and run when connected |
| 🟢 **Community** | Submitted by anyone via pull request; passes automated checks + human review | **Browse and choose deliberately. Audit before use** — skills run with your machine's privileges |
| 🔗 **Curated (external)** | Great skills from Anthropic and the wider community | Linked with attribution on the website; install from their original source |

> ⚠️ **Skills execute code with your own permissions.** Automated checks here
> prove a skill is *well-formed and statically clean* — they **cannot** prove it
> is *safe*. Treat installing a skill like installing software. See
> [SECURITY.md](SECURITY.md).

## Install (Claude Code)

```bash
# Add this marketplace once
/plugin marketplace add nekko-labs/nekko-dojo-skills

# Install a skill
/plugin install domain-finder@nekko-dojo-skills

# Later, pull updates
/plugin marketplace update nekko-dojo-skills
```

## Skills

| Skill | Tier | Category | Description |
|---|---|---|---|
| [domain-finder](plugins/domain-finder) | Nekko official | research | Brainstorm startup/project names, check domain availability across TLDs via RDAP, and vet brand/trademark conflicts. |
| [nyaa](plugins/nyaa) | Nekko official | engineering | Convene a council of four reviewer cats (security, deps/supply-chain, correctness/concurrency, style) over a PR or working diff, pulling in external bot reviews too. |
| [resume-checker](plugins/resume-checker) | Nekko official | career | Check a resume against automated candidate-screening (ATS) signals and AI-centric job expectations, score it against specific jobs, then interactively apply fixes and show what changed. |

## Repository layout

```
.claude-plugin/marketplace.json   # the marketplace catalog (installable plugins)
catalog.json                      # machine-readable index consumed by the website
plugins/<name>/                   # one plugin per skill
  .claude-plugin/plugin.json
  skills/<name>/SKILL.md          # the skill (agentskills.io standard)
schema/                           # JSON Schema for SKILL.md frontmatter
tools/                            # static validators (used by CI; safe to run locally)
.github/workflows/                # untrusted-PR-safe validation + commenting
```

## Contributing a skill

Anyone can submit a community skill via pull request. Read
**[CONTRIBUTING.md](CONTRIBUTING.md)** first — it covers the required SKILL.md
shape, the rules CI enforces, and the security expectations.

Run the same checks CI runs, locally:

```bash
node tools/validate-skill.mjs --all
node tools/lint-skill-security.mjs --all
```

## License

[MIT](LICENSE). Individual skills may declare their own license in their
SKILL.md frontmatter.
