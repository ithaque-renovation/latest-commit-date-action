# Latest commit date

This action checks the date of the latest commit in the Git history.

## Usage

Add the action to your workflow like so:

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

You can checkout a specific ref in the Checkout Action, this will impact which history is read by `latest-commit-date-action`.
See [Checkout Action's documentation](https://github.com/actions/checkout) for more information on how to control the ref.

```yml
# Example
steps:
  - uses: actions/checkout@v3
    with:
      ref: my-feature-branch # Ref can be a branch, a SHA or a tag

  - uses: ithaque-renovation/latest-commit-date-action@v1
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
- `latest-commit-date`: The date of the latest commit in the Git history of the specified ref
- `is-today`: A boolean indicating whether the current date and the latest commit date are the same (true) or different (false)
