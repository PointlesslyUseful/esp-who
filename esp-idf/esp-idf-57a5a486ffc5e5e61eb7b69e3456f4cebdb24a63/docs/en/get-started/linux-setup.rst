*********************************************
Standard Setup of Toolchain for Linux
*********************************************

:link_to_translation:`zh_CN:[中文]`

Install Prerequisites
=====================

To compile with ESP-IDF you need to get the following packages:

- CentOS 7::

    sudo yum install git wget ncurses-devel flex bison gperf python cmake ninja-build ccache

- Ubuntu and Debian::

    sudo apt-get install git wget libncurses-dev flex bison gperf python python-pip python-setuptools cmake ninja-build ccache libffi-dev libssl-dev

- Arch::

    sudo pacman -S --needed gcc git make ncurses flex bison gperf python-pip cmake ninja ccache

.. note::
    CMake version 3.5 or newer is required for use with ESP-IDF. Older Linux distributions may require updating, enabling of a "backports" repository, or installing of a "cmake3" package rather than "cmake".

Additional Tips
===============

Permission issues /dev/ttyUSB0
------------------------------

With some Linux distributions you may get the ``Failed to open port /dev/ttyUSB0`` error message when flashing the ESP32. :ref:`This can be solved by adding the current user to the dialout group<linux-dialout-group>`.

Arch Linux Users
----------------

To run the precompiled gdb (xtensa-esp32-elf-gdb) in Arch Linux requires ncurses 5, but Arch uses ncurses 6.

Backwards compatibility libraries are available in AUR_ for native and lib32 configurations:

- https://aur.archlinux.org/packages/ncurses5-compat-libs/
- https://aur.archlinux.org/packages/lib32-ncurses5-compat-libs/

Before installing these packages you might need to add the author's public key to your keyring as described in the "Comments" section at the links above.

Alternatively, use crosstool-NG to compile a gdb that links against ncurses 6.

Setting up Python 3 as default for Ubuntu and Debian
----------------------------------------------------

Ubuntu and Debian are still providing Python 2.7 as the default interpreter. Python 3 can be installed as follows::

    sudo apt-get install python3 python3-pip python3-setuptools

Making Python 3 the default interpreter is possible by running::

    sudo update-alternatives --install /usr/bin/python python /usr/bin/python3 10

.. note::
    This is system-wide change which may affect all of the applications.

Next Steps
==========

To carry on with development environment setup, proceed to :ref:`get-started-get-esp-idf`.


Related Documents
=================

.. toctree::
    :maxdepth: 1

    linux-setup-scratch


.. _AUR: https://wiki.archlinux.org/index.php/Arch_User_Repository
