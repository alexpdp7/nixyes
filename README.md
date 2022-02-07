# Services

## `talk`

```
$ talk otheruser@localhost ( optional tty name )
```

`otheruser` will get a prompt to show how to reply.

## `wall`

```
$ wall <message to broadcast>
```

## Mail

Run `mutt`.
You should be able to mail other users by their username.

### Mailman3

```
$ sudo django-admin createsuperuser --pythonpath /usr/share/mailman3-web --settings settings --username alex --email alex@nixyes
$ mutt
$ lynx
```

## IRC

Run `weechat`.

```
/server add localhost localhost
/connect localhost
/join #...
```

# Hacking

The default inventory is a script using [cloud-run](https://github.com/alexpdp7/cloud-run).
`cloud-run` uses `qemu` to spin VMs using cloud images.

If you don't want to use `cloud-run`, then overwrite `inventory` with a non-executable file containing an inventory that contains a `nixyes` host.

Otherwise, install `cloud-run`, then run:

```
$ cloud-run run debian-bullseye nixyes --mem 2G --forward 8443:443
```

This will spin up a VM.
The process will remain attached to the console of the VM until it is shut down.

Switch to another terminal, and run:

```
$ poetry run ansible-playbook configure.yml 
```

To ssh into the VM, run:

```
$ ssh $(cloud-run ssh nixyes)
```

Shut down the `nixyes` VM so the `cloud-run run` process exits.

Use `cloud-run ssh nixyes --user otheruser` to log in as `otheruser`.

## References

This uses Ansible Core. Documentation is at:

https://docs.ansible.com/ansible-core/2.12/index.html

## Ideas

* Configure skel so weechat autoconnects to localhost.
* Configure skel so weechat autorejoins channels.
* Make postfix, ngircd, inetd listen on loopback
