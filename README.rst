========
xmr-mine
========

Mine for Monero_ on Arch Linux!  In addition to the *xmr-mine* wrapper
script, this project contains Arch build files and pre-compiled binaries of xmr-stak_ in both CPU only and CPU + Nvidia versions.


Requirements
============

xmr-stak
    The *xmr-mine* is wrapper script extending the functionality of
    *xmr-stak* at the command line.  Some for of *xmr-stak* must be
    installed.  (xmr-stak-git_ is available in the AUR as well as this repo.)

timedatectl set-ntp true
    This script ensures system clock is synced via the
    *systemd-timesyncd.service* prior to launching *xmr-stak*.


Installation
============

xmr-stak miners can be installed by executing ``makepkg -sri`` within their
PKGBUILD directories.  Or, if you're unable to compile yourself and you trust
me enough, you can install the pre-compiled packages in *pkg/* with
``pacman -U [package]``.

Then copy the *xmr-mine* script to your local path and edit the config
variables at the head of the script with your desired wallet and pool info.

A valid machine hostname and domain must be specified by MINER_NAME
in order to correctly display miner stats.

Synopsis
========

``xmr-mine [options]``


Description
===========

Check for internet connection and wait for system clock sync.  Ensure
processor supports AES.  Check if *xmr-stak* is already running.  Generate
*config.txt* file from script variables and arguments.  Launch *xmr-stak*.


Options
=======

``--background, -B``
    Launch in quiet daemon mode and fork to background.

``--currency, -C <CURRENCY>``
    Specify what currency to mine for.

``--dryrun, -D``
    Run script and generate *config.txt* without launching *xmr-stak*.

``--help``
    Print help.

``--kill, -K``
    Kill any instances of *xmr-stak*.

``--name, --pass <POOL PASSWORD>``
    Password used to identify miner on pool.  $HOSTNAME is used if nothing
    is specified.

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

Script requires system clock sync prior to launching xmr-stak to
ensure uptime status is calculated correctly.

Script requires processor to have AES support because, for some reason,
the new *xmr-stak* core dumps on me on CPUs without AES (on Arch Linux).

Any number of CryptoNight currencies may be specified in *xmr-mine.conf*
as long as a valid wallet and pool address are given there as well.

Multiple GPU configurations can be saved in *~/.xmr-mine*.  GPU configuration
is chosen based on device name and config filename.


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
