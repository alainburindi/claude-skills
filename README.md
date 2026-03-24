# Claude Skills

A collection of Claude Code slash commands for the team.

## Installation

```bash
/plugin install claude-skills@alainburindi
```

## Available Skills

| Skill | Command | Description |
|---|---|---|
| Mac Migration | `/mac-migration` | Migrate your dev environment from an old Mac to a new Mac |

## Usage

### Mac Migration
```bash
/mac-migration                  # Start from the beginning
/mac-migration audit            # Jump to Phase 1: Audit old Mac
/mac-migration git-check        # Jump to Phase 2: Check unpushed git work
/mac-migration generate-script  # Jump to Phase 3: Generate setup script
/mac-migration transfer         # Jump to Phase 4: Transfer files
/mac-migration databases        # Jump to Phase 5: Migrate databases
/mac-migration apps             # Jump to Phase 6: Copy apps and data
/mac-migration dotfiles         # Jump to Phase 7: Copy dotfiles
/mac-migration claude-data      # Jump to Phase 8: Migrate Claude Code data
/mac-migration shell            # Jump to Phase 9: Optimize shell
/mac-migration auth             # Jump to Phase 10: Re-authenticate
```

## Adding a New Skill

1. Create a new folder under `skills/`
2. Add a `SKILL.md` file
3. Add any reference files under `references/`
4. Update this README

## Contributing

PRs welcome!
