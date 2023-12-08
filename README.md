# ansible

Ansible is a configuration management tool which works both on push and pull mechanisms.

### Ansible is very famous and is widely used in the industry and it is quite popular !!! want to know the pros of it?

...
1) Ansible is an agent-less software !!!
2) Ansible uses SSH as a default mechanism to communicate with other servers. (port number:22)
3) The only thing that Ansible Node expects is, its  communication to other servers that needs CM !.
4) Ansible is the only tool that works with both push and pull mechanism.
5) Common credentials across the board (Ansible server should be able to ssh to any of the servers )
6) Ansible goes by declarative approach and their documentation is really vast and good
7) Operations are parallel with ansible, multiple CM's are doable.
8) Code does not need to be on the top of a local server !!!

### Important points to be Noted
....
  1) Ansible in the banckend uses Python 
  2) When u install Ansible, by default it installs Ansible version 2 which is from Python 2, 
  3) Python 2 is sunset since Jan 2020
  4) Latest version of Ansible are Python 3 based (so to install Ansible > 2, you need to have Python 3)
  5) By default on all AWS AMIs , u will get Python 2.
  

  ### Ansible Documentation Reference :

    https://docs.ansible.com/ansible/latest/index.html




Ansible is an open source product and it was acquired by RedHat in 2020 and redhat was acquired by IBM. Normally IBM makes thing proprietary but it is still open source.

Ansible ......> Redhat......> IBM  ( IBM is a Redhat Product now & still open source)

### INVENTORY FILE

.....

Inventory file is nothing but the list of machine IP or DNS names that you want ansible to manage


### How can we operate Ansible ?

Ansible can be operated in two ways :

  1) Manual approach ( u can execute one action at a time)
  2) Automated approach (u can execute multiple actions parallely using playbooks)


###  Manual Approach

   $ ansible -i inv all -e ansible_user=centos -e ansible_password=DevOps321 -m(module) shell -a(attribute) uptime

## one of widely asked interview qustion

How to know the list of machines mentioned in the inventory are up or not?

   $ ansible -i inv all -e ansible_user=centos -e ansible_password=DevOps321 -m ping (to check if a particular machine is up or not)

                  (all is a group which includes everything) (-e stands for external variable) (ansible_user is a predefined var which ansible software has it) (-m stands for module, we are telling module ping, ping pong test to do)

                  Collection or Module both are same thing

#### What is a playbook ?

....
     On High level, Playbook is an ANSIBLE SCRIPT to execute things parallely. 

     A playbook is a list of plays..

     A play is a list of tasks..

     A task is an action that you want to execute..
.....

#### What is the language used by Playbook ?

.....
      YAML is the language used by ANSIBLE to write Playbooks.

### YAML : Yet another markup language  :
....
    YAML is Indentation specific.
.....    

#### What is a markup language ?

.....
      Markup language is a presentation language !!!!

      Ex. html, xml
....    


## SSH is 22(ssh is a secure shell, encrypted), whereas https (web based protocol) is 443

Ansible by default work on Push, Ansible will push instructions to all nodes.

Parallel operations are possible with Ansible.

Pip is a python package installer


....

#### YAML is all about 3 ways of representing data that's based on the datatype

....
     1) Dictionary : a key value pair

                 ex: 
                 course: Devops
                  (key)   (value)

     2) List       : a key with multiple values

             ex:
                Course:
                    - Devops
                    - aws
                    - gcp

### How to run ansible-playbooks

...
    $ ansible-playbook -i inv all -e ansible_user=centos -e ansible_password=DevOps321 playBookName.yaml 

### When to use quotes  fro variables in an Ansible playbook ?
...
   Ansible supports quotes for Variables!

   When you are just using the variable only, then you do not need to place quotes instead use it directly {{ENV}}

   When your variables in between the lines, then ensure you place them in quotes instrad of using directly "Name of the environment is {{ENV}}"

   Ansible always suggests to organise the files, tasks and variables in a standard format using ROLES.

     > Roles play a very important role in Ansible
     
     
  ### Role directory structure 

 An Ansible role has a defined directory structure with eight main standard directories. You must include at least one of these directories in each role. You can omit any directories the role does not use. For example:

...

roles/
    frontend/             # this hierarchy represents a "role"
        tasks/            #
            main.yml      #  <-- tasks file can include smaller files if warranted
        handlers/         #
            main.yml      #  <-- handlers file
        templates/        #  <-- files for use with the template resource
            ntp.conf.j2   #  <------- templates end in .j2
        files/            #
            bar.txt       #  <-- files for use with the copy resource
            foo.sh        #  <-- script files for use with the script resource
        vars/             #
            main.yml      #  <-- variables associated with this role
        defaults/         #
            main.yml      #  <-- default lower priority variables for this role
        meta/             #
            main.yml      #  <-- role dependencies
            
...            