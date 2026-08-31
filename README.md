# Mailbutler Agent Skill

Mailbutler is a narrative-aware inbox-triage skill for AI agents. It reads real mail through an owner-approved adapter, surfaces only what deserves attention, and keeps drafting and sending behind separate per-message approvals.

The durable abstraction is simple: **filter every email through an evidence-backed model of what currently matters to the owner.**

## Why it is different

- Read-only triage with explicit mutation boundaries.
- Untrusted-email handling that resists prompt injection.
- Relevance scored against active arcs and open loops, not generic importance.
- Fail-open handling when a message cannot be read confidently.
- Provenance-backed local narrative with no committed mailbox data.
- Provider-neutral model routing and a documented data boundary.

## Install

```bash
npx skills add AntreasAntoniou/mailbutler-agent-skill
```

The skill expects an approved mailbox adapter. Its examples use the [`gog`](https://github.com/steipete/gogcli) CLI for Gmail. Authenticate the adapter separately; this repository contains no credentials, mailbox content, or account configuration.

## Validate

```bash
python3 -m unittest discover -s tests
python3 scripts/judgment_tools.py <judgments.json>
```

## Privacy

Mailbox data and the local narrative are sensitive. Keep narrative state out of repositories and do not introduce a new model, logging, analytics, or storage provider without the mailbox owner's approval. See [the security contract](references/security-contract.md).

## Name and non-affiliation

This repository publishes an independent open-source **agent skill** named `mailbutler`. It is not affiliated with, endorsed by, or connected to Mailbutler GmbH or its Mailbutler email-extension product. The repository name intentionally includes `agent-skill` to make that distinction clear.

## License

MIT. See [LICENSE](LICENSE).
