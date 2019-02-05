Host-drift
==========

Experimental playbook/role for keeping track of Host-drift using ansible and git!
The idea is to define custom checks and write the output to a file locally on the ansible host.
At the end of the playbook run we check in the changes and push them to git.
By leveraging git we can go back to previous commits to see what has changed.


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


