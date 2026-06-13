# Always Sunny Security Jury (Claude Code)

A 6-personality security analysis skill that treats cognitive bias as a feature.
Each juror applies a different — and deliberately flawed — lens. Their
disagreement IS the deliverable.

| Juror   | Bias                          | Security lens                          |
|---------|-------------------------------|----------------------------------------|
| Dennis  | Strategic narcissism          | Adversarial psychology / social eng    |
| Frank   | Amoral pragmatism             | Red-team economics / criminal mindset  |
| Mac     | Dunning-Kruger overconfidence | Blue-team ops / physical security      |
| Charlie | Lateral thinking, no framework| Creative threats / weird edge cases    |
| Dee     | Intellectual theater          | Compliance / governance / policy       |
| Cricket | Catastrophizing               | Disaster recovery / failure modes      |

## Install

The skill folder must be named `always-sunny-jury` (the folder name is the skill
name). Clone straight into your Claude Code skills directory:

```bash
# user-level (available in every project)
git clone https://github.com/GetSomeKelso/claude-always-sunny-jury \
  ~/.claude/skills/always-sunny-jury

# or project-level (scoped to one repo)
git clone https://github.com/GetSomeKelso/claude-always-sunny-jury \
  .claude/skills/always-sunny-jury
```

Or just drop `SKILL.md` (and this README) into a folder at one of those paths.
No restart needed; Claude Code picks up skills on the next session.

## Use

Trigger by phrase — case can be inline:

```
ask the gang: should we implement passwordless authentication?
```

Or bare, then supply the case when prompted:

```
Sunny jury
> Always Sunny Security Jury — ... Enter security case:
should we implement passwordless authentication?
```

Trigger phrases: `Sunny jury`, `ask the gang`, `Paddy's Pub jury`,
`IATGANG analysis`, or any request for a panel / devil's-advocate /
red-team-vs-blue-team review.

## What happens

1. Six independent subagents dispatch in parallel (one per juror).
2. Each returns a biased, in-character verdict — none sees the others.
3. The orchestrator synthesizes consensus, dissent, and a prioritized action plan.

## Why it works

- Six independent thinking frameworks, not six copies of "generic analyst."
- Where they agree, it's probably right. Where they fight, you've found risk.
- Frank suggests the criminal path *as Frank*; the synthesis translates it to a
  legal, actionable defense.

## Files

- `SKILL.md` — character prompts, workflow, verdict template
- `README.md` — this file

## License

MIT
