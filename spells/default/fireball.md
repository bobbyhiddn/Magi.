# Fireball (fb)

## Overview
The Fireball spell safely deletes files or directories by moving them to a '.graveyard' realm. This provides a temporary location for deleted files, allowing for potential recovery if needed.

## Features
- Safe file/directory deletion
- Graveyard storage system
- Recovery possibility
- User confirmation
- Size management

## Requirements
- Python package: `click`
- Active Necromancy session (graveyard realm)

## Installation
Built into Magi.CLI core spells.

## Usage
```bash
cast fb <file_or_directory>
```
or
```bash
cast fireball <file_or_directory>
```

## Process
1. Confirms graveyard exists (requires Necromancy)
2. Requests user confirmation
3. Moves target to graveyard
4. Manages graveyard size (max 13 items)

## Examples

### Delete a File
```bash
cast fb obsolete_script.py
```

### Delete a Directory
```bash
cast fb old_project/
```

## Safety Features
1. Confirmation prompts
2. Graveyard storage
3. Recovery possible via raise_dead
4. Size management
5. Path verification

## Storage Location
Files are moved to `~/.sanctum/.graveyard/`

## Common Use Cases
- Removing unused files
- Cleaning directories
- Project cleanup
- Test file removal
- Temporary file management

## Best Practices
1. Verify target path before casting
2. Use necromancy to ensure graveyard exists
3. Remember important filenames for recovery
4. Monitor graveyard size
5. Regularly clean old files

## Notes
- Requires active graveyard
- Limited to 13 most recent items
- Oldest items automatically removed
- Recovery possible with raise_dead spell
- Confirmation required for safety