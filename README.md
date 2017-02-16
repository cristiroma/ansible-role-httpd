httpd
=====

Standard prefork httpd installation.

Requirements
------------

CentOS 7 image

Role Variables
--------------

```
    apache_virtual_hosts:
      - {
          vh_domain: "domain1.com", vh_home: "/var/www/html/site1",
          template: "apache-vh-simple.conf.j2", dest: "domain1.conf",
        }
      - {
          vh_domain: "domain2.com", vh_home: "/var/www/html/domain2",
          template: "apache-vh-simple.conf.j2", dest: "domain2.conf",
        }

    apache_expires_default: "access plus 1 months"
    apache_expires_default_images: "{{ apache_expires_default }}"
    apache_expires_default_js: "{{ apache_expires_default }}"
    apache_expires_default_css: "{{ apache_expires_default }}"
    apache_expires_default_pdf: "{{ apache_expires_default }}"
```

Dependencies
------------

``cristiroma.production`` (optional)

Example Playbook
----------------

To create a new VHs on existing server:

```
 ansible-playbook -u sysadmin -b -i hosts.test --tags="create-vh" play.yml
```

    - hosts: servers
      roles:
         - { role: cristiroma.httpd }

License
-------

BSD

Author Information
------------------

This role was created and maintained by @cristiroma
