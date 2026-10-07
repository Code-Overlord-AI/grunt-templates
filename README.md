# Code Overlord Grunt templates

Public Auto-Configure prompts and native effort capabilities for [Code Overlord](https://codeoverlord.dev), a product of **Xcribe Limited** (England and Wales, company 14860348).

- **Recommended** supplies 13 model-specific roles, exact at each immutable catalog revision across Claude Code, Codex and Pi. It follows only verified direct successors within the same role, family, tier, provider and harness, preserving distinct harness choices, reuses matching Grunts, and hides generic unpinned defaults without deleting harnesses or changing System Grunt references. Unrelated custom Grunts are preserved.
- **Latest** updates existing pinned models within their provider, family and tier.
- **Balanced** supplies an everyday Luna Grunt and a deeper-work Sol Grunt through Codex.
- **capabilities.json** describes native per-launch effort choices. X High is preferred where supported; Max and Ultra are separate choices. Cursor remains available without app effort controls. Droid is excluded.

The app resolves `main` once and reads the catalog, capabilities and selected prompt at that immutable Git commit. Public reads require no login. Selecting Run applies a template through the user's System Grunt; fetching updates alone changes no Grunts.

Recommendations are reviewed daily. `last_verified` records successful source research, not fetch time or a successful live test for every account. Installed-client and account discovery always wins. The initial versions are conservative minimum **qualified** versions (Codex 0.160.0, Claude Code 2.1.289, Pi 1.0.2), not claims about the first upstream release supporting a feature. Haiku 5.5 is separately qualified for Claude Code 2.1.293 and later. Unknown combinations stay native. Antigravity's headless effort flag is documented; its interactive adapter remains unqualified in this initial catalog.

Pi choices were checked against the public 1.0.2 package's provider metadata and upstream thinking-level resolver. They intentionally differ by provider/model; unsupported X High must not be silently promoted to Max. Codex choices also require runtime model-list/account restrictions. Claude organization caps can reduce effective effort; requested values alone are not proof of effective values.

## Maintenance

Check official provider sources and upstream harness metadata daily. Update affected prompts and capability entries together in one main-branch commit. Advance successful verification dates even if recommendations are unchanged; retain old dates on failed checks. Keep prompt changes meaningful: put daily timestamps in the catalog, so timestamp-only commits do not trigger recommendation notifications.

Before publication, validate JSON/schema, allowed adapters and paths, exact model/provider identities, version ranges, option/default membership and source links. No arbitrary command adapters, executable downloads, tokens, private configuration or customer identifiers belong here. New adapter protocols need an app release; data updates using an existing adapter do not.

Contact [hello@codeoverlord.dev](mailto:hello@codeoverlord.dev), [support](https://codeoverlord.dev/support), [privacy](https://codeoverlord.dev/privacy).
