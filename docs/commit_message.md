# Commit Message Convention

Based on [Conventional Commits](https://www.conventionalcommits.org/).

## Format

```
<type>(<scope>): <description>

[optional body]
```

## Types

| Type       | When to use                                             |
| ---------- | ------------------------------------------------------- |
| `feat`     | New feature or capability                               |
| `fix`      | Bug fix                                                 |
| `refactor` | Code change that neither fixes a bug nor adds a feature |
| `chore`    | Build process, tooling, dependencies, CI changes        |
| `docs`     | Documentation only                                      |
| `test`     | Adding or updating tests                                |
| `perf`     | Performance improvement                                 |

## Scope

Optional. Use the module, package, or feature area name.

- Monorepo: package name (e.g. `feat(api): ...`, `fix(web): ...`)
- Single package: feature area (e.g. `feat(auth): ...`, `fix(db): ...`)

## Rules

- Description: use an imperative, concise phrase with no period at the end
- Language: Japanese
- Keep the first line under 72 characters
- Use body for "why", not "what" (the diff shows "what")

## Examples

Good:

- `feat(api): ユーザー認証エンドポイントを追加`
- `fix: キュー処理の競合状態を解消`
- `chore: 依存関係を更新`
- `refactor(auth): トークン検証を純粋関数として分離`

Bad:

- `Fixed bug` (no type, vague)
- `feat: ユーザー認証システムに関する新機能を追加するための変更` (too long)
- `update` (no type, no description)
