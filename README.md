# Actions

Shared actions for all organization repos.

```yaml
- uses: HereticSoftware/actions/<action>@<sha> # v1.0.0
```

Pin to a commit SHA with the release tag as a comment; Renovate (`helpers:pinGitHubActionDigests`) updates both.

## [cake-file](cake-file/action.yaml)

Runs `dotnet run --file <file> -c Release -- --target <target> <arguments>`.

| Input | Required | Default | Description |
|---|---|---|---|
| `file` | | `cake.cs` | Cake file to execute. |
| `target` | ✓ | | Cake target. |
| `arguments` | | | Additional arguments, separated by spaces. |

```yaml
- uses: HereticSoftware/actions/cake-file@<sha>
  with:
    target: Renovate
    arguments: --repository=${{ github.repository }}
```

## [enforce-tag-on-branch](enforce-tag-on-branch/action.yaml)

On tag runs, fails when the tagged commit is not on `origin/<branch>`. Passes on non-tag runs. Requires a checkout with `fetch-depth: 0`.

| Input | Required | Default | Description |
|---|---|---|---|
| `branch` | | `main` | Branch the tag must be on. |

```yaml
- uses: actions/checkout@<sha>
  with:
    fetch-depth: 0
- uses: HereticSoftware/actions/enforce-tag-on-branch@<sha>
```
