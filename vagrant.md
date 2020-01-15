### Vagrant commands

See the status of Vagrant VM created from current directory

`vagrant status`

See status of all Vagrant VMs

`vagrant global-status`

Execute commands for any VM using it's ID rather than changing to work directory **(deletes box and disk files from the environment directory)**

`vagrant destroy <id>`

Shutdown VM

`vagrant halt`

Start VM

`vagrant up`

Save state of the VM

`vagrant suspend`

Start suspended VM

`vagrant resume`

The equivalent of running *vagrant halt* followed by *vagrant up* **(The configured provisioners will not run again, by default)**

`vagrant reload`

To force the provisioners to re-run by specifying the --provision flag

`vagrant reload --provision`



