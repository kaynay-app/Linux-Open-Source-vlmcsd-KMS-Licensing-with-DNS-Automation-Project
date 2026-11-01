### Phase 2: Active Directory DNS Infrastructure Automation
To eliminate manual script configurations on endpoints, lookup paths were built directly into the Active Directory DNS Manager (`dnsmgmt.msc`) on the Primary Domain Controller (`KLM-DC02`):

1. **Forward A-Record Pointers:** Created a static pointer mapping `kms.somedomain.local` directly to the `KLM-KMS-SERVERFQDN` IP address.
2. **Reverse Lookup Zones:** Constructed a new primary Active Directory integrated IPv4 Reverse Lookup Zone for the `10.x.x` subnet to eliminate pointer resolution (`Non-existent domain`) faults.
3. **Automated Activation Routing (SRV Record):** Injected a global network Service Location (SRV) record inside the `_tcp` tree folder of the local domain directory:
   * **Service:** `_vlmcs`
   * **Port:** `1688`
   * **Target Host:** `kms.somedomain.local`

---
