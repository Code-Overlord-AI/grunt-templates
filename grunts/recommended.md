# The Dark Lord's Choice

Set up this exact roster of model-specific Grunts for every harness installed on this desktop, each launched the same way as on the reference desktop it mirrors. A row whose harness is not installed here is outside the run: do not create, skip or report it, and leave that harness's built-in alone. After a successful run the Grunts list matches the installed part of the roster: the same IDs, names, models and launch settings. The table is exact at each immutable catalog revision, and the catalog's `roster` lists the same rows.

| Grunt ID | Name | Harness | Provider | Exact model |
|---|---|---|---|---|
| claude-code-haiku | Haiku | claude-code | anthropic | claude-haiku-5-5 |
| claude-code-sonnet | Sonnet | claude-code | anthropic | claude-sonnet-5-5 |
| claude-code-opus | Opus | claude-code | anthropic | claude-opus-5-5 |
| claude-code-fable | Fable | claude-code | anthropic | claude-fable-5-1 |
| codex-gpt-6-astra | 6 Astra | codex | openai | gpt-6-astra |
| codex-gpt-5.6-sol | 6.1 Sol | codex | openai | gpt-6.1-sol |
| codex-gpt-5.6-terra | 5.6 Terra | codex | openai | gpt-5.6-terra |
| codex-gpt-5.6-luna | 6 Luna | codex | openai | gpt-6-luna |
| pi-deepseek-v4-0731 | Deepseek v4-1 (Pi) | pi | openrouter | deepseek/deepseek-v4.1-flash |
| pi-glm-5-3-flash | GLM 5.3 Flash (Pi) | pi | openrouter | z-ai/glm-5.3-flash |
| claude-code-glm | GLM 5.3 | claude-code | openrouter | z-ai/glm-5.3 |
| pi-mimo-v2-6-flash | MiMo v2.6 Flash (Pi) | pi | openrouter | xiaomi/mimo-v2.6-flash |
| claude-code-mimo-v2-6-flash | MiMo v2.6 Flash (Claude Code) | claude-code | openrouter | xiaomi/mimo-v2.6-flash |

Grunt IDs are stable handles. Rituals, Minions and the System Grunt launch Grunts by ID, so an ID stays the same after its model moves on (`codex-gpt-5.6-sol` runs 6.1 Sol). Keep the separate Pi and Claude Code entries even where their model is the same. Generic unpinned Grunts and unattached model profiles are not part of this roster.

## Launch settings

Build each Grunt from this desktop's own built-in Grunt for the same harness (`claude-code`, `codex` or `pi`), so it starts exactly the way that harness already starts here:

- Copy the built-in's command, flags, default count, stagger delay, paste mode and ready pattern. Its flags carry the user's own Skip approvals choice for that harness: keep them exactly, add no other flags and remove none. Drop only a model or provider selection, if the built-in carries one.
- Claude Code and Codex Grunts also copy the built-in's install and upgrade commands. Pi Grunts leave both empty; the built-in Pi owns them.
- Do not copy MCP overrides; new Grunts inherit the global MCP settings. Attach no model profile.
- If the harness's built-in is missing, use the harness's plain command with no flags and report it.

Then add the model:

- **Codex:** append `-m <model>` after the copied flags.
- **Pi:** append `--provider openrouter --model <slug>` after the copied flags.
- **Claude Code on Anthropic:** set all seven of `ANTHROPIC_MODEL`, `ANTHROPIC_DEFAULT_HAIKU_MODEL`, `ANTHROPIC_DEFAULT_SONNET_MODEL`, `ANTHROPIC_DEFAULT_OPUS_MODEL`, `ANTHROPIC_DEFAULT_FABLE_MODEL`, `ANTHROPIC_SMALL_FAST_MODEL` and `CLAUDE_CODE_SUBAGENT_MODEL` to the exact model, so subagents and background calls stay on it. No other env.
- **Claude Code on OpenRouter:** set `ANTHROPIC_BASE_URL=https://openrouter.ai/api`; set `ANTHROPIC_MODEL`, `ANTHROPIC_DEFAULT_HAIKU_MODEL` and `ANTHROPIC_SMALL_FAST_MODEL` to the exact slug; set `API_TIMEOUT_MS=600000` and `CLAUDE_CODE_DISABLE_NONESSENTIAL_TRAFFIC=1`; bind `ANTHROPIC_AUTH_TOKEN` as described under Credentials. No other env.

