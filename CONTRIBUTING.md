# Contributing

Thanks for taking the time to improve this project.

## Before opening an issue or pull request

- Search existing issues and discussions for duplicates.
- Describe the n8n version and node involved.
- Include a minimal sanitized reproduction; never attach credentials, tokens, chat IDs, personal data, or complete private execution payloads.
- Keep changes focused and explain how they were tested.

## Workflow changes

1. Fork the repository and create a topic branch.
2. Make the smallest change that addresses the problem.
3. Import the workflow into a disposable n8n workspace and validate the changed node settings.
4. Test both the rate-change TRUE path and the no-change FALSE path when comparison logic changes.
5. Review the exported JSON for secrets and private instance metadata before committing.
6. Open a pull request with a concise summary, screenshots when useful, and a verification checklist.

## Documentation and accuracy

Do not describe indicative rates as guaranteed bank quotes. Do not invent results, model behavior, uptime, or financial outcomes. Keep the two rate directions distinct: customer sells EUR to a bank versus customer buys EUR from a bank.
