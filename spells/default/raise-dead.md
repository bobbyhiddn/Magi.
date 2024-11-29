# Raise Dead (rd)

## Overview
The Raise Dead spell recovers files from the graveyard realm, allowing you to restore previously deleted files and directories.

## Features
- File recovery
- Interactive selection
- Automatic renaming
- Graveyard management
- Path restoration

## Requirements
- Python package: `click`
- Active Necromancy session (graveyard realm)

## Installation
Built into Magi.CLI core spells.

## Usage
Restore specific file:
```bash
cast rd <filename>
```

Interactive mode:
```bash
cast rd
```

## Recovery Process
1. Lists available files in graveyard
2. Allows file selection
3. Restores with "undead_" prefix
4. Moves to current directory
5. Removes from graveyard

## Examples

### Interactive Recovery
```bash
cast rd
```

### Direct Recovery
```bash
cast rd important_file.txt
```

## Output Location
Files are restored to the current directory with "undead_" prefix:
- Original: script.py
- Restored: undead_script.py

## Common Use Cases
1. Recovering deleted files
2. Restoring backup copies
3. Retrieving test files
4. Emergency recovery
5. File version recovery

## Best Practices
1. Check graveyard contents first
2. Note original filenames
3. Verify restoration location
4. Check available space
5. Remember filename changes

## Notes
- Requires existing graveyard
- Automatic prefix addition
- Interactive file selection
- Current directory restoration
- Original file removal from graveyard