On a Grunt you reuse, set the model pins, env values and name above. Keep the flags, env, references and other settings the user already has; do not change its Skip approvals flags.

## Which Grunts to create or reuse

Read current Grunts and their versions, the System Grunt, Minion and Ritual references, installed harnesses, effective model pins and provider routing, model profiles and access restrictions, plus the launch receipt's immutable template revision and run ID, before writing. Names and legacy IDs are not model identity; match on exact harness, provider and model.

For each row:

1. Reuse a unique Grunt with the exact harness/provider/model, keeping its existing ID. Grunts that earlier revisions of this preset created under `template-recommended-*` IDs count as this preset's own entries; reuse them rather than adding a second copy.
2. When a verified direct successor advances a role, reuse that role's entry: the one identified by provenance or an earlier immutable revision, or a unique verified direct predecessor within the same role, family, tier, provider and harness. Update all its pins and its name in place without changing its ID. A proven predecessor for this role is not an unrelated tuple.
3. If several exact matches exist, use the one with the table's Grunt ID when present. Otherwise report the ambiguity and skip without adding a duplicate.
4. When nothing matches, create the Grunt with the table's ID. If that ID is held by an unrelated tuple, report a conflict and skip. Never overwrite it, replace IDs or add suffixed duplicates. Ambiguous role or predecessor identity is a conflict; do not adopt another custom Grunt merely because its family looks similar.

Repeat runs update the same entries. Record template ID, role and immutable revision only through supported nonsecret run/provenance fields; do not invent Armoury fields. Do not rewrite shared model profiles or global CLI files.

## On and off

Switch on every roster Grunt that is configured successfully (`show_in_grunts_menu=true`).

The roster replaces the bare `claude-code`, `codex` and `pi` built-ins. Switch each of those off (`show_in_grunts_menu=false`) only when all of these hold:

- it is still generic and unpinned;
- at least one roster Grunt on its harness was configured successfully in this run or is already working;
- it is not the System Grunt, and no Minion or Ritual launches it.

Off means off everywhere: an off Grunt cannot launch from Summon, Minions, Rituals, phones or as the System Grunt. When any condition fails, or you cannot tell, leave it on and report why. Leave `agy` and `cursor` on. Change nothing else on a built-in and never delete one. Custom Grunts outside the roster keep their settings and their on/off state; if a built-in ID now holds a model-specific or custom configuration, report it and leave it alone.

## Credentials

Anthropic roles require native Anthropic access; Codex roles require native Codex/OpenAI access. Do not install, upgrade or authenticate a harness, ask for keys in chat, upload configuration or publish private data.

Local Pi OpenRouter roles automatically use the supported shared OpenRouter provider credential at native launch with the ordinary provider/model flags; no new per-Grunt field, profile or secret reference is needed. Valid explicit Grunt `OPENROUTER_API_KEY` env and resolved Grunt/Minion secret references take precedence over the shared fallback; an invalid explicit reference must fail rather than silently fall back. Raw Minion `OPENROUTER_API_KEY` configuration is rejected by the existing credential-shaped env-key policy and is not a supported override. Pi receives the selected credential as process `OPENROUTER_API_KEY` at native launch; that process environment is distinct from raw Minion configuration. The shared local fallback wins over ambient shell credentials and Pi's saved OpenRouter login. When no explicit or shared managed key exists, valid ambient/native Pi authentication remains usable; do not require another key. Only genuinely missing, invalid or unavailable authentication yields a credential prerequisite/skipped result and guidance to the shared OpenRouter key setting. Remote Pi requires existing deliberate credential forwarding/reference or native remote login; do not forward the shared desktop slot.

