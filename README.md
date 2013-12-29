# Overview

This is a build pack provides Zend Server on Heroku. Current version is 6.1. In the future the web server and Zend Server binaries will be probably be moved to the stack. This will save space for each container and make pushes and restart almost instant. For the time being they are included in the build pack for portability and ease of installation.

## Buildpack components

* Zend Server 6.1 Enterprise edition.
* Zend Server 6.1 configuration files
* PHP 5.4
* Nginx web server


# Installation
## Requirements
* Working cloud foundry v2 environment with dea_ng and gorouter
* The lucid64 cloud foundry stack should be installed and enabled - check settings in /vagrant/dea_ng/config/dea.yml
* xz compression utility - it's installed automatically by vagrant if you follow the guide below

# Usage
1. Create a folder on your workstation - make sure it has a file named index.php (if you don't do this then you'll have to manually specify which buildpack to use for the app).
2. heroku push --buildpack=https://github.com/dror-g/zend-server-heroku.git   
3. wait for the app to start
4. Once it's started go to the Zend Server GUI on the app link.    For example : http://dave2.herokuapp.io/ZendServer
5. Enter a user name and password to use to authenticate with the GUI.


```
* Code tracing does not yet work in this version.
* Scaling is not yet supported.
* You can change settings using the gui and apply them - but they won't survive application pushes and restarts.
* Application generated data is not persistent (this is a limitation of Cloud Foundry) unless saved to a third party storage provider (like S3).
* You'll be asked to re-bootstrap Zend Server after each app push/restart (Please note that this is optional - I've pre-entered license details so all features should work without this. It is only necessary for using the Zend Server GUI or API).
* Mysql is not used automatically - If you require MySQL then you'll have to setup your own server and configure your app to use it.
* Each container has their own full copy of Zend Server at the moment so it consumes about 300MB.

