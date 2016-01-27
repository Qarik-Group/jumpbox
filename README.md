Jumpbox
=======

Best practices for deploying a secure BOSH director say you should
set up a "jumpbox" and restrict access to the director so that
only that jumpbox can connect to it.

This repository contains `jumpbox`, a utility that will install
all necessary utilities for running BOSH deployments, including:

  - **rvm** - For managing versions of Ruby and the BOSH CLI gems
  - **ruby** - For the BOSH CLI
  - **bosh** - The BOSH CLI itself
  - **genesis** - For creating multi-tiered deployment repos
  - **spruce** - A YAML multitool for managing BOSH manifests
  - **jq** - A JSON query utility


Installation
------------

Grab the latest copy from Github and put it in your `$PATH`:

    sudo curl -o /usr/local/bin/jumpbox \
      https://raw.githubusercontent.com/jhunt/jumpbox/master/bin/jumpbox
    sudo chmod 0755 /usr/local/bin/genesis

Usage
-----

`jumpbox` operates in two modes: `system` and `user`

You only have to run **system** mode once per box.  It installs
global utilities that live outside of individual user home
directories, like `spruce`, `jq`, etc.

    sudo jumpbox system

Every user on the jumpbox needs to run **user** mode at least
once.  This will set up `rvm`, the ruby dependencies and the
`bosh` CLI utility, inside that user's home directory.

    jumpbox user


Contributing
------------

1. Fork it
2. Create your feature branch (`git checkout -b my-new-feature`)
3. Commit your changes (`git commit -am 'Added some feature'`)
4. Push to the branch (`git push origin my-new-feature`)
5. Create new Pull Request
