<!-- DOCSIBLE START -->
# Ansible Role: role_posteio


Ansible role for installing and configuring Poste.io Email Server


## Table of Contents

- [Requirements](#requirements)
- [Dependencies](#dependencies)
- [Role Variables](#role-variables)
- [Task Overview](#task-overview)
- [Example Playbook](#example-playbook)
- [Documentation Maintenance](#documentation-maintenance)
- [License](#license)
- [Author Information](#author-information)

## Requirements



- Ansible >= 2.9


- Supported platforms:
  - AlmaLinux (7, 8, 9)



## Dependencies


This role requires the following roles and collections:




  
    
  

  
    
  

  
    
  

  
    
  

  
    
  



**Roles:**

- [role_base](https://github.com/ginanck/role_base.git) (version: master)

- [role_docker](https://github.com/ginanck/role_docker.git) (version: master)




**Collections:**

- `community.docker` (>= 4.8.1)

- `community.general` (>= 6.6.1)

- `ansible.posix` (>= 1.5.4)



To install all dependencies:
```bash
ansible-galaxy install -r meta/install_requirements.yml
```


## Role Variables

**These are static variables with lower priority**



#### File: defaults/main.yml

| Var | Type | Value |
|-----|------|-------|
| [posteio_data_path](defaults/main.yml#L8) | str | `{{ posteio_dir }}/data` |
| [posteio_dir](defaults/main.yml#L7) | str | `/opt/posteio` |
| [posteio_hostname](defaults/main.yml#L10) | str | `mail.nnc.guru` |
| [posteio_image_name](defaults/main.yml#L5) | str | `ghcr.io/ginanck/posteio-mailserver:{{ posteio_image_tag }}` |
| [posteio_image_tag](defaults/main.yml#L4) | str | `2.4.10` |
| [posteio_listen_on](defaults/main.yml#L13) | str | `127.0.0.1` |
| [posteio_send_on](defaults/main.yml#L14) | str | `127.0.0.1` |
| [posteio_timezone](defaults/main.yml#L12) | str | `Europe/Helsinki` |




## Task Overview


This role performs the following tasks:


### File: `tasks/main.yml`

| Task Name | Module | Has Conditions | Line |
|-----------|--------|----------------|------|
| [Create poste.io installation directory](tasks/main.yml#L) | ansible.builtin.file | No | N/A |
| [Create Poste.io docker-compose file](tasks/main.yml#L) | ansible.builtin.template | No | N/A |
| [Create Poste.io management scripts](tasks/main.yml#L) | ansible.builtin.template | No | N/A |
| [Create Poste.io systemd service file](tasks/main.yml#L) | ansible.builtin.template | No | N/A |
| [Reload systemd daemon](tasks/main.yml#L) | ansible.builtin.systemd | Yes | N/A |
| [Check Poste.io service status](tasks/main.yml#L) | ansible.builtin.systemd | No | N/A |
| [Enable Poste.io service](tasks/main.yml#L) | ansible.builtin.systemd | Yes | N/A |






## Example Playbook

```yaml
---
- hosts: all
  become: yes
  roles:
    - role: role_posteio

      vars:
        posteio_image_tag: 2.4.10
        posteio_image_name: ghcr.io/ginanck/posteio-mailserver:{{ posteio_image_tag }}
        posteio_dir: /opt/posteio

```

## License


license (GPL-2.0-or-later, MIT, etc)


## Author Information


**Author:** gkorkmaz




**GitHub:** [gkorkmaz](https://github.com/gkorkmaz)

---
*This documentation was automatically generated using [docsible](https://github.com/zbohm/docsible).*
<!-- DOCSIBLE END -->
