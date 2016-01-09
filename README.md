# Vsftpd

An Ansible role for installing and configuring vsftpd on CentOS/RHEL 7.  

## Requirements

- SELinux is expected to be running

## Role Variables

`defaults/main.yml`

| Name           | Default Value | Description                        |
| -------------- | ------------- | -----------------------------------|
| vsftpd_shares_root | /srv/shares | The default ftp directory where your shares will be placed |
| vsftpd_shares | -      | List of dicts defining the ftp shares that need to be created (see example below) |
| vsftpd_groups | -      | List of dicts defining the groups that need to be created (see example below) |
| vsftpd_users | -      | List of dicts defining the users that need to be created (see example below) |

## Dependencies

This role has no depencies and will work on its own.

## Defining users and groups

If your system doesn't have any users or groups that are yet created, it's possible to do so by using this role.  

To define users, you'll have to provide at least a name, comment, group(s) and password.  
Because of the default values of the other variables, a user will then be created with a home directory and its shell location at "/bin/bash".  
Those variables can be specified according to preference as shown in this example: 

```Yaml 
vsftpd_users:
  - username: testuser
    comment: 'A test user'
    groups:
      - pirates
    password: 'testpassword'
    shell: /sbin/nologin
    create_homedir: yes
``` 

To define groups, you'll just have to provide a name.  
```Yaml
vsftpd_groups: 
      - pirates
``` 

## Defining shares

To define a share, you start with giving it a name:

```Yaml
vsftpd_shares:
  - name: readonlyshare
```
Because of the default settings of the other variables, this will create a share with only read access for registered users.  
To further define permissions and group ownership, you'll have to specify the variables directory_mode and group, as shown in this example:

```Yaml
vsftpd_shares:
  - name: exampleshare
    group: pirates
    directory_mode: u=rwx,g=rwx,o=rwx
```

## Example playbook

```Yaml
- hosts: all
  sudo: yes
  roles:
    - encron.vsftpd
  vars:
    vsftpd_shares_root: '/ftp/shares'
    vsftpd_shares:
      - name: exampleshare
        group: pirates
        directory_mode: u=rwx,g=rwx,o=rwx
    vsftpd_groups: 
      - pirates
    vsftpd_users:
      - username: testuser
        comment: 'A test user'
        groups:
          - pirates
        password: 'testpassword'
        shell: /sbin/nologin
        create_homedir: yes
```

## License

MIT
