# snmp_agent_module
snmp agent module for snmpd server

Steps you must follow to create and add a MIB module to an SNMP agent.

1. Dependencies:

snmp
snmpd
snmp-mibs-downloader
libsnmp-dev
libsnmp-perl

2. Directories tree

snmp_agent_module/mibs
snmp_agent_module/src
snmp_agent_module/lib

3. MIB txt file

4. add our mib to /etc/snmp.conf

add our path to mibs dir

add to var mibdirs our mib path

and line
mibs +test-MIB

5. Generate c code

$ mib2c -c mib2c.scalar.conf sysTestGroup

edit generated files .c

10. modify snmpd.conf and add our module

dlmod sysTestGroup patho_to_our.so

reinit dnmpd:

$sudo service snmpd restart

$service snmpd status

11. try the module with:

snmpwalk -v2c -On -c  public localhost miEnterprise
snmpget -v2c -c public localhost sysInfoCurrentProcs.0
snmpset -v2c -c public localhost sysInfoCurrentProcs.0 i 4

References.

https://www.iana.org/assignments/ianaiftype-mib/ianaiftype-mib

SNMPv2-MIB.txt
http://www.net-snmp.org/docs/mibs/SNMPv2-MIB.txt

https://www.iana.org/assignments/enterprise-numbers

37267 tecnobit



