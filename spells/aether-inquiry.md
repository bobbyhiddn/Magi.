# Aether Inquiry (ai)

## Overview
The Aether Inquiry spell allows you to communicate with an AI oracle powered by OpenAI's GPT models. It provides a powerful interface for asking questions, generating code, and analyzing files or entire directories.

## Features
- Interactive AI conversations
- File and directory analysis
- Code generation
- Conversation history management
- Multiple export formats

## Requirements
- OpenAI API key (set as `OPENAI_API_KEY` environment variable)
- Python packages: `click`, `openai`

## Installation
```bash
cast ponder aether_inquiry
```

## Usage
Basic invocation:
```bash
cast ai
```

With file analysis:
```bash
cast ai path/to/file.py
```

With directory analysis:
```bash
cast ai path/to/directory
```

## Commands During Session
- `quit` - End the session with option to save conversation
- `scribe` - Save the last response in various formats:
  - spell: Creates a .spell file in .tome directory
  - bash: Creates a .sh script
  - python: Creates a .py script
  - markdown: Creates a .md file
  - copy: Creates a plain text file

## Storage Locations
- Conversations are stored in `~/.sanctum/.aether/`
- Generated files are stored in the current directory or .tome directory for spells

## Examples

### Basic Question
```bash
cast ai
You: How can I optimize a Python list comprehension?
```

### File Analysis
```bash
cast ai complex_script.py
You: Can you explain what this code does?
```

### Directory Analysis
```bash
cast ai ./my_project
You: Can you analyze the structure of this project?
```

### Code Generation
```bash
cast ai
You: Can you help me write a script to batch rename files?
# After receiving response
You: scribe
# Choose python to save as a Python script
```

## Common Use Cases
1. **Code Analysis**: Understanding complex codebases
2. **Code Generation**: Creating new scripts and spells
3. **File System Tasks**: Analyzing and managing files/directories
4. **Educational**: Learning programming concepts
5. **Documentation**: Generating documentation for code

## Tips
- Provide context when analyzing files or directories
- Use `scribe` to save useful code or information
- Save important conversations for future reference
- Use directory analysis for project understanding
- Leverage the AI's ability to explain complex code

## Notes
- The spell requires a valid OpenAI API key
- Conversations can be saved and resumed later
- All generated files are saved locally
- The AI uses GPT-4 for optimal responses