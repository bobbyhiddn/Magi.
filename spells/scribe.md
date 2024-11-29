# Scribe (scb)

## Overview
The Scribe spell transcribes files and directories into well-formatted markdown documents. It's an essential tool for documentation, code review, and project analysis.

## Features
- File content transcription
- Directory structure mapping
- Git-aware processing
- Multiple storage options
- Unicode support

## Requirements
- Python package: `click`

## Installation
```bash
cast ponder scribe
```

## Usage
Basic transcription:
```bash
cast scb <path>
```

With Git inclusion:
```bash
cast scb <path> --include-git
```

## Storage Options
1. Local storage (current directory)
2. Aether storage (~/.sanctum/.aether/)

## Examples

### Transcribe a File
```bash
cast scb important_script.py
```

### Transcribe a Directory
```bash
cast scb ./project_folder
```

### Include Git Files
```bash
cast scb ./project_folder --include-git
```

## Output Format

### File Transcription
```markdown
# filename.ext

```content```
```

### Directory Transcription
```markdown
# Directory: directory_name

## /subdirectory/
/subdirectory/file.ext: 
```content```
```

## Features in Detail

### File Handling
- Text file content extraction
- Binary file detection
- Unicode error handling
- Code block formatting

### Directory Processing
- Recursive traversal
- Git directory handling
- Path preservation
- File type detection

### Storage Management
- Timestamp-based naming
- Aether integration
- Local storage option
- UTF-8 encoding

## Common Use Cases
1. Project documentation
2. Code review preparation
3. Archive creation
4. Knowledge sharing
5. Project analysis

## Best Practices
- Choose appropriate storage location
- Consider Git inclusion needs
- Review large directories first
- Use meaningful timestamps
- Organize transcriptions logically

## Technical Details
- Uses UTF-8 encoding
- Handles file read errors
- Preserves directory structure
- Supports various file types
- Timestamped output files

## Notes
- Large directories may take time
- Binary files are noted but not transcribed
- Git files are optional
- Unicode characters are preserved
- Output is always markdown format