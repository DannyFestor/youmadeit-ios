# Domain Docs

How the engineering skills should consume the domain documentation when exploring this repo.

## Before exploring, read these

- **`GLOSSARY.md`** in the parent repo, `youmadeit`. This clone sits in the parent's `ios/` folder, and a worktree sits deeper inside it, so walk up to the first folder that holds `GLOSSARY.md`. On GitHub: <https://github.com/DannyFestor/youmadeit/blob/main/GLOSSARY.md>.
- **`docs/adr/`** in this repo: decisions inside the iOS client. Read the ones that touch the area you're about to work in.
- **`docs/adr/`** in the parent: decisions that cross repos, such as the contract, the auth transport, the mobile auth flows, the native clients and the Local Day. Read the ones that touch your area too.

If any of these files don't exist, **proceed silently**. Don't flag their absence; don't suggest creating them upfront. The `/domain-modeling` skill creates them lazily when terms or decisions actually get resolved.

## ADR numbers

One number names one decision across all repos. New ADRs in this repo number from 0200; the app numbers from 0100, the Android client from 0300, and the parent counts below 0100. So a number alone tells you which repo holds it.

## Use the glossary's vocabulary

When your output names a domain concept (in an issue title, a refactor proposal, a hypothesis, a test name), use the term as defined in `GLOSSARY.md`. Don't drift to synonyms the glossary explicitly avoids.

If the concept you need isn't in the glossary yet, that's a signal: either you're inventing language the project doesn't use (reconsider) or there's a real gap (note it for `/domain-modeling`).

## Flag ADR conflicts

If your output contradicts an existing ADR, surface it explicitly rather than silently overriding:

> _Contradicts ADR-0015 (native Kotlin and Swift clients), but worth reopening because…_
