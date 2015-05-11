.. _server:

======
Server
======

The server hosts several applications related to INSPIRE activities of Geonovum. This chapter provides technical details about the server and applications.

Default settings are used unless specified otherwise.

System specs
============
Created May 8th 2015

    [vps60747]

    IPv4 address..: 141.138.192.61

    IPv6 address..: 2a02:348:76:c03d::1 

    Hostname......: vps60747.public.cloudvps.com

    Image.........: ubuntu1404-bare.conf

    RAM...........: 2048MB

    Disk..........: 40 GB

    Cpus..........: 2


Host
====

Geonovum domain: TODO

CloudVPS hostname: vps60747.public.cloudvps.com

IPv4: 141.138.192.61


Backup
============
Auto-backup by CloudVPS, Object Store. See docs http://www.cloudvps.com/community/knowledge-base/cloudvps-boss-linux-backup-to-object-store/

Backups databases and files daily.

Accounts
============
Besides the ``root`` account, there is a user account ``inspire``. The user ``inspire`` has the appropriate rights to manage the applications for the INSPIRE lab.

user ``inspire`` has rights on tomcat7:
    ``usermod -aG tomcat7 inspire``

user ``inspire`` has sudo rights (created using visudo) for restarting some services, like Apache, Tomcat, Postgresql.

Application and database users
------------------------------
Usernames for applications and databases are only available within Geonovum.

Software
============
Following software is installed, using Ubuntu's APT tooling.

* Apache2
* MySql 5.5
* PHP5, php5-mysql
* Java, openjdk-7-jdk
* Tomcat 7
* PostgreSQL 9.3 + PostGIS 2.1

Apache2
-------

Enabled:

* PHP5
* mod_proxy, mod_proxy_ajp

Tomcat 7
--------

* Java: OpenJDK 7
* Java options:

   ``JAVA_OPTS="-Djava.awt.headless=true -server -Xmx1024M -Xms256M -XX:SoftRefLRUPolicyMSPerMB=36000
   -XX:MaxPermSize=256m -XX:+UseParallelGC"``

* Proxy AJP enabled

Applications
============

namespaceregister
-----------------

* Database: ``namespaces``
* Base URL: ``http://vps60747.public.cloudvps.com/namespaces/``

smartcities
-----------------

* Database: ``smartcities``
* Base URL: ``http://vps60747.public.cloudvps.com/smartcities/``

Geoserver WMS/WFS + TJS
-----------------------
Custom compiled version for TJS (base: v 2.8)

TODO: TJS installation and data configuration

* Base URL: ``http://vps60747.public.cloudvps.com/geoserver``

