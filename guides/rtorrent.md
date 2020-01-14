### Introduction

#### What is xmlrpc-c

http://xmlrpc-c.sourceforge.net/

XML-RPC is a quick-and-easy way to make procedure calls over the Internet. It converts the procedure call into an XML document, sends it to a remote server using HTTP, and gets back the response as XML.

#### What is rTorrent

The rTorrent bittorrent client uses ncurses and is ideal for use with tmux, screen or dtach. Alternatively, version 0.9.7+ has a built-in daemon mode disabling the user interface, so you can only control it via XMLRPC. It supports saving of sessions, allows the user to add/remove torrents, and much more.

### Installation using your distros package manager - optional.

#### Debian Stable and Ubuntu LTS versions

Please check these links to see which version will be installed and what version of the dependencies will be installed:

[Debian stable rTorrent version](https://packages.debian.org/buster/rtorrent)

[Ubuntu LTS rTorrent version](https://packages.ubuntu.com/bionic/rtorrent)

#### Installation

This is a simple and effective way to install `xmlrpc-c`, `libtorrent` and `rtorrent` but may mean you are limited to specific versions and features. You would do this for simplicity and for easier maintenance of the setup.

	apt install rtorrent

### Build from source

These commands will work on a clean install of Debian Stable or Ubuntu LTS (18.04) and install only the required components to complete this guide.

#### Prerequisites

Update and prepare your system:

	apt update && apt upgrade -y && apt autoremove -y

Install the required dependencies:

	apt install -y autoconf automake libtool pkg-config libssl-dev libcurl4-openssl-dev build-essential zlib1g-dev libcppunit-dev libncurses-dev libncurses5-dev libsigc++-2.0-dev

#### xmlrpc-c installation

Please use either the stable or advanced release for installation. Not both.

Stable version

	wget -qO ~/xmlrpc-c.tar.gz https://github.com/mirror/xmlrpc-c/archive/master.tar.gz
	tar -xf ~/xmlrpc-c.tar.gz -C ~/
	cd ~/xmlrpc-c-master/stable
	./configure --prefix=/usr/local --disable-wininet-client --disable-libwww-client --disable-abyss-server --disable-abyss-threads --disable-abyss-openssl --disable-cgi-server --disable-cplusplus
	make -j$(nproc)
	make install
	cd ~/ && rm -rf ~/xmlrpc-c{.tar.gz,-master} && ldconfig

Advanced version

	wget -qO ~/xmlrpc-c.tar.gz https://github.com/mirror/xmlrpc-c/archive/master.tar.gz
	tar -xf ~/xmlrpc-c.tar.gz -C ~/
	cd ~/xmlrpc-c-master/advanced
	./configure --prefix=/usr/local --disable-wininet-client --disable-libwww-client --disable-abyss-server --disable-abyss-threads --disable-abyss-openssl --disable-cgi-server --disable-cplusplus
	make -j$(nproc)
	make install
	cd ~/ && rm -rf ~/xmlrpc-c{.tar.gz,-master} && ldconfig

#### xmlrpc-c installation notes

Please use this link to see notes and extended information on the installation of this program for it's source code.

https://www.reddit.com/r/seedboxes/wiki/guides/xmlrpc-c_info

#### rtorrent and libtorrent stable github release

https://rakshasa.github.io/rtorrent/

This is to install the current stable rtorrent and libtorrent version. Copy and paste these commands to install libtorrent

Libtorrent

    wget -qO ~/libtorrent.tar.gz http://rtorrent.net/downloads/libtorrent-0.13.6.tar.gz
    tar xf ~/libtorrent.tar.gz
    cd ~/$(tar tf ~/libtorrent.tar.gz | head -1 | cut -f1 -d"/")
    ./configure --prefix=/usr/local --disable-debug --with-posix-fallocate
    make -j$(nproc)
    make install
    cd ~/ && rm -rf ~/libtorrent{.tar.gz,-$(tar tf ~/libtorrent.tar.gz | grep -om1 "0.*[^/]")} && ldconfig
    echo -e "Installation complete\n"

rtorrent

    wget -qO ~/rtorrent.tar.gz http://rtorrent.net/downloads/rtorrent-0.9.6.tar.gz
    tar xf ~/rtorrent.tar.gz
    cd ~/$(tar tf ~/rtorrent.tar.gz | head -1 | cut -f1 -d"/")
    ./configure --prefix=/usr/local --disable-debug --with-xmlrpc-c
    make -j$(nproc)
    make install
    cd ~/ && rm -rf ~/rtorrent{.tar.gz,-$(tar tf ~/rtorrent.tar.gz | grep -om1 "0.*[^/]")} && ldconfig
    echo -e "Installation complete\n"

#### rtorrent and libtorrent latest github release

This is to install the latest rtorrent and libtorrent release version. Copy and paste these commands to install libtorrent

Libtorrent

    wget -qO ~/libtorrent.tar.gz "$(curl -sNL https://git.io/JeyDk | grep -Po 'ht(.*)libtorrent-(.*)gz')"
    tar xf ~/libtorrent.tar.gz
    cd ~/$(tar tf ~/libtorrent.tar.gz | head -1 | cut -f1 -d"/")
    ./configure --prefix=/usr/local --disable-debug --with-posix-fallocate
    make -j$(nproc)
    make install
    cd ~/ && rm -rf ~/libtorrent{.tar.gz,-$(tar tf ~/libtorrent.tar.gz | grep -om1 "0.*[^/]")} && ldconfig
    echo -e "Installation complete\n"

rtorrent

    wget -qO ~/rtorrent.tar.gz "$(curl -sNL https://git.io/JeyDk | grep -Po 'ht(.*)rtorrent-(.*)gz')"
    tar xf ~/rtorrent.tar.gz
    cd ~/$(tar tf ~/rtorrent.tar.gz | head -1 | cut -f1 -d"/")
    ./configure --prefix=/usr/local --disable-debug --with-xmlrpc-c
    make -j$(nproc)
    make install
    cd ~/ && rm -rf ~/rtorrent{.tar.gz,-$(tar tf ~/rtorrent.tar.gz | grep -om1 "0.*[^/]")} && ldconfig
    echo -e "Installation complete\n"

#### rtorrent and libtorrent (github master branch)

This is to install rtorrent and libtorrent from the github master branch. Copy and paste these commands to install libtorrent

    wget -qO ~/libtorrent.tar.gz https://github.com/rakshasa/libtorrent/archive/master.tar.gz
    tar -xf ~/libtorrent.tar.gz -C ~/
    cd ~/libtorrent-master && ./autogen.sh
    ./configure --prefix=/usr/local --disable-debug --with-posix-fallocate
    make -j$(nproc)
    make install
    cd ~/ && rm -rf ~/libtorrent{.tar.gz,-master} && ldconfig
    echo -e "Installation complete\n"

Copy and paste these commands to install rtorrent

    wget -qO ~/rtorrent.tar.gz https://github.com/rakshasa/rtorrent/archive/master.tar.gz
    tar -xf ~/rtorrent.tar.gz -C ~/
    cd ~/rtorrent-master && ./autogen.sh
    ./configure --prefix=/usr/local --disable-debug --with-xmlrpc-c
    make -j$(nproc)
    make install
    cd ~/ && rm -rf ~/rtorrent{.tar.gz,-master} && ldconfig
    echo -e "Installation complete\n"

#### rtorrent and libtorrent other (older) versions

Installation of these won't be specifically supported here but you can use this link to find URLs to the required releases you need.

http://rtorrent.net/downloads/

#### libtorrent installation notes

https://www.reddit.com/r/seedboxes/wiki/guides/libtorrent_info

#### rtorrent installation notes

https://www.reddit.com/r/seedboxes/wiki/guides/rtorrent_info