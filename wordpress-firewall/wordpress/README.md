ole Name
=========

This role is to implement a web server.		

Requirements
------------

- php		
- mariadb		
- wordpress		
- httpd		
- mod_ssl		
- iptables		

Role Variables
--------------

Variables are defined in the vars folder		

Example Playbook
----------------

```yml		
    - hosts: "{{ your_host_webserver }}"		
      become: yes		
      vars:		
       - node		
      tasks:		
       - name: Generate a self signed openssl certificate	
          command: |		
           openssl req -x509 -days 365 -nodes \		
           -subj '/C=IR/ST=Teh/L=Tehran View/O=IT/CN=www.project.me' \		
           -key "{{ key_dir }}project-me.key" \		
           -out "{{ cert_dir }}project-me.crt"		
          tags: gen_cert		
```		
