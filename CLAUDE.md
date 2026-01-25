# VPS Foundation - Ansible Collection

## IMPORTANT - File Editing

**NEVER edit files in `~/.ansible/collections/` - these are installed Galaxy modules!**

Always edit source files in this repository:
- Roles: `vps_foundation/roles/`
- Playbooks: `vps_foundation/playbooks/`

## After Changes

After any change to Ansible files, run:
```bash
ansible-galaxy collection install . --force
```
