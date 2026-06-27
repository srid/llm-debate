---
name: debate
description: >-
  Use when the user wants a structured debate between this agent and one other
  AI agent running on a Kolu terminal — set the stance and end-state, exchange
  turns via the kolu skill, and optionally converge on a ratified ledger of
  agreed facts. Triggers on "debate <topic> with the agent on terminal …",
  "have Codex/opencode debate me", "start a debate", "run an LLM debate",
  "argue this back and forth with another agent".
---

# Debate

Run a structured debate between this agent and **one external agent** running on
another Kolu terminal. Each debate is a directory of numbered turn-files.

## Start

1. **Ask the user** (AskUserQuestion tool) two setup questions:
   - **End-state** — converge on a ratified ledger of agreed facts, or open-ended exploration?
   - **Stance** — assigned opposing standpoints + steelman, or neutral collaborative inquiry?
2. Get the **topic** and the external agent's **terminal ID**.
3. Create `debates/<label>/01.md` and state the topic at the top.

## Layout

```
debates/<label>/
  01.md                # opening turn (topic stated at the top)
  02.md                # other agent's turn
  03.md                # ...
  conclusion.md        # agreed ledger — faithful & precise (only when converging)
  conclusion.simple.md # plain-language, heavily-formatted companion (alongside conclusion.md)
```

`<label>` names the debate; turns are numbered files in order.

## Turns

- Reach the external agent with the kolu skill's **`kaval-tui send <terminalID> …`**
  (the agent type running there is auto-detected by snapshotting the terminal).
  Any agent CLI qualifies — not just Codex.
- Each turn is the **next numbered file**; never rewrite another participant's file.
- **Hand off explicitly:** after taking a turn, ping the other terminal with
  `kaval-tui send` so it knows to proceed. Do **not** use `pulam-tui` or any
  done-signal polling — the agents prompt each other directly with `kaval-tui send`.
- Keep prompts to the other agent **short and unbiased** — don't leak your own
  argument when asking for theirs.
- Cite grounding sources inline when the topic has an authoritative reference.

## Conduct

- Steelman before rebutting; concede what's genuinely true; forge new insight.
- End per the chosen end-state. When converging, write **two** files:
  - `conclusion.md` — the faithful ledger: every agreed claim, every amendment, and every
    open question, in precise wording. This is the record.
  - `conclusion.simple.md` — a plain-language, scannable companion saying the **same**
    thing for a general reader. It changes *presentation only* — never alter, weaken, or
    drop a conclusion or open item from `conclusion.md`. Two standing conventions:
    - **Plain language.** Translate jargon and terms of art into everyday words (gloss or
      footnote any that must stay); short sentences, concrete examples, a practical voice.
      No arcane prose.
    - **Liberal Markdown for glanceability.** Use the full toolkit — a metadata table, an
      at-a-glance summary table, GitHub alerts (`> [!TIP]`/`[!NOTE]`/`[!WARNING]`/
      `[!IMPORTANT]`), bold lead-ins, ordered/unordered lists, blockquotes, horizontal
      rules, and footnotes for citations — so a reader can grasp it at a glance.
- Debates are not published externally.

## Deferred

- Supporting 3+ participants — the debate becomes a converging tree, modelled as
  dotted-path turn-files (`01.01-codex.md`) plus a `participants.json` ID→label
  map. Not yet implemented.
