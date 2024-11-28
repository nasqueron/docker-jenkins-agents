### Docker images for Jenkins agents

This repository offers Dockerfile to build images to run Jenkins agents
for CI and CD purposes.

#### nasqueron/jenkins-agent-barebone

This image contains only what's required by Jenkins:

* an OpenSSH server
* Java
* ant

#### nasqueron/jenkins-agent-php

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
  * PHP 8.2
  * Composer
* Node 20
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

#### nasqueron/jenkins-agent-node

This image contains:

* The software required by Jenkins:
  * an OpenSSH server
  * Java
  * ant
* Version control:
  * Git
* Node:
  * Node 19.x
  * node-sass
  * Spectacle
