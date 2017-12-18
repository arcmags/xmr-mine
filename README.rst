========
xmr-mine
========

Mine for Monero_ on Arch Linux!  In addition to the *xmr-mine* wrapper
script, this project contains Arch build files and pre-compiled binaries of xmr-stak_ in both CPU only and CPU + Nvidia versions. (and xmrig_)


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

``--config, -C``
    Use XMR_CONFIG (defined in script variables) file as *config.txt*.

``--cpu``
    Use XMR_CPU (defined in script variables) file as *cpu.txt*.

``--dryrun, -D``
    Run script and generate *config.txt* without launching *xmr-stak*.

``--gen-config, -G``
    Let *xmr-stak* generate a new *config.txt* file in DIR_MINE.
    Newly generated config files must be copied manually to XMR_CONFIG
    if future use is desired.

``--kill, -K``
    Kill any instances of *xmr-stak*.

``--nvidia, -N``
    Use XMR_NVIDIA (defined in script variables) file as *nvidia.txt*.

``--quiet, -Q``
    Launch *xmr-stak* in daemon mode.  Pipe all output to */dev/null*.

``--random-pool, -R``
    Randomize pool weights.

``--show-hash, -H``
    Print hash rate.

``--show-status, -S``
    Print current pool status and hash rate.

``--show-wallet, -W``
    Print XMR wallet address.

``--wallet, -w <XMR ADDRESS>``
    Specify xmr wallet to mine to.


Environment Variables
=====================

The default behavior of xmr-mine can may be affected by setting
optional environment variables.

``XMR_WALLET``
    Default wallet address mined to.

``XMR_POOL``
    Default xmr mining pool address and port number.  This is added
    to the list of pool address and given the highest weight.

``XMR_POOL_PASSWORD``
    Pool password to use for default pool XMR_POOL.  HOSTNAME is
    used if left unset.  Some pools are capable of monitoring
    individual miners identified by the pool password.

``XMR_CONFIG_DIRECTORY``
    Directory to save and source xmr-stak configuration files from.
    *~/.xmr-mine* is used by default if left unset.


Configuration Files
===================

All


Notes
=====

Script requires system clock sync prior to launching xmr-stak to
ensure uptime status is calculated correctly.

Script requires processor to have AES support because, for some reason,
the new *xmr-stak* core dumps on me on CPUs without AES (on Arch Linux).

*xmr-stak* may not generate the best (or even remotely decent) *nvidia.txt*
config for some GPUs.  Right now, only one possible *nvidia.txt* can be used
by the the script.  (Possible future implementation of multiple nvidia
configs selected by card type.)


Credits
=======

:Author:
    arcmags

:License:
    GPL 3.0



.. _Monero: https://getmonero.org/
.. _xmr-stak: https://github.com/fireice-uk/xmr-stak
.. _xmrig: https://github.com/xmrig/xmrig
.. _xmr-stak-git: https://aur.archlinux.org/packages/xmr-stak-git
