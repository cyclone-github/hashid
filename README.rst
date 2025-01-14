This is a forked version of hashid by c0re which has been updated by cyclone to include severa dozen more algos.

hashID \| hash-identifier
=========================

Identify the different types of hashes used to encrypt data and especially passwords.

This replaces `hash-identifier <http://code.google.com/p/hash-identifier/>`__, which
is outdated!

hashID is a tool written in Python 3 which supports the
identification of over 220+ unique hash types using regular expressions.

It is able to identify a single hash, parse a file or read multiple
files in a directory and identify the hashes within them.
hashID is also capable of including the corresponding
`hashcat <https://hashcat.net/oclhashcat/>`__ mode and/or
`JohnTheRipper <http://www.openwall.com/john/>`__ format in its output.

hashID works out of the box with Python 2 ≥ 2.7.x or Python 3 ≥ 3.3 on any platform.

*Note: When identifying a hash on *nix operating systems use single
quotes to prevent interpolation.*

Installation
------------

clone the repository:

.. code:: console

    $ git clone https://github.com/cyclone-github/hashID.git
    $ cd hashid

Usage
-----

.. code:: console

    $ ./hashid.py [-h] [-e] [-m] [-j] [-o FILE] [--version] INPUT

+---------------------------+-------------------------------------------------------+
| Parameter                 | Description                                           |
+===========================+=======================================================+
| INPUT                     | input to analyze (default: STDIN)                     |
+---------------------------+-------------------------------------------------------+
| -e, --extended            | list all hash algorithms including salted passwords   |
+---------------------------+-------------------------------------------------------+
| -m, --mode                | show corresponding hashcat mode in output             |
+---------------------------+-------------------------------------------------------+
| -j, --john                | show corresponding JohnTheRipper format in output     |
+---------------------------+-------------------------------------------------------+
| -o FILE, --outfile FILE   | write output to file (default: STDOUT)                |
+---------------------------+-------------------------------------------------------+
| --help                    | show help message and exit                            |
+---------------------------+-------------------------------------------------------+
| --version                 | show program's version number and exit                |
+---------------------------+-------------------------------------------------------+

Screenshot
----------

.. code:: console

    $ ./hashid.py '$P$8ohUJ.1sdFw09/bMaAQPTGDNi2BIUt1'
    Analyzing '$P$8ohUJ.1sdFw09/bMaAQPTGDNi2BIUt1'
    [+] Wordpress ≥ v2.6.2
    [+] Joomla ≥ v2.5.18
    [+] PHPass' Portable Hash

    $ ./hashid.py -mj '$racf$*AAAAAAAA*3c44ee7f409c9a9b'
    Analyzing '$racf$*AAAAAAAA*3c44ee7f409c9a9b'
    [+] RACF [Hashcat Mode: 8500][JtR Format: racf]

    $ ./hashid.py hashes.txt
    --File 'hashes.txt'--
    Analyzing '*85ADE5DDF71E348162894C71D73324C043838751'
    [+] MySQL5.x
    [+] MySQL4.1
    Analyzing '$2a$08$VPzNKPAY60FsAbnq.c.h5.XTCZtC1z.j3hnlDFGImN9FcpfR1QnLq'
    [+] Blowfish(OpenBSD)
    [+] Woltlab Burning Board 4.x
    [+] bcrypt
    --End of file 'hashes.txt'--

Resources
---------

-  http://psypanda.github.io/hashID/
-  http://pythonhosted.org/passlib/index.html
-  http://openwall.info/wiki/john
-  http://openwall.info/wiki/john/sample-hashes
-  http://hashcat.net/wiki/doku.php?id=example\_hashes
