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



### File: `defaults/main.yml`

| Variable | Default Value | Description |
|----------|---------------|-------------|
| `posteio_image_tag` | `2.4.10` | None |
| `posteio_image_name` | `ghcr.io/ginanck/posteio-mailserver:{{ posteio_image_tag }}` | None |
| `posteio_dir` | `/opt/posteio` | None |
| `posteio_data_path` | `{{ posteio_dir }}/data` | None |
| `posteio_hostname` | `mail.nnc.guru` | None |
| `posteio_timezone` | `Europe/Helsinki` | None |
| `posteio_listen_on` | `127.0.0.1` | None |
| `posteio_send_on` | `127.0.0.1` | None |




## Task Overview


This role performs the following tasks:


### `main.yml`


- **Create poste.io installation directory**
- **Create Poste.io docker-compose file**
- **Create Poste.io management scripts**
- **Create Poste.io systemd service file**
- **Reload systemd daemon**
- **Check Poste.io service status**
- **Enable Poste.io service**




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

## Documentation Maintenance

### Updating Dependencies

1. **Update** `meta/main.yml`:
   ```yaml
   documented_requirements:
     - src: https://github.com/user/role.git
       version: master
     - name: collection.name
       version: 1.0.0
   ```

2. **Sync** `meta/install_requirements.yml` with the same requirements

3. **Regenerate** documentation:
   ```bash
   pre-commit run --all-files
   ```

### Template Updates

- Edit `.docsible_template.md` for structure changes
- Test with: `docsible --role . --md-template .docsible_template.md -nob -com -tl`
- Commit both template and generated README.md

### Quick Checklist

When updating dependencies:
- [ ] Add to `meta/main.yml` → `documented_requirements`
- [ ] Add to `meta/install_requirements.yml`
- [ ] Run `pre-commit run --all-files`
- [ ] Verify generated README.md
- [ ] Commit all changes

## License


license (GPL-2.0-or-later, MIT, etc)


## Author Information


**Author:** gkorkmaz




**GitHub:** [gkorkmaz](https://github.com/gkorkmaz)

---
*This documentation was automatically generated using [docsible](https://github.com/zbohm/docsible).*
<!-- DOCSIBLE END -->