The two Claude Code OpenRouter Grunts carry their key as a `secret_refs` entry for `ANTHROPIC_AUTH_TOKEN`. Keep an existing reference. For a new entry, reuse an OpenRouter reference this desktop already holds: another Claude Code Grunt's `ANTHROPIC_AUTH_TOKEN` routed to `https://openrouter.ai/api`, a Grunt's `OPENROUTER_API_KEY` reference, or a `vault:` secret this desktop holds for OpenRouter. Never invent a reference or copy one into public files. If none exists, skip that Grunt and report that its OpenRouter key reference is missing. The shared OpenRouter key setting covers Pi only. Never embed key values, write credentials to command arguments or global configuration, or widen any provider's credential scope.

## Verification

Before creating a Grunt or changing its model, get a short real answer from its exact model through the installed native CLI on this desktop. Use a nonpersistent invocation and never save a temporary Grunt for the check. Exit status alone is not an answer: inspect the reply. If the harness, account, credential or model is unavailable (including offline), leave that Grunt unchanged, mark it skipped with the reason and carry on with the rest. Never substitute another model to turn a skip into success, and never claim access from configuration or a catalog listing.

Haiku 5.5 requires Claude Code 2.1.293 or later. An older installed version leaves that role skipped until the user upgrades.

For every write use expected_version compare-and-set and reread the saved state. On conflict, reread and recompute only the intended changes. Reconcile uncertain writes before retrying the same run. Keep a private recovery record of changed fields through supported configuration history and run results, without exposing secrets. Changes apply to future launches; do not interrupt active sessions.

## Successors

Daily maintenance may advance a verified direct successor only within the SAME role, family, tier, provider and harness, updating every applicable pin together while keeping Grunt IDs, and publishing the resulting exact table at a new immutable catalog revision. Names follow the table: Haiku, Sonnet, Opus and Fable carry no version; the other names change when the version they state changes. Preserve Terra's generation unless a direct successor is verified under that policy. No suitable verified successor means preserve the current pin and report it. Another family, cheap/capable tier, provider or harness requires a new explicit user choice; never silently switch Terra to Sol or substitute an unavailable model. Official source verification establishes model identity, not your account access or a working harness.

Model identity sources:

- Anthropic API IDs: https://platform.claude.com/docs/en/models/overview
- Haiku 5.5 identity and availability: https://platform.claude.com/docs/en/models/haiku-5-5/overview
- Claude Code model support and effort: https://code.claude.com/docs/en/model-config
- Codex models and rollout: https://learn.chatgpt.com/docs/models
- Terra API ID: https://developers.openai.com/api/docs/models/gpt-5.6-terra
- OpenRouter model slugs: https://openrouter.ai/api/v1/models
- Pi provider credential environment: https://github.com/earendil-works/pi/blob/main/packages/coding-agent/docs/providers.md
- Claude Code OpenRouter routing: https://openrouter.ai/docs/cookbook/coding-agents/claude-code-integration

## Effort

Effort belongs to each launch. Preserve the user's X High preference where the exact harness/provider/model and runtime metadata support it, and keep saved explicit launch choices. Use the existing verified capabilities catalog and actual account/CLI restrictions; Haiku 5.5's verified native choices are Low, Medium, High, X High and Max. Fall back to supported native behavior; High, Max and Ultra are distinct and unsupported X High must not be promoted to Max. Unknown combinations stay native. Do not create effort-specific Grunts or infer effort support from model existence. Cursor remains an available harness without app effort controls; Droid is excluded from recommendations.

## Report

Treat Run as the explicit request to apply this preset, using Code Overlord's supported Armoury operations in the active workspace. Finish with one result per role: Grunt ID, exact harness/provider/model, added/updated/unchanged/skipped/failed, on/off result, actual native answer result and reason. Report built-in on/off changes, and each one you left on with its reason, separately. Include immutable template revision, run ID, counts and private recovery reference; distinguish complete, partial, cancelled and failed. Unavailable or unverified roles stay visible in the report, never silently replaced or described as working.
