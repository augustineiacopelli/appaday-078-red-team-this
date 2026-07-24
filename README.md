# 078 · Red Team This

**Live:** https://augustineiacopelli.github.io/appaday-078-red-team-this/

An adversarial pre-send pass, turned into a tool. Paste a document, email, memo, or argument before you send it, and Claude reads it like a hostile-but-fair reviewer whose only job is to find where it is most exposed. It returns three things and nothing else: the single weakest load-bearing claim with why it collapses and what would shore it up, every number or vague quantifier you cannot yet back, and the one hardest question a skeptical reader opens with.

Part of the [AppADay](https://augustineiacopelli.github.io/appaday/) project.

---

## What it does

You give it the material and, optionally, one line of context about what it is and who receives it. Claude comes back with a blunt overall read and a send-readiness verdict (not yet, close, or hold), then marks up three findings:

- **Weakest claim** — the one load-bearing assertion that fails first under scrutiny, quoted from your own words, with the skeptic's move against it and the specific fix.
- **Unsupported numbers** — every figure, statistic, or quantified claim presented without support, including vague quantifiers dressed up as precision, each with the source, denominator, timeframe, or comparison it needs.
- **Hardest question** — the single question you cannot yet answer, and why it is the dangerous one.

The point is to fail privately now so you do not fail publicly later.

---

## How to use it

1. Open the Settings gear and paste your Anthropic API key. Add a reviewer name if you like. Both stay in your browser's localStorage and are sent nowhere but Anthropic.
2. Paste the document and, optionally, a line of context.
3. Press **Red team it**.
4. Read the markup, fix what it found, and run it again until the verdict moves.

---

## Technical notes

- Single-file vanilla HTML, CSS, and JavaScript. No frameworks, no build step, no dependencies beyond Google Fonts.
- AI features call the Anthropic Messages API directly from the browser using `const CLAUDE_MODEL = 'claude-sonnet-5'` and the `anthropic-dangerous-direct-browser-access` header, with the user's own key.
- The reviewer returns strict JSON against a fixed schema; the app strips any stray fencing, parses defensively, and renders clean in-voice error states for a rejected key, rate limiting, network failure, or an unparseable reply.
- Editor's-desk visual language on cool graphite: Oswald for condensed labels, Newsreader for the reviewer's prose, JetBrains Mono for extracted claims and figures set as exhibits. Red is a restrained editorial mark with amber as a second signal.
- Fully responsive down to a 375px viewport, visible keyboard focus, and reduced-motion respected.

---

*Ship something every day. It compounds.*
