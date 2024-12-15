# Scribe (scb) - Complete Documentation

## Overview
The Scribe spell transcribes files and directories into well-formatted markdown documents, supporting various output options including aether storage, local files, and clipboard. It provides comprehensive support for directory traversal with optional Git-awareness.

## Core Features

### 1. Content Transcription
- Text file content extraction
- Directory structure mapping
- Binary file detection
- Unicode support
- Git-aware processing

### 2. Output Options
- Aether storage (~/.sanctum/.aether/)
- Local directory storage
- Clipboard copying
- Timestamped filenames
- Multiple saving options simultaneously

### 3. Git Integration
- .gitignore pattern support
- Optional .git directory inclusion
- Pattern-based file exclusion
- Clean directory mapping

## Technical Requirements

### Dependencies
```python
__requires__ = ['click', 'pyperclip', 'pathspec']
```

### Storage Structure
```plaintext
~/.sanctum/
└── .aether/
    └── transcription_{name}_{timestamp}.md
```

## Basic Usage

### Command Syntax
```bash
# Basic transcription
cast scb <path>

# Include Git files
cast scb <path> --include-git

# Verbose output
cast scb <path> -v
```

### Interactive Options
Each transcription prompts for:
1. Aether storage
2. Local storage (if not using aether)
3. Clipboard copying

## Complete Example Session

```bash
$ cast scribe .
 Transcribing your chosen realm...
 Send transcription to the aether? [y/N]: y
 The transcription has been sent to the aether.
 Copy transcription to clipboard? [y/N]:
```

Alternative flow with local storage:
```bash
$ cast scribe .
 Transcribing your chosen realm...
 Send transcription to the aether? [y/N]: 
 Save to local directory? [y/N]: y
 The transcription has been saved to [...]/transcription_dirname_20241215_093503.md
 Copy transcription to clipboard? [y/N]: y
 Transcription copied to clipboard!
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

## Feature Details

### File Processing
- Text content extraction
- Binary file detection
- Unicode error handling
- Markdown formatting
- Content preservation

### Directory Handling
- Recursive traversal
- Path normalization
- Git integration
- Pattern matching
- Error handling

### Storage Management
- Multiple storage options
- Timestamp generation
- Path handling
- Directory creation
- File naming

## Best Practices

### 1. Storage Selection
- Use aether for permanent storage
- Use local for temporary needs
- Use clipboard for immediate use
- Consider file organization
- Plan storage hierarchy

### 2. Git Integration
- Consider .gitignore patterns
- Decide on .git inclusion
- Review excluded files
- Check pattern matching
- Verify output completeness

### 3. Large Directories
- Review directory size first
- Consider storage space
- Check processing time
- Monitor memory usage
- Verify output completeness

### 4. Content Organization
- Use meaningful timestamps
- Organize by project
- Maintain consistent naming
- Review transcriptions
- Clean up old files

## Common Use Cases

### 1. Project Documentation
```bash
cast scb ./project_root
# Save to aether for permanent documentation
```

### 2. Code Review
```bash
cast scb ./feature_branch
# Copy to clipboard for immediate review
```

### 3. Knowledge Sharing
```bash
cast scb ./documentation
# Save locally for sharing
```

## Technical Details

### File Reading
- 1024-byte readability test
- UTF-8 encoding
- Error handling for binary files
- Unicode replacement characters
- Efficient memory usage

### Path Handling
- Absolute path resolution
- Relative path support
- Directory traversal
- Name collision handling
- Cross-platform compatibility

### Git Integration
- PathSpec pattern matching
- .gitignore parsing
- Directory exclusion
- Pattern compilation
- Efficient matching

## Error Handling

### File Operations
- Unicode decode errors
- IO errors
- Permission issues
- Path validation
- Resource cleanup

### Storage Operations
- Directory creation
- File writing
- Permission checking
- Space verification
- Resource cleanup

## Tips
- Review large directories before transcription
- Use meaningful names for local storage
- Regularly clean aether storage
- Test git pattern matching
- Verify transcription completeness

## Notes
- Large directories may take time to process
- Binary files are noted but not transcribed
- Git files are excluded by default
- Unicode characters are preserved
- All output is in markdown format
- Timestamps use YYYYMMdd_HHMMSS format

## Future Considerations
1. Additional output formats
2. Enhanced file type detection
3. Improved pattern matching
4. Performance optimizations
5. Extended metadata support