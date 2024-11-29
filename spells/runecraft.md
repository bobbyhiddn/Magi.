# Runecraft (rc)

## Overview
Runecraft creates mystical GUI buttons (runes) for executing scripts. Each rune is a draggable, clickable button with a unique AI-generated design, perfect for frequently used scripts.

## Features
- AI-generated rune designs
- Draggable GUI buttons
- Support for multiple script types
- Persistent rune storage
- Close button integration

## Requirements
- OpenAI API key (set as `OPENAI_API_KEY` environment variable)
- Python packages: `click`, `requests`, `Pillow`, `openai`, `PyQt5`

## Installation
```bash
cast ponder runecraft
```

## Usage
```bash
cast rc <script_path>
```

## Supported Script Types
- Python (.py)
- Bash (.sh)
- Spell files (.spell)

## Storage Location
Runes are stored in `~/.sanctum/.runes/` with the following structure:
```
.runes/
└── script_name/
    ├── script_name_gui.py
    └── script_name_image.png
```

## Examples

### Creating a Rune for Python Script
```bash
cast rc my_script.py
```

### Creating a Rune for Bash Script
```bash
cast rc backup.sh
```

### Creating a Rune for Spell File
```bash
cast rc my_macro.spell
```

## GUI Features
- Draggable interface
- Click to execute
- Close button
- Always-on-top window
- Transparent background
- Shadow effects

## Rune Generation Process
1. AI generates unique rune design
2. Image is processed into circular format
3. GUI wrapper is created
4. Execution handler is configured
5. Rune is displayed and activated

## Technical Details
- Uses DALL-E for image generation
- PyQt5 for GUI implementation
- Supports multiple instances
- Persists between sessions
- Independent process execution

## Best Practices
1. Use descriptive script names
2. Keep scripts in consistent locations
3. Test scripts before creating runes
4. Organize runes by function
5. Clean up unused runes

## Common Use Cases
- Frequently used scripts
- System maintenance tasks
- Development workflows
- Backup routines
- Quick tools access

## Customization
The rune appearance is influenced by:
- Script name
- AI generation parameters
- Window size settings
- Shadow effects
- Button placement

## Notes
- Requires GUI environment
- Runes persist until manually closed
- Each rune runs in its own window
- Scripts execute in terminal context
- Multiple runes can run simultaneously