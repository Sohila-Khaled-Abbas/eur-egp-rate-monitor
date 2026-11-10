# Security Policy

## Supported material

This repository is a portfolio workflow template. Security reports are welcome for the published workflow JSON, documentation, and any future helper code maintained here.

## Reporting a vulnerability

Please do not publish credentials, tokens, personal chat identifiers, private execution payloads, or an exploitable vulnerability in a public issue.

Use GitHub's **Report a vulnerability** action under the repository's **Security** tab to submit a private vulnerability report. Include:

- the affected file, node, or workflow stage;
- the impact and realistic attack conditions;
- reproducible steps or a minimal proof of concept;
- a suggested mitigation, when known.

I will review reports as time permits and coordinate a fix or clarification before public disclosure. This is a personal portfolio repository and does not provide a guaranteed response-time SLA.

## Credential and data handling

- Never commit OpenRouter API keys, Telegram bot tokens, Telegram chat IDs, n8n credential exports, .env files, instance databases, or execution data.
- Configure provider credentials through n8n's credential manager.
- Replace the Telegram chat-ID placeholder locally after import.
- Re-select the Data Table in both Data Table nodes after creating it in your own instance.
- Treat n8n exports as potentially sensitive even when credential values are stored separately. Review every export before publishing it.
- If a secret is committed accidentally, revoke or rotate it with the provider immediately. Removing it in a later commit does not make the exposed secret safe.

## Scope

The workflow consumes a public rate feed and sends a notification to a Telegram destination configured by the operator. It does not require inbound public webhooks. Issues in third-party services, the public API, n8n itself, Telegram, or OpenRouter should be reported to their respective maintainers.
