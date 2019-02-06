Host-drift
==========

Experimental playbook/role for keeping track of Host-drift using ansible and git!  

The idea is to define custom checks and write the output to a file locally to a git repo on the ansible host.  
At the end of the playbook run we check in the changes and push them to git.  
By leveraging git we can go back to previous commits to see what has changed.  
We can also make use of webhooks of the upstream git repo to notify if any changes have been detected!  

Usage 
-----
Create an inventory and run the example playbook. 
Extra nice if we use a [dynamic inventory](https://docs.ansible.com/ansible/latest/user_guide/intro_dynamic_inventory.html).

```
# inventory

host1
host2

```

Create a git repo and make sure it has an upstream remote called origin.  
Usually this is as simple as creating a repo on ie. Github and running the git clone procedure.  
_You really want to use git over ssh and ensure that your ansible host users public key is allowed to push_   
_The drift role can't handle user authentication_  

```
$ git clone git@github.com:user/host-drift-repo.git /home/user/hostdrift
```

Define the local git repo path for where we are going to save the output/result.  

```
- hosts: host1,host2
  become: true
  vars:
    git_repo_path: /home/user/hostdrift/  <--
  tasks:
  ....
```

Run the playbook!

```
$ ansible-playbook -i inventory run-host-check.yml

```

On the initial run it will push all the output files into your git repo.  
On the second run, it will only push changes detected by git (git diff ).


