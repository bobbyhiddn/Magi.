# **.spell File Specification and Plans**

The `.spell` file is currently a straightforward artifact for defining and executing "spells" as command macros within the Magi ecosystem. It allows users to automate tasks by bundling commands together. However, this document outlines not only its current capabilities but also the roadmap for evolving `.spell` files into a more robust and versatile format in the future.

---

## **Current Functionality**

### **Purpose**
- `.spell` files serve as simple command macros, allowing users to group CLI commands into reusable scripts.
- They act as a lightweight abstraction for invoking pre-defined tasks, making automation accessible for CLI users.

### **Structure**
A `.spell` file is a plain text file with minimal structure, focusing on simplicity and ease of use.

#### **Components**
1. **Description:**
   - Brief overview of the spell's purpose.
   
   Example:
   ```plaintext
   # Description: A spell to list files in a directory
   ```

2. **Commands:**
   - The core logic, consisting of one or more shell commands.
   
   Example:
   ```plaintext
   # Commands:
   ls -la {{directory}}
   ```

3. **Alias (Optional):**
   - A short name to invoke the spell.

   Example:
   ```plaintext
   # Alias: listdir
   ```

4. **Parameters:**
   - Optional placeholders within commands that can be dynamically replaced during execution.

   Example:
   ```plaintext
   # Parameters:
   #   directory: The target directory to list
   ```

---

## **Execution**

### **CLI Integration**
`.spell` files can be invoked using the `cast` command.

#### **Examples:**
1. **Executing a Spell:**
   ```bash
   cast ponder listdir
   ```
   If `listdir` is the alias for a `.spell` file, it will execute the associated command(s).

2. **Interactive Prompt for Parameters:**
   - If the `.spell` file includes parameters, the user is prompted to provide them at runtime.

---

## **Roadmap**

### **Phase 0: Command Macros (Current State)**
- `.spell` files remain simple command macros with minimal metadata and no additional execution layers.
- Focus on usability and lightweight automation.

---

### **Phase 1: Baseline Functionality**
- **Definition and Execution:**
  - Maintain current `.spell` execution model with minor enhancements, such as metadata parsing and improved parameter handling.

- **Basic Sharing:**
  - Synchronize `.spell` files with **Magi.Spells** and **Magi.Chamber** for distributed access.

---

### **Phase 2: Enhanced Validation and Modularity**
- Transition `.spell` files from simple macros to more structured, modular scripts.

#### **Enhancements:**
1. **Parameter Validation:**
   - Define parameter types and constraints in `.spell` files.
   - CLI prompts users to provide valid input during execution.

   Example:
   ```plaintext
   # Parameters:
   #   directory: The target directory to list (type=string, required=true)
   ```

2. **Dependency Handling:**
   - Include external libraries or tools required for the spell.
   - Automatically resolve dependencies during execution.

3. **Containerized Execution:**
   - Enable `.spell` files to specify runtime environments using containers.

   Example:
   ```plaintext
   # Runtime: docker
   # Container: magi/spell-runtime:latest
   ```

---

### **Phase 3: Ecosystem Integration**
- `.spell` files become core components of the broader Magi ecosystem, integrating with web-based interfaces and APIs.

#### **Enhancements:**
1. **Versioning:**
   - Introduce version control for `.spell` files to support updates and backward compatibility.

2. **Web UI Integration:**
   - Cast `.spell` files through **Magi.Chamber**'s browser interface.
   - Provide user-friendly forms for parameter input.

3. **Spell Market:**
   - Curate a marketplace for sharing and monetizing `.spell` files.

---

### **Phase 4: Advanced Features and Monetization**
- `.spell` files achieve full modularity and maturity, capable of being executed securely in isolated environments.

#### **Premium Features:**
1. **Sandboxed Execution:**
   - Execute `.spell` files in isolated containers for security and consistency.

2. **API Integration:**
   - Publish `.spell` logic as APIs for external systems to invoke.

3. **Premium Spells:**
   - Introduce monetization by offering premium `.spell` files and casting services.

---

## **Future Format**

The `.spell` file format will evolve into a structured, YAML-based syntax to accommodate advanced features while retaining readability.

### **Proposed Format:**
```yaml
name: ListDirectory
alias: ldir
description: A spell to list files in a directory
version: 1.0.0
author: Bobby Hiddn
parameters:
  directory:
    type: string
    required: true
commands:
  - ls -la {{directory}}
dependencies:
  - coreutils
runtime:
  container: magi/spell-runtime:latest
```

---

## **Call to Action**

- Experiment with `.spell` files in their current macro form.
- Contribute to **Magi.Spells** by creating and sharing new `.spell` files.
- Collaborate to define the future structure and capabilities of `.spell` files.
- Provide feedback to guide the evolution of `.spell` files into a robust, modular scripting solution.

This roadmap ensures that `.spell` files grow from simple command macros into powerful, interoperable tools central to the Magi ecosystem.