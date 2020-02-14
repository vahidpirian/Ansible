Role Name
=========

This role is to put a firewall in front of a web server that provides the WordPress website.		

Requirements
------------

This role requires a server to install the firewall.		

Role Variables
--------------

In this role, three variables are defined as follows:		

- firewall_ip: Ip address your firewall server		
- webserver_ip: Ip address your web serber		
- host_name_firewall: your firewall host name		


Example Playbook
----------------
```yml		
- hosts: "{{ your_host }}"		
  become: yes		
  vars:		
   - worker		
   - 192.168.1.8		
   - 192.168.1.7		
  tasks:		

   - name: Add new rule to PREROUTING_WEB chain		
     iptables:		
      table: nat		
      chain: PREROUTING_WEB		
      action: insert		
      protocol: tcp		
      destination: "{{ firewall_ip }}"		
      destination_port: 80		
      jump: DNAT		
      to_destination: "{{ webserver_ip }}:80"		
     tags: add_rule_prerouting_web		
```		
