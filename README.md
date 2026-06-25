# Windows Server DHCP Lab

![Status](https://img.shields.io/badge/Project-Completed-success)
![Windows Server](https://img.shields.io/badge/Platform-Windows%20Server-0078D4)
![DHCP](https://img.shields.io/badge/Service-DHCP-2F6FED)

A completed Windows Server lab in which I installed and configured DHCP, created an IPv4 scope, assigned network options, created a reservation and validated client lease behavior.

> **Status:** Completed and validated. This repository documents work already performed in a private lab. Real subnets, addresses, hostnames and domain details have been generalized.

## Objectives completed

- Installed the DHCP Server role
- Authorized the server in Active Directory
- Created and activated an IPv4 scope
- Configured the address pool and exclusions
- Applied gateway, DNS and domain-name options
- Created a device reservation
- Renewed client leases
- Reviewed active leases and DHCP events
- Documented troubleshooting findings

## Implementation summary

1. Added the DHCP Server role and management tools.
2. Completed post-installation authorization in Active Directory.
3. Created an IPv4 scope for the lab network.
4. Defined the available address range and excluded infrastructure addresses.
5. Configured scope options for the default gateway, DNS server and DNS suffix.
6. Activated the scope.
7. Created a reservation using a client hardware address.
8. Renewed the client configuration and confirmed the expected lease.
9. Reviewed the DHCP console and event logs for validation.

## Validation commands

Set `$ScopeId` to the network address of the scope used in the lab before running the commands:

```powershell
$ScopeId = '10.10.20.0'

Get-DhcpServerv4Scope -ScopeId $ScopeId
Get-DhcpServerv4OptionValue -ScopeId $ScopeId
Get-DhcpServerv4Lease -ScopeId $ScopeId
Get-DhcpServerv4Reservation -ScopeId $ScopeId
```

On the test client, renew the DHCP lease through the approved support workflow and review the resulting IP configuration. Confirm that the address belongs to the intended scope, does not overlap an exclusion, and includes the expected gateway, DNS server and DNS suffix.

## Outcome

The DHCP server successfully issued valid network settings to the Windows client devices. The configured reservation consistently assigned the intended address to the selected client, and the scope options supplied the correct gateway and internal DNS configuration.

## Findings

- A correctly created scope did not issue addresses until it was activated and the DHCP server was authorized.
- Exclusions and reservations served different purposes: exclusions removed addresses from dynamic allocation, while reservations tied an address to a specific client.
- DHCP option 006 was critical in the domain lab because clients needed the internal DNS server rather than a public resolver.
- A client could retain an older lease until it was renewed.
- Reviewing both the client configuration and the server lease table gave stronger evidence than checking only one side.
- Careful scope planning prevented accidental overlap with statically addressed infrastructure devices.

## Skills demonstrated

- Windows Server role installation
- DHCP scope design
- Address-pool planning
- DHCP options and reservations
- Active Directory authorization
- Client lease troubleshooting
- PowerShell validation
- Technical documentation

## Security notes

- No real production addressing is included.
- All network values shown in examples are sanitized lab examples.
- The lab was completed in a controlled non-production environment.

## Author

**Dewald Pretorius** — L2 IT Support Engineer
