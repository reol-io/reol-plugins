# ReOL plugin

Use ReOL apps, agents, assets, and connections from a supported plugin host. Version **0.1.0** bundles **reol-setup** and **reol-workflows**, with a connection to the existing ReOL service.

## Install

Give your Codex agent this one instruction:

> Install the ReOL plugin and its bundled Skills from https://github.com/reol-io/reol-plugins: add that marketplace, install and enable reol@reol-plugins, then guide me through any required ReOL sign-in and consent and check read-only access.

With **Codex CLI 0.163.0**, the two supported commands can also be run on one shell line:

```sh
codex plugin marketplace add reol-io/reol-plugins && codex plugin add reol@reol-plugins
```

The first command adds the source; the second installs the plugin and its Skills. Adding the marketplace alone does not install ReOL. Review the host's installation prompts. If your client lacks `plugin add`, use its supported Plugins interface to install ReOL from this marketplace. Availability depends on the host and workspace policy. See [OpenAI plugin packaging guidance](https://developers.openai.com/plugins/build/plugins).

Installation and sign-in are separate. Complete any OAuth sign-in and consent through the host or ReOL page; never paste credentials into chat or package files. Open a fresh conversation if needed to load installed tools and Skills. Ask **“Help me connect ReOL and check what I can access.”** The setup Skill checks the current tools, identity and app access with a read-only operation.

The package uses Streamable HTTP at `https://mcp.reol.io/mcp`. Host-managed authentication uses the existing service's discovery flow. It does not deploy another service. A successful package installation does not establish successful OAuth or app access.

## Use

- “Show me the ReOL apps I can access.”
- “Help me find the asset and exact version I need.”
- “What can I do with my selected ReOL app?”

The Skills read current operation guidance at runtime, keep the selected Participant identity where required, preserve exact asset versions, and check an uncertain write outcome before retrying. Available actions depend on your account and app access.

## Check, update, or remove

```sh
codex plugin list --json
codex plugin marketplace upgrade reol-plugins
codex plugin add reol@reol-plugins
codex plugin remove reol@reol-plugins
codex plugin marketplace remove reol-plugins
```

Run list to inspect installation, upgrade to refresh the Git marketplace, and add again to install the published version. Removing the plugin removes its local package; removing a marketplace removes its source registration. Use the host's connection settings to manage OAuth connections separately.

## Release files

- `.agents/plugins/marketplace.json`: install-source catalog.
- `plugins/reol/plugin.json`: portable Agent Plugins manifest.
- `plugins/reol/mcp.json`: existing ReOL MCP endpoint.
- `plugins/reol/skills/reol-setup/SKILL.md`: setup and read-only access checks.
- `plugins/reol/skills/reol-workflows/SKILL.md`: ordinary workflows using current search and docs.
- `reol-0.1.0.zip`: plugin-only archive with one `reol/` root.
- `SHA256SUMS`: release file checksums.

This repository distributes release snapshots through a repository marketplace. A universal public Plugins Directory listing is separate and is not claimed. Pull requests, Issues, Discussions, Wiki, Projects and Actions are disabled on this release source. Public repositories can still be read and forked.

Help: [ReOL documentation](https://reol.io/docs/). Contact: contact@reol.io.
