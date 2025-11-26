# command-changelog

A Claude Code slash command for generating changelogs from git commits.

## Installation

```bash
# Clone to your preferred location
git clone git@github.com:claude-commands/command-changelog.git <clone-path>/command-changelog

# Symlink (use full path to cloned repo)
ln -s <clone-path>/command-changelog/changelog.md ~/.claude/commands/changelog.md
```

## Usage

```
/changelog           # Since last tag
/changelog v1.2.0    # Since specific tag
/changelog HEAD~50   # Last 50 commits
```

## What it does

1. Finds the last release tag (or uses specified starting point)
2. Parses commits following Conventional Commits specification
3. Categorizes into Keep a Changelog sections
4. Extracts issue/PR references
5. Generates formatted changelog ready for release

## Output Format

```markdown
## [Unreleased] - 2025-11-26

### Added
- User authentication flow (#123)
- API rate limiting support

### Fixed
- Pagination bug in search results (#456)
- Memory leak in connection pool

### Changed
- **BREAKING**: Renamed `getUser` to `fetchUser`
- Improved query performance by 40%
```

## Features

- **Conventional Commits**: Parses `feat:`, `fix:`, `BREAKING CHANGE:`, etc.
- **Keep a Changelog**: Follows the standard format
- **Smart categorization**: Infers category even for non-conventional commits
- **Reference linking**: Extracts `#123`, `fixes #456` references
- **Version suggestion**: Recommends semver bump based on changes

## Supported Commit Types

| Type | Changelog Section |
|------|-------------------|
| `feat:` | Added |
| `fix:` | Fixed |
| `perf:` | Changed |
| `refactor:` | Changed |
| `BREAKING CHANGE:` | Changed (Breaking) |
| `deprecate:` | Deprecated |
| `remove:` | Removed |
| `security:` | Security |

## Requirements

- Git repository with commits
- Claude Code with Sonnet model access

## Updates

```bash
cd <clone-path>/command-changelog && git pull
```
