# Repository conventions

## Naming

All repository names are **lowercase kebab-case**, shaped as:

```
<prefix>-<area>-<thing>
```

| Prefix | Meaning | Example |
|---|---|---|
| `zs-` | Zscaler work, 2025 onward | `zs-ot-ebc-dashboard` |
| `cp-` | Check Point era — archived (repos date from 2022–2024) | `cp-cloudguard-ruleset-tools` |
| `cp-archive-` | Superseded by a consolidated `cp-` toolkit | `cp-archive-dome9-permissions` |
| `ham-` | Amateur radio | `ham-aprs-igate` |
| `tool-` | Small personal utilities | `tool-xbox-usage-monitor` |
| `learn-` | Course material and exercises | `learn-terraform-associate` |
| `lab-` | Sandbox and scratch work | `lab-react-firebase-test` |
| *(none)* | Standalone personal projects and the site | `daily-intel-briefing` |

Rules:

- Lowercase only. No `PascalCase`, no `snake_case`, no mixed styles.
- Spell things out — `cloudguard`, not `cg`; `terraform`, not `tf`.
- The `<area>` is the product or domain (`cloudguard`, `spectral`, `ot`, `cloud-connector`).
- Never rename `nilsujma-dev` — it is the profile repository, and renaming it removes the profile page.
- Never rename `nilsujma.io` without updating GitHub Pages — the published URL contains the repo name.

## Suggested `zs-` areas

`zs-ot-*` · `zs-iot-*` · `zs-cloud-connector-*` · `zs-zpa-*` · `zs-zia-*` · `zs-lab-*` · `zs-demo-*`

## Topics

Every repository carries topics so the account is filterable without relying on names alone.

- **Era:** `zscaler`, `check-point`
- **Product:** `cloudguard`, `spectral`, `shiftleft`, `dome9`, `cloud-connector`, `zpa`, `zia`
- **Domain:** `cspm`, `appsec`, `iam`, `devsecops`, `kubernetes`, `terraform`, `ot-security`, `iot`
- **Lifecycle:** `archived`, `superseded`, `template`

## Starting a new repository

```sh
gh repo create nilsujma-dev/zs-<area>-<thing> \
  --private \
  --template nilsujma-dev/zs-repo-template \
  --description "One sentence on what this does."
```

Then set topics:

```sh
echo '{"names":["zscaler","<area>"]}' \
  | gh api -X PUT repos/nilsujma-dev/zs-<area>-<thing>/topics --input -
```

## Lifecycle

- **Active** — current work, writable.
- **Archived** — read-only. Used for a finished era or a dead experiment. Reversible.
- **Superseded** — archived *and* absorbed into a consolidated repo; the description says where it went.
