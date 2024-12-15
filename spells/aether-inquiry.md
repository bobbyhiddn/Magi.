# Aether Inquiry (ai) - Complete Documentation

## Overview
The Aether Inquiry spell creates a bridge to an AI oracle powered by OpenAI's GPT-4 model, enabling interactive conversations, code analysis, and file system exploration. It features conversation persistence, file analysis capabilities, and multiple export formats for generated content.

## Core Features

### 1. Interactive Conversations
- Real-time AI communication
- Context-aware responses
- Multi-turn discussions
- Code generation
- Technical explanations

### 2. File System Analysis
- Individual file analysis
- Directory traversal
- Binary file detection
- Unicode handling
- Recursive content exploration

### 3. Content Generation
- Code generation
- Documentation creation
- Problem-solving assistance
- Technical explanations
- Script development

### 4. Export Capabilities
Multiple export formats supported:
- Spell Files (.spell): Stored in .tome directory
- Bash Scripts (.sh): Executable shell scripts
- Python Scripts (.py): Python source files
- Markdown (.md): Documentation format
- Text Files (.txt): Plain text exports

## Technical Requirements

### Dependencies
```python
__requires__ = ['click', 'openai']
```

### Environment Variables
- `OPENAI_API_KEY`: Required for AI functionality
- `SANCTUM_PATH`: Base path for storage locations

### Storage Structure
```
~/.sanctum/
└── .aether/
    ├── Inquiry-{timestamp}.md     # Saved conversations
    └── directory_contents_{timestamp}.md  # Directory analyses
```

## Basic Usage

### Command Syntax
```bash
# Basic invocation
cast ai

# File analysis
cast ai path/to/file.py

# Directory analysis
cast ai path/to/directory

# Multiple files
cast ai file1.py file2.py directory1
```

### Interactive Commands
During an active session:

1. **quit**: Exit and save conversation (optional)
   ```bash
   You: quit
   Save this conversation? [y/N]:
   ```

2. **scribe**: Export last response
   ```bash
   You: scribe
   Save as (yaml, python, bash, markdown, copy):
   Enter name for file:
   ```

## Complete Example: Creating a Timer Spell

### Step 1: Initiate Conversation
```bash
$ cast ai
You: I need a spell that can set a timer for 5 minutes
```

### Step 2: Receive Response
```bash
mAGI: Certainly! I shall conjure a spell named `temporal_timer` that sets a countdown timer for 5 minutes.

```yaml
name: temporal_timer
description: A spell that manipulates time by setting a countdown timer for 5 minutes, alerting you when the time has elapsed. 
type: script
shell_type: python
requires:
  - click
code: |
  #!/usr/bin/env python3
  import click
  import time

  @click.command()
  @click.option('--minutes', default=5, help='Number of minutes for the timer.')
  def timer(minutes):
      """Start a countdown timer for the specified number of minutes."""
      total_seconds = minutes * 60
      click.echo(f"Starting a {minutes}-minute timer...")
      for remaining in range(total_seconds, 0, -1):
          mins, secs = divmod(remaining, 60)
          timeformat = '{:02d}:{:02d}'.format(mins, secs)
          print(f"Time left: {timeformat}", end='\r')
          time.sleep(1)
      click.echo("\nTime's up!")

  if __name__ == '__main__':
      timer()
```
```

### Step 3: Save Configuration
```bash
You: scribe
Save as (yaml, python, bash, markdown, copy): yaml
Enter name for YAML file (without extension): timer

YAML configuration saved as timer.yaml
```

### Step 4: Create Spell
```bash
$ cast sc timer.yaml
  » Adding: spell\main.py
  » Adding: spell\spell.yaml
- Adding files to bundle:
  Adding: spell\main.py
  Adding: spell\spell.yaml
- Generating sigil at: [path]/temporal_timer_sigil.svg
✨ Spell crafted successfully: [path]/temporal_timer.spell
```

### Step 5: Use Spell
```bash
$ cast temporal_timer
Starting a 5-minute timer...
Time left: 05:00
[...]
Time left: 00:01
Time's up!
```

## Using the Scribe Command

### Available Formats

1. **YAML Format** (for spell creation):
```bash
You: scribe
Save as (yaml, python, bash, markdown, copy): yaml
Enter name for YAML file (without extension): spell_name
```

2. **Python Format**:
```bash
You: scribe
Save as (yaml, python, bash, markdown, copy): python
Enter name for Python file (without extension): script_name
```

3. **Bash Format**:
```bash
You: scribe
Save as (yaml, python, bash, markdown, copy): bash
Enter name for Bash file (without extension): script_name
```

4. **Markdown Format**:
```bash
You: scribe
Save as (yaml, python, bash, markdown, copy): markdown
Enter name for Markdown file (without extension): doc_name
```

5. **Copy Format**:
```bash
You: scribe
Save as (yaml, python, bash, markdown, copy): copy
Enter name for text file (without extension): text_name
```

### Output Locations
- Spell files (.spell): `~/.sanctum/.tome/`
- Scripts (.py, .sh): Current directory
- Documentation (.md): Current directory
- Text files (.txt): Current directory

## Best Practices

### File Analysis
1. Start with specific files/directories
2. Provide context in questions
3. Use recursive analysis when needed
4. Review generated transcriptions
5. Save important analyses

### Conversation Management
1. Save important conversations
2. Use descriptive filenames
3. Review conversation history
4. Maintain focused context
5. Export valuable responses

### Code Generation
1. Review generated code
2. Test before implementation
3. Save useful snippets
4. Document generated code
5. Verify dependencies

### Using Scribe
1. Choose appropriate format
2. Use descriptive filenames
3. Verify content before saving
4. Organize saved files
5. Test generated code

## Common Use Cases

### 1. Code Analysis
```bash
cast ai complex_module.py
You: Can you explain the main algorithms in this code?
You: What are potential optimization opportunities?
```

### 2. Project Review
```bash
cast ai ./project_directory
You: What's the overall architecture?
You: Are there any potential security issues?
```

### 3. Code Generation
```bash
cast ai
You: Help me write a script to process log files
# Review response
You: scribe
# Save as Python script
```

## Error Handling

### API Key Management
- Checks for OPENAI_API_KEY environment variable
- Provides clear error messages
- Graceful handling of missing keys
- API initialization verification

### File Operations
- Unicode error handling
- Binary file detection
- Permission error handling
- Path validation
- Resource cleanup

## Tips
- Provide context when analyzing files/directories
- Use `scribe` to save useful code or information
- Save important conversations for future reference
- Use directory analysis for project understanding
- Leverage the AI's ability to explain complex code

## Notes
- Requires valid OpenAI API key
- Conversations can be saved and resumed later
- All generated files are saved locally
- The AI uses GPT-4 for optimal responses
- Internet connection required for operation

## Future Considerations
1. Local LLM support
2. Enhanced file type support
3. Improved conversation management
4. Additional export formats
5. Extended analysis capabilities