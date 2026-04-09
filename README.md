# construct

**Execute a blueprint spec with zero codebase exploration** — the builder reads the spec, uses cached workspace knowledge, and writes code.

## The Problem It Solves

After `/blueprint` produces a spec, you still need a builder that won't re-scan the codebase. `construct` enforces that contract: no grep, no directory listing, no reading files outside the spec. Just implementation.

## When to Use

Run `/construct` immediately after `/blueprint` has produced a spec:

```
/brainstorming  →  /concise-planning  →  /blueprint  →  /construct
```

Paste the spec into the prompt (or reference it), and the builder takes over.

## Constraints Enforced

- No codebase exploration tools (grep, find, ls, file reads outside the spec)
- 90% Confidence Rule: hard stop before guessing, asks the user instead
- No deviation: no unrequested refactors, cleanup, or added features
- Topological execution: steps implemented in spec order, one at a time

## Confidence Gate

Before each step, the builder self-evaluates. If confidence drops below 0.9 on types, file paths, or patterns, it stops and asks a targeted question rather than guessing.

## Usage

```
/construct
```

Then paste your `/blueprint` output. The builder will parse the full spec before writing a single line of code.
