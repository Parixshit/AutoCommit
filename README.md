# Auto commit workflow

[![Auto commit](https://github.com/Parixshit/red/actions/workflows/auto_commit.yml/badge.svg?branch=workflow)](https://github.com/Parixshit/red/actions/workflows/auto_commit.yml)

This GitHub Actions workflow is designed to automatically generate and commit changes to a repository's `README.md` file on a schedule and when the `workflow` branch is pushed.

### Workflow

The `auto_commit` job runs on the `ubuntu-latest` virtual machine and has write permissions to the repository's contents. The job consists of the following steps:

1. **Checkout repo:** This step checks out the `main` branch of the repository using the `actions/checkout@v3` action.
2. **Generate commits:** This step generates a random number of commits (up to 30) with a randomized date and commit message. The commit message includes the iteration number, total number of iterations, and commit date. The commit message also indicates that it is an automated commit generated by this workflow.
3. **Push changes:** This step pushes the generated commits to the `main` branch of the repository.

### Schedule

This workflow is triggered on a schedule using a cron expression that runs every Sunday, Monday, Wednesday, Thursday, and Saturday at midnight UTC (`0 0 * * 0,1,3,4,6`).