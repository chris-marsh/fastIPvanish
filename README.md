#fastIPvanish

USAGE

    fastIPvanish [-l] [-d] [-W] [-Wr] [-t file] [-c file] filter

DESCRIPTION

    Automatically find and connect to the fastest responding VPN server. 

    fastIPvanish will ping the VPN servers of IPVanish (https://www.ipvanish.com),
    returning the times and show the fastest responding server. Optionally, a
    config file can be written to file and used to start an openvpn session.

OPTIONS

    -l    - list the ping result from each server
    -W    - write a vpn config to file
    -Wr   - write a vpn config file and start/restart openvpn
    -d    - output a vpn config
    -t    - specify a template file, default is ./templates/default.tmpl
    -c    - specify an output config file, default is ./config.ovpn
    -h    - outputs this message

EXAMPLE 1

    $ ./fastIPvanish ZA
    Starting server pings ... waiting ...
    Best ping time was jnb-c02.ipvanish.com @ 195.959ms
    
EXAMPLE 2

    $ ./fastIPvanish -W Seattle
    Starting server pings ... waiting ...
    Best ping time was sea-a12.ipvanish.com @ 148.956ms
    Saving config file: /home/user/fastIPvanish/config.ovpn

EXAMPLE 3

    $ ./fastIPvanish -l -d Liverpool
    Starting server pings ... waiting ...

    Pinging lpl-c01.ipvanish.com : 29.485
    Pinging lpl-c02.ipvanish.com : 49.505
    Pinging lpl-c03.ipvanish.com : 43.210
    Pinging lpl-c04.ipvanish.com : 47.525
    Pinging lpl-c05.ipvanish.com : 39.772

    Best ping time was lpl-c01.ipvanish.com @ 29.485ms

    client
    dev tun
    proto udp
    remote lpl-c01.ipvanish.com 443
    resolv-retry infinite
    nobind
    persist-key
    persist-tun
    persist-remote-ip
    ca /home/user/fastIPvanish/etc/ca.ipvanish.com.crt
    remote-cert-tls server
    auth-nocache
    auth-user-pass /home/user/fastIPvanish/etc/login.conf
    comp-lzo
    verb 3
    auth SHA256
    cipher AES-256-CBC
    keysize 256
    tls-cipher TLS-DHE-RSA-WITH-AES-256-CBC-SHA

EXAMPLE 3

    $ ./fastIPvanish -d -Wr New-York -t ./templates/openelec.tmpl
    Starting server pings ... waiting ...
    Best ping time was nyc-a03.ipvanish.com @ 88.209ms

    client
    dev tun
    proto udp
    remote nyc-a04.ipvanish.com 1194
    resolv-retry infinite
    nobind
    persist-key
    persist-tun
    persist-remote-ip
    keepalive 10 120
    ca /home/user/fastIPvanish/etc/ca.ipvanish.com.crt
    remote-cert-tls server
    auth-nocache
    auth-user-pass /home/user/fastIPvanish/etc/login.conf
    comp-lzo
    verb 3
    auth SHA256
    cipher AES-256-CBC
    keysize 256
    tls-cipher TLS-DHE-RSA-WITH-AES-128-CBC-SHA

    Saving config file: /home/user/fastIPvanish/config.ovpn
    Stop any running openvpn process and start openvpn with new config? [Y/n] y
    [...]

##Installation

###Method 1 - Downloading with git

    $ git clone https://github.com/chris-marsh/fastIPvanish.git
    $ cd fastIPvanish

###Method 2 - Download the zip archive

    Download the archive from https://github.com/chris-marsh/fastIPvanish/archive/master.zip

    $ wget https://github.com/chris-marsh/fastIPvanish/archive/master.zip
    $ unzip ./master.zip
    $ mv ./fastIPvanish-master ./fastIPvanish
    $ cd ./fastIPvanish

###Configure the login with your IPVanish username and password

    $ cp ./etc/login.conf.example ./etc/login.conf

    Edit ./etc/login.conf and change 'USERNAME' and 'PASSWORD' to your actual details.
