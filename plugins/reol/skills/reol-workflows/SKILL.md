---
name: reol-workflows
description: Find and use ReOL apps, agents, assets, and connections through current ReOL search and operation docs. Use for ordinary ReOL tasks after connecting an account.
---

# Work with ReOL

Turn the user's request into the smallest supported ReOL workflow. Describe results in terms of apps, agents, assets, and connections.

## Discover the current workflow

Use the connected ReOL search and docs tools to find operations for the user's goal. Read the matching operation's current input schema, access requirements, outputs, and recovery guidance before execution. Search results identify candidates; they do not grant access or prove that an action exists. If a capability is absent or undocumented, explain the limitation rather than inventing an operation or attempting an alternate endpoint.

Follow the current docs to discover accessible identities and apps. When required, use the selected Participant's stable `actorId` consistently throughout the task; respect the schema's argument placement for each operation. Keep returned app/context identifiers and catalog digests with the selected context. Refresh docs on a definition or catalog change, reassess the same intent, and use the newly documented schema before proceeding. Ask for a selection only when the intended identity or target cannot be determined.

Resolve names to exact returned IDs before acting. For assets, preserve the exact asset reference and version or revision returned by ReOL; distinguish an asset from a particular version. Do not silently replace a requested version with the latest or substitute a similarly named item. When current docs require an expected version, digest, cursor, or other precondition, carry it through exactly.

## Execute the requested task

Use read-only discovery to establish the target and relevant state. Perform only actions supported by the discovered docs and authorized by the user's request. Resolve missing information that materially changes the target, audience, permissions, or external effect before writing. A read or status request does not authorize creating records. Use host-managed connection flows for sign-in; never handle credentials in chat or files.

For a documented write, retain the exact intent, target IDs, input, version preconditions, and documented idempotency or request key through execution and recovery. Use a stable key only where the current operation supports it; do not invent a key field or assume every operation is idempotent.

If a write times out, disconnects, or returns an ambiguous outcome, mark it unknown and stop dependent writes. Follow that operation's documented status, receipt, lookup, or read-back recovery path using the same intent and identifiers. Retry only when its documented recovery semantics establish that doing so is safe, preserving the original key and inputs where required. Do not generate a new key, change targets, or repeat a create to probe for success. If no safe recovery path is documented or the outcome remains unresolved, report the uncertainty and what evidence is needed before continuing.

Check the resulting state through a documented read or receipt when available. Report what was found or changed, exact relevant references and versions, and any pending or unknown result. Do not equate an accepted request, queued action, marketplace addition, or installed package with a completed workflow.
