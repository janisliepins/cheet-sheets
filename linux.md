### wget

Download any file by given URL

`wget http://mirrors.kernel.org/ubuntu/pool/universe/d/dlocate/dlocate_1.07+nmu1_all.deb`


### dpkg

List all installed packages

`sudo dpkg -l | less`

Install downloaded package

`sudo dpkg -i dlocate_1.07+nmu1_all.deb`

Remove application and any configuration files that comes with it

`sudo dpkg --purge dlocate`


### apt

Apt source list in `/etc/apt/sources.list` where, e.g.

`deb http://fi.archive.ubuntu.com/ubuntu bionic-updates main restricted`

1. location of deb packages
2. current ubuntu version
3. keywords:
  * *main* - officialy supported software
  * *restricted* - supported software which is not availabe under completely free license
  * *universe* - community maintained software
  * *multiverse* - software which is not free

Download latest releases and create internal package list

`sudo apt-get update`

Install package and all it's dependencies

`sudo apt-get install dlocate`

Remove package **(this does not remove dependecies and configuration files)**

`sudo apt-get remove dlocate`

Remove package and configuration files **(this does not remove dependecies)**

`sudo apt-get purge dlocate`

Remove any unused packages

`sudo apt autoremove`

Information about package

`sudo apt-cache depends apache2`

Search for package

`sudo apt-cache search nginx`

Upgrade all currently installed packages, new versions of currently installed packages that can not be upgraded without changing install status of another package will be left at their current version

`sudo apt-get upgrade`

Upgrade everything, install and remove any packages required to complete the upgrade

`sudo apt-get dist-upgrade`


