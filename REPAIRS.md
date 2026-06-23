# Repairs and Remediation Performed

The completed DHCP lab included corrective work when clients did not initially receive the intended network configuration.

## Repairs completed

- Authorized the DHCP server in Active Directory.
- Activated the IPv4 scope after confirming the address range.
- Corrected exclusions that overlapped with infrastructure addresses.
- Corrected gateway, DNS server and domain-name scope options.
- Corrected the hardware address used by the reservation.
- Released and renewed the affected client lease.
- Removed stale test leases where necessary and repeated allocation testing.
- Revalidated the client configuration against the server lease table.

The final scope issued the intended address, gateway and internal DNS settings.

**This was tested by me to be working. User experience may vary.**
