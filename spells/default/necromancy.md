# Necromancy (nc)

## Overview
The Necromancy spell creates a '.graveyard' realm to store deleted files. It's a prerequisite for the Fireball spell and works in conjunction with Raise_Dead for file recovery.

## Features
- Graveyard creation
- Persistent storage
- System integration
- Multi-spell support
- Location management

## Requirements
- Python package: `click`

## Installation
Built into Magi.CLI core spells.

## Usage
```bash
cast nc
```
or
```bash
cast necromancy
```

## Storage Location
Creates `.graveyard` in `~/.sanctum/.graveyard/`

## Examples

### Initialize Graveyard
```bash
cast nc
```

## Related Spells
- Fireball (fb) - Sends files to graveyard
- Raise_Dead (rd) - Recovers files from graveyard

## System Integration
1. Creates permanent storage location
2. Enables file deletion safety net
3. Supports recovery operations
4. Maintains file organization
5. Manages storage space

## Common Use Cases
- Setting up new environments
- Preparing for file cleanup
- Establishing recovery system
- System initialization
- Safety net creation

## Best Practices
1. Initialize before using Fireball
2. Check graveyard status regularly
3. Monitor available space
4. Clean old files periodically
5. Maintain graveyard organization

## Notes
- One-time setup per environment
- Required for Fireball spell
- Persistent between sessions
- Maximum 13 files stored
- Automatic oldest file removal