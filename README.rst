========
xmr-mine
========

Mine for Monero_ on Arch Linux!

This script simplifies the execution of xmr-stak_ by enabling the
command line selection of different pools or currencies without
the need to constantly edit a configuration file.  All currency and
pool settings can be kept in the *xmr-mine.conf* file, which is
sourced upon script execution.  Additionally, this script can load
device specific configuration files contained in the configuration
directory as the *nvidia.txt* file.

The xmr-mine configuration directory defaults to *~/.xmr-mine* with
a fallback to the *./.xmr-mine* directory contained within this repo.


Requirements
============

xmr-stak v2.4.3
    The *xmr-mine* wrapper script extends the functionality of
    *xmr-stak* at the command line.  Some form of *xmr-stak* must be
    installed.


Synopsis
========

``xmr-mine [options]``


Description
===========

Parse command line arguments.
Check if already running.
Check internet connection.
Check processor for AES support.
Use any preexisting *config.txt*, *pools.txt*, *cpu.txt*,
or *nividia.txt* files.
Use any device specific nivida config files.
Build config.txt.
Build pools.txt (source *xmr-mine.conf*).
Launch xmr-stak.


Options
=======

``--background, -B``
    Launch in quiet daemon mode and fork to background.

``--currency, -C <CURRENCY>``
    Set currency to mine for.  Any currency with a wallet and pool
    given in *xmr-mine.conf* may be used.

``--dryrun, -D``
    Generate *config.txt* and *pools.txt* without launching *xmr-stak*.

``--help``
    Print help.

``--kill, -K``
    Kill any instance of *xmr-stak*.

``--pass <POOL PASSWORD>``
    Password used to identify miner on pool.
    *$HOSTNAME* is used if nothing is specified.

``--pool, -p <ADDRESS:PORT>``
    Add pool to *pools.txt* with highest weight.

``--proxy <ADDRESS:PORT>``
    Add xmr-node-proxy_ address to *pools.txt* with highest weight.

``--quiet, -Q``
    Launch *xmr-stak* in daemon mode.  Pipe all output to */dev/null*.

``--random-pool, -R``
    Randomize pool weights.

``--status, -S``
    Print current pool status and hash rate.

``--wallet, -w <ADDRESS>``
    Specify wallet address to mine to.


Environment Variables
=====================

``MINER_CONFIG_DIR``
    Directory containing any *xmr-stak* configuration files.
    *~/.xmr-mine* is used by default.


Notes
=====

Script requires processor to have AES support.

Any number of CryptoNight currencies may be specified in
*xmr-mine.conf*.

Device specific GPU configurations can be saved in *~/.xmr-mine*.
GPU configuration is chosen based on device name and config filename.
See example.


Credits
=======

:Author:
    arcmags

:License:
    GPL 3.0

:Donate(xmr):
    41dUPANhvCvLUuRVJpUc9cRFnsLHzWiTPUhyuamrVwa61xoP
    uxZaD6R28cLqxEhTaC6LuwcHtkbUi2uELDD88MoQHJKePvP


.. _Monero: https://getmonero.org/
.. _xmr-stak: https://github.com/fireice-uk/xmr-stak
.. _xmr-node-proxy: https://github.com/Snipa22/xmr-node-proxy
