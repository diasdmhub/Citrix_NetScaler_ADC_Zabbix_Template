# SNMP Tables

> [**From Citrix NetScaler SNMP reference**](https://developer-docs.netscaler.com/en-us/adc-snmp-oid-reference)

### System

> **`system` - `1.3.6.1.2.1.1` - This provides standard SNMP MIB-2 information about the system.**

| Monitoring | OID                 | MIB Name    | Macro | Description |
| :--------: | ------------------- | ----------- | ----- | ----------- |
|            | **1.3.6.1.2.1.1.1** | sysDescr    |       | A textual description of the entity. This value should include the full name and version identification ofthe system's hardware type, software operating-system, and networking software. |
|            | **1.3.6.1.2.1.1.2** | sysObjectID |       | The vendor's authoritative identification of the network management subsystem contained in the entity. This value is allocated within the SMI enterprises subtree (1.3.6.1.4.1) and provides an easy and unambiguous means for determining what kind of box is being managed. |
| ✅         | **1.3.6.1.2.1.1.3** | sysUpTime   |       | The time (in hundredths of a second) since the network management portion of the system was last re-initialized. |
| ✅         | **1.3.6.1.2.1.1.4** | sysContact  |       | The textual identification of the contact person for this managed node, together with information on how to contact this person. If no contact information is known, the value is the zero-length string. |
| ✅         | **1.3.6.1.2.1.1.5** | sysName     |       | An administratively-assigned name for this managed node. By convention, this is the node's fully-qualified domain name. If the name is unknown, the value is the zero-length string. |
| ✅         | **1.3.6.1.2.1.1.6** | sysLocation |       | The physical location of this node (e.g., 'telephone closet, 3rd floor'). If the location is unknown, the value is the zero-length string. |
|            | **1.3.6.1.2.1.1.7** | sysServices |       | A value which indicates the set of services that this entity may potentially offer. The value is a sum. This sum initially takes the value zero. Then, foreach layer L, in the range 1 through 7, that this node performs transactions for, 2 raised to (L - 1) is added to the sum. For example, a node which performs only routing functions would have a value of 4 (2^(3-1)). In contrast, a node which is a host offering application services would have a value of 72 (2^(4-1) + 2^(7-1)). Note that in the context of the Internet suite of protocols, values should be calculated accordingly: layer functionality1 physical (e.g., repeaters) 2 datalink/subnetwork (e.g., bridges) 3 internet (e.g., supports the IP) 4 end-to-end (e.g., supports the TCP) 7 applications (e.g., supports the SMTP). For systems including OSI protocols, layers 5 and 6 may also be counted. |

> **`nsSysGroup` - `1.3.6.1.4.1.5951.4.1.1` - This provides information about the system properties of Netscaler product.**

| Monitoring | OID                           | MIB Name                       | Macro | Description |
| :--------: | ----------------------------  | ------------------------------ | ----- | ----------- |
| ✅         | **1.3.6.1.4.1.5951.4.1.1.1**  | sysBuildVersion                |       | This shows the version of the kernel build running on the Citrix ADC. |
|            | **1.3.6.1.4.1.5951.4.1.1.2**  | sysIpAddress                   |       | This shows the configured IP address of the Citrix ADC. |
|            | **1.3.6.1.4.1.5951.4.1.1.3**  | sysNetmask                     |       | This shows the configured sub-net mask of the Citrix ADC. |
| ✅         | **1.3.6.1.4.1.5951.4.1.1.6**  | sysHighAvailabilityMode        |       | This shows whether Citrix ADC is in standalone mode or whether it is primary or secondary in case of failover mode. |
|            | **1.3.6.1.4.1.5951.4.1.1.7**  | sysGateway                     |       | This represents the default gateway configured on the Citrix ADC. |
|            | **1.3.6.1.4.1.5951.4.1.1.8**  | sysCurMappedIpCount            |       | This represents the number of Mapped IPs currently configured on the Citrix ADC system. |
|            | **1.3.6.1.4.1.5951.4.1.1.9**  | sysCustomID                    |       | Configurable Identifier for the system. |
|            | **1.3.6.1.4.1.5951.4.1.1.10** | sysHardwareVersionId           |       | The hardware version ID of the Citrix ADC system. |
|            | **1.3.6.1.4.1.5951.4.1.1.11** | sysHardwareVersionDesc         |       | The hardware version description of the Citrix ADC system. |
|            | **1.3.6.1.4.1.5951.4.1.1.12** | sysTotConfigChanges            |       | The number of times a configuration change was made on the Citrix ADC. |
|            | **1.3.6.1.4.1.5951.4.1.1.13** | sysTotSaveConfigs              |       | Number of times the system configuration was saved on the Citrix ADC. |
| ✅         | **1.3.6.1.4.1.5951.4.1.1.14** | sysHardwareSerialNumber        |       | The serial number of the Citrix ADC system. |
|            | **1.3.6.1.4.1.5951.4.1.1.15** | sysHardwareEncodedSerialNumber |       | The encoded serial no of the Citrix ADC system. |
| ✅         | **1.3.6.1.4.1.5951.4.1.1.16** | sysModelId                     |       | The model ID is populated if the system is such that it is license controlled. If the system does not support license based models, then the model id will be zero. |

> **`nsFeatureInfo` - `1.3.6.1.4.1.5951.4.1.1.20` - This provides information about the various features in the Netscaler product.**

> **`nsModeInfo` - `1.3.6.1.4.1.5951.4.1.1.21` - This provides information about the mode a certain feature is in, in the Netscaler product.**

> **`aclStatsGroup` - `1.3.6.1.4.1.5951.4.1.1.22.1` - This provides statistical information about the configured ACLs in the Netscaler product.**

> **`saclStatsGroup` - `1.3.6.1.4.1.5951.4.1.1.22.3` - This provides statistical information about the configured SimpleACLs in the Netscaler product.**

> **`acl6StatsGroup` - `1.3.6.1.4.1.5951.4.1.1.22.4` - This provides statistical information about the configured ACLs6 in the Netscaler product.**

> **`pbrStatsGroup` - `1.3.6.1.4.1.5951.4.1.1.22.5` - This provides statistical information about the configured PBRs in the Netscaler product.**

> **`sacl6StatsGroup` - `1.3.6.1.4.1.5951.4.1.1.22.6` - This provides statistical information about the configured SimpleACL6s in the Netscaler product.**

> **`pbr6StatsGroup` - `1.3.6.1.4.1.5951.4.1.1.22.7` - This provides statistical information about the configured PBR6s, in the rs9000 product family of Citrix ADC**

### HA

> **`nsHighAvailabilityGroup` - `1.3.6.1.4.1.5951.4.1.1.23` - This provides information about the High Availability feature in the Netscaler product.**

| Monitoring | OID                              | MIB Name                          | Macro | Description |
| ---------- | -------------------------------- | --------------------------------- | ----- | ----------- |
| ✅         | **1.3.6.1.4.1.5951.4.1.1.23.1**  | haPeerId                          |       | The unique identifier to represent the failover peer Citrix ADC |
| ✅         | **1.3.6.1.4.1.5951.4.1.1.23.2**  | haPeerIpAddress                   |       | This represents the ipaddress of the failover peer Citrix ADC(Only for HA over IPv4). For HA over IPv6 (as well as IPv4) haPeerInetAddr will contain this information |
| ✅         | **1.3.6.1.4.1.5951.4.1.1.23.3**  | haPeerState                       |       | This represents the state of the failover peer Citrix ADC whether Primary or Secondary |
| ✅         | **1.3.6.1.4.1.5951.4.1.1.23.4**  | haTotStateTransitions             |       | Total number of master state changes that the Citrix ADC has made from primary to secondary and vice-versa |
| ✅         | **1.3.6.1.4.1.5951.4.1.1.23.5**  | haTimeofLastStateTransition       |       | This represents the time since the Citrix ADC underwent a state change from primary to secondary or vice-versa |
|            | **1.3.6.1.4.1.5951.4.1.1.23.6**  | haTotStateFail                    |       | Number of times state changed to PARTIAL_FAIL/PARTIAL_FAIL_SSL/ROUTEMONITOR_FAIL/COMPLETE_FAIL |
|            | **1.3.6.1.4.1.5951.4.1.1.23.7**  | haErrSyncFailure                  |       | Number of times the configuration of the primary and secondary nodes failed to synchronize since that last transition. A synchronization failure results in mismatched configuration. It can be caused by a mismatch in the Remote Procedural Call (RPC) password on the two nodes forming the high availability pair. |
|            | **1.3.6.1.4.1.5951.4.1.1.23.8**  | haErrTotNodeDown                  |       | Total number of heart-beats missed while the peer node was DOWN. |
|            | **1.3.6.1.4.1.5951.4.1.1.23.9**  | haErrPropMemFail                  |       | Total number of times memory allocation failed during command propagation. |
|            | **1.3.6.1.4.1.5951.4.1.1.23.10** | haErrNsbMemFail                   |       | Total number of times memory allocation failed while sending heartbeats. |
|            | **1.3.6.1.4.1.5951.4.1.1.23.11** | haErrPortSilent                   |       | Total number of times heartbeat packets were not received on any enabled interface for the duration of the Dead Interval |
|            | **1.3.6.1.4.1.5951.4.1.1.23.12** | haTotTimerRecoveries              |       | Total number of times HA engine recovered from tight loops. (i.e., Total number of times HA timers are not called for MAX down time). |
|            | **1.3.6.1.4.1.5951.4.1.1.23.14** | haNicsMonitorFailed               |       | Interfaces on which HA heartbeats are not being seen |
|            | **1.3.6.1.4.1.5951.4.1.1.23.15** | haLastMasterStateTransitionReason |       | The reason for the last master state transition. This gives the conditions under which this node assumed the current state. The current state is available at the oid sysHighAvailabilityMode.0 |
|            | **1.3.6.1.4.1.5951.4.1.1.23.17** | haErrPropTimeout                  |       | Number of times propagation timed out. |
|            | **1.3.6.1.4.1.5951.4.1.1.23.18** | haCurDerivedInc                   |       | Derived incarnation based on IOCTLs received |
|            | **1.3.6.1.4.1.5951.4.1.1.23.19** | haCurPeerInc                      |       | The peer’s incarnation as seen from heartbeats |
|            | **1.3.6.1.4.1.5951.4.1.1.23.20** | haErrMasterDispute                |       | Number of HA master disputes |
|            | **1.3.6.1.4.1.5951.4.1.1.23.21** | haTotPktTx                        |       | Number of heartbeat packets sent to the peer node. Heartbeats are sent at regular intervals (default is 200 milliseconds) to determine the state of the peer node. |
|            | **1.3.6.1.4.1.5951.4.1.1.23.22** | haTotPktRx                        |       | Number of heartbeat packets received from the peer node. Heartbeats are sent at regular intervals (default is 200 milliseconds) to determine the state of the peer node |
| ✅         | **1.3.6.1.4.1.5951.4.1.1.23.23** | haCurStatus                       |       | Whether a Citrix ADC is configured for high availability. Possible values are YES and NO. If the value is NO, the high availability statistics below are invalid |
| ✅         | **1.3.6.1.4.1.5951.4.1.1.23.24** | haCurState                        |       | State of the HA node, based on its health, in a high availability setup. Possible values are:<br>UP - Indicates that the node is accessible and can function as either a primary or secondary node.<br>DISABLED - Indicates that the high availability status of the node has been manually disabled. Synchronization and propagation cannot take place between the peer nodes.<br>INIT - Indicates that the node is in the process of becoming part of the high availability configuration.<br>PARTIALFAIL - Indicates that one of the high availability monitored interfaces has failed because of a card or link failure. This state triggers a failover.<br>COMPLETEFAIL - Indicates that all the interfaces of the node are unusable, because the interfaces on which high availability monitoring is enabled are not connected or are manually disabled. This state triggers a failover.<br>DUMB - Indicates that the node is in listening mode. It does not participate in high availability transitions or transfer configuration from the peer node. This is a configured value, not a statistic.<br>PARTIALFAILSSL - Indicates that the SSL card has failed. This state triggers a failover.<br>ROUTEMONITORFAIL - Indicates that the route monitor has failed. This state triggers a failover. |
|            | **1.3.6.1.4.1.5951.4.1.1.23.25** | haPeerInetAddrType                |       | The address type of haPeerInetAddr |
|            | **1.3.6.1.4.1.5951.4.1.1.23.26** | haPeerInetAddr                    |       | This represents the Internet Address of the failover peer Citrix ADC |

### Resources

> **`nsResourceGroup` - `1.3.6.1.4.1.5951.4.1.1.41` - This provides information about system resources in the Netscaler product.**

| Monitoring | OID                             | MIB Name    | Macro | Description |
| :--------: | ------------------------------- | ----------- | ----- | ----------- |
| ✅         | **1.3.6.1.4.1.5951.4.1.1.41.1** | resCpuUsage |       | CPU utilization percentage |
| ✅         | **1.3.6.1.4.1.5951.4.1.1.41.2** | resMemUsage |       | Percentage of memory utilization on Citrix ADC |
| ✅         | **1.3.6.1.4.1.5951.4.1.1.41.3** | numCPUs     |       | The number of active CPUs |
| ✅         | **1.3.6.1.4.1.5951.4.1.1.41.4** | memSizeMB   |       | Total amount of system memory, in megabytes |
|            | **1.3.6.1.4.1.5951.4.1.1.41.5** | numSSLCards |       | Number of SSL Cards on the system |

### CPU Resources

> **`nsCPUTable` - `1.3.6.1.4.1.5951.4.1.1.41.6` - This table contains information about each CPU in Citrix ADC.**

| Monitoring | OID                                  | MIB Name   | Macro | Description |
| :--------: | ------------------------------------ | ---------- | ----- | ----------- |
| ✅         | **1.3.6.1.4.1.5951.4.1.1.41.6.1.1**  | nsCPUname  |       | The name of the CPU |
| ✅         | **1.3.6.1.4.1.5951.4.1.1.41.6.1.2**  | nsCPUusage |       | CPU utilization percentage |

### System Health

> **`nsSysHealthTable` - `1.3.6.1.4.1.5951.4.1.1.41.7` - This table contains information about the System Health status of the Citrix ADC, such as voltage, fan and temperature**

| Monitoring | OID                                  | MIB Name              | Macro | Description |
| :--------: | ------------------------------------ | --------------------- | ----- | ----------- |
| ✅         | **1.3.6.1.4.1.5951.4.1.1.41.7.1.1**  | sysHealthCounterName  |       | This is the health counter name. |
| ✅         | **1.3.6.1.4.1.5951.4.1.1.41.7.1.2**  | sysHealthCounterValue |       | The health counters value. The units are ‘mv’, RPM and degrees Celsius for voltage, fan and temperatures respectively. |

### System Health Disk

> **`nsSysHealthDiskTable` - `1.3.6.1.4.1.5951.4.1.1.41.8` - This table contains information about the disk space of the Citrix ADC**

| Monitoring | OID                                  | MIB Name             | Macro | Description |
| :--------: | ------------------------------------ | -------------------- | ----- | ----------- |
| ✅         | **1.3.6.1.4.1.5951.4.1.1.41.8.1.1** | sysHealthDiskName     |       | The disk name. Disk name always starts with the "disk" keyword. Eg: disk0, disk1. Currently disk0 is mapped to "/flash" and disk1 mapped to "/var" partitions. |
| ✅         | **1.3.6.1.4.1.5951.4.1.1.41.8.1.2** | sysHealthDiskSize     |       | The total disk space in MBytes (includes available and used spaces also). |
| ✅         | **1.3.6.1.4.1.5951.4.1.1.41.8.1.3** | sysHealthDiskAvail    |       | The total disk space available in MBytes. |
| ✅         | **1.3.6.1.4.1.5951.4.1.1.41.8.1.4** | sysHealthDiskUsed     |       | The total disk space used in MBytes.	 |
| ✅         | **1.3.6.1.4.1.5951.4.1.1.41.8.1.5** | sysHealthDiskPerusage |       | The Percentage of the disk space used. |

### File system

> **`nsSysHealthDiskTable` - `1.3.6.1.4.1.5951.4.1.1.41.8` - This table contains information about the disk space of the Citrix ADC**

| Monitoring | OID                                 | MIB Name              | Macro | Description |
| :--------: | ----------------------------------- | --------------------- | ----- | ----------- |
| ✅         | **1.3.6.1.4.1.5951.4.1.1.41.8.1.1** | sysHealthDiskName     |       | The disk name. Disk name always starts with the ‘disk’ keyword. Eg: disk0, disk1. Currently disk0 is mapped to /flash and disk1 mapped to /var partitions. |
| ✅         | **1.3.6.1.4.1.5951.4.1.1.41.8.1.2** | sysHealthDiskSize     |       | The total disk space in MBytes (includes available and used spaces also) |
| ✅         | **1.3.6.1.4.1.5951.4.1.1.41.8.1.3** | sysHealthDiskAvail    |       | The total disk space available in MBytes. |
| ✅         | **1.3.6.1.4.1.5951.4.1.1.41.8.1.4** | sysHealthDiskUsed     |       | The total disk space used in MBytes. |
| ✅         | **1.3.6.1.4.1.5951.4.1.1.41.8.1.5** | sysHealthDiskPerusage |       | The Percentage of the disk space used. |

### Interfaces

> **`nsIfStatsTable` - `1.3.6.1.4.1.5951.4.1.1.54` - The interface related statistics Table.**

| Monitoring | OID                                | MIB Name                     | Macro | Description |
| :--------: | ---------------------------------- | ---------------------------- | ----- | ----------- |
|            | **1.3.6.1.4.1.5951.4.1.1.54.1.1**  | ifName                       |       | The name of the interface. |
|            | **1.3.6.1.4.1.5951.4.1.1.54.1.2**  | ifMedia                      |       | The media type of the interface. |
|            | **1.3.6.1.4.1.5951.4.1.1.54.1.3**  | ifTotRxBytes                 |       | Number of bytes received by an interface since the Citrix ADC was started or the interface statistics were cleared. |
|            | **1.3.6.1.4.1.5951.4.1.1.54.1.4**  | ifRxAvgBandwidthUsage        |       | The average bandwidth, in bits per second, at which the specified interface has been receiving packets since the Citrix ADC was started or the interface statistics were cleared. |
|            | **1.3.6.1.4.1.5951.4.1.1.54.1.5**  | ifTotRxPkts                  |       | Number of packets received by an interface since the Citrix ADC was started or the interface statistics were cleared. |
|            | **1.3.6.1.4.1.5951.4.1.1.54.1.6**  | ifRxAvgPacketRate            |       | Average rate, in packets per second, of incoming packets on the specified interface since the Citrix ADC was started or the interface statistics were cleared. |
|            | **1.3.6.1.4.1.5951.4.1.1.54.1.7**  | ifTotTxBytes                 |       | Number of bytes transmitted by an interface since the Citrix ADC was started or the interface statistics were cleared. |
|            | **1.3.6.1.4.1.5951.4.1.1.54.1.8**  | ifTxAvgBandwidthUsage        |       | The average bandwidth, in bits per second, at which the specified interface has been transmitting packets since the Citrix ADC was started or the interface statistics were cleared. |
|            | **1.3.6.1.4.1.5951.4.1.1.54.1.9**  | ifTotTxPkts                  |       | Number of packets transmitted by an interface since the Citrix ADC was started or the interface statistics were cleared. |
|            | **1.3.6.1.4.1.5951.4.1.1.54.1.10** | ifTxAvgPacketRate            |       | Average rate, in packets per second, of outgoing packets on the specified interface since the Citrix ADC was started or the interface statistics were cleared. |
|            | **1.3.6.1.4.1.5951.4.1.1.54.1.11** | ifRxCRCErrors                |       | Number of packets received with the wrong checksum by the specified interface since the Citrix ADC was started or the interface statistics were cleared. This indicates the number of Jabber frames received instead of CRC errors on the 10G data ports of Citrix ADC 12000-10G platform and the data ports of Citrix ADC MPX 15000 and 17000 platforms. |
|            | **1.3.6.1.4.1.5951.4.1.1.54.1.12** | ifRxFrameErrors              |       | Number of Jumbo frames(frame size greater than 1518 bytes) received by the specified interface since the Citrix ADC was started or the interface statistics were cleared. |
|            | **1.3.6.1.4.1.5951.4.1.1.54.1.13** | ifRxAlignmentErrors          |       | Number of packets received with an alignment error (an error that occurs when the total number of bits of a received frame is not divisible by eight) by the specified interface. Since the Citrix ADC was started or the interface statistics were cleared. |
|            | **1.3.6.1.4.1.5951.4.1.1.54.1.18** | ifTxCarrierError             |       | Number of Carrier Sense errors that occur when an interface attempts to transmit a frame but is unable to do so as no carrier is detected. This statistic is applicable only to half-duplex transmissions and is available only on 1G data ports of the Citrix ADC 12000 platform and management ports of Citrix ADC MPX 15000 and 17000 platforms. (1) Loop back interface (LO) of all platforms indicates PE fails to send packets to BSD stack because of lack of resources in BSD stack. (2) Number of non Cisco Heart beat packet drop on internal interface. Applicable for internal interface(which is used to communicate between NXOS-NSVSB) of VPX’s running on Cisco Nexus platform |
|            | **1.3.6.1.4.1.5951.4.1.1.54.1.19** | ifTotRxMbits                 |       | The total data, in megabits, received by an interface since the Citrix ADC was started or the interface statistics were cleared. This statistic also includes the Ethernet overhead bytes, i.e. preamble, inter-packet gap, and CRC. |
|            | **1.3.6.1.4.1.5951.4.1.1.54.1.20** | ifTotTxMbits                 |       | The total data, in megabits, transmitted by an interface since the Citrix ADC was started or the interface statistics were cleared. This statistic also includes the Ethernet overhead bytes, i.e. preamble, inter-packet gap, and CRC. |
|            | **1.3.6.1.4.1.5951.4.1.1.54.1.21** | ifTotCitrixADCPkts           |       | Number of packets, destined to the Citrix ADC, received by an interface since the Citrix ADC was started or the interface statistics were cleared. The packets destined to Citrix ADC are those that have the same MAC address as that of an interface or a VMAC address owned by the Citrix ADC. |
|            | **1.3.6.1.4.1.5951.4.1.1.54.1.22** | ifErrDroppedRxPkts           |       | Number of inbound packets dropped by the specified interface. Commonly dropped packets are multicast frames, spanning tree BPDUs, packets destined to a MAC not owned by the Citrix ADC when L2 mode is disabled, or packets tagged for a VLAN that is not bound to the interface. This statistic will increment in most healthy networks at a steady rate regardless of traffic load. If a sharp spike in dropped packets occurs, it generally indicates an issue with connected L2 switches, such as a forwarding database overflow resulting in packets being broadcast on all ports. |
|            | **1.3.6.1.4.1.5951.4.1.1.54.1.23** | ifErrLinkHangs               |       | Number of times the specified interface detected hangs in the transmit and receive paths since the Citrix ADC was started or the interface statistics were cleared. |
|            | **1.3.6.1.4.1.5951.4.1.1.54.1.24** | ifLinkReinits                |       | Number of times the link has been re-initialized. A re-initialization occurs due to link state change, configuration parameter change, or administrative reset operation. |
|            | **1.3.6.1.4.1.5951.4.1.1.54.1.26** | ifErrCongestedPktsDrops      |       | Number of outbound packets dropped from the normal and low-priority transmit (Tx) overflow queues, during congestion on the specified interface, since the Citrix ADC was started or the interface statistics were cleared. This could be caused by one of the following: 1) Packets that have been in the overflow queue for more than 10 milliseconds. 2) Shortage of free receive buffers on the Citrix ADC. |
|            | **1.3.6.1.4.1.5951.4.1.1.54.1.27** | ifErrCongestionLimitPktDrops |       | Number of transmit (Tx) packets dropped from normal and low-priority transmit overflow queues, during congestion on the specified interface, since the Citrix ADC was started or the interface statistics were cleared. This is caused when the overflow queue limits are exceeded. |
|            | **1.3.6.1.4.1.5951.4.1.1.54.1.28** | ifErrPktRx                   |       | Number of inbound packets dropped by the hardware on a specified interface once the Citrix ADC starts or the interface statistics are cleared. This happens due to following reasons: 1) The hardware receives packets at a rate higher rate than that at which the software is processing packets. In this case, the hardware FIFO overruns and starts dropping the packets . 2) The specified interface fails to receive inbound packets from the appliance because of insufficient memory. 3) The specified interface receives packets with CRC errors (Alignment or Frame Check Sequence). 4) The specified interface receives overly long packets. 5) The specified interface receives packets with alignment errors. 6) The software does less buffering because it is running out of available memory. When hardware detects that there is no space into which to push newly arrived packets, it starts dropping them. 7) The specified interface receives packets with Frame Check Sequence (FCS) errors. 8) The specified interface receives packets smaller than 64 bytes. 9) The specified interface discards error-free inbound packets because of insufficient resources. For example: NIC buffers. 10) Packets are missed because of collision detection, link lost, physical decoding error, or MAC abort. |
|            | **1.3.6.1.4.1.5951.4.1.1.54.1.29** | ifErrRxFIFO                  |       | Number packet drops due to insufficient space in the receive queue, on the specified interface, since the Citrix ADC was started or the interface statistics were cleared. This statistic is only available on the data ports of the Citrix ADC 12000 platform and the Citrix ADC MPX 15000 and 17000 platforms. |
|            | **1.3.6.1.4.1.5951.4.1.1.54.1.30** | ifErrRxNoBuffs               |       | Number of times the NIC hardware reported an error, due to packets drops caused by lack of buffers. This statistic is available on: (1) All ports except management ports on Citrix ADC MPX 15000 and 17000 platforms. (2) All 1G ports on Citrix ADC MPX 7500, 9500, 10500, 12500, 15500, 17500, 19500, and 21500 platforms. |
|            | **1.3.6.1.4.1.5951.4.1.1.54.1.32** | ifErrRxFCS                   |       | Number of packets received with Frame Check Sequence(FCS) errors, on the specified interface, since the Citrix ADC was started or the interface statistics were cleared. This statistic is available only on data ports of the Citrix ADC 12000 platform and Citrix ADC MPX 15000 and 17000 platforms. |
|            | **1.3.6.1.4.1.5951.4.1.1.54.1.33** | ifErrPktTx                   |       | Number of outbound packets dropped by the hardware on a specified interface since the Citrix ADC was started or the interface statistics were cleared. This could happen due to length (undersize or oversize) errors and lack of resources. This statistic is available only for: (1) Loop back interface (LO) of all platforms. (2) All data ports on the Citrix ADC 12000 platform. (3) Management ports on the MPX 15000 and 17000 platforms. |
|            | **1.3.6.1.4.1.5951.4.1.1.54.1.34** | ifErrTxFIFO                  |       | Number of times the hardware reported an error in accumulating packets for transmission on the specified interface. This statistic is only available on 10G ports of the Citrix ADC 12000-10G platform and data ports of the Citrix ADC MPX 15000 and 17000 platforms. (1) Loop back interfaces (LO) of all platform indicates packets crossed allowed limit, which is 10K PPS on LO interface |
|            | **1.3.6.1.4.1.5951.4.1.1.54.1.36** | ifErrTxOverflow              |       | Number of packets that have passed through the overflow queues, during transmission on the specified interface, since the Citrix ADC was started or the interface statistics were cleared. This gets incremented only on congested ports. |
|            | **1.3.6.1.4.1.5951.4.1.1.54.1.38** | ifErrDroppedTxPkts           |       | Number of packets dropped in transmission by the specified interface due to one of the following reasons. (1) VLAN mismatch. (2) Oversized packets. (3) Interface congestion. (4) Loopback packets sent on non loop back interface. |
|            | **1.3.6.1.4.1.5951.4.1.1.54.1.39** | ifTotRxXonPause              |       | Number of Pause frames received on the specified interface with pause time set to zero. This statistic is not available on 10G ports of the Citrix ADC 12000-10G platform and data ports of the Citrix ADC MPX 15000 and 17000 platforms. |
|            | **1.3.6.1.4.1.5951.4.1.1.54.1.40** | ifTotRxXoffPause             |       | Number of Pause frames received by the specified interface with the pause time greater than zero. This statistic is only available on 10G ports of the Citrix ADC 12000-10G platform and data ports of the Citrix ADC MPX 15000 and 17000 platforms. |
|            | **1.3.6.1.4.1.5951.4.1.1.54.1.41** | ifTotXoffStateEntered        |       | Number of times transmission was stopped on the specified interface due to the receipt of Pause frames. This statistic is only available on 10G ports of the Citrix ADC 12000-10G platform and data ports of the Citrix ADC MPX 15000 and 17000 platforms. |
|            | **1.3.6.1.4.1.5951.4.1.1.54.1.42** | ifTotXonSent                 |       | Number of pause frames, sent by the specified interface, with pause time set to zero to restart transmission. This statistic is not available on 10G ports of the Citrix ADC 12000-10G platform and data ports of the Citrix ADC MPX 15000 and 17000 platforms. |
|            | **1.3.6.1.4.1.5951.4.1.1.54.1.43** | ifTotXoffSent                |       | Number of Pause frames sent by the specified interface with the pause time greater than zero. This statistic is only available on 10G ports of the Citrix ADC 12000-10G platform and data ports of the Citrix ADC MPX 15000 and 17000 platforms. This statistic also includes the Pause frames with pause time equal to zero. |
|            | **1.3.6.1.4.1.5951.4.1.1.54.1.44** | ifnicStsStalls               |       | Number of times the status updates for a specified interface were stalled since the Citrix ADC was started or the interface statistics were cleared. A status stall is detected when the status of the interface is not updated by the NIC hardware within 0.8 seconds of the last update. |
|            | **1.3.6.1.4.1.5951.4.1.1.54.1.45** | ifnicTxStalls                |       | Number of times the interface stalled, when transmitting packets, since the Citrix ADC was started or the interface statistics were cleared. Transmit (Tx) stalls are detected when a packet posted for transmission is not transmitted in 4 seconds. |
|            | **1.3.6.1.4.1.5951.4.1.1.54.1.46** | ifnicRxStalls                |       | Number of times the interface stalled, when receiving packets, since the Citrix ADC was started or the interface statistics were cleared. Receive (Rx) stalls are detected when the following conditions are met: (1)The link is up for more than 10 minutes. (2)Packets are transmitted, but no packets is received for 16 seconds. |
|            | **1.3.6.1.4.1.5951.4.1.1.54.1.47** | ifnicErrDisables             |       | Number of times the specified interface is disabled by the Citrix ADC, due to continuous Receive (Rx) or Transmit (Tx) stalls, since the Citrix ADC was started or the interface statistics were cleared. The Citrix ADC disables an interface when one of the following conditions is met: (1) Three consecutive transmit stalls occurs with at most gap of 10 seconds between any two stalls. (2) Three consecutive receive stalls occurs with at most gap of 120 seconds between any two stalls. |
|            | **1.3.6.1.4.1.5951.4.1.1.54.1.48** | ifThroughput                 |       | Interface throughput in Mbps |
|            | **1.3.6.1.4.1.5951.4.1.1.54.1.49** | ifMinThroughput              |       | Interface minimum throughput in Mbps |
|            | **1.3.6.1.4.1.5951.4.1.1.54.1.50** | ifErrDroppedRxPktsRl         |       | Number of packets dropped due to license limit on the specified interface. |
|            | **1.3.6.1.4.1.5951.4.1.1.54.1.51** | ifErrRxNoNSB                 |       | Number of times the Citrix ADC failed to allocate buffers, for inbound packets, for the specified interface since the Citrix ADC was started or the interface statistics were cleared. |
|            | **1.3.6.1.4.1.5951.4.1.1.54.1.52** | ifInterfaceAlias             |       | Alias Name for the Interface |

