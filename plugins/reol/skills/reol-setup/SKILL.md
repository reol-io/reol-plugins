---
name: reol-setup
description: Connect ReOL, check available access, and select an agent identity and app before starting a ReOL workflow. Use for first setup or connection and identity problems.
---

# Set up ReOL

Help the user connect ReOL and establish the context for their task.

1. Check whether this plugin's ReOL tools are available. A marketplace being added or a package being listed does not mean the plugin is installed, enabled, authenticated, or usable. If tools are missing, guide the user to install and enable ReOL in the host's Plugins interface, then check tool availability in a fresh conversation when needed. Report the exact pending step.
2. Use the host's existing ReOL OAuth connection flow for `https://mcp.reol.io/mcp`. Let the user complete sign-in and consent in the host or provider page. Reuse an existing connection when available. Never request, extract, display, or save tokens, passwords, client secrets, cookies, or authorization headers; never put credentials in plugin files. Do not invent an app binding or configure a replacement server.
3. Read the available ReOL docs tool and use its search tool to discover the current read-only identity and app discovery operations. Read their exact schemas before calling them. Do not guess operation names, argument placement, account IDs, or scopes. Search/docs discovery must lead execution.
4. When the current docs require a Participant, show accessible identities and use the user's selected Participant's stable `actorId`. Retain that selection for the task and pass it in the location required by each discovered schema. Do not substitute an email, display name, account identity, or newly created Participant. Reconfirm only if the selection is ambiguous or must change. Identify the requested app and use its returned context identifiers and current catalog/version references as documented.
5. Verify access with a relevant documented read-only call. Distinguish tools available, OAuth completed, selected identity, and successful app read. An access error or consent screen is not proof of connection success. Do not create an app, agent, asset, connection, subscription, or other record just to test setup.

Continue the user's task after a successful check. If blocked, report the observed gate and the next user action without exposing sensitive connection details. Public help is available at https://reol.io/docs/; support contact is contact@reol.io.
