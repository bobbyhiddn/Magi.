# Spellcraft (sc) - Technical Documentation

## Core Components

### Spell Bundles
A spell bundle (`.spell` file) is a packaged set of scripts and configuration that includes:
- `spell.yaml` - Metadata and configuration file
- Main script file (in `spell/` directory)
- Artifacts (in `artifacts/` directory)
- Dependencies (via `requirements.txt` if Python)

### Creation Methods

1. **Command Mode (Macro)**
   ```bash
   cast sc <num_commands> <spell_name>
   ```
   Creates a spell from a sequence of shell commands.

2. **Script Mode**
   ```bash
   cast sc <script.py|script.sh> [spell_name]
   ```
   Creates a spell from a Python or shell script.

3. **YAML Mode**
   ```bash
   cast sc <config>.yaml
   ```
   Creates a spell from a YAML specification with dependencies and artifacts.

## YAML Configuration Format

### Basic Structure
```yaml
name: spell_name
description: Spell description
type: bundled|script
shell_type: python|shell

# Optional Python dependencies
requires:
  - package_name>=version
  - another_package

# Main spell code
code: |
  # Your Python or shell script here
  print("Hello from the spell!")

# Optional artifacts
artifacts:
  - path: relative/path/to/file
    content: |
      File contents here
```

### Example Configurations

1. **Simple Python CLI**
```yaml
name: hello
description: A simple greeting spell
type: script
shell_type: python

code: |
  import click
  
  @click.command()
  def main():
      """A simple greeting."""
      print("Hello from the magical realm!")
  
  if __name__ == '__main__':
      main()
```

2. **Web Application**
```yaml
name: web_spell
description: A simple web server spell
type: bundled
shell_type: python

requires:
  - flask
  - click

code: |
  from flask import Flask, render_template
  import click

  app = Flask(__name__)

  @app.route('/')
  def home():
      return render_template('index.html')

  @click.command()
  def main():
      """Start the magical web server."""
      app.run(port=5000)

  if __name__ == '__main__':
      main()

artifacts:
  - path: templates/index.html
    content: |
      <!DOCTYPE html>
      <html>
        <head><title>Magic Web</title></head>
        <body><h1>Welcome to the magical web!</h1></body>
      </html>
```

3. **Data Processing**
```yaml
name: data_processor
description: Process data using a model
type: bundled
shell_type: python

requires:
  - pandas
  - scikit-learn
  - click

code: |
  import click
  import pandas as pd
  from pathlib import Path
  import joblib
  
  @click.command()
  @click.argument('input_file')
  @click.argument('output_file')
  def main(input_file, output_file):
      """Process data using a model."""
      model_path = Path(__file__).parent.parent / 'artifacts/model/model.joblib'
      model = joblib.load(model_path)
      data = pd.read_csv(input_file)
      results = pd.DataFrame(model.predict(data))
      results.to_csv(output_file, index=False)

artifacts:
  - path: model/model.joblib
    content: |
      # Model binary content
```

## Directory Structure

### Generated Spell Bundle
```
spell_name.spell/
├── spell.json           # Metadata and configuration
├── spell/
│   ├── spell.yaml      # Spell-specific configuration
│   ├── main.py/main.sh # Entry point
│   └── templates/      # For web apps
├── artifacts/          # Additional files
│   ├── templates/
│   ├── static/
│   ├── model/
│   └── config/
├── requirements.txt    # Python dependencies
└── spell_name_sigil.svg # Unique spell sigil
```

### 1. Command-Based Spell
```
~/.sanctum/.tome/git_backup.spell
├── spell.json           # Metadata and configuration
├── git_backup.sh        # Main script
└── git_backup_sigil.svg # Unique spell sigil
```

Example `spell.json`:
```json
{
  "name": "git_backup",
  "description": "Backup and push repository changes",
  "version": "1.0.0",
  "type": "macro",
  "shell_type": "bash",
  "entry_point": "git_backup.sh",
  "created_at": "2024-11-29T08:31:23Z",
  "sigil_hash": "a1b2c3d4e5f6g7h8"
}
```

