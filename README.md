# Vagrant Package Manager

This is not actually a package manager, but rather a helper to make `npm` work
nicer with shared folders in Vagrant.

## Setup Vagrant

+ Add a customize line into your `Vagrantfile`:

Replace `<synced folder>` with the path to your synced folder. With a default
vagrant setup the path would simply be `/vagrant`.

```hcl
config.vm.provider "virtualbox" do |v|
  v.customize ["setextradata", :id, "VBoxInternal2/SharedFoldersEnableSymlinksCreate/<synced folder>", "1"]
end
```

+ Run your terminal (Command Prompt, Git Bash, Powershell, ...) in Administrator mode.
Simply right click on the app icon and select "Run as Administrator". Then setup
vagrant as normal:

```bash
$ vagrant up
...
$ vagrant ssh
```

NOTE: Make sure you run `vagrant up` while in Administrator mode.

## Install

```bash
$ sudo npm install -g vagrant-pm
```

## Usage

### Initialize Symlink

```bash
$ cd my-project
$ vpm init
Created link node_modules -> /home/vagrant/.vagrant_modules/my-project/node_modules
```

By default the symlink will be created in `$HOME/.vagrant_modules`, it can be
overidden with the `VPM_MODULES_PATH` environment variable:

```bash
$ export VPM_MODULES_PATH=/tmp/foo
$ vpm init
Created link node_modules -> /tmp/foo/my-project/node_modules
```

### Clean out modules

Delete the symlink and the modules in the target.

```bash
$ vpm clean
Cleaned node_modules.
```
