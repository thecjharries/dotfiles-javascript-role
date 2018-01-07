# `dotfiles-javascript-role`

[![Build Status](https://travis-ci.org/thecjharries/dotfiles-javascript-role.svg?branch=master)](https://travis-ci.org/thecjharries/dotfiles-javascript-role)

## Requirements

Fedora 27 is recommended.

## Role Variables

Defaults are below.
```yml
---
owning_user: "{{ ansible_user }}"
owning_group: "{{ ansible_user }}"
root_dir: "/home/{{ ansible_user }}"
config_dir: "{{ root_dir }}/.config"

nodesource_src_path: /opt/installers/nodesource

npmrc_block: |
    init-author-name={{ author_name }}
    init-author-email={{ author_email }}
    init-author-url={{ author_url }}
    init-version=0.0.0
    init-license=ISC
```

Additionally, these `vars` are set:
```yml
---
needed_packages:
  - make
  - gcc-c++
```

Finally, these variables must be set:

```yml
author_name
author_email
author_url
```

## Dependencies

```yml
---
- src: git+https://github.com/thecjharries/dotfiles-common-software-role.git
- src: git+https://github.com/thecjharries/dotfiles-package-installer-role.git
```

## Example Playbook

```yml
---
- hosts: all

  roles:
    - role: dotfiles-javascript-role
      author_name: Rick James
      author_email: something@clever.com
      author_url: clever.com

```

## License

ISC