### 2. Directory-Based Spell
```
~/.sanctum/.tome/process_logs.spell
├── spell.json              # Metadata and configuration
├── spell/
│   ├── spell.yaml         # Spell-specific configuration
│   ├── main.py            # Main script
│   ├── helpers.py         # Additional modules
│   └── config.json        # Runtime configuration
├── artifacts/             # Additional resources
│   ├── templates/
│   └── static/
└── process_logs_sigil.svg # Unique spell sigil
```

### 3. YAML-Based Spell
```
~/.sanctum/.tome/web_app.spell
├── spell.json           # Metadata and configuration
├── spell/
│   ├── spell.yaml      # Generated from YAML config
│   └── main.py         # Generated script
├── artifacts/          # Generated from YAML artifacts
│   ├── templates/
│   │   └── index.html
│   └── static/
│       └── style.css
├── requirements.txt    # Python dependencies
└── web_app_sigil.svg  # Unique spell sigil
```

Example `spell.json`:
```json
{
  "name": "web_app",
  "description": "Simple Flask web application",
  "version": "1.0.0",
  "type": "bundled",
  "shell_type": "python",
  "entry_point": "spell/main.py",
  "created_at": "2024-11-29T10:15:45Z",
  "sigil_hash": "b2c3d4e5f6g7h8i9"
}
```

Example `spell.yaml`:
```yaml
name: web_app
description: Simple Flask web application
version: 1.0.0
type: bundled
shell_type: python
entry_point: spell/main.py
```

## Features

### Dependency Management
- Automatically installs Python packages during spell creation
- Uses system's pip for package management
- Supports version specifications in requirements

### Artifact Handling
- Supports inline file content in YAML
- Special handling for Flask templates
- Organizes files in appropriate directories
- Maintains correct file permissions

### Shell Support
- Python scripts with Click CLI
- Bash scripts for system operations
- Macro commands for simple operations

## Usage Examples

### 1. Web Application
```bash
# Create and run a web spell
$ cast sc web_spell.yaml
$ cast web_spell.spell
# Access at http://localhost:5000
```

### 2. Data Processing
```bash
# Create and run a data processing spell
$ cast sc data_processor.yaml
$ cast data_processor.spell input.csv output.csv
```

### 3. System Check
```bash
# Create and run a system check spell
$ cast sc system_check.yaml
$ cast system_check.spell
```

## Best Practices

1. **Dependencies**
   - Specify minimum required versions
   - Keep dependencies minimal
   - Test with fresh installations

2. **Artifacts**
   - Use appropriate directories
   - Keep file content clean
   - Handle paths correctly

3. **Code Organization**
   - Use Click for CLI
   - Handle errors gracefully
   - Follow language conventions

4. **Documentation**
   - Include clear descriptions
   - Document parameters
   - Provide usage examples

## Common Issues

1. **Dependency Installation**
   ```bash
   Error: No module named 'package'
   # Solution: Check requirements.txt and pip installation
   ```

2. **Template Not Found**
   ```bash
   Error: jinja2.exceptions.TemplateNotFound
   # Solution: Check templates directory structure
   ```

3. **Permission Issues**
   ```bash
   Error: Permission denied
   # Solution: Check file permissions, especially for shell scripts
   ```

## Sigil Generation

Each spell bundle includes a unique magical sigil, generated using a combination of runic alphabets. The sigil is derived from the spell's metadata hash, ensuring each spell has a unique visual identifier.

### Sigil Components

1. **Runic Alphabets**
   - Elder Futhark (24 characters)
   - Younger Futhark (16 characters)
   - Medieval Runes (24 characters)
   - Ogham (21 characters)

2. **Generation Process**
   ```python
   # Generate metadata hash
   metadata = {
       "name": spell_name,
       "description": description,
       "type": spell_type,
       "version": "1.0.0"
   }
   sigil_hash = hashlib.md5(f"{spell_name}_{description}_{spell_type}".encode()).hexdigest()
   ```

3. **Bundle Integration**
   - Stored as SVG in spell bundle
   - Generated during bundle creation
   - Used for spell identification and integrity verification

The sigil serves as both a visual identifier and a magical seal for the spell bundle, with its appearance uniquely determined by the spell's metadata hash.

## Future Enhancements
- Virtual environment support
- Remote artifact sourcing (URL, Git)
- Enhanced error handling
- Comprehensive logging
- Test suite integration
