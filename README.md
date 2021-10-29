# Libssh-2 Ruby

#Setup

## Install Prerequisites

This library relies on the C library libssh2. Install it with

    $ brew install libssh2

It also requires openssl and crypto_malloc. Brew install these also if required.

    $ brew install openssl

## Create Makefile

Run the following file to check that you have all the prerequisites and create the Makefile.

    $ ruby ext/libssh2_ruby_c/extconf.rb

If the command succeeds, run the Makefile.

    $ cd ext/libssh2_ruby_c
    $ make

You should now have several .o files and libssh2_ruby_c.bundle inside the ext/libssh2_ruby_c directory



## Running the Tests

This library has an acceptance test suite to verify everything is working.
Since it is an acceptance test library, it will make actually SSH connections
to verify things are working properly.

Use either the sds FTP/SFTP server via. The username and password for these servers are salsify/salsify and ports are 21212/2022 by default.

    $ sds start -s ftp

An alternative is also launching https://github.com/rastasheep/ubuntu-sshd

The username and password by default are root/root, and the port can be viewed in your docker app.

Running the suite is easy. First,
create a `config.yml` based on the `config.yml.example` file in the `spec`
directory. This must be configured to point to a real server that can an
SSH connection can be established to with both password and key based auth.
Once the `config.yml` is in place, run the tests:

    $ rspec

