# Automated-Commit

Automated-Commit is a simple and reusable example of a GitHub Actions workflow that periodically updates a file (`TIMESTAMP.txt`) with the current date and time and performs an automatic commit when it detects changes.

## Description

This repository demonstrates how to automate routine tasks in a repository using GitHub Actions. The main workflow:

- Clones the content from the `master` branch.
- Updates (or creates) a `TIMESTAMP.txt` file with the current date and time.
- Performs a commit if the file changed.
- Pushes the commit back to the `master` branch.

The goal is to serve as a template for automatic maintenance tasks (for example, periodic updates, status files, or similar scheduled tasks).

## Features

- Automatically executable on schedule (every 12 hours by default).
- Allows manual execution from the Actions tab (`workflow_dispatch`).
- Minimal configuration: Git name and email configured in the workflow.

## Workflow Structure

The workflow is defined in `.github/workflows/master.yml` and includes:

- Triggers: `schedule` (cron every 12 hours) and `workflow_dispatch` for manual execution.
- Main job: `update_commit` that runs on `ubuntu-latest`.
- Steps: checkout, configure Git, update `TIMESTAMP.txt`, commit, and push.
- Permissions: the workflow needs write permissions (default GITHUB_TOKEN usually suffices).

## Requirements

- A repository on GitHub.
- GitHub Actions enabled in the repository.

## Installation and Usage

1. Use this repository as a template (click the "Use this template" button) or clone it locally.
2. Open `.github/workflows/master.yml` and customize the configuration values (see "Configuration" section below).
3. Push the changes to `master` to activate the workflow.

### Manual Execution

1. Go to the `Actions` tab in your repository.
2. Select the `Automated-Commit` workflow.
3. Click "Run workflow" and confirm the branch.

## Configuration

Edit `.github/workflows/master.yml` as needed:

- Configure the `GIT_USER_EMAIL` and `GIT_USER_NAME` variables in Settings > Secrets and variables > Variables (optional; if not set, the default GitHub Actions account will be used).
- Change the cron frequency if you need a different interval.
- If you prefer, change the filename `TIMESTAMP.txt` to another target file.

Security best practice: use the `GITHUB_TOKEN` provided by Actions for automatic pushes; avoid putting personal access tokens in plain text.

## Common Customizations

- Modify the cron: change the expression in `schedule` within the yml file.
- Change the target file: update the filename that the script writes to.
- Add tests or validations: insert additional steps before the commit to validate changes.

## Contributing

Contributions are welcome:

1. Open an issue to discuss major changes.
2. Send Pull Requests with clear descriptions.

## Support

For questions or issues, open an issue in the `Issues` section of the repository.

---

Thank you for using Automated-Commit.
