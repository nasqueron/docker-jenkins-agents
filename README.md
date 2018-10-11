### Docker images for Jenkins slaves

This repository offers Dockerfile to build images to run Jenkins slaves
for CI and CD purposes.

#### nasqueron/jenkins-slave-barebone

This image contains only what's required by Jenkins:

* an OpenSSH server
* Java
* ant

#### nasqueron/jenkins-slave-php

This image contains:

* The software required by Jenkins:
  * an OpenSSH server
  * Java
  * ant
* Version control:
  * Git
  * Mercurial
  * Subversion
* PHP:
  * PHP 5
  * Composer
* The usual CI tools described in jenkins-php.org:
  * PHPUnit
  * PHP_CodeSniffer
  * phpcpd
  * phpDox
  * PDepend
  * phploc
  * PHPMD
* Code review:
  * Arcanist

#### nasqueron/jenkins-slave-node

This image contains:

* The software required by Jenkins:
  * an OpenSSH server
  * Java
  * ant
* Version control:
  * Git
* Node:
  * Node 9.x
  * PhantomJS
  * node-sass
  * Spectacle
