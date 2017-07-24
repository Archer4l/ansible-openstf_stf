Role Name
=========

This role install openstf and configure it.

You need use this parameters for configure apache, docker and openstf:
---
    tls_certificate_name: *you host*
    
    apache_vhosts_ssl:
        - servername: *you host*
          certificate_name: "{{ tls_certificate_name }}"
          extra_parameters: |
              ProxyPass / http://localhost:7100/
              ProxyPassReverse / http://localhost:7100/
              <Proxy *>
                    Order deny,allow
                    Allow from all
              </Proxy>
    
    openstf_ldap_url: "ldap://_server_:389"
    openstf_ldap_search_dn: "CN=Users,DC=example,DC=com"
    openstf_ldap_bind_dn: "CN=user,CN=Users,DC=example,DC=com"
    openstf_ldap_bind_credentials: "password"
    openstf_ldap_search_field: "sAMAccountName"
    
    
openstf_ldap_url - ldaps not working, yet, USE LDAP  