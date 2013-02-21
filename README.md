Description
===========

Installs and configures Tomcat version 7, OpenAM 10.0.

Requirements
============

Platform:

* Debian, Ubuntu (OpenJDK)


The following Opscode cookbooks are dependencies:

* java
* apt
* opendj `(If you wish to have seperate opendj)`

Attributes
==========
* `node["tomcat-openam"]["opendj"]["arg-val"]["baseDN"]` - LDAP BaseDN value, default `dc=example,dc=com`
* `node["tomcat-openam"]["opendj"]["arg-val"]["rootUserDN"]` - LDAP root user name, default `'n=Directory Manager'`
* `node["tomcat-openam"]["opendj"]["arg-val"]["rootUserPassword"]` - LDAP root user password, default `secret12`
* `node["tomcat-openam"]["opendj"]["arg-val"]["ldapPort"]` - LDAP port value, default `1389`

* `node["tomcat-openam"]["java-options"]` - Heap storage limits, default `-Xms256m -Xmx1024m`

* `node["tomcat-openam"]["cfg"]["server-url"]` - OpenAM server url, default `http://#{node["tomcat-openam"]["dns"]}:8080`
* `node["tomcat-openam"]["cfg"]["deployment-uri"]` - OpenAM deployment uri, default `/openam`
* `node["tomcat-openam"]["cfg"]["base-dir"]` - OpenAM base directory, default `/home/ubuntu/openam`
* `node["tomcat-openam"]["cfg"]["locale"]` - Locale for OpenAM, default `en_US`
* `node["tomcat-openam"]["cfg"]["platform-locale"]` - Platform Locale for OpenAM, defualt `en_US`
* `node["tomcat-openam"]["cfg"]["admin-pwd"]` - OpenAM admin password, default `adminp3me`
* `node["tomcat-openam"]["cfg"]["amldapuserpasswd"]` - LDAP user password, default `adminl3me`
* `node["tomcat-openam"]["cfg"]["cookie-domain"]` - Domain for cookie, default `node[:ec2][:public_hostname]`
* `node["tomcat-openam"]["cfg"]["data-store"]` - OpenAM data store, default `embedded`

* `node["tomcat-openam"]["cfg"]["directory"]["ssl"]` - OpenAM SSL directory, default `SIMPLE`
* `node["tomcat-openam"]["cfg"]["directory"]["server"]` - OpenAM server directory, default `node["tomcat-openam"]["dns"]`
* `node["tomcat-openam"]["cfg"]["directory"]["port"]` - OpenAM directory port, default `50389`
* `node["tomcat-openam"]["cfg"]["directory"]["admin-port"]` - OpenAM directory admin-port, default `5444`
* `node["tomcat-openam"]["cfg"]["directory"]["jmx-port"]` - OpenAM directory jmx-port, default `5689`
* `node["tomcat-openam"]["cfg"]["root-suffix"]` OpenAM root-suffix, default `o=openam`
* `node["tomcat-openam"]["cfg"]["ds-dirmgrdn"]` - Directory Manager name, default `cn=Directory Manager`
* `node["tomcat-openam"]["cfg"]["ds-dirmgrpasswd"]` - Directory manager password, default `emdstor3me`
* `node["tomcat-openam"]["cfg"]["user-store"]["type"]` - User store type, default `LDAPv3ForOpenDS`
* `node["tomcat-openam"]["cfg"]["user-store"]["ssl"]` - User store SSL, default `SIMPLE`
* `node["tomcat-openam"]["cfg"]["user-store"]["host"]` - User store host (OpenDJ URL) `Only if` you need seperate OpenDJ (for the recipe tomcat-openam::configure)
* `node["tomcat-openam"]["cfg"]["user-store"]["port"]` - User store port, default `1389`
* `node["tomcat-openam"]["cfg"]["user-store"]["suffix"]` - User store suffix, default `dc=example,dc=com`
* `node["tomcat-openam"]["cfg"]["user-store"]["mgrdn"]` - User store manager domain name, default `cn=Directory Manager`
* `node["tomcat-openam"]["cfg"]["user-store"]["passwd"]` - User store password, default `secret12`

Usage
=====

Simply include the recipe where you want Tomcat on apache server with OpenAM installed.

An example for a tomcat-openam full_stack role:

	`name "openam_fullstack"`
	`run_list "recipe[apt]", "recipe[apache2]", "recipe[tomcat-openam::full_stack]"`




License and Author
==================

Author:: Kishore Kumar (<nkishore@megam.co.in>)
Author:: Thomas Alrin (<alrin@megam.co.in>)


Copyright:: 2012, Megam Systems

Licensed under the Apache License, Version 2.0 (the "License");
you may not use this file except in compliance with the License.
You may obtain a copy of the License at

    http://www.apache.org/licenses/LICENSE-2.0

Unless required by applicable law or agreed to in writing, software
distributed under the License is distributed on an "AS IS" BASIS,
WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
See the License for the specific language governing permissions and
limitations under the License.
