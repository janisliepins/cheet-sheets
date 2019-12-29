### Vagrant commands

Power off VM

`vagrant halt`

Start powered off VM

`vagrant up`

Save state of the VM

`vagrant suspend`

Start suspended VM

`vagrant resume`

The equivalent of running a halt followed by an up **(The configured provisioners will not run again, by default)**

`vagrant reload`

To force the provisioners to re-run by specifying the --provision flag

`vagrant reload --provision`



