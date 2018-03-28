========
xmr-mine
========

Mine for Monero_ on Arch Linux!  In addition to the *xmr-mine* wrapper
script, this project contains Arch build files and pre-compiled
binaries of xmr-stak_ in both CPU only and CPU + Nvidia versions.

This script simplifies the execution of *xmr-stak* and enables the
command line selection of different pools or currencies without
editing configuration files.  All currency and pool settings are kept
in the *xmr-mine.conf* file.  Additionally, this script loads any
device specific *nvidia.txt* configuration files contained in the
configuration directory.

The xmr-mine configuration directory defaults to *~/.xmr-mine* with
a fallback to the *./.xmr-mine* directory contained within this repo.

Requirements
============

xmr-stak v2.3.0
    The *xmr-mine* is wrapper script extending the functionality of
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
    Specify what currency to mine for.

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

``--show-status, -S``
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
.. _xmr-stak-git: https://aur.archlinux.org/packages/xmr-stak-git
.. _xmr-node-proxy: https://github.com/Snipa22/xmr-node-proxy
