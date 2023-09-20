# Latest commit date

This action checks the date of the latest commit in your Git history.

## Usage

Add the action to your workflows like so:

```yml
name: My GitHub Actions workflow

on: ...

jobs:
  my-job:
    runs-on: ubuntu-latest

    steps:
      - uses: actions/checkout@v3 # You need to checkout the repository first

      - uses: ithaque-renovation/latest-commit-date-action@v1
```

### Inputs

You can specify a `branch` input variable to check the commit history of a specific branch. Default value for `branch` is `main`.

```yml
steps:
  - uses: actions/checkout@v3

  - uses: ithaque-renovation/latest-commit-date-action@v1
    with:
      branch: my-feature-branch
```

### Outputs

You can retrieve the outputs of the action in a later step:

```yml
steps:
  - uses: actions/checkout@v3

  - id: my-step # Call the action with an ID to retrieve the outputs
    uses: ithaque-renovation/latest-commit-date-action@v1

  - run: echo ${{ steps.my-step.outputs.latest-commit-date }}
```

Available outputs:

- `current-date`: The current date at the time the action runs
- `latest-commit-date`: The date of the latest commit in the Git history of the specified branch
- `is-today`: A boolean indicating whether the current date and the latest commit date are the same (true) or different (false)
