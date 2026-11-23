# unoverse org starter

Everything a new org starts with on unoverse: one repo is one org, its folders at the root.

| Folder | Holds |
|---|---|
| `identity/` | who the org is: organisation, brand, purpose, story. Empty until you fill them |
| `styles/` | the org's look, as design tokens |
| `projects/` | the org's projects: a spec, its epics and its cards. Read `projects/AGENTS.md` first |
| `components/`, `templates/`, `apps/`, `atoms/` | what the org's screens are made of |
| `skills/`, `blocks/`, `agents/` | the org's Agents and what they know |
| `nodes/`, `objects/`, `pipelines/` | how the org connects to other systems and reads its documents |

## Start an org

1. **Use this template** (the button above) to make your org's repo.
2. In `unoverse.yaml`, change `org: my-org` to your org's name: lowercase letters, digits and hyphens.
3. In your unoverse Workspace, open the org's **Source** tab and connect this repo.

From then on, your org's Agents work on this repo by pull request, and every pull request is
checked by the same lint your universe runs.

Documentation: [docs.unoverse.ai](https://docs.unoverse.ai)
