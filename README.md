Host-drift
==========

Experimental playbook/role for keeping track of Host-drift using ansible and git!

Create an inventory and run the example playbook. 

```
# inventory

host1
host2

```

```
$ ansible-playbook -i inventory run-host-check.yml
---

$ cat hostcheck/host1/java-version


```
