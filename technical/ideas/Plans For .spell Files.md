# **.spell File Specification and Future Vision**

The `.spell` file is the cornerstone of the Magi ecosystem, currently functioning as a simple mechanism for defining and executing command macros. However, the roadmap for `.spell` files envisions their evolution into a robust, modular, and self-contained scripting format, while maintaining their lightweight nature. This document outlines the current functionality and future plans, including features like bundling artifacts, procedural sigil confirmation, and API integrations.

---

## **Current Functionality**

### **Purpose**
- `.spell` files are currently lightweight command macros used to automate CLI tasks.
- They provide a way to define, package, and invoke commands repeatedly.

### **Structure**
A `.spell` file is plain text, designed for simplicity and usability.

#### **Components**
1. **Description:**
   - A concise explanation of the spell’s purpose.
   ```plaintext
   # Description: A spell to archive files
   ```

2. **Commands:**
   - A series of commands executed when the spell is cast.
   ```plaintext
   # Commands:
   tar -czvf {{archive_name}}.tar.gz {{directory}}
   ```

3. **Parameters:**
   - Placeholders in commands that can be dynamically replaced at runtime.
   ```plaintext
   # Parameters:
   #   directory: The target directory to archive
   #   archive_name: The name of the output archive
   ```

4. **Alias:**
   - A shorthand name for invoking the spell.
   ```plaintext
   # Alias: archive
   ```

---

## **Execution**

### **Casting a Spell**
- Spells are invoked using the `cast` command, allowing users to provide parameters interactively or through direct input.

#### **Examples**
1. **Casting with Prompt:**
   ```bash
   cast ponder archive
   ```
   Prompts the user to enter the required parameters.

2. **Direct Invocation:**
   ```bash
   cast ponder archive --directory=docs --archive_name=docs_backup
   ```

---

## **Roadmap**

### **Phase 0: Command Macros (Current State)**
- `.spell` files are simple macros focusing on lightweight task automation.
- Minimal metadata and no advanced features.

---

### **Phase 1: Enhancements and Synchronization**
- Introduce basic bundling and CI/CD integration.
- Enable `.spell` files to sync seamlessly with **Magi.Spells** and **Magi.Chamber**.

#### **Enhancements**
1. **Artifact Bundling:**
   - Package `.spell` files with non-code artifacts, such as templates, configuration files, or static assets required for execution.
   - These artifacts will travel with the `.spell` file, ensuring portability and reproducibility.

   Example:
   ```plaintext
   # Artifacts:
   #   /templates/report_template.md
   #   /configs/default_config.json
   ```

2. **Chamber Integration:**
   - CI/CD pipelines for automatic spell validation and distribution.

---

### **Phase 2: Structured Format and Modularity**
- `.spell` files evolve into structured, YAML-based bundles for better readability and flexibility.

#### **Enhancements**
1. **Lightweight Bundles:**
   - `.spell` files will serve as portable bundles carrying:
     - Command logic
     - Required artifacts (templates, configs, static files)
     - Metadata for validation and execution

   Example:
   ```yaml
   name: ArchiveDirectory
   alias: archive
   description: A spell to archive files in a directory
   version: 1.0.0
   parameters:
     directory:
       type: string
       required: true
     archive_name:
       type: string
       required: true
   commands:
     - tar -czvf {{archive_name}}.tar.gz {{directory}}
   artifacts:
     - templates/report_template.md
     - configs/default_config.json
   ```

2. **Containerized Execution:**
   - Enable spells to define runtime environments using containers for modularity and isolation.

---

### **Phase 3: Ecosystem Integration**
- `.spell` files become central to the **Magi** ecosystem, supporting advanced features like browser-based execution, API calls, and monetization.

#### **New Features**
1. **Procedural Sigil Confirmation:**
   - Each `.spell` file is associated with a procedurally generated sigil.
   - The sigil serves as a visual and cryptographic confirmation key, validated by the Magi API.

   Example Workflow:
   - Users submit a `.spell` file to the API for casting.
   - The API generates and returns a unique sigil that confirms the spell's validity and execution status.

2. **Levels of Spells:**
   - Introduce levels to differentiate spells by maturity and execution environment:
     - **Level 1:** CLI-castable spells. Python scripts in the spells directory.
     - **Level 2:** Fully reviewed, documented spells with artifact bundling but no browser integration.
     - **Level 3:** Spells integrated with browser interfaces and APIs, offering user-friendly execution and advanced features.

3. **API Casting:**
   - Publish `.spell` logic as APIs, allowing third-party systems to invoke spells programmatically.

---

### **Phase 4: Advanced Monetization**
- `.spell` files enable monetization through tiered access and premium features.

#### **Premium Features**
1. **Browser Integration:**
   - Users can cast Level 3 spells directly from the browser.
   - A polished UI simplifies parameter input and displays results interactively.

2. **Subscription Model:**
   - Users receive a free first use of each spell.
   - Beyond the initial use, access is gated by a subscription package (e.g., $5 for a set number of casts).

---

## **Call to Action**

1. **Collaborate:**
   - Contribute to **Magi.Spells** by developing new `.spell` files and submitting them for review.

2. **Experiment:**
   - Test the current macro capabilities of `.spell` files and provide feedback.

3. **Innovate:**
   - Help shape the future of `.spell` files by proposing features and use cases.

This roadmap ensures that `.spell` files will evolve from basic command macros to a cornerstone of the Magi ecosystem, enabling automation, collaboration, and monetization in a modular and secure framework.