### vServer

> **`vserverTable` - `1.3.6.1.4.1.5951.4.1.3.1.1` - The vServers table ** This is indexed on the vsvrName**

| Monitoring | OID                               | MIB Name                       | Macro                         | Description |
| ---------- | :-------------------------------: | :----------------------------: | :---------------------------: | :----------------------------------------------------------------------------------------------------------- |
| ✅         | **1.3.6.1.4.1.5951.4.1.3.1.1.2**  | vsvrIpAddress                  | `{#NS.VSERVER.IP}`            | IP address of the vServer |
| ✅         | **1.3.6.1.4.1.5951.4.1.3.1.1.5**  | vsvrState                      | `{#NS.VSERVER.STATE}`         | vServer state |
|            | **1.3.6.1.4.1.5951.4.1.3.1.1.7**  | vsvrCurClntConnections         | `{#NS.VSERVER.CONN.CLI}`      | Number of current client connections |
|            | **1.3.6.1.4.1.5951.4.1.3.1.1.8**  | vsvrCurSrvrConnections         | `{#NS.VSERVER.CONN.SRV}`      | Number of current connections to the actual servers behind the virtual server |
|            | **1.3.6.1.4.1.5951.4.1.3.1.1.10** | vsvrSurgeCount                 |                               | Number of requests in the surge queue |
|            | **1.3.6.1.4.1.5951.4.1.3.1.1.37** | vsvrCurServicesDown            | `{#NS.VSERVER.SVC.DOWN}`      | The current number of services which are bound to this vServer and are in the down state |
|            | **1.3.6.1.4.1.5951.4.1.3.1.1.38** | vsvrCurServicesUnKnown         | `{#NS.VSERVER.SVC.UNKNOWN}`   | The current number of services which are bound to this vServer and are in the unKnown state |
|            | **1.3.6.1.4.1.5951.4.1.3.1.1.39** | vsvrCurServicesOutOfSvc        | `{#NS.VSERVER.SVC.OUTOFSVC}`  | The current number of services which are bound to this vServer and are in the outOfService state |
|            | **1.3.6.1.4.1.5951.4.1.3.1.1.40** | vsvrCurServicesTransToOutOfSvc | `{#NS.VSERVER.SVC.TROUTSVC}`  | The current number of services which are bound to this vServer and are in the transitionToOutOfService state |
|            | **1.3.6.1.4.1.5951.4.1.3.1.1.41** | vsvrCurServicesUp              | `{#NS.VSERVER.SVC.UP}`        | The current number of services which are bound to this vServer and are in the up state |
| ✅         | **1.3.6.1.4.1.5951.4.1.3.1.1.43** | vsvrRequestRate                | `{#NS.VSERVER.REQ.RATE}`      | Request rate in requests per second for this service or virtual server |
| ✅         | **1.3.6.1.4.1.5951.4.1.3.1.1.44** | vsvrRxBytesRate                | `{#NS.VSERVER.BYTE.RXRATE}`   | Request rate in bytes per second fot this service or virtual server |
| ✅         | **1.3.6.1.4.1.5951.4.1.3.1.1.45** | vsvrTxBytesRate                | `{#NS.VSERVER.BYTE.TXRATE}`   | Response rate in bytes per second for this service or virtual server |
|            | **1.3.6.1.4.1.5951.4.1.3.1.1.46** | vsvrSynfloodRate               | `{#NS.VSERVER.SYN.FLOODRATE}` | Rate of unacknowledged SYN packets for this service or virtual server |
|            | **1.3.6.1.4.1.5951.4.1.3.1.1.56** | vsvrTotalClients               | `{#NS.VSERVER.TOTAL.CLIENTS}` | Total number of established client connections |
|            | **1.3.6.1.4.1.5951.4.1.3.1.1.59** | vsvrFullName                   | `{#NS.VSERVER.FULL.NAME}`     | The name of the vServer |
| ✅         | **1.3.6.1.4.1.5951.4.1.3.1.1.62** | vsvrHealth                     | `{#NS.VSERVER.HEALTH}`        | The percentage of UP services bound to this vServer |
|            | **1.3.6.1.4.1.5951.4.1.3.1.1.65** | vsvrTotalServers               | `{#NS.VSERVER.TOTAL.SERVERS}` | Total number of established server connections |
| ✅         | **1.3.6.1.4.1.5951.4.1.3.1.1.71** | vsvrEstablishedConn            | `{#NS.VSERVER.CONN.STAB}`     | Number of client connections in ESTABLISHED state |

