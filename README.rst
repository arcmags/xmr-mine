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

A valid machine lookup name must be specified by MINER_NAME in order
to correctly display miner stats.

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

``-B, --background``
    Launch in quiet daemon mode and fork to background.

``-C, --config``
    Use XMR_CONFIG (defined in script variables) file as *config.txt*.

``--cpu``
    Use XMR_CPU (defined in script variables) file as *cpu.txt*.

``-D, --dryrun``
    Run script and generate *config.txt* without launching *xmr-stak*.

``-G, --gen-config, --generate-config``
    Let *xmr-stak* generate a new *config.txt* file in DIR_MINE.
    Newly generated config files must be copied manually to XMR_CONFIG
    if future use is desired.

``-H, --hash``
    Print hash rate.

``-I, --incognito``
    Launch *xmr-stak* in daemon mode piping all output to */dev/null*.

``-K, --kill``
    Kill any instances of *xmr-stak*.

``-N, --nvidia``
    Use XMR_NVIDIA (defined in script variables) file as *nvidia.txt*.

``-R, --random-pool, --random-weight``
    Randomize pool weights.

``-S, --status``
    Print current pool status and hash rate.

``-W, --wallet``
    Print XMR wallet address.


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
