Variables Lab
=========

One of the trickier aspects of Ansible is variable precedence. This lab is meant to introduce variable precedence and demonstrate where to put variables in the MVP, why we put them there, and when to put a particular varialbe in a particular spot.


What Makes a Good Variable Name
------------
Variable names should be letters, numbers, and underscores. Variables should always start with a letter.
*foo-port*, *foo port*, *foo.port* and *12* are not valid variable names.


YAML also supports dictionaries which map keys to values. For instance:

```
foo:
  field1: one
  field2: two
```
You can then reference a specific field in the dictionary using either bracket notation or dot notation:

```
foo['field1']
foo.field1
```

Variable Precedence
------------

We have seven places to put a variable in the Ansible best practices MVP. In order of precedence they are:

* role defaults
* host_vars
* group_vars
* playbooks
* role vars
* include vars
* extra vars passed in at the command line 

Print Variables - Debug Statement
------------

```
- debug:
    msg: "{{ defaults_var }}"
```

Run the ansible-playbook Command to Print the Variables
------------

```
ansible-playbook playbooks/variables.yml -vvv -e extra_var="extra_var"
```

Directions
------------
1. Create a new variable "new_variable" in the /home/snops/ansible_SP/roles/variables/default/main.yml file
2. Create a new debug statement in the /home/snops/ansible_SP/roles/variables/tasks/main.yml file
```
- debug:
    msg: "{{ new_variable }}"
```
3. Override the variable by walking through the order of precedence:
  * role defaults
  * host_vars
  * group_vars
  * playbooks
  * role vars
  * include vars
  * extra vars passed in at the command line

4. Each new layer should override the previous layers of variable precednece
