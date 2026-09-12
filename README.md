<!-- BEGIN_ANSIBLE_DOCS -->
# Ansible Role: ansible_git
Clone and update Git repositories on managed hosts


## Requirements

| Platform | Versions |
| -------- | -------- |
| Debian | bullseye, bookworm |
| EL | 8 |

## Role Arguments


### Entrypoint: main

Clone and update Git repositories on managed hosts

Install git package (Debian and RHEL-based systems). To skip, `--skip-tags preflightchecks`

Clone git repositories from specified url and optional parameters (revision, refspec) on a local path (defaults to `$HOME/<git_repo_url_last_part>`)

If local clone exists, it will be updated to specified (optional) parameters

Variable `ansible_git_repositories_filter` can be used to filter repositories to process

|Option|Description|Type|Required|Default|
|---|---|---|---|---|
| ansible_git_repositories_common | List of git repositories to clone on managed nodes. If already present, clones will be updated to specified references There are two lists available, which are merged on run. Useful for instance to have one common in group_vars and another specific for each host This one is intended to be the common list | list of dicts of 'ansible_git_repositories_common' options | no | [] |
| ansible_git_repositories | List of git repositories to clone on managed nodes. If already present, clones will be updated to specified references There are two lists available, which are merged on run. Useful for instance to have one common in group_vars and another specific for each host This one is intended to be a more specific list | list of dicts of 'ansible_git_repositories' options | no | [] |
| ansible_git_repositories_filter | Filter to git repositories to process. Supports regex | str | no | None |

#### Options for main > ansible_git_repositories_common

|Option|Description|Type|Required|Default|
|---|---|---|---|---|
| repoUrl | Git repository URL | str | yes |  |
| repoRevision | Git repository revision; could be a branch, tag or commit | str | no | main |
| repoRefspec | Git repository custom refspec (https://git-scm.com/book/en/v2/Git-Internals-The-Refspec) | str | no | None |
| repoIsBare | Whether to clone the repository as bare | bool | no | False |
| repoDestPath | Full path to clone the repository to | str | no | $HOME/<repoUrl_last_part> |

#### Options for main > ansible_git_repositories

|Option|Description|Type|Required|Default|
|---|---|---|---|---|
| repoUrl | Git repository URL | str | yes |  |
| repoRevision | Git repository revision; could be a branch, tag or commit | str | no | main |
| repoRefspec | Git repository custom refspec (https://git-scm.com/book/en/v2/Git-Internals-The-Refspec) | str | no | None |
| repoIsBare | Whether to clone the repository as bare | bool | no | False |
| repoDestPath | Full path to clone the repository to | str | no | $HOME/<repoUrl_last_part> |



## Dependencies
None.

## Example Playbook

```
- hosts: all
  tasks:
    - name: Importing role: ansible_git
      ansible.builtin.import_role:
        name: ansible_git
      vars:
```

## License

MIT

## Author and Project Information
Pierre TOURON

<!-- END_ANSIBLE_DOCS -->
