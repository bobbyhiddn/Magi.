# Magi Roadmap

This roadmap outlines the phased development of the Magi ecosystem, detailing the progression from a command-line tool to a fully monetized, browser-based spellcasting platform with API support and user access controls.

---

## **Phase 0: CLI Tool (Complete)**

### **Overview**
The Magi project began as a CLI-based tool providing developers with magical "spells" for tasks ranging from directory transcription to AI-powered code generation.

### **Features**
- **Core CLI Functionality:** Spells are executed locally via `cast <spell_name>`.
- **Examples of Spells:**
  - `scribe` for markdown transcriptions.
  - `aether_inquiry` for AI-based questions.
- **Extensibility:** CLI supports custom spell development and integration.

### **Status:** ✅ Completed

---

## **Phase 1: Chamber (In Progress)**

### **Overview**
The introduction of **Magi.Chamber** brings remote spell hosting and CI/CD integrations, making spells modular and shareable.

### **Key Features**
1. **Spell Repository Integration:**
   - Spells moved to **Magi.Spells**, enabling modular management.
   - CI/CD pipelines automatically sync spells between repositories.
   
2. **Magi.Chamber Features:**
   - Centralized server for hosting and retrieving spells remotely.
   - Auto-sync with **Magi.Spells** repository using GitHub Actions.
   - Users can "ponder" spells to download them or execute them locally.

3. **Developer Workflow:**
   - New spells are developed in **Magi.Spells**.
   - Once reviewed and approved, they sync to Chamber.

4. **CLI Integration:**
   - `cast ponder` allows users to retrieve individual spells or sync the full library.

### **Goals**
- Complete stabilization of Chamber.
- Ensure seamless CI/CD workflows.
- Document developer and user workflows for spell creation and retrieval.

### **Status:** ⚙️ In Progress

---

## **Phase 2: Browser-Based Spellcasting**

### **Overview**
The focus shifts to providing browser-based access to Magi.Chamber. This allows users to interact with spells via a user-friendly web interface.

### **Features**
1. **Spellcasting Web Interface:**
   - Spells can be executed through a browser.
   - Each spell has a dedicated page with:
     - Usage instructions.
     - Execution options.
     - Input/output visualization (e.g., URL input for `PageCraft`).

2. **Spell Levels:**
   - **Level 1 Spells:** CLI-compatible spells, runnable via command line or local execution.
   - **Level 2 Spells:** Fully mature and documented spells available for remote execution.
   - **Level 3 Spells:** Spells integrated into the browser and API for seamless usage.

3. **Enhanced Documentation:**
   - Spells include structured documentation pages (Markdown-to-HTML conversion using tools like Jinja2 and Bootstrap).

4. **Containerized Execution:**
   - Spells are executed within isolated containers to ensure security and modularity.

### **Goals**
- Develop a browser-based UI for executing Level 3 spells.
- Extend CI/CD pipelines to validate spell maturity levels (1 → 2 → 3).
- Establish APIs for programmatic spellcasting.

### **Status:** 🚧 Planned

---

## **Phase 3: Monetization & User Access Controls**

### **Overview**
This phase introduces a subscription-based model to monetize browser-based spellcasting and API integrations.

### **Monetization Features**
1. **Free Tier:**
   - Users get **one free use per spell executed via API or Browser**.
   - Local spells will always remain free and open source.

2. **Subscription Tiers:**
   - **Basic Tier:** $5/month for 20 executions.
   - **Pro Tier:** $10/month for unlimited executions.
   - **Pay-As-You-Go:** $0.25 per spell execution.

3. **Spell Levels & Access:**
   - **Level 1 Spells:** Free for CLI use.
   - **Level 2 Spells:** Free for local use, monetized for remote execution.
   - **Level 3 Spells:** Subscription required for web/API execution.

4. **User Access Controls:**
   - Authentication via OAuth2 or email/password.
   - Usage tracking (free vs. paid executions).
   - Subscription management and payment integration via Stripe/PayPal.

5. **API Integration:**
   - Developers can programmatically cast spells via REST APIs.
   - API key management for authenticated usage.

### **Browser Features**
- **Interactive Execution Pages:** Each spell has a user-friendly interface for execution and customization.
- **Usage Dashboard:** Users can track their spellcasting history and subscription status.

### **Goals**
- Build and deploy the monetization framework.
- Implement secure and scalable authentication/authorization.
- Integrate payment processing and subscription management.

### **Status:** 🔮 Conceptual

---

## **Vision: Magi.Library**

To unify the ecosystem, the **Magi.Library** repository serves as a parent project, documenting the architecture and providing an entry point for contributors and users.

### **Repository Highlights**
1. **Centralized Documentation:**
   - Detailed guides on CLI, Chamber, and browser-based usage.
   - Contribution guides for new spell creation.
   
2. **Architecture Overview:**
   - CI/CD pipelines for spell management.
   - API and containerization workflows.

3. **Community Engagement:**
   - Encourages open-source contributions to the Magi ecosystem.
   - Transparency in development and monetization plans.

---

## **Future Outlook**

The Magi ecosystem evolves as a platform for creative and productive spellcasting, balancing open-source principles with a sustainable monetization model. With each phase, it grows closer to fulfilling its vision of merging the magical and the technical.

**May your spells always succeed, and your code be forever magical.** ✨