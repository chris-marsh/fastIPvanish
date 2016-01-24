fastIPvanish

USAGE

    fastIPvanish [-d] [-W] [-Wr] filter

DESCRIPTION

    fastIPvanish will ping the servers of IPVanish, returning the times
    and shows the fastest responding server. Optionally, a config file
    can be written to file and used to start an openvpn session.

OPTIONS

    -W    - write a vpn config to file
    -Wr   - write a vpn config file and start/restart openvpn
    -d    - output a vpn config
    -t    - specify a template file, default is ./vpn_template.tmpl
    -c    - specify an output config file, default is ./vpn_config.ovpn
    -h    - outputs this message

EXAMPLES

    fastIPvanish -Wr -d London
    fastIPvanish -d US
    fastIPvanish -Wr New-York
    fastIPvanish -W Amsterdam
