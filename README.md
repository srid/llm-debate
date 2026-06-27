# llm-debate

An [APM](https://github.com/microsoft/apm) (Agent Package Manager) package for running structured debates between AI agents across [Kolu](https://github.com/juspay/kolu) terminals.

It provides the **`debate`** skill: this agent and one other agent (Codex, opencode, …) take turns in a shared `debates/<label>/` directory — assigned stances, steelmanning each other, optionally converging on a ratified ledger of agreed facts.


https://github.com/user-attachments/assets/849bdb3e-72a5-40ee-92d5-c4c1d6a748e2

[Announced on X](https://x.com/sridca/status/2070695108593225842)

## Install

Requires the [`apm`](https://github.com/microsoft/apm) CLI — the Agent Package Manager for AI-native development ([install instructions](https://microsoft.github.io/apm/)).

```sh
apm install srid/llm-debate
```

## Use

Invoke the `debate` skill — e.g. *"start a debate with the agent on terminal `<id>`"*. It asks for the stance and end-state, then drives the other agent via the [kolu](https://github.com/juspay/kolu) skill, one numbered turn-file at a time.

Full workflow: [`.apm/skills/debate/SKILL.md`](.apm/skills/debate/SKILL.md).

## Examples

All between **Claude** (Opus 4.8) and **Codex** (gpt-5.5); each folder opens on a plain-language summary of the result.

### Sensuous enjoyment — a three-round series

One question, sharpened across three successive debates:

1. **[The best way to increase *sensuous* (not affective) enjoyment](debates/sensuous-enjoyment/)** — the collaborative, truth-seeking opener. Nine turns of steelmanning and conceding, converging on a [ratified nine-point ledger](debates/sensuous-enjoyment/conclusion.md).
2. **[Re-examined under actualism](debates/sensuous-actualism/)** — a non-spiritual follow-up that re-runs the question on actualist terms (Richard's actualism; *no "feeling it in the body"*). Five turns, converging on a [ratified ledger](debates/sensuous-actualism/conclusion.md) that overturns the first debate's affect-friendly compromise.
3. **[The same topic, now fully sourced](debates/sensuous-actualism-sourced/)** — a third, *adversarial* round: the agents fact-check each other against actualfreedom.com.au, close the prior round's open residuals, and footnote **every claim** to a verbatim quote from the source. Five turns, converging on a [fully-sourced ledger](debates/sensuous-actualism-sourced/conclusion.md).

### Tools & productivity

- **[The most effective & fun way to prevent "open loops" anxiety in the LLM era](debates/open-loops-llm/)** — an open-ended, collaborative exploration that converges on a concrete software design. Seven turns — grounded by an 8-agent research sweep — correct the GTD/Zeigarnik mechanism, split **resolution vs. sedation**, and land on **Loop Deck**: a local-first "decommitment assistant" that helps you hold *less*, not more. The folder opens on a front page with the full UX spec and a [hand-drawn diagram](debates/open-loops-llm/concepts.svg).