<BR>

## SNMP Traps

> **`netScalerEventsV2` - `1.3.6.1.4.1.5951.1.1.0` - The events for NetScaler**
> - _**Each trap contains additional data from the sending device. This data is nested in the table below.**_

| Monitoring | OID                                    | MIB Name                        | Macro | Description |
| ---------- | :------------------------------------- | :-----------------------------: | :---: | :---------- |
| ✅         | **1.3.6.1.6.3.1.1.5.5**                | `authenticationFailure`         |       | An authenticationFailure trap signifies that the SNMP entity has received a protocol message that is not properly authenticated. While all implementations of SNMP entities MAY be capable of generating this trap, the snmpEnableAuthenTraps object indicates whether this trap will be generated. |
|            | ➡️ **1.3.6.1.2.1.1.3**                 | `sysUpTimeInstance`             |       | The time (in hundredths of a second) since the network management portion of the system was last re-initialized. |
|            | ➡️ **1.3.6.1.6.3.1.1.4.1**             | `snmpTrapOID`                   |       | The authoritative identification of the notification currently being sent. This variable occurs as the second varbind in every SNMPv2-Trap-PDU and InformRequest-PDU. |
|            | ➡️ **1.3.6.1.4.1.9.2.1.5**             | `authAddr`                      |       | This variable contains the last SNMP authorization failure IP address. |
|            | ➡️ **1.3.6.1.4.1.9.9.412.1.1.1**       | `cExtSnmpTargetAuthInetType`    |       | This contains the type of address `cExtSnmpTargetAuthInetAddr` holds when a host sends an unauthentic SNMP message. |
|            | ➡️ **1.3.6.1.4.1.9.9.412.1.1.2**       | `cExtSnmpTargetAuthInetAddr`    |       | This contains the address of the host from which snmp-agent has received a SNMP message that is not authentic. |
|            | **1.3.6.1.4.1.5951.1.1.0.26**          | `maxClients`                    |       | This trap is sent when the number of clients hits the maxClients value for a service |
|            | ➡️ **1.3.6.1.4.1.5951.4.1.2.1.1.1**    | `svcServiceName`                |       | The name of the service. |
|            | ➡️ **1.3.6.1.4.1.5951.4.1.2.1.1.8**    | `svcEstablishedConn`            |       | Total number of connections in ESTABLISHED state. |
|            | ➡️ **1.3.6.1.4.1.5951.4.1.10.2.1**     | `alarmHighThreshold`            |       | This is the high threshold value configured for this alarm. When this threshold is crossed an SNMP alarm is generated. |
|            | ➡️ **1.3.6.1.4.1.5951.4.1.2.1.1.54**   | `svcServiceFullName`            |       | The name of the service. |
|            | ➡️ **1.3.6.1.4.1.5951.4.1.1.2**        | `sysIpAddress`                  |       | This shows the configured ipaddress of the Citrix ADC. |
|            | **1.3.6.1.4.1.5951.1.1.0.27**          | `maxClientsNormal`              |       | This trap is sent when the number of clients falls below 70% of maxClients value for a service. |
|            | ➡️ **1.3.6.1.4.1.5951.4.1.2.1.1.1**    | `svcServiceName`                |       | The name of the service. |
|            | ➡️ **1.3.6.1.4.1.5951.4.1.2.1.1.8**    | `svcEstablishedConn`            |       | Total number of connections in ESTABLISHED state. |
|            | ➡️ **1.3.6.1.4.1.5951.4.1.10.2.2**     | `alarmNormalThreshold`          |       | This is the normal threshold configured for this alarm which triggers the return-to-normal alarm. |
|            | ➡️ **1.3.6.1.4.1.5951.4.1.2.1.1.54**   | `svcServiceFullName`            |       | The name of the service. |
|            | ➡️ **1.3.6.1.4.1.5951.4.1.1.2**        | `sysIpAddress`                  |       | This shows the configured 
| ✅         | **1.3.6.1.4.1.5951.1.1.0.55**          | `netScalerLoginFailure`         |       | This trap is sent when a login attempt to the NetScaler fails |
|            | ➡️ **1.3.6.1.2.1.1.3**                 | `sysUpTimeInstance`             |       | The time (in hundredths of a second) since the network management portion of the system was last re-initialized. |
|            | ➡️ **1.3.6.1.6.3.1.1.4.1**             | `snmpTrapOID`                   |       | The authoritative identification of the notification currently being sent. This variable occurs as the second varbind in every SNMPv2-Trap-PDU and InformRequest-PDU. |
|            | ➡️ **1.3.6.1.4.1.5951.4.1.10.2.4**     | `nsUserName`                    |       | This represents the name of the system user. |
|            | ➡️ **1.3.6.1.4.1.5951.4.1.10.2.23**    | `nsClientIPAddr`                |       | This represents the IP Address of the machine trying to access / connected to Citrix ADC. |
|            | ➡️ **1.3.6.1.4.1.5951.4.1.1.2**        | `sysIpAddress`                  |       | This shows the configured ipaddress of the Citrix ADC. |
|            | **1.3.6.1.4.1.5951.1.1.0.56**          | `sslCertificateExpiry`          |       | This trap is sent as an advance notification when an SSL certificate is due to expire. |
|            | ➡️ **1.3.6.1.4.1.5951.4.1.1.56.1.1.1** | `sslCertKeyName`                |       | The certificate key pair Name. |
|            | ➡️ **1.3.6.1.4.1.5951.4.1.1.56.1.1.5** | `sslDaysToExpire`               |       | Number of days remaining for the certificate to expire. |
|            | ➡️ **1.3.6.1.4.1.5951.4.1.1.2**        | `sysIpAddress`                  |       | This shows the configured ipaddress of the Citrix ADC. |
| ✅         | **1.3.6.1.4.1.5951.1.1.0.77**          | `rateLmtThresholdExceed`        |       | This trap is sent when the client exceeds the ratelimit threshold. |
|            | ➡️ **1.3.6.1.2.1.1.3**                 | `sysUpTimeInstance`             |       | The time (in hundredths of a second) since the network management portion of the system was last re-initialized. |
|            | ➡️ **1.3.6.1.6.3.1.1.4.1**             | `snmpTrapOID`                   |       | The authoritative identification of the notification currently being sent. This variable occurs as the second varbind in every SNMPv2-Trap-PDU and InformRequest-PDU. |
|            | ➡️ **1.3.6.1.4.1.5951.4.1.10.2.13**    | `alarmRateLmtThresholdExceeded` |       | This specifies the name of the rate limit identifier that exceeded the threshold. |
|            | ➡️ **1.3.6.1.4.1.5951.4.1.10.2.14**    | `ipAddressGathered`             |       | This specifies the list of ip addresses that may have been gathered during the expression evaluation. |
|            | ➡️ **1.3.6.1.4.1.5951.4.1.10.2.15**    | `stringComputed`                |       | This contains the string computed during the expression evaluation. |
|            | ➡️ **1.3.6.1.4.1.5951.4.1.10.2.48**    | `platformLicensedThroughput`    |       | This represents the platform licensed throughput. |
|            | ➡️ **1.3.6.1.4.1.5951.4.1.1.2**        | `sysIpAddress`                  |       | This shows the configured ipaddress of the Citrix ADC. |
|            | **1.3.6.1.4.1.5951.1.1.0.86**          | `ipConflict`                    |       | This trap indicates that ip conflict is present with another device in the network. |
|            | ➡️ **1.3.6.1.4.1.5951.4.1.10.2.24**    | `ipConflictAddr`                |       | The IP configured in Citrix ADC conflicting in the network. |
|            | ➡️ **1.3.6.1.4.1.5951.4.1.10.2.66**    | `ipConflictMacAddr`             |       | The MAC address of the machine having the conflicting IP configured in the network. |
|            | ➡️ **1.3.6.1.4.1.5951.4.1.1.2**        | `sysIpAddress`                  |       | This shows the configured ipaddress of the Citrix ADC. |
|            | **1.3.6.1.4.1.5951.1.1.0.117**         | `sslCardFailed`                 |       | This trap is sent when SSL Card has failed |
|            | ➡️ **1.3.6.1.4.1.5951.4.1.10.2.33**    | `sslCardStatusMsg`              |       | This represents the interpretation details of sslCardStatus. |
|            | ➡️ **1.3.6.1.4.1.5951.4.1.1.2**        | `sysIpAddress`                  |       | This shows the configured ipaddress of the Citrix ADC. |