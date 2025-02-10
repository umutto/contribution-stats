# Contribution Statis

This GitHub Action calculates and comments on pull requests with monthly lines of code contribution statistics. When a pull request is made to your `main` branch (or configured branch), this action will:

1. Calculate the total lines of code added and removed in your repository for the current month.
2. Calculate the lines of code added and removed by the pull request author (or a specified contributor) for the current month.
3. Calculate the contribution percentage based on lines of code added.
4. Add a comment to the pull request with these statistics.

## Inputs

- **`contributor-name` (optional):**

  - The git username to analyze contributions for.
  - If not provided, it defaults to the author of the pull request that triggered the action.
  - Example use in workflow:

    ```yaml
    uses: umutto/contribution-stats@v1
    with:
      contributor-name: "some-git-user"
    ```

## Outputs

Adds a comment to the pull request that triggered the action, listing the monthly contribution stats for the given user.

## Usage

To use this action, create a workflow file (e.g., `.github/workflows/contribution-stats.yml`) in your repository and add the following step:

```yaml
name: Contribution Statistics

on:
  pull_request:
    branches:
      - main

jobs:
  calculate_stats:
    runs-on: ubuntu-latest
    steps:
      - uses: umutto/contribution-stats@v1
```
