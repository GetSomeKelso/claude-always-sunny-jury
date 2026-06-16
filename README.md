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

## Two modes

**Mode A — Trial by Gang.** Six jurors analyze in parallel isolation, blind to
each other. Fast and punchy; the synthesis surfaces where they agree and where
they split. No arbiter — the disagreement is the deliverable. ~6 subagents.

**Mode B — Full Deliberation.** The courtroom. Six opening arguments (isolated) →
six cross-examinations (each juror reads everyone else's take and rebuts in
character) → **The Lawyer**, an exhausted competent attorney, renders a practical
ruling with liability analysis from the chaos. ~13 subagents. Inspired by
*Reynolds vs. Reynolds: The Cereal Defense* (S8E10) and *McPoyle vs. Ponderosa:
The Trial of the Century* (S11E7).

Unlike the OpenCode original, the whole run — including Mode B's three phases —
completes in a **single turn**: Claude Code's Task tool returns subagent results
inline, so each phase dispatches as soon as the previous one returns.

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

Triggering is hybrid: the trigger phrase picks the mode and can carry the case
inline. A bare invocation falls back to an `A`/`B` menu.

**Mode A (inline):**
```
ask the gang: should we implement passwordless authentication?
Sunny jury: is CI/CD without branch protection compliant?
devil's advocate: our RDP exposure risk
```

**Mode B (inline):**
```
trial by the gang: should we migrate to passwordless auth?
full deliberation: is our supply chain actually secure?
cereal defense: what if we just stopped patching and bought cyber insurance?
McPoyle vs Ponderosa: MFA bypass techniques
```

**Bare invocation → menu:**
```
Sunny jury
> Always Sunny Security Jury — ... Select mode: [A] ... [B] ... Enter A or B:
A
> Enter security case:
should we implement passwordless authentication?
```

### Trigger phrases

- **Mode A:** `ask the gang`, `Sunny jury`, `Paddy's Pub jury`, `IATGANG analysis`,
  `security jury`, `panel review`, `devil's advocate`, `red-team-vs-blue-team`,
  `get the gang`, `jury session`
- **Mode B:** `trial by the gang`, `full deliberation`, `cereal defense`,
  `McPoyle vs Ponderosa`, `Reynolds vs Reynolds`, `let them argue`, `cross-examine`,
  `objection`

## What you get

- **Mode A** renders a verdict: executive consensus, confidence level, each
  juror's finding (Frank's shown RAW with a legal translation), a 4-tier action
  plan, and a dissent register.
- **Mode B** renders a full deliberation record: opening arguments →
  cross-examination & chaos → The Lawyer's ruling (verdict, strongest/weakest
  argument, liability exposure, the actual solution).

## Why it works

- Six independent thinking frameworks, not six copies of "generic analyst."
- Where they agree, it's probably right. Where they fight, you've found risk.
- Frank suggests the criminal path *as Frank*; the synthesis (Mode A) or The
  Lawyer (Mode B) translates it into legal, actionable defense.

Note: Frank's realism is bounded by the subagent's own judgment, not the persona.
Normal AppSec threat-modeling engages fully; a request for genuinely dangerous
operational specifics will be softened or declined regardless of the costume —
that's correct behavior.

## Files

- `SKILL.md` — character prompts, mode routing, workflow, verdict templates
- `README.md` — this file

## License

MIT
