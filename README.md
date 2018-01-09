# ipaddr filter examples
The [ipaddr filter](http://docs.ansible.com/ansible/latest/playbooks_filters_ipaddr.html) is a Jinja2 filter designed to provide an interface to [netaddr](https://pypi.python.org/pypi/netaddr).  This github repo provides examples with the Ansible [template module](http://docs.ansible.com/ansible/latest/template_module.html) to augment the [ipaddr documentation](http://docs.ansible.com/ansible/latest/playbooks_filters_ipaddr.html).

# The Playbook
```yaml
---
- hosts: localhost
  connection: local
  gather_facts: false
  vars:
    sean_subnet: "192.168.1.0/24"
  tasks:
    - template:
        src: ./template.j2
        dest: ./rendered
```

# Running the playbook
Use the ansible-playbook command to run the included playbook.

`[sean@rhel7]$ ansible-playbook ipaddr_test.yml`

The playbook will create a local file called `rendered` which renders the included `template.j2` which includes examples with the ipaddr filter.

# View the playbook
[Click here to view the playbook](ipaddr_test.yml)

# View the rendered template
The rendered config will provider numerous examples.  For example:
```
Jinja2: {% raw %} Prefix: {{ sean_subnet | ipaddr('prefix') }} {% endraw %}
Renders: Prefix: {{ sean_subnet | ipaddr('prefix') }}
```

[Click here to view the rendered template](rendered)

 ---
![Red Hat Ansible Automation](rh-ansible-automation.png)

Red Hat® Ansible® Automation includes three products:

- [Red Hat® Ansible® Engine](https://www.ansible.com/ansible-engine): a fully supported product built on the foundational capabilities of the Ansible project.

- [Red Hat® Ansible® Networking Add-On](https://www.ansible.com/ansible-engine): provides support for select networking modules from Arista (EOS), Cisco (IOS, IOS XR, NX-OS), Juniper (Junos OS), Open vSwitch, and VyOS.

- [Red Hat® Ansible® Tower](https://www.ansible.com/tower): makes it easy to scale automation, manage complex deployments and speed productivity. Extend the power of Ansible with workflows to streamline jobs and simple tools to share solutions with your team.

Want more info?
[Read this blog post for more info about Engine, the networking add-on and Tower](https://www.ansible.com/blog/red-hat-ansible-automation-engine-vs-tower)
