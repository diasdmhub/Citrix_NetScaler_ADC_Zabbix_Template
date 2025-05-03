# Citrix NetScaler ADC Zabbix Template by SNMP

<div align="right">

[![License](https://img.shields.io/badge/License-GPL3-blue?logo=opensourceinitiative&logoColor=fff)][license]
[![Version](https://img.shields.io/badge/Version-726-blue?logo=zotero&color=0aa8d2)][latest_release]

</div>

<BR>

## OVERVIEW

[**Citrix NetScaler (ADC)**][netscaleradc] is an appliance that load balances access to internal or external applications.

Three NetScaler platforms are commonly used: `VPX`, `MPX` and `SDX`. The first, `VPX`, is virtual and can be deployed in many virtualized environments. It is useful for smaller environments and depends on the capacity and resources of the hypervisor in use. The `MPX` platform integrates software with Citrix hardware. In this case, the software is optimized for the specific hardware, which includes chips dedicated to SSL processing. `SDX`, on the other hand, is a virtualization _appliance_ (_XenServer_) for NetScaler itself, enabling high throughput and application access scaling.

To monitor this joint solution, this monitoring template allows you to quickly capture the key metrics of the load balancers in the environment. As the instances change, the monitoring is automatically updated. The metrics history also allows you to observe the behavior and trends of the key indicators.

<BR>

## TEMPLATES

For more flexibility, there are two independent templates that include two monitoring methods, one for passive data collection via SNMP and another for active SNMP _Trap_ capture. This way of organizing both methods simplifies the management of monitored items.

- ⬇️ [`Citrix ADC NetScaler by SNMP`](#template-citrix-adc-netscaler-by-snmp)
    - Focus on general NetScaler passive monitoring using SNMP
- ⬇️ [`Citrix ADC NetScaler Traps by SNMP`](#template-citrix-adc-netscaler-traps-by-snmp)
    - Focus on general NetScaler active monitoring using SNMP Traps

<BR>

## TESTED VERSION

> ⚠️ **This template has been customized for a specific production environment and stripped down for this publication. It may not meet the needs of other environments. It is recommended to customize the template to meet your specific needs. Feedback is welcome.**

Tested on Citrix (ADC) NetScaler `VPX` and `SDX` devices with version `13.1` and `14.1`.

- [Citrix NetScaler SNMP reference][snmpref]

<BR>

---
### ➡️ [Download (releases)][releases]
---
#### ➡️ [*How to import templates*][import_templates]
---
#### ➡️ [*SNMP Tables*][snmp_tables]
---

<BR>


## HOSTS DISCOVERY

Depending on the size of the environment, a Zabbix network discovery can help to add the load balancer hosts. Zabbix discovery rules are based on network ranges or IPs and can be executed on a schedule. For example, a network discovery can query SNMP objects on the active NetScaler IP range for scpecifc data. A discovery action then checks the discovery rule data and looks for the values received. If the  data matches the conditions, an operation is performed to automatically include the host. The host name can be the SNMP received value, DNS name, or IP, depending on how you configure your discovery rule. In addition, the above templates can be linked to the host to enable monitoring.

> ![many items](/image/net_discovery_rule_60.png)

> ℹ️ **Despite this initial host configuration, it is recommended to update the host information with a clear description so that it can be easily identified. It is also recommended that you populate the inventory data.**

> ⚠️ **Care should be taken when adding many hosts to Zabbix at once. If the environment is large enough, NetScaler services can easily impact on Zabbix processes, especially if the environment is not well optimized. If there are many hosts, a dedicated proxy can help to alleviate the load.**

> ![many items](/image/proxy_vps.png)

<BR>

## Template `Citrix ADC NetScaler by SNMP`

> **Focus on general NetScaler passive monitoring using SNMP**

### MACROS

| Macro                              | Default Value      | Description            |
| ---------------------------------- | :----------------: | ---------------------- |
| `{$NS.IF.CONTROL}`                 | `1`                | Link status trigger will be fired only for interfaces where the context macro equals 1 |
| `{$NS.IF.ADMINSTATUS.NOT_MATCHES}` | `^2$`              | Filters **out** network interfaces that matches this regex. Ignore interfaces with administrative status down (2) by default |
| `{$NS.IF.ALIAS.MATCHES}`           | `.*`               | Filters **only** network interface aliases that match this regex |
| `{$NS.IF.ALIAS.NOT_MATCHES}`       | `CHANGE_IF_NEEDED` | Filters **out** network interface aliases that match this regex |
| `{$NS.IF.DESCR.MATCHES}`           | `.*`               | Filters **only** network interface descriptions that match this regex |
| `{$NS.IF.DESCR.NOT_MATCHES}`       | `CHANGE_IF_NEEDED` | Filters **out** network interface descriptions that match this regex |
| `{$NS.IF.NAME.MATCHES}`            | `.*`               | Filters **only** network interface names that match this regex |
| `{$NS.IF.NAME.NOT_MATCHES}`        | `(^Software Loopback Interface\|^NULL[0-9.]*$\|^[Ll]o[0-9.]*$\|^[Ss]ystem$\|^Nu[0-9.]*$\|^veth[0-9a-z]+$\|docker[0-9]+\|br-[a-z0-9]{12})` | Filters **out** network interface names that match this regex. Filters out loopbacks, nulls, docker veth links and docker0 bridge by default |
| `{$NS.IF.OPERSTATUS.MATCHES}`      | `.*`               | Filters **only** network interfaces with operational status that match this regex |
| `{$NS.IF.OPERSTATUS.NOT_MATCHES}`  | `^6$`              | Filters **out** network interfaces with operational status that match this regex. Ignore status `notPresent (6)` by default |
| `{$NS.IF.TYPE.MATCHES}`            | `.*`               | Filters **only** network interface types that match this regex |
| `{$NS.IF.TYPE.NOT_MATCHES}`        | `CHANGE_IF_NEEDED` | Filters **out** network interface types that match this regex |
| `{$NS.IF.ERROR.WARN}`              | `10`               | Warning threshold of packet drops. Can be used with interface name as context |
| `{$NS.IF.UTIL.MAX}`                | `90`               | Interface threshold for bandwidth usage trigger. Can be used with interface name as context |
| `{$NS.SYS.CPU.CRIT}`               | `95`               | Critical threshold for high CPU utilization percentage |
| `{$NS.SYS.CPU.WARN}`               | `80`               | Warning threshold for high CPU utilization percentage |
| `{$NS.SYS.DISK.UTIL.WARN}`         | `90`               | Disk utilization warning threshold in percentage |
| `{$NS.SYS.MEM.CRIT}`               | `95`               | Critical threshold for high memory utilization percentage |
| `{$NS.SYS.MEM.WARN}`               | `80`               | Warning threshold for high memory utilization percentage |
| `{$NS.SYS.TEMP.WARN}`              | `65`               | Temperature warning threshold in degree Celsius |
| `{$NS.VSERVER.NAME.MATCHES}`       | `.*`               | Filters **out** and discovers **only** vServer names that match this regex |
| `{$NS.VSERVER.NAME.NOT_MATCHES}`   | `(?i)test`         | Filters **out** and **does not** discover vServer names that match this regex |
| `{$SNMP.TIMEOUT}`                  | `5m`               | SNMP connection timeout threshold |

<BR>

### ITEMS

| Name                              | Description |
| --------------------------------- | ----------- |
| NetScaler Walk HA                 | This walk item collects data about the High Availability feature in the Netscaler ADC |
| NetScaler Walk Network Interfaces | This walk item collects interface statistics data from standard SNMP IF-MIB |
| NetScaler Walk Resources          | This walk item collects data about the system resources in the NetScaler ADC |
| NetScaler Walk System Disk        | This walk item collects data about disks of the NetScaler ADC |
| NetScaler Walk System Health      | This walk item collects data about the system health status of the NetScaler ADC, including sensors and sometimes disks |
| NetScaler Walk System Information | This walk item collects standard SNMP MIB-2 data about the system |
| NetScaler Walk vServer Health     | This walk item collects health data of vServers |
| NetScaler Walk vServer Requests   | This walk item collects statistics data of vServers |
| CPU utilization                   | CPU utilization percentage |
| Memory total                      | Total amount of system memory in megabytes and converted to bytes |
| Memory utilization                | Memory utilization percentage |
| Number of active CPUs             | The number of active CPUs for the host |
| HA Current State                  | State of the HA node, based on its health, in a high availability setup |
| HA Current Status                 | Whether a Citrix ADC is configured for high availability. Possible values are `YES` and `NO` |
| HA Peer ID                        | The unique identifier to represent the failover peer Citrix ADC |
| HA Peer IP Address                | This represents the IP address for HA over IPv4 of the failover NetScaler ADC peer |
| HA Peer State                     | This represents the state of the failover NetScaler ADC peer. Whether it is Primary or Secondary |
| HA Time of Last State Transition  | This represents the time since the NetScaler ADC underwent a state change from `primary` to `secondary` or vice-versa |
| HA Total State Transitions        | Total number of master state changes that the Citrix ADC has made from primary to secondary and vice-versa |
| System Contact                    | The textual identification of the contact person for this managed node, together with information on how to contact this person |
| System Description                | This shows the version of the kernel build running on the NetScaler ADC |
| System HA Mode                    | This shows whether NetScaler ADC is in standalone mode or whether it is Primary or Secondary in case of failover mode |
| System Hardware Serial Number     | The serial number of the Citrix ADC system |
| System Location                   | The physical location of this node. If the location is unknown, the value is the zero-length string |
| System Model ID                   | The model ID is populated if the system is such that it is license controlled. If the system does not support license based models, then the model id will be zero |
| System Name                       | An administratively-assigned name for this managed node. By convention, this is the node's fully-qualified domain name. If the name is unknown, the value is the zero-length string |
| System Uptime                     | The time since the network management portion of the system was last re-initialized |
| SNMP Agent Availability           | Availability of SNMP checks on the host. The value of this item corresponds to availability icons in the host list |

<BR>

### TRIGGERS

| Name                        | Description |
| --------------------------- | ----------- |
| CPU Utilization Critical    | This trigger indicates that the CPU utilization is critical for the last 5 checks |
| CPU Utilization High        | This trigger indicates that the CPU utilization is high for the last 5 checks |
| Memory Utilization Critical | This trigger indicates that the CPU utilization is critical for the last 5 checks |
| Memory Utilization High     | This trigger indicates that the memory utilization is high for the last 5 checks |
| HA Mode Changed             | There has been an HA mode change on the host |
| Host has been restarted     | Uptime is less than 10 minutes |
| No SNMP data collection     | SNMP is not available for polling for the last `{$SNMP.TIMEOUT}`. Please check the device connectivity and SNMP settings |

<BR>

### ➡️ DISCOVERY RULE `Discovery Network interfaces`

> **Discovers NetScaler device interfaces from standard IF-MIB**

#### ITEM PROTOTYPES

| Name                                                                       | Description |
| -------------------------------------------------------------------------- | ----------- |
| Interface `{#NS.IF.NAME}`(`{#NS.IF.ALIAS}`) - Bits received                | The total number of octets **received** on the interface, including framing characters. Converted to bits |
| Interface `{#NS.IF.NAME}`(`{#NS.IF.ALIAS}`) - Bits sent                    | The total number of octets **transmitted** out of the interface, including framing characters. Converted to bits |
| Interface `{#NS.IF.NAME}`(`{#NS.IF.ALIAS}`) - Inbound Packets discarded    | The number of **inbound** packets that were discarded, even though no errors were detected to prevent them from being delivered to a higher-layer protocol |
| Interface `{#NS.IF.NAME}`(`{#NS.IF.ALIAS}`) - Outbound Packets discarded   | The number of **outbound** packets that were discarded, even though no errors were detected to prevent them from being delivered to a higher-layer protocol |
| Interface `{#NS.IF.NAME}`(`{#NS.IF.ALIAS}`) - Inbound Packets with errors  | The number of **inbound** packets that contained errors that prevented them from being delivered to a higher-layer protocol |
| Interface `{#NS.IF.NAME}`(`{#NS.IF.ALIAS}`) - Outbound Packets with errors | The number of **outbound** packets that failed to be transmitted due to errors |
| Interface `{#NS.IF.NAME}`(`{#NS.IF.ALIAS}`) - Speed                        | An estimate of the interfaces current bandwidth in units of 1000000 bits per second (Mbps). Converted to bits |
| Interface `{#NS.IF.NAME}`(`{#NS.IF.ALIAS}`) - Operational status           | The current operational state of the interface |

<BR>

#### TRIGGER PROTOTYPES

| Name                                                               | Description |
| ------------------------------------------------------------------ | ----------- |
| Interface `{#NS.IF.NAME}`(`{#NS.IF.ALIAS}`) - High bandwidth usage | Utilization of the network interface is close to its estimated maximum bandwidth |
| Interface `{#NS.IF.NAME}`(`{#NS.IF.ALIAS}`) - High error rate      | The network interface has a high error rate |
| Interface `{#NS.IF.NAME}`(`{#NS.IF.ALIAS}`) - Link down            | This trigger is true when the operations status is down, and the operational status was up to (1) sometime before, and macro `{$IFCONTROL:"{#IFNAME}"}` is set to `1` |

<BR>

### ➡️ DISCOVERY RULE `Discovery System Disk`

> **Discovers system partitions**

#### ITEM PROTOTYPES

| Name                                           | Description |
| ---------------------------------------------- | ----------- |
| Filesystem Available - `{#NS.SYS.DISK.NAME}`   | The "`{#NS.SYS.DISK.NAME}`" partition available space |
| Filesystem Size - `{#NS.SYS.DISK.NAME}`        | The "`{#NS.SYS.DISK.NAME}`" partition total size |
| Filesystem Used - `{#NS.SYS.DISK.NAME}`        | The "`{#NS.SYS.DISK.NAME}`" partition used space |
| Filesystem Utilization - `{#NS.SYS.DISK.NAME}` | The "`{#NS.SYS.DISK.NAME}`" partition utilization percentage |

<BR>

#### TRIGGER PROTOTYPES

| Name                                                | Description |
| --------------------------------------------------- | ----------- |
| High Filesystem Utilization - `{#NS.SYS.DISK.NAME}` | Indicates that the filesystem has a high utilization rate and is running out of free space |

<BR>

### ➡️ DISCOVERY RULE `Discovery System Health Fan`

> **Discovers system fans**

#### ITEM PROTOTYPES

| Name                        | Description |
| --------------------------- | ----------- |
| Fan `{#NS.SYS.HEALTH.NAME}` | The health counter value for the fan speed. The value will always be zero if the associated pin is not connected to the health monitoring chip |

<BR>

### ➡️ DISCOVERY RULE `Discovery System Health Temperature`

> **Discovers system temperature sensors**

#### ITEM PROTOTYPES

| Name                                | Description |
| ----------------------------------- | ----------- |
| Temperature `{#NS.SYS.HEALTH.NAME}` | The health counter value for the internal chip temperature sensor "`{#NS.SYS.HEALTH.NAME}`". The value will always be zero if the associated pin is not connected to the health monitoring chip |

<BR>

#### TRIGGER PROTOTYPES

| Name                                         | Description |
| -------------------------------------------- | ----------- |
| High Temperature for `{#NS.SYS.HEALTH.NAME}` | Indicates that the module has a high temperature |

<BR>

### ➡️ DISCOVERY RULE `Discovery System Health Voltage`

> **Discovers system voltage sensors**

#### ITEM PROTOTYPES

| Name                            | Description |
| ------------------------------- | ----------- |
| Voltage `{#NS.SYS.HEALTH.NAME}` | The health counter value for the voltage sensor "`{#NS.SYS.HEALTH.NAME}`". Some values will be zero if the associated pin is not connected to the health monitoring chip or component the component is absent |

<BR>

### ➡️ DISCOVERY RULE `Discovery vServer Health`

> **Discover vServer names for health data**

#### ITEM PROTOTYPES

| Name                                                     | Description |
| -------------------------------------------------------- | ----------- |
| `{#NS.VSERVER.FULL.NAME}` - vServer Health               | The percentage of UP services bound to this vServer |
| `{#NS.VSERVER.FULL.NAME}` - vServer IP                   | IP address of the vServer |
| `{#NS.VSERVER.FULL.NAME}` - vServer State                | vServer state |
| `{#NS.VSERVER.FULL.NAME}` - vServer Total Bound Services | The current number of services which are bound to this vServer |

<BR>

### ➡️ DISCOVERY RULE `Discovery vServer Requests`

> **Discovers vServer names for statistics data**

#### ITEM PROTOTYPES

| Name                                                               | Description |
| ------------------------------------------------------------------ | ----------- |
| `{#NS.VSERVER.FULL.NAME}` - vServer Client Established Connections | Number of client connections in established state |
| `{#NS.VSERVER.FULL.NAME}` - vServer Request Rate                   | Request rate in requests per second for this service or virtual server |
| `{#NS.VSERVER.FULL.NAME}` - vServer Request Rate in Bytes          | Request rate in bytes per second fot this service or virtual server |
| `{#NS.VSERVER.FULL.NAME}` - vServer Response Rate in Bytes         | Response rate in bytes per second for this service or virtual server |

<BR>

#### TRIGGER PROTOTYPES

| Name                                                     | Description |
| -------------------------------------------------------- | ----------- |
| `{#NS.VSERVER.FULL.NAME}` - vServer Connections Abnormal | (**Experimental - Set not to discover**) The trigger is true when the recent connections are multiple standard deviations from the baseline |

<BR>

## Template `Citrix ADC NetScaler Traps by SNMP`

> **Focus on general NetScaler active monitoring using SNMP Traps**

### ITEMS

| Name                                                       | Description |
| ---------------------------------------------------------- | ----------- |
| SNMP Trap Community Authentication Failure                 | The host sends this SNMP trap to indicate that the SNMP entity has received a protocol message that is not properly authenticated |
| SNMP Trap Community Authentication Failure Daily Count     | Number of daily `authenticationFailure` (`1.3.6.1.6.3.1.1.5.5`) traps received |
| SNMP Trap NetScaler Client Rate Limit Exceeded             | The host sends this SNMP trap when the client exceeds the ratelimit threshold |
| SNMP Trap NetScaler Client Rate Limit Exceeded Daily Count | Number of daily `rateLmtThresholdExceed` (`1.3.6.1.4.1.5951.1.1.0.77`) traps received |
| SNMP Trap NetScaler Login Failure                          | The host sends this SNMP trap when a login attempt to the NetScaler ADC fails |
| SNMP Trap NetScaler Login Failure Count                    | Number of daily `netScalerLoginFailure` (`1.3.6.1.4.1.5951.1.1.0.55`) traps received |

<BR>

### TRIGGERS

| Name                                 | Description |
| ------------------------------------ | ----------- |
| NetScaler Client Rate Limit Exceeded | This trigger is true when the NetScaler device sends an SNMP trap indicating that the rate limit threshold has been exceeded |
| NetScaler Login Failure              | This trigger is true when the NetScaler device sends an SNMP trap indicating that a login attempt failed |

[netscaleradc]: https://www.citrix.com/platform/netscaler/
[snmpref]: https://developer-docs.netscaler.com/en-us/adc-snmp-oid-reference
[releases]: https://github.com/diasdmhub/Citrix_NetScaler_ADC_Zabbix_Template/releases
[latest_release]: https://github.com/diasdmhub/Citrix_NetScaler_ADC_Zabbix_Template/releases/tag/latest
[import_templates]: https://www.zabbix.com/documentation/current/en/manual/xml_export_import/templates#importing
[license]: ./LICENSE
[snmp_tables]: ./snmp_tables.md