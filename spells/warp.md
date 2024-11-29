# Warp (wp)

## Overview
The Warp spell provides an elegant solution for managing and connecting to SSH sessions. It handles key generation, session management, and quick connections to remote servers.

## Features
- SSH session management
- RSA key generation
- Session aliases
- Key management
- Interactive interface

## Requirements
- Python packages: `click`, `paramiko`, `cryptography`

## Installation
```bash
cast ponder warp
```

## Usage
```bash
cast wp [alias]
```

## Session Storage
Sessions are stored in `~/.sanctum/.circle`
SSH keys are stored in `~/.sanctum/keys/`

## Command Options
- No arguments: Interactive session menu
- With alias: Direct connection attempt
- 'E': Edit existing sessions
- 'A': Add new session
- 'Q': Quit the spell

## Examples

### Interactive Session
```bash
cast wp
```

### Direct Connection
```bash
cast wp dev-server
```

### Add New Session
```bash
cast wp
> A
> Enter alias: dev-server
> Enter host: example.com
> Enter username: developer
```

## Key Management Options
- Generate new RSA key pair (G)
- Use existing private key (P)
- No key authentication (N)

## Session Management
1. List all sessions
2. Add new sessions
3. Delete sessions
4. Edit existing sessions
5. Quick connect

## Security Features
- RSA key generation
- Key-based authentication
- Secure key storage
- Password fallback
- Protected session data

## Common Use Cases
1. Development servers
2. Cloud instances
3. Remote administration
4. Multiple server management
5. Quick server access

## Best Practices
- Use descriptive aliases
- Generate unique keys
- Regular session cleanup
- Secure key storage
- Document connections

## Technical Details
- 2048-bit RSA keys
- Automated key deployment
- Session state persistence
- Multi-platform support
- Concurrent session support

## Notes
- Keys are stored locally
- Sessions persist between uses
- Password fallback available
- Interactive session management
- Supports multiple identities