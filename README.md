# ldapserver-demo

sources: https://www.digitalocean.com/community/tutorials/how-to-install-and-configure-a-basic-ldap-server-on-an-ubuntu-12-04-vps, http://www.linuxdevcenter.com/pub/a/linux/2003/08/14/libldap.html

Guide: http://www.zytrax.com/books/ldap/apa/


4 Debian jessie / sid

    # aptitude install slapd
    # dpkg-reconfigure slapd
    

You will be asked a series of questions about how you'd like to configure the software.

Omit OpenLDAP server configuration? No

DNS domain name?

This will create the base structure of your directory path. Read the message to understand how it works.
There are no set rules for how to configure this. If you have an actual domain name on this server, you can use that. Otherwise, use whatever you'd like.
In this article, we will call it test.com 
Organization name?

Again, this is up to you
We will use example in this guide. 
Administrator password?

Use the password you configured during installation, or choose another one 
Database backend to use? HDB

Remove the database when slapd is purged? No

Move old database? Yes

    # aptitude install phpldapadmin
    # aptitude install php-xml

config /etc/phpldapadmin/config.php

    $servers->setValue('server','host','domain_nam_or_IP_address');
    $servers->setValue('server','base',array('dc=test,dc=com'));
    $servers->setValue('login','bind_id','cn=admin,dc=test,dc=com');

Open your browser and navigate to ldapserverhost/phpldapadmin

Login with the password you provided while installing slapd. Click on `Create new entry here` and select `Generic: Simple Security Object` and you can add a user.

Glossary
--------
DN = Distinguished Name
