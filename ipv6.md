
# Freebox Revolution v6 - new to IPv6

My host is vanilla GNU/Linux **debian** jessie 8.6 (attow) and I'm using default v6 tools

via the **Freebox OS** console,
**Freebox Settings** page,
**Advanced** mode,
**IPv6 configuration** page,
**Activated**

I understand the box provides a **/61** addressing space which is way enough ( 8 subnets /64 )

[  I read a post somewhere related to a **/60** range but I can't confirm/infirm  ]

the subnets are `2A01:aaaa:bbbb:ccc[0-7]::/64` and explicit routing can be configured via the console

` FE80::aCaa:bbFF:FEcc:dddd `  is the Link-local address of the box ( EUI-64 ) from the inside

the ipv6 prefix of the box is `2A01:aaaa:bbbb:ccc0::/61`   for SLAAC as well as Global privacy addresses

the Global address of the box (ie gateway) is at `2A01:aaaa:bbbb:ccc0::1/61`

it responds to the icmpv6 **echo** from the inside on the Link-local and from the outside on Global (when authorized) [ ping6 ]

from the inside, the box serves **http** and **https** console on the Link-local address [ curl [-I] --interface http://[ip] ]

nginx : http 1.1 / is moved temporarily ( 302 ) and redirected to /login.php ( 200 )

SSL is configured for the box ( see below via Let's Encryt - freeboxos.fr ) but not authorized

**https** cannot be served from the numeric address ( certificate FQDN check ), didn't check via freeboxos.fr

ping / ping6 response time is variable almost to the freeboxbx ( from scaleway ~ 30ms ping / 33ms ping6 ) 

my host got 3 addresses via icmpv6 auto-configuration :

1. `FE80::aCaa:bbFF:FEcc:dddd` Link-Local ( EUI-64 )
1. `2A01:aaaa:bbbb:ccc0:aCaa:bbFF:FEcc:dddd` Global address ( SLAAC )
1. `2A01:aaaa:bbbb:ccc0:wwww:xxxx:yyyy:zzzz` Global address ( privacy )

from the outside the host is reachable via both Global addresses

from the outside the box is not reachable via its Global SLAAC

scaleway / iconfig.co / gestoip

tbc ... ip6tables
