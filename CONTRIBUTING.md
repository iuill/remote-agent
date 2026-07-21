# Contributing

This document is for people developing `remote-agent` itself. User-facing setup belongs in the
README.

## Development Setup

Open the repository in a Dev Container to get Node.js 24, the repository-pinned pnpm version,
TypeScript 7 support, and `gitleaks`. Dependencies are installed automatically when
the container is created.

TypeScript 7 is the project compiler and editor language server. TypeScript 6 remains installed
under the `typescript` package name only as a compatibility API for development tools that have not
yet migrated to the TypeScript 7 API.

Alternatively, use the Nix development environment:

```bash
direnv allow
pnpm install
```

The app is split into a Node API/BFF and a browser SPA. Start both in development mode with:

```bash
pnpm dev
```

Useful commands:

```bash
pnpm fix
pnpm lint
pnpm typecheck
pnpm test
pnpm build
```

`lefthook` runs formatting, lint fixes, and staged secret scanning before commits. The secret scan
uses `gitleaks`, which is provided by both development environments.

## Generated Files

Regenerate checked-in generated artifacts with:

```bash
pnpm generate
```

This updates files such as the database documentation and OpenAPI document when the corresponding
source definitions change.

## Release Checks

The release script performs the publish-time validation flow:

```bash
pnpm release
```

It validates the package, checks bundled dependency licenses, updates generated artifacts, creates
the release commit/tag, and pushes the release refs.

## Project References

Before making larger changes, read the relevant project references:

- `docs/coding-guideline.md`
- `docs/coding-process.md`
- `docs/commit_message.md`
- `docs/branch_naming.md`
- `docs/e2e-exploratory-testing-process.md`
