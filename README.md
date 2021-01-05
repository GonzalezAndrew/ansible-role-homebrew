# Ansible Role Homebrew
![CI](https://github.com/GonzalezAndrew/ansible-role-homebrew/workflows/CI/badge.svg)

Ansible role that will install Homebrew on MacOS or Linux.


Requirements
------------

None.


Role Variables
--------------


Available variables are listed below along with their default values. (see [defaults/main.yml](defaults/main.yml))

The GitHub repository for Homebrew core.

```
homebrew_repo: https://github.com/Homebrew/brew
```

The path where Homebrew will be installed. 
```
homebrew_prefix: "{{ (ansible_os_family == 'Darwin') | ternary('/usr/local', '/home/linuxbrew/.linuxbrew') }}"
homebrew_install_path: "{{ homebrew_prefix }}/Homebrew"
homebrew_brew_bin_path: "{{ homebrew_prefix }}/bin"
```

A list of packages you would like to install via `brew install`.   
```
homebrew_installed_packages:
  - jq
  - { name: vim, install_options: "with-luajit,override-system-vi" }
```

A list of packages you wish to uninstall.
```
homebrew_uninstalled_packages: []
```

Whether you would like to upgrade all packages that are installed.
```
homebrew_upgrade_all_packages: false
```

Homebrew taps you would like to ensure are configured.
```
homebrew_taps:
  - homebrew/core
  - { name: my_company/internal_tap, url: 'https://example.com/path/to/tap.git' }
```

Applications you would like to install with `cask`. 
```
homebrew_cask_apps:
  - google-chrome
  - { name: slack, install_options:"debug,appdir=/Applications" }
```

A list of `cask` applications you would like uninstalled.
```
homebrew_cask_uninstalled_apps: []
```

The directory where your cask applications should be installed to.
```
homebrew_cask_appdir: /Applications
homebrew_cask_accept_external_apps: false
```

Whether to install applications & packages via a Brewfile. If you wish to use a Brewfile, ensure you have `homebrew/bundle` tap configured (This can be done with `homebrew_taps`).
```
homebrew_use_brewfile: false
homebrew_brewfile_dir: '~'
```

Remove the cache when an application or package is installed via Homebrew.
```
homebrew_clear_cache: false
```

A list of additional folders inside the Homebre directory.
```
homebrew_folders_additional: []
```

Dependencies
------------

None.


Example Playbook
----------------

    - hosts: localhost
      vars:
        homebrew_installed_packages:
          - zsh
      roles:
         - gonzalezandrew.homebrew

License
-------

MIT


Author Information
------------------

This role was created in 2020 by Andrew Gonzalez.
