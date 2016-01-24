#fastIPvanish

USAGE

    fastIPvanish [-d] [-W] [-Wr] [t] file [c] file filter

DESCRIPTION

    fastIPvanish will ping the servers of IPVanish, returning the times
    and shows the fastest responding server. Optionally, a config file
    can be written to file and used to start an openvpn session.

OPTIONS

    -W    - write a vpn config to file
    -Wr   - write a vpn config file and start/restart openvpn
    -d    - output a vpn config
    -t    - specify a template file, default is ./templates/default.tmpl
    -c    - specify an output config file, default is ./config.ovpn
    -h    - outputs this message

EXAMPLES

    fastIPvanish -Wr -d London
    fastIPvanish -d US
    fastIPvanish -Wr New-York
    fastIPvanish -W Amsterdam
    
    [fastIPvanish] $ ./fastIPvanish -d London
    Pinging lcy-c01.ipvanish.com ... 34.040
    Pinging lcy-c02.ipvanish.com ... 27.190
    Pinging lon-a01.ipvanish.com ... 20.880
    Pinging lon-a02.ipvanish.com ... 22.247
    Pinging lon-a03.ipvanish.com ... 15.493
    Pinging lon-a04.ipvanish.com ... 15.537
    [...]
    Pinging lon-c01.ipvanish.com ... 71.098
    Pinging lon-c02.ipvanish.com ... 60.764

    Best ping time was lon-a03.ipvanish.com @ 15ms
    
    client
    dev tun
    proto udp
    remote lon-a03.ipvanish.com 443
    resolv-retry infinite
    nobind
    persist-key
    keepalive 10 120
    persist-remote-ip
    ca ./ca.ipvanish.com.crt
    tls-remote lon-a03.ipvanish.com
    auth-user-pass ./pass.txt
    verb 3
    comp-lzo
    auth SHA256
    cipher AES-256-CBC
    keysize 256
    tls-cipher TLS-DHE-RSA-WITH-AES-128-CBC-SHA
