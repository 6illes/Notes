
# Freebox Revolution v6 - new to IPv6

My host is vanilla GNU/Linux **debian** jessie 8.6 (attow) and I'm using default v6 tools

I understand the freebox provides a **/61** address space    ( 8 /64 ranges )

[  I read information related to a **/60** but I can't confirm/infirm  ]

via the **Freebox OS** console,
**Freebox Settings** page,
**Advanced** mode,
**IPv6 configuration** page,
**Activated**

` FE80::aCaa:bbFF:FEcc:dddd `  Link-local address of the freebox ( SLAAC )

SSL is configured for my freebox ( see below via Let's Encryt )

from the inside the freebox serves **http** and **https** console on the LL FE80::... address

nginx : http 1.1 / is moved temporarily ( 302 ) and redirected to /login.php ( 200 )

**https** cannot be served via the numeric address ( certificate FQDN check )

the ipv6 prefix of my freebox is `2A01:aaaa:bbbb:ccc0::/61`

the gateway (ie the freebox) at `2A01:aaaa:bbbb:ccc0::1/61` responds to the icmpv6 echo

the freebox responds also on the out interface via the Link-Local address ( SLAAC )

the 8 subnets are `2A01:aaaa:bbbb:ccc[0-7]::/64` and the console interface allows to route each of those

ping / ping6 response time is variable almost to the freeboxbx ( from scaleway ~ 30ms ping / 33ms ping6 ) 

my host got 3 addresses via icmpv6 auto-configuration :

1. `FE80::aCaa:bbFF:FEcc:dddd` Link-Local
1. `2A01:aaaa:bbbb:ccc0:aCaa:bbFF:FEcc:dddd` Global address ( SLAAC )
1. `2A01:aaaa:bbbb:ccc0:wwww:xxxx:yyyy:zzzz` Global address ( privacy )

thx scaleway iconfig.co and gestoip

tbc ... ip6tables


