# check_apcpdu
nagios check for SNMP-enabled APC Power Distribution Units

Refer to embedded documentation in script for usage details

# Requirements
perl, snmpget on nagios server

# Configuration
You will need a section in the services.cfg file on the nagios server that looks similar to the following.
```
      # Define a service to check the APC PDU
      # Parameters are SNMP community name
      define service {
              use                             generic-service
              hostgroup_name                  all_apcpdu
              service_description             APC PDU
              check_command                   check_apcpdu!public
              }
```

You will also need a command definition similar to the following in commands.cfg on the nagios server
```
      # 'check_apcpdu' command definition
      # parameters are -H hostname -C snmp_community
      define command{
              command_name    check_apcpdu
              command_line    $USER1$/check_apcpdu -H $HOSTADDRESS$ -C $ARG1$
              }
```

# Sample Output

```
APC PDU OK - power_consumption:7.1amps max_log:15.0amps
```
