# Vagrant Package Manager

This is not actually a package manager, but rather a helper to make `npm` work
nicer in shared folders in Vagrant.

## Install

```bash
sudo npm install -g vagrant-pm
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
