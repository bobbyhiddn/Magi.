# Spellcraft (sc) - Technical Documentation

## Core Components

Spellcraft is the primary interface for crafting and managing magical spells in Magi CLI. This tool provides flexible methods for spell creation, bundling, and execution, supporting various configurations and file structures.

---

## .Spell Structure

### Generated Spell Bundle

```plaintext
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

### Spell Bundles

A spell bundle (`.spell` file) is a packaged set of scripts and configurations that includes:

- `spell.yaml` - Metadata and configuration file
- Main script file (in `spell/` directory)
- Artifacts (in `artifacts/` directory)
- Dependencies (via `requirements.txt` if Python)

---

## Creation Methods

### 1. Command Mode (Macro)

```bash
cast sc <num_commands> <spell_name>
```

Creates a spell from a sequence of shell commands.

### 2. Script Mode

```bash
cast sc <script.py|script.sh> [spell_name]
```

Creates a spell from a Python or shell script.

### 3. YAML Mode

```bash
cast sc <config>.yaml
```

Creates a spell from a YAML specification with dependencies and artifacts.

### 4. Prestructured Folder Mode

```bash
cast sc <folder>.spell/
```

Bundles a prestructured folder that specifically ends in `.spell/`, containing `spell.yaml` and related files, into a `.spell` file.

---

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

#### Simple Python CLI

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

#### Web Application

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

#### Data Processing

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

---

## Features

### Dependency Management

- Automatically installs Python packages during spell creation.
- Uses system's pip for package management.
- Supports version specifications in requirements.

### Artifact Handling

- Supports inline file content in YAML.
- Organizes files in appropriate directories.
- Maintains correct file permissions.

### Shell Support

- Python scripts with Click CLI.
- Bash scripts for system operations.
- Macro commands for simple operations.

---

## Usage Examples

### 1. Web Application

```bash
# Create and run a web spell
$ cast sc web_spell.yaml
$ cast web_spell
# Access at http://localhost:5000
```

### 2. Data Processing

```bash
# Create and run a data processing spell
$ cast sc data_processor.yaml
$ cast data_processor input.csv output.csv
```

### 3. System Check

```bash
# Create and run a system check spell
$ cast sc system_check.yaml
$ cast system_check
```

### 4. Bundling a Prestructured Spell Folder

```bash
# Bundle a folder containing a prestructured spell
$ cast sc bundled_spell.spell/
$ cast bundled_spell
```

---

## Best Practices

1. **Dependencies**

   - Specify minimum required versions.
   - Keep dependencies minimal.
   - Test with fresh installations.

2. **Artifacts**

   - Use appropriate directories.
   - Keep file content clean.
   - Handle paths correctly.

3. **Code Organization**

   - Use Click for CLI.
   - Handle errors gracefully.
   - Follow language conventions.

4. **Documentation**

   - Include clear descriptions.
   - Document parameters.
   - Provide usage examples.

---

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

---

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

- Stored as SVG in spell bundle.
- Generated during bundle creation.
- Used for spell identification and integrity verification.

### Sigil Validation and Tampering Detection

Sigils are integral for verifying the integrity of a spell bundle. During execution, the stored hash in the spell metadata is compared to the hash of the current bundle contents.

1. **Successful Validation:**
   - If the hashes match, the spell executes normally, ensuring no unauthorized modifications were made.

2. **Tampering Detection:**
   - If the hashes mismatch, the spell execution is halted, and an error message is displayed.

   **Example Output:**
   ```plaintext
   Sigil hash mismatch! Spell has been tampered with.
   Stored: 274dd2bdf6f563763c13962da40f04481c964f9ea3c1555f37ebb57d24460e5c
   Current: 8657ac8fb646b6f9a9e83b1289f1a4898ad15f440c3277490369ac80b81aff2c
   ```
   This mechanism ensures the integrity and trustworthiness of all spells.

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

- Stored as SVG in spell bundle.
- Generated during bundle creation.
- Used for spell identification and integrity verification.

The sigil serves as both a visual identifier and a magical seal for the spell bundle, with its appearance uniquely determined by the spell's metadata hash.

---

## Future Enhancements

1. Virtual environment support.
2. Improved artifact fetching (URL, Git).
3. Enhanced error handling.
4. Comprehensive logging.
5. Test suite integration.
