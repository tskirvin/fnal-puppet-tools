fnal-puppet-tools
=================

Tools for managing puppet at FermiLab.

## hiera-wrapper

This script provides a simple wrapper around the standard `hiera` command
to help debug hiera issues.  It is fairly tied to the USCMS-T1
implementation of hiera, which has four levels:

1. (common data)
1. system class (e.g. 'server' or 'worker')
1. system role (e.g. 'puppetmaster' or 'puppetdb')
1. hostname

Sample usage:

    cmspuppet1 ~# ./hiera-wrapper --role puppetmaster puppet::config::reports --array
    # /usr/bin/hiera -c /etc/puppet/hiera.yaml -a puppet::config::reports environment=production role::base::hier_top=server role::base::hier_role=puppetmaster ::role=puppetmaster
    ["puppetdb"]
