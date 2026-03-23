# LEAP Registry

The official registry of community experiments and labs for [LEAP2](https://github.com/leaplive/LEAP2).

## Browse

```bash
leap discover
leap discover --tag algorithms
```

Install an entry:

```bash
leap add <repository-url>
```

## Entry schema

Each entry in `registry.yaml` has:

| Field | Required | Description |
|-------|----------|-------------|
| `name` | yes | Unique identifier (lowercase, hyphens) |
| `type` | yes | `experiment` or `lab` |
| `description` | yes | One-line description |
| `repository` | yes | Public git URL |
| `display_name` | no | Human-readable name (defaults to `name`) |
| `author` | no | Author name or GitHub username |
| `tags` | no | List of tags for filtering |

## Submit an entry

### Option 1: `leap publish` (recommended)

From your project root:

```bash
leap publish my-experiment
```

This will:
1. Run `leap doctor` and abort if there are errors
2. Validate required fields (description, repository)
3. Verify the repository is reachable
4. Check for uncommitted or unpushed changes
5. Create a GitHub issue on this repo via `gh` CLI

### Option 2: Manual issue

Open an [issue](https://github.com/leaplive/registry/issues/new) with a YAML code block:

````
```yaml
- name: my-experiment
  type: experiment
  display_name: My Experiment
  description: What it does
  author: your-github-username
  repository: https://github.com/you/my-experiment
  tags: [topic1, topic2]
```
````

## Review process

1. Submit via `leap publish` or manual issue
2. Maintainer verifies the repository is public and contains a valid LEAP experiment/lab
3. Entry is added to `registry.yaml` and the issue is closed
