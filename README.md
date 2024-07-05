# Milestone Sync Action

This action Scaffold and update GitHub milestones based on a YAML definition.

NOTE: This action relies on having the file
available in the working directory. This means that if the
manifest file lives in a GitHub repository, the repository
will need to be checked out before this action is run.

## Inputs

## `milestones-file`

**Optional** The path of the milestones file.
Defaults to `manifest.yaml`.

## `GH_TOKEN`

**Required** The GitHub Token to read & write milestones

Ensure the following permissions are set

```yaml
    permissions:
      contents: read
      issues: write
```

## Example usage

```yaml
steps:
  - uses: actions/checkout@v4

  - uses: pbronneberg/milestone-sync-action@v1
  - with:
      milestones-file: ".github/milestones.yml"
      GH_TOKEN: ${{ secrets.GITHUB_TOKEN }}
```

## Example milestones YAML

```yaml
- title: "My first milestone"
  description: |
    A multi-line description on what is delivered.
    It should of course not create illegal YAML characters
  dueDate: 2024-08-01
- title: "Next major milestone"
  description: The next thing to deliver
  dueDate: 2024-09-01
```
