# Auto Commit

[![Auto commit](https://github.com/Parixshit/AutoCommit/actions/workflows/auto_commit.yml/badge.svg)](https://github.com/Parixshit/AutoCommit/actions/workflows/auto_commit.yml)

This GitHub Actions workflow is designed to automatically generate and commit changes to a repository's `README.md` file on a schedule and when the `workflow_dispatch` event is triggered.

## Workflow

The `auto_commit` job runs on the `ubuntu-latest` virtual machine and has write permissions to the repository's contents. The job consists of the following steps:

1. **Check Repository and Branch:** This step checks if the specified repository and branch exist, and exits with an error if they do not.
2. **Checkout Repository:** This step checks out the specified branch of the repository using the `actions/checkout@v3` action.
3. **Configure Git:** This step configures the Git user to match the account that will be used for committing changes.
4. **Download Emojis:** This step downloads a list of emojis from the [Gitmoji](https://gitmoji.dev/) project using the `curl` and `jq` commands.
5. **Generate Commits:** This step generates a random number of commits (up to 30) with a random emoji and message using the fetched emojis and a timestamp based on the current time in the Asia/Kolkata timezone. The number of commits can be customized using the `num_commits` input, which has a default value of a random number between 1 and 30. If `num_commits` is greater than 30, `shuf` command is used to generate a random commit date from the last 365 days using the `date` command with the timezone set to Asia/Kolkata
6. **Push Changes:** This step pushes the generated commits to the specified branch of the repository using the `git push` command.

## Schedule

This workflow is triggered on a schedule using a cron expression that runs every day at midnight UTC (`0 0 * * 0,1,3,4,6`), except for Tuesdays and Fridays. The schedule can be adjusted by modifying the `cron` expression in the workflow file.

## Manual Trigger

This workflow can also be manually triggered using the `workflow_dispatch` event, which allows the user to specify the number of commits to generate using the `num_commits` input.
