# Services

## `talk`

```
$ talk otheruser@localhost ( optional tty name )
```

`otheruser` will get a prompt to show how to reply.

## Mail

Run `mutt`. You should be able to mail other users by their username.

# Hacking

```
$ poetry run ansible-playbook configure.yml 
```

This uses Ansible Core. Documentation is at:

https://docs.ansible.com/ansible-core/2.12/index.html
