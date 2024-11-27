# Magi System Architecture

## Component Structure

### Core Components
1. Magi.Chamber (Primary Repository)
   - Houses the central distribution system
   - Contains submodules:
     - Magi.Library (Documentation & Architecture)
     - Magi.Spells (Spell Repository)
   - Manages spell distribution and verification

2. Magi.CLI (Client)
   - Interfaces with Magi.Chamber
   - Manages local spell cache
   - Handles spell execution

## Repository Structure
```
Magi.Chamber/
├── chamber/           # Main distribution server
├── submodules/
│   ├── Magi.Library/ # Documentation & Architecture
│   │   ├── technical/
│   │   └── repos/
│   └── Magi.Spells/  # Spell repository
└── api/              # REST endpoints

Magi.CLI/
├── magi/             # Client implementation
├── sanctum/          # Local storage
└── cast/            # Command executor
```

## System Flow

1. **Spell Update Flow**
```
Magi.Spells (submodule) → Magi.Chamber → Distribution API → Magi.CLI
```

2. **Documentation Update Flow**
```
Magi.Library (submodule) → Magi.Chamber → Web Interface
```

3. **Client Interaction Flow**
```
User → Magi.CLI → Magi.Chamber API → Submodule Content → Local Cache
```

## Submodule Management

### Magi.Library
- Purpose: Central documentation and architectural specifications
- Integration: Direct submodule in Magi.Chamber
- Updates: Version controlled through Chamber

### Magi.Spells
- Purpose: Spell repository and versioning
- Integration: Direct submodule in Magi.Chamber
- Updates: Automated through webhooks and GitHub Actions

## Client-Server Relationship

1. **Magi.CLI (Client)**
   - Consumes Chamber API
   - Maintains local spell cache
   - Handles user interactions

2. **Magi.Chamber (Server)**
   - Manages submodules
   - Provides distribution API
   - Serves documentation
