Based on your query and the provided sources detailing the configuration of a Site-to-Site IPsec VPN using Cisco Packet Tracer, here is a comprehensive list of the commands used and mentioned in the video transcript.

The configuration requires steps covering basic routing (OSPF), licensing the security feature, defining interested traffic (ACL), configuring IKE Phase 1 (ISAKMP), configuring IKE Phase 2 (IPsec/Transform Set), and applying the configuration (Crypto Map).

### I. Global Configuration and Routing (OSPF Example)

These commands were used to enable basic connectivity between the networks before the VPN tunnel was established.

| Purpose                                  | Command                                 |
| :--------------------------------------- | :-------------------------------------- |
| Enter privileged EXEC mode               | `enable`                                |
| Enter global configuration mode          | `config t`                              |
| Start OSPF process (using process ID 11) | `router ospf 11`                        |
| Define router ID                         | `router-id 2.1.2.1`                     |
| Advertise HQ network (e.g., on Router A) | `network 192.168.10.0 0.0.0.255 area 0` |
| Advertise WAN link (e.g., on Router A)   | `network 20.20.20.0 0.0.0.3 area 0`     |
| Exit configuration mode                  | `exit`                                  |
| Save configuration                       | `do wr` (or `write memory`)             |

### II. Enabling Security Technology Package (2911 Routers)

The security technology package must be enabled on the 2911 routers for IPsec VPN configuration to work.

| Purpose                                                    | Command                                                   |
| :--------------------------------------------------------- | :-------------------------------------------------------- |
| Enter global configuration mode                            | `config t`                                                |
| Enable Security K9 technology package                      | `license boot module c2900 technology package securityk9` |
| Accept licensing agreement                                 | `yes`                                                     |
| Save configuration                                         | `do right`                                                |
| Reload the router (often necessary for license activation) | `reload`                                                  |
| Verify license status                                      | `show version`                                            |

### III. Defining Interested Traffic (Extended ACL 130)

An extended Access Control List (ACL 130) is used to define the traffic that should be encrypted by the IPsec tunnel. **Note:** The source initially used the subnet mask and had to delete the incorrect entries and use the wildcard mask.

| Context                                                        | Command                                                                             |
| :------------------------------------------------------------- | :---------------------------------------------------------------------------------- |
| **Router A (HQ)** - Delete incorrect entry                     | `no access-list 130 permit ip 192.168.0.0 255.255.255.0 192.168.20.0 255.255.255.0` |
| **Router A (HQ)** - Correct ACL (Source 10.0 to Dest 20.0)     | `access-list 130 permit ip 192.168.0.0 0.0.255.255 10.1.1.0 0.0.0.255`              |
| **Router B (Branch)** - Delete incorrect entry                 | (Implied deletion of entry using subnet mask)                                       |
| **Router B (Branch)** - Correct ACL (Source 20.0 to Dest 10.0) | `access-list 130 permit ip 10.1.1.0 0.0.0.255 192.168.0.0 0.0.255.255`              |


### IV. IKE Phase 1 Configuration (ISAKMP Policy)

IKE Phase 1 (Internet Key Exchange) establishes the secure channel parameters, known as the ISAKMP policy, on both routers.

| Purpose                                                                      | Command                                                    |
| :--------------------------------------------------------------------------- | :--------------------------------------------------------- |
| Create ISAKMP policy 10                                                      | `crypto isakmp policy 10`                                  |
| Set encryption algorithm (AES 256)                                           | `encryption aes 256`                                       |
| Set authentication method (Pre-Shared Key)                                   | `authentication pre-share`                                 |
| Set Diffie-Hellman group for key exchange                                    | `group 5`                                                  |
| Exit ISAKMP configuration mode                                               | `exit`                                                     |
| **Router A (HQ):** Configure shared key (`detect45`) for Peer 30.30.30.2     | `crypto isakmp key e address 30.30.30.2(destination IP)`   |
| **Router B (Branch):** Configure shared key (`detect45`) for Peer 20.20.20.2 | `crypto isakmp key detect45 address 20.20.20.2(source IP)` |

### V. IKE Phase 2 Configuration (IPsec Policy & Crypto Map)

IKE Phase 2 establishes the IPsec Security Association (SA) by defining a transform set and binding all elements (ACL, Transform Set, Peer) into a crypto map.

#### Transform Set (Both Routers)

| Purpose                             | Command                                                  |
| :---------------------------------- | :------------------------------------------------------- |
| Create transform set named `VPNset` | `crypto ipsec transform-set VPNset esp-aes esp-sha-hmac` |

#### Crypto Map Configuration (Router A)

| Purpose                                                  | Command                                                      |
| :------------------------------------------------------- | :----------------------------------------------------------- |
| Create crypto map `VPNmap` (Sequence 10, ISAKMP enabled) | `crypto map VPNmap 10 ipsec-isakmp`                          |
| Add a description                                        | `description this vpm connects to site B branch servers....` |
| Define the peer IP address (30.30.30.2)                  | `set peer 30.30.30.2(destination IP)`                        |
| Bind the transform set                                   | `set transform-set VPNset`                                   |
| Bind the ACL 130 to the map                              | `match address 130`                                          |

#### Crypto Map Configuration (Router B)

| Purpose                                                  | Command                                                  |
| :------------------------------------------------------- | :------------------------------------------------------- |
| Create crypto map `VPNmap` (Sequence 10, ISAKMP enabled) | `crypto map VPNmap 10 ipsec-isakmp`                      |
| Add a description                                        | `description this connects to site A Which is a Company` |
| Define the peer IP address (20.20.20.2)                  | `set peer 20.20.20.2`                                    |
| Bind the transform set                                   | `set transform-set VPNset`                               |
| Bind the ACL 130 to the map                              | `match address 130`                                      |


### VI. Applying Crypto Map to Outgoing Interface

The crypto map must be applied to the interface connecting to the ISP for the policy to take effect. The interface used in the sources was Serial 0/3/0.

| Purpose                            | Command                               |
| :--------------------------------- | :------------------------------------ |
| Enter interface configuration mode | `interface serial 0/3/0(source int.)` |
| Apply the crypto map               | `crypto map VPNmap`                   |
| Exit configuration mode            | `exit`                                |


### VII. Testing and Verification Commands

These commands were used to test connectivity and verify the status of the IPsec tunnel.

| Purpose                                                              | Command                                       | Sources |
| :------------------------------------------------------------------- | :-------------------------------------------- | :------ |
| Test connectivity                                                    | `ping 192.168.20.20` (Example ping to Site B) |         |
| Show starting configuration (for review/troubleshooting)             | `do show start`                               |         |
| **Verify IPsec Security Association status** (Check packet counters) | `show crypto ipsec sa`                        |         |