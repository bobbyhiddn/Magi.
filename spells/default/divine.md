# Divine (dv)

## Overview
The Divine spell reveals detailed information about files and directories, including size, permissions, and modification times. It can also search for specific files within directories.

## Features
- Detailed file information
- Directory content listing
- File search capability
- Recursive search
- Detailed timestamps

## Requirements
- Python package: `click`

## Installation
Built into Magi.CLI core spells.

## Usage
List current directory:
```bash
cast dv
```

Search for file:
```bash
cast dv <search_term>
```

## Output Information
- File/directory name
- File size in bytes
- File permissions (octal)
- Last modified timestamp
- Path (for search results)

## Examples

### List Directory Contents
```bash
cast dv
```

### Search for File
```bash
cast dv config
```

### Search in Subdirectories
```bash
cast dv .py  # Finds all Python files
```

## Display Format
```
filename    Size: X bytes    Permissions: XXX    Last Modified: YYYY-MM-DD HH:MM:SS
```

## Common Use Cases
1. File exploration
2. System inspection
3. Permission checking
4. File searching
5. Timestamp verification

## Search Features
- Partial name matching
- Extension filtering
- Recursive searching
- Path display
- Full details for each match

## Best Practices
1. Use specific search terms
2. Check permissions before operations
3. Verify timestamps when needed
4. Monitor file sizes
5. Review directory contents regularly

## Notes
- Recursive by default when searching
- Shows hidden files
- Real-time information
- Pattern matching for search
- Comprehensive file details