# Try-Ceph : What is it 

Try-Ceph requires bare mininum work to get your FIRST CEPH CLUSTER running for your testing purpose and learning purpose. Anyone who wants to have a quick look at CEPH , this is the fastes way to get to their first Ceph cluster.

## Try-Ceph features includes

* Quickest way to get your first test Ceph cluster up and running.
* Automated Ceph installation and configuration within the box.
* Installs and configure  ceph-dash : A Ceph graphical dashboard for monitoring.
* Installs and configure Object Storage which is accessible via S3 or Swift API
* User can define number of Monitor and OSD nodes for the Ceph cluster.
* It  uses Vagrant --> Ansible --> Ceph --> Ceph-dash

## Requirements

* Host machine OS - Mac OSX or any LINUX distribution ( tested on CentOS , Ubuntu )
* Virtuliaztion platform - Oracle VirtualBox ( tested ) or VMWare workstation
* Disk Space on host machine - >5GB ( 1 mon & 1 OSD node with 2 OSD's ) 
* Host configuration management - Ansible

## How to get started with Try-Ceph

Prerequiste : Make sure your host machine should comply with the requirements mentioned above. 
Before "vagrant up" operation sometimes   ' git config --global url."https://".insteadOf git:// ' is needed to solve Ceph installation packages.


STEP - 1 : ``` $ git clone https://github.com/ksingh7/Try-Ceph.git ```


```
$ git clone https://github.com/ksingh7/Try-Ceph.git
Cloning into 'Try-Ceph'...
remote: Counting objects: 127, done.
remote: Compressing objects: 100% (68/68), done.
remote: Total 127 (delta 19), reused 105 (delta 11)
Receiving objects: 100% (127/127), 29.23 KiB | 0 bytes/s, done.
Resolving deltas: 100% (19/19), done.
Checking connectivity... done.
$
```
STEP - 2 : ``` $ cd Try-Ceph ```

```
NOTE : By default vagrant will provision 1 MON and 3 OSD node , if you need more MON / OSD nodes , please change the NMONS and NOSDS parameteraunder  Vagrantfile.
```

STEP - 3 : ``` $ vagrant up ```

```
$ vagrant up
Bringing machine 'mon0' up with 'virtualbox' provider...
Bringing machine 'osd0' up with 'virtualbox' provider...
==> mon0: Importing base box 'TryCeph-ksingh'...
==> mon0: Matching MAC address for NAT networking...
==> mon0: Setting the name of the VM: Try-Ceph_mon0_1421769347423_11309
==> mon0: Clearing any previously set network interfaces...
==> mon0: Preparing network interfaces based on configuration...
    mon0: Adapter 1: nat
    mon0: Adapter 2: hostonly
==> mon0: Forwarding ports...
    mon0: 22 => 2222 (adapter 1)
==> mon0: Running 'pre-boot' VM customizations...
==> mon0: Booting VM...
==> mon0: Waiting for machine to boot. This may take a few minutes...
    mon0: SSH address: 127.0.0.1:2222
    mon0: SSH username: vagrant
    mon0: SSH auth method: private key
    mon0: Warning: Connection timeout. Retrying...
    mon0: Warning: Connection timeout. Retrying...
==> mon0: Machine booted and ready!
==> mon0: Checking for guest additions in VM...
==> mon0: Setting hostname...
==> mon0: Configuring and enabling network interfaces...
==> mon0: Mounting shared folders...
    mon0: /vagrant => /private/tmp/Try-Ceph
==> osd0: Importing base box 'TryCeph-ksingh'...
==> osd0: Matching MAC address for NAT networking...
==> osd0: Setting the name of the VM: Try-Ceph_osd0_1421769412403_51414
==> osd0: Fixed port collision for 22 => 2222. Now on port 2200.
==> osd0: Clearing any previously set network interfaces...
==> osd0: Preparing network interfaces based on configuration...
    osd0: Adapter 1: nat
    osd0: Adapter 2: hostonly
    osd0: Adapter 3: hostonly
==> osd0: Forwarding ports...
    osd0: 22 => 2200 (adapter 1)
==> osd0: Running 'pre-boot' VM customizations...
==> osd0: Booting VM...
==> osd0: Waiting for machine to boot. This may take a few minutes...
    osd0: SSH address: 127.0.0.1:2200
    osd0: SSH username: vagrant
    osd0: SSH auth method: private key
    osd0: Warning: Connection timeout. Retrying...
    osd0: Warning: Remote connection disconnect. Retrying...
==> osd0: Machine booted and ready!
==> osd0: Checking for guest additions in VM...
==> osd0: Setting hostname...
==> osd0: Configuring and enabling network interfaces...
==> osd0: Mounting shared folders...
    osd0: /vagrant => /private/tmp/Try-Ceph
==> osd0: Running provisioner: ansible...
PYTHONUNBUFFERED=1 ANSIBLE_FORCE_COLOR=true ANSIBLE_HOST_KEY_CHECKING=false ANSIBLE_SSH_ARGS='-o UserKnownHostsFile=/dev/null -o ControlMaster=auto -o ControlPersist=60s' ansible-playbook --private-key=/Users/ksingh/.vagrant.d/insecure_private_key --user=vagrant --connection=ssh --limit='all' --inventory-file=/private/tmp/Try-Ceph/.vagrant/provisioners/ansible/inventory --extra-vars={"fsid":"10c95f01-2dd2-4863-affa-60c4eafcd8d2","monitor_secret":"AQBNTxZRWId7JxAA/Ac4ToR7ZfNdOGDSToGHpA=="} site.yml

PLAY [mons;osds] **************************************************************

GATHERING FACTS ***************************************************************
ok: [osd0]
ok: [mon0]

TASK: [common | Copying Ceph key] *********************************************
changed: [osd0]
changed: [mon0]

TASK: [common | Importing Ceph GPG  key] **************************************
changed: [osd0]
changed: [mon0]

TASK: [common | Copying EPEL key] *********************************************
changed: [osd0]
changed: [mon0]

TASK: [common | Importing EPEL GPG  key] **************************************
changed: [mon0]
changed: [osd0]

TASK: [common | Adding ceph to YUM repo] **************************************
changed: [osd0]
changed: [mon0]

TASK: [common | Creating directories required by ceph [/var/lib/ceph]] ********
changed: [osd0]
changed: [mon0]

TASK: [common | Creating directories required by ceph [/var/lib/ceph/{{ item }}]] ***
changed: [mon0] => (item=tmp)
changed: [osd0] => (item=tmp)
changed: [mon0] => (item=mon)
changed: [osd0] => (item=mon)
changed: [mon0] => (item=bootstrap-osd)
changed: [osd0] => (item=bootstrap-osd)

TASK: [common | Creating directories required by ceph [/var/log/ceph]] ********
changed: [osd0]
changed: [mon0]

TASK: [common | Creating directories required by ceph [/etc/ceph]] ************
changed: [osd0]
changed: [mon0]

TASK: [common | Installing Ceph packages] *************************************
changed: [osd0]
changed: [mon0]

TASK: [common | Generating Ceph configuration file] ***************************
changed: [osd0]
changed: [mon0]

PLAY [mons] *******************************************************************

GATHERING FACTS ***************************************************************
ok: [mon0]

TASK: [mons | Creating monitor initial keyring] *******************************
changed: [mon0]

TASK: [mons | Setting initial monitor key permissions] ************************
ok: [mon0]

TASK: [mons | Creating monitor directory] *************************************
changed: [mon0]

TASK: [mons | Creating administrator keyring , Generating a client.admin user and adding the user to the keyring] ***
changed: [mon0]

TASK: [mons | Adding the client.admin key to the ceph.mon.keyring.] ***********
changed: [mon0]

TASK: [mons | Generating a monitor map using the hostname,host IP address and the FSID. Save it as /tmp/monmap] ***
changed: [mon0]

TASK: [mons | Populating the monitor daemon with the monitor map and keyring.] ***
changed: [mon0]

TASK: [mons | Start and add that the monitor service to the init sequence] ****
changed: [mon0]

TASK: [mons | Adding the new monitor to the cluster] **************************
changed: [mon0]

TASK: [mons | Copy keys to the ansible server under fetch dirctory] ***********
changed: [mon0] => (item=/var/lib/ceph/bootstrap-osd/ceph.keyring)
changed: [mon0] => (item=/var/lib/ceph/mon/ceph-mon0/keyring)
ok: [mon0] => (item=/etc/ceph/ceph.bootstrap-osd.keyring)
ok: [mon0] => (item=/etc/ceph/ceph.mon.keyring)
changed: [mon0] => (item=/etc/ceph/ceph.conf)
changed: [mon0] => (item=/etc/ceph/ceph.client.admin.keyring)

TASK: [mons | Cloning ceph-dash from github] **********************************
changed: [mon0]

TASK: [mons | Upgrading jinja2 for ceph-dash] *********************************
changed: [mon0]

TASK: [mons | Executing ceph-dash] ********************************************
<job 247130811836.5139> finished on mon0

PLAY [osds] *******************************************************************

GATHERING FACTS ***************************************************************
ok: [osd0]

TASK: [osds | Creating directories required by ceph] **************************
ok: [osd0] => (item=tmp)
ok: [osd0] => (item=mon)
ok: [osd0] => (item=mds)
ok: [osd0] => (item=bootstrap-osd)
ok: [osd0] => (item=bootstrap-mds)

TASK: [osds | Gathering keys from MON node to OSD node [ STEP-1 ]] ************
changed: [osd0]

TASK: [osds | Copying OSD bootstrap key to OSD node] **************************
changed: [osd0]

TASK: [osds | Zapping OSD] ****************************************************
changed: [osd0] => (item=/dev/sdb)
changed: [osd0] => (item=/dev/sdc)

TASK: [osds | Prepare OSD disk(s)] ********************************************
changed: [osd0] => (item=/dev/sdb)
changed: [osd0] => (item=/dev/sdc)

TASK: [osds | Activating  OSD] ************************************************
changed: [osd0] => (item=/dev/sdb)
changed: [osd0] => (item=/dev/sdc)

TASK: [osds | Start and add that the OSD service to the init sequence] ********
changed: [osd0]

PLAY RECAP ********************************************************************
mon0                       : ok=27   changed=22   unreachable=0    failed=0
osd0                       : ok=20   changed=17   unreachable=0    failed=0

$
```

STEP - 4 : Check Ceph cluster status

```
$ vagrant ssh mon0 -c "sudo ceph -s"
    cluster 10c95f01-2dd2-4863-affa-60c4eafcd8d2
     health HEALTH_OK
     monmap e1: 1 mons at {mon0=192.168.101.10:6789/0}, election epoch 2, quorum 0 mon0
     osdmap e17: 6 osds: 6 up, 6 in
      pgmap v25: 192 pgs, 3 pools, 0 bytes data, 0 objects
            207 MB used, 65126 MB / 65333 MB avail
                 192 active+clean
Connection to 127.0.0.1 closed.
$
```

STEP - 5 : To check status of your cluster using Ceph dashboard. Point your host browser to http://192.168.101.10:5000

![Try-Ceph Dashboard](https://raw.githubusercontent.com/ksingh7/Try-Ceph/master/screenshot/ceph-dash.png) 

STEP - 6 : To access object storage via S3
* Node mon0 is preconfigured for s3 which can be accessed via [s3cmd](http://s3tools.org/s3cmd)
``` 
    # vagrant ssh mon0 
    $ sudo su -
    # s3cmd ls                          # List S3 bucket
    # s3cmd mb s3://first-bucket        # Make S3 bucket
    # s3cmd ls                          # List S3 bucket
```
STEP - 7 : To access object storage via SWIFT
* Install swift cli tools to a node that have access to mon0 machine ( 192.168.101.10 )
``` # swift -A http://192.168.101.10/auth/1.0 -U demo:swift -K 'SwiftSecretKey' list ```

## Destro Try-Ceph setup

STEP - 1 : Check status of your  vagrant instances ``` $ vagrant status ```

STEP - 2 : Halt vagrant instances ``` $ vagrant halt mon0 osd0 osd1 osd2 ```

STEP - 3 : Destroy vagrant instances ``` $ vagrant destroy -f mon0 osd0 osd1 osd2 ```


