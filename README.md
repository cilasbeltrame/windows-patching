# Windows Patching Playbook  

> **Note**: This is the first draft of the Windows Patching Playbook.
This repository contains an Ansible playbook for automating the process of applying Windows patches. It includes a well-structured approach for pre-patch preparation, applying updates, and performing post-patch validation.  

## Playbook Overview  

The playbook, `windows_patching.yml`, is structured to manage the Windows patching workflow with the following steps:  

1. **Create Snapshot**: Ensures a backup is created before applying patches.  
2. **Search**: Searches for available Windows updates.  
3. **Apply Patches**: Installs the identified patches.  
4. **Reboot**: Reboots the system if required to finalize the updates.  

Additional roles (e.g., `app`, `db`, `sendmail`) can be included based on your requirements by uncommenting the respective lines.  

## Playbook Structure  

```yaml
- name: Windows updates
  strategy: free
  hosts: all
  gather_facts: true
  roles:
    - create-snapshot
    #- app
    #- db
    - search
    - patches
    - reboot
    #- sendmail
    - validation-services
