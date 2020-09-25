# Define_Ansible_Playbook
Udacity Excercise

Exercise: Define Ansible Playbook
For this exercise, your objective will be to print the contents of an environment variable to the console using an Ansible Playbook via a role.

Instructions:
For this exercise, it assumes you already have installed Ansible in your workstation.

Create a new Ansible Playbook file named main.yml (starting out, it's just a blank text file).
Create a new directory named roles.
In the roles directory, create a new folder called print.
Inside print, create a new folder called tasks.
Your folder structure should look like this:

  /main.yml
  /roles
  /roles/print
  /roles/print/tasks

  Create a task to be executed by the role. Name it /roles/print/tasks/main.yml and add the following content:

  ---
 - name: Print env variable
   shell: echo $PATH
   register: print_result

 - name: print message
   debug:
     msg: "{{ print_result.stdout_lines }}"

Navigate back to the folder that contains your Playbook (in case you navigated away).

Add the following code to your Playbook file:

---
- name: Exercise #1
  hosts: localhost

  roles:
   - print

Notice that we reference a role named print. We didn't mention a path to the task file. That's because Ansible knows where to look as long as we follow the folder structure convention!

Run your playbook using the command ansible-playbook main.yml.

You should see some results like the following:

TASK [print : print message]     ************************************************************************
ok: [localhost] => {
    "msg": [
        "/home/user/.local/bin:/home/user/bin:/usr/local/sbin:/usr/local/bin:/usr/    sbin:/usr/bin:/sbin:/bin:/usr/games:/usr/local/games:/snap/bin"
    ]
}


Congratulations!
You can now print to the console. Big deal, right? Well, in a way, it IS a big deal. Now that you know how to build a simple Ansible Playbook with a role, you can probably imagine how to do more complicated things. Many times starting is the key to finishing.

