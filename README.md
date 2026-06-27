# llm-debate

An [APM](https://github.com/microsoft/apm) (Agent Package Manager) package for running structured debates between AI agents across [Kolu](https://github.com/juspay/kolu) terminals.

It provides the **`debate`** skill: this agent and one other agent (Codex, opencode, …) take turns in a shared `debates/<label>/` directory — assigned stances, steelmanning each other, optionally converging on a ratified ledger of agreed facts.

## Install

Requires the [`apm`](https://github.com/microsoft/apm) CLI — the Agent Package Manager for AI-native development ([install instructions](https://microsoft.github.io/apm/)).

```sh
apm install srid/llm-debate
```

## Use

Invoke the `debate` skill — e.g. *"start a debate with the agent on terminal `<id>`"*. It asks for the stance and end-state, then drives the other agent via the [kolu](https://github.com/juspay/kolu) skill, one numbered turn-file at a time.

Full workflow: [`.apm/skills/debate/SKILL.md`](.apm/skills/debate/SKILL.md).

## Examples

- **[The best way to increase *sensuous* (not affective) enjoyment](debates/sensuous-enjoyment/)** — a collaborative, truth-seeking debate between Claude (Opus 4.8) and Codex (gpt-5.5). Nine turns of steelmanning and conceding, converging on a [ratified nine-point ledger](debates/sensuous-enjoyment/conclusion.md). The folder opens on a plain-language summary of the result.
- **[The same topic, re-examined under actualism](debates/sensuous-actualism/)** — a non-spiritual follow-up that re-runs the question on actualist terms (Richard's actualism; *no "feeling it in the body"*). Five turns between the same two agents, converging on a [ratified ledger](debates/sensuous-actualism/conclusion.md) that overturns the first debate's affect-friendly compromise. The folder opens on a plain-language summary.
