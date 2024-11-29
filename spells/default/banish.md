# Banish (bn)

## Overview
The Banish spell exiles files or directories to a temporary location (/tmp/.exile or C:\temp\.exile), removing them from the current workspace without permanent deletion.

## Features
- Temporary file removal
- Cross-platform support
- Directory support
- Location management
- Path preservation

## Requirements
- Python package: `click`

## Installation
Built into Magi.CLI core spells.

## Usage
```bash
cast bn <file_or_directory>
```
or
```bash
cast banish <file_or_directory>
```

## Storage Location
- Unix: `/tmp/.exile/`
- Windows: `C:\temp\.exile\`

## Examples

### Banish a File
```bash
cast bn temporary_file.txt
```

### Banish a Directory
```bash
cast bn test_directory
```

## System Integration
1. Creates exile directory if needed
2. Moves target to exile location
3. Preserves file/directory name
4. Maintains file structure
5. Cross-platform compatibility

## Common Use Cases
1. Temporary file removal
2. Workspace cleanup
3. Test file management
4. Quick organization
5. Temporary archiving

## Best Practices
1. Verify target path
2. Check exile directory location
3. Remember exiled file names
4. Monitor exile directory size
5. Clean exile directory periodically

## Notes
- Location varies by platform
- Directory created automatically
- Files remain until system cleanup
- No automatic recovery spell
- Useful for temporary removal