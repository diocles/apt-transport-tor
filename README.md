# apt-transport-tor

Easily install Debian packages via Tor.

This package implements an APT "acquire method" that handles URLs starting
with "tor://" in your sources.list.

## Installation

### Via apt

This package will soon be available in Debian:

    apt-get install apt-transport-tor

### From source

If you are working from a git checkout, first run:

    autoreconf -i

Then, or if installing from a tarball:

    ./configure --prefix=/usr
    make
    sudo make install

## Usage

Edit your /etc/apt/sources.list like so, adjusting the suite/components
appropriately for your system:

    deb     tor://http.debian.net/debian unstable main
    deb-src tor://http.debian.net/debian unstable main

Note the use of http.debian.net so that a mirror close to your exit node
will be automatically chosen.

Alternatively, if you have the Tor hidden service address of a Debian
mirror, you can use that:

    deb     tor://<long string>.onion/debian unstable main
    deb-src tor://<long string>.onion/debian unstable main

## Caveats

Downloading your Debian packages over Tor prevents an attacker who is
sniffing your network connection from being able to tell which packages
you are fetching, or even that your traffic is Debian-related.

However, this does not necessarily defend you from, amongst other things:

* a global passive adversary (who could potentially correlate the exit
  node's traffic with your local Tor traffic)
* an attacker looking at the size of your downloads, and making an
  educated guess about the contents
* an attacker who has broken into your machine

Download speeds will be slower via Tor.

## Copyright & Licensing

Copyright (C) 2014 Tim Retout <diocles@debian.org>

apt-transport-tor was forked from the APT https transport.  APT has this
copyright notice:

    Apt is copyright 1997, 1998, 1999 Jason Gunthorpe and others.

License:

    This program is free software; you can redistribute it and/or modify
    it under the terms of the GNU General Public License as published by
    the Free Software Foundation; either version 2 of the License, or
    (at your option) any later version.

    This program is distributed in the hope that it will be useful,
    but WITHOUT ANY WARRANTY; without even the implied warranty of
    MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the
    GNU General Public License for more details.

    You should have received a copy of the GNU General Public License
    along with this program; if not, write to the Free Software
    Foundation, Inc., 51 Franklin St, Fifth Floor, Boston, MA 02110-1301, USA.

## Feedback

Comments and suggestions to: Tim Retout <diocles@debian.org>

Bug reports should be sent to the Debian BTS.
