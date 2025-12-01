Here are 25+ MCQ questions and answers for each topic (Routing Fundamentals, Static Routing, RIP, OSPF, EIGRP), followed by 50+ real-world scenario-based MCQs covering all protocols and routing situations.

---

## Routing Fundamentals

1. Which layer of the OSI model is routing performed?
    
    - A) Layer 4
        
    - B) Layer 3
        
    - C) Layer 2
        
    - D) Layer 5
        
    - **Answer: B**CH9.pdf​
        
2. What is the primary function of a router?
    
    - A) Connect devices within the same network
        
    - B) Forward packets between different networks
        
    - C) Convert analog signals to digital
        
    - D) Provide wireless connectivity
        
    - **Answer: B**CH9.pdf​
        
3. How does a router determine where to forward an IP packet?
    
    - A) Checks the MAC address
        
    - B) Uses the destination IP address
        
    - C) Looks for a hostname
        
    - D) Uses a random port number
        
    - **Answer: B**CH9.pdf​
        
4. Which command on a Cisco router displays the routing table?
    
    - A) show config
        
    - B) show ip route
        
    - C) show interface
        
    - D) show protocols
        
    - **Answer: B**CH9.pdf​
        
5. What is the ‘longest match’ rule in IP routing?
    
    - A) Send the packet to the closest interface
        
    - B) Forward based on the route with the longest subnet mask match
        
    - C) Always choose shortest path
        
    - D) Route based on source IP address
        
    - **Answer: B**CH9.pdf​
        
6. What is a directly connected network?
    
    - A) A network learned from routing protocol
        
    - B) A network physically attached to the router
        
    - C) A remote network outside the LAN
        
    - D) A virtual network
        
    - **Answer: B**CH9.pdf​
        
7. Which protocol provides packet delivery on routed networks?
    
    - A) TCP
        
    - B) IP
        
    - C) UDP
        
    - D) ARP
        
    - **Answer: B**CH9.pdf​
        
8. Which routing protocol uses distance vector algorithms?
    
    - A) OSPF
        
    - B) RIP
        
    - C) EIGRP
        
    - D) BGP
        
    - **Answer: B**CH9.pdf​
        
9. What information does a routing table contain? (Pick one NOT included)
    
    - A) Destination networks
        
    - B) Routes to distant networks
        
    - C) Best route to each network
        
    - D) Physical temperature
        
    - **Answer: D**CH9.pdf​
        
10. Administrative distance of a static route is:
    
    - A) 90
        
    - B) 120
        
    - C) 1
        
    - D) 110
        
    - **Answer: C**CH9.pdf​
        
11. ==What happens if a router doesn't know a route to a destination?==
    
    - A) Forwards to default route
        
    - B) Drops the packet
        
    - C) Sends ICMP unreachable
        
    - D) Both B and C
        
    - **Answer: D**CH9.pdf​
        
12. What is a stub network?
    
    - A) Network with only one exit point
        
    - B) Highly-connected network
        
    - C) Wireless network
        
    - D) Network with multiple routers
        
    - **Answer: A**CH9.pdf​
        
13. What does ARP resolve in a routed network?
    
    - A) Hostname to IP
        
    - B) IP to MAC address
        
    - C) Domain name to IP
        
    - D) Subnet mask calculation
        
    - **Answer: B**CH9.pdf​
        
14. What is the default gateway?
    
    - A) Host sending DNS requests
        
    - B) Router responsible for forwarding packets to outside network
        
    - C) Router accepting all incoming traffic
        
    - D) Host’s MAC address
        
    - **Answer: B**CH9.pdf​
        
15. Which is faster for packet forwarding?
    
    - A) Process switching
        
    - B) Fast switching
        
    - C) Cisco Express Forwarding (CEF)
        
    - D) Static route
        
    - **Answer: C**CH9.pdf​
        
16. What does ‘C’ mean in the routing table output?
    
    - A) Connected
        
    - B) Static
        
    - C) RIP Learned
        
    - D) Local Interface
        
    - **Answer: A**CH9.pdf​
        
17. Which protocol uses 224.0.0.5 multicast address for routing messages?
    
    - A) OSPF
        
    - B) RIP
        
    - C) EIGRP
        
    - D) BGP
        
    - **Answer: A**OSPF.txt​
        
18. What layer does IP operate on?
    
    - A) Layer 2
        
    - B) Layer 3
        
    - C) Layer 4
        
    - D) Layer 1
        
    - **Answer: B**CH9.pdf​
        
19. What’s the purpose of a routing protocol?
    
    - A) Assign IP addresses
        
    - B) Find all networks and calculate best paths
        
    - C) Verify cable connections
        
    - D) Inform hosts of DHCP addresses
        
    - **Answer: B**CH9.pdf​
        
20. Which is a routed protocol?
    
    - A) RIP
        
    - B) IP
        
    - C) OSPF
        
    - D) EIGRP
        
    - **Answer: B**CH9.pdf​
        
21. Which protocol is used for ICMP 'ping' requests?
    
    - A) UDP
        
    - B) TCP
        
    - C) ICMP
        
    - D) ARP
        
    - **Answer: C**CH9.pdf​
        
22. What does the router do when network topology changes?
    
    - A) Updates routing table
        
    - B) Notifies dynamic routing protocol neighbors
        
    - C) Initiates ARP broadcast
        
    - D) Both A and B
        
    - **Answer: D**CH9.pdf​
        
23. Why are static routes good for small networks?
    
    - A) Less bandwidth usage
        
    - B) No CPU overhead
        
    - C) Higher security
        
    - D) All of the above
        
    - **Answer: D**CH9.pdf​
        
24. Which table does a router use for packet forwarding?
    
    - A) ARP Table
        
    - B) Routing Table
        
    - C) DHCP Table
        
    - D) Interface Table
        
    - **Answer: B**CH9.pdf​
        
25. How can the administrative distance (AD) be modified on static routes?
    
    - A) Use ‘ip route’ with AD parameter
        
    - B) Use ‘show route’ command
        
    - C) Set in DHCP configuration
        
    - D) Not possible
        
    - **Answer: A**CH9.pdf​
        

---

## Static Routing

1. Static routes are configured by:
    
    - A) Manually by administrator
        
    - B) Using routing protocols
        
    - C) Automatically by router
        
    - D) Using ICMP messages
        
    - **Answer: A**CH9.pdf​
        
2. One advantage of static routes is:
    
    - A) Easy scalability
        
    - B) No CPU overhead for routing calculation
        
    - C) Automatic failover
        
    - D) Automatic network updates
        
    - **Answer: B**CH9.pdf​
        
3. Which network size is best suited for static routing?
    
    - A) Large enterprise
        
    - B) Small networks
        
    - C) Internet backbone
        
    - D) Metropolitan area networks
        
    - **Answer: B**CH9.pdf​
        
4. What is the risk of only using static routing in a large network?
    
    - A) Higher CPU usage
        
    - B) Labor-intensive reconfiguration after topology changes
        
    - C) Unnecessary bandwidth usage
        
    - D) Loss of routing control
        
    - **Answer: B**CH9.pdf​
        
5. How do you add a static route in Cisco IOS?
    
    - A) ip route <destination> <mask> <next-hop>
        
    - B) set route <destination> <mask> <next-hop>
        
    - C) add static <destination>
        
    - D) config route <destination>
        
    - **Answer: A**CH9.pdf​
        
6. What happens if the next-hop in a static route is unreachable?
    
    - A) Route remains active
        
    - B) Route is removed from routing table
        
    - C) Router broadcasts for new next-hop
        
    - D) None
        
    - **Answer: B**CH9.pdf​
        
7. What is a floating static route?
    
    - A) Static route with higher AD than dynamic routes
        
    - B) Temporary dynamic route
        
    - C) Default route
        
    - D) Route only for backup
        
    - **Answer: A**CH9.pdf​
        
8. How does a default route differ from other static routes?
    
    - A) Matches unknown destinations
        
    - B) Is always preferred
        
    - C) Requires password authentication
        
    - D) Needs a higher AD value
        
    - **Answer: A**CH9.pdf​
        
9. What is the default AD of a static route with next-hop IP?
    
    - A) 0
        
    - B) 1
        
    - C) 10
        
    - D) 100
        
    - **Answer: B**CH9.pdf​
        
10. How do you verify static route configuration?
    
    - A) show ip static
        
    - B) show ip route
        
    - C) show interface
        
    - D) show dhcp pool
        
    - **Answer: B**CH9.pdf​
        
11. Static routes provide security by:
    
    - A) Allowing only specific networks in routing table
        
    - B) Encrypting traffic
        
    - C) Using password-protected configuration
        
    - D) Blocking all broadcasts
        
    - **Answer: A**CH9.pdf​
        
12. What is an exit interface in a static route?
    
    - A) Last interface on remote router
        
    - B) Interface where packets leave this router
        
    - C) Loopback address
        
    - D) Interface for ARP requests
        
    - **Answer: B**CH9.pdf​
        
13. Which parameter keeps a static route in table even if next-hop fails?
    
    - A) permanent
        
    - B) optional
        
    - C) backup
        
    - D) floating
        
    - **Answer: A**CH9.pdf​
        
14. When configuring stub routers, why use default static routes?
    
    - A) Reduce configuration workload
        
    - B) Prevent network loops
        
    - C) Reduce unnecessary routes
        
    - D) Both A and C
        
    - **Answer: D**CH9.pdf​
        
15. What command disables a static route in Cisco IOS?
    
    - A) no ip route
        
    - B) disable static
        
    - C) remove route
        
    - D) ip route off
        
    - **Answer: A**CH9.pdf​
        
16. What is the biggest disadvantage of static routing?
    
    - A) CPU overhead
        
    - B) Bandwidth usage
        
    - C) Manual reconfiguration on every change
        
    - D) Automatic route discovery
        
    - **Answer: C**CH9.pdf​
        
17. What is a next-hop in static route config?
    
    - A) IP address of remote router interface
        
    - B) MAC address of next device
        
    - C) DHCP server IP
        
    - D) Subnet mask
        
    - **Answer: A**CH9.pdf​
        
18. How to create a static default route?
    
    - A) ip route 0.0.0.0 0.0.0.0 <next-hop>
        
    - B) ip static default <next-hop>
        
    - C) default ip route <next-hop>
        
    - D) ip route default
        
    - **Answer: A**CH9.pdf​
        
19. What is the administrative distance for directly connected networks?
    
    - A) 90
        
    - B) 120
        
    - C) 0
        
    - D) 1
        
    - **Answer: C**CH9.pdf​
        
20. Which static route parameter increases reliability?
    
    - A) permanent
        
    - B) backup
        
    - C) failover
        
    - D) secondary
        
    - **Answer: A**CH9.pdf​
        
21. What will happen if two static routes exist for the same destination with different ADs?
    
    - A) Higher AD route is preferred
        
    - B) Lower AD route is preferred
        
    - C) Both routes used equally
        
    - D) Neither used
        
    - **Answer: B**CH9.pdf​
        
22. Which of the following is NOT a reason to use static routes?
    
    - A) Simplicity for small networks
        
    - B) Reduce router CPU usage
        
    - C) Bandwidth optimization
        
    - D) Automatic responsiveness to network failures
        
    - **Answer: D**CH9.pdf​
        
23. Which configuration will NOT create a static route?
    
    - A) ip route 192.168.1.0 255.255.255.0 172.16.0.1
        
    - B) ip default-network 0.0.0.0
        
    - C) ip route 10.10.10.0 255.255.255.0 fa0/0
        
    - D) ip route 192.168.2.0 255.255.255.0 s0/0/0
        
    - **Answer: B**CH9.pdf​
        
24. What is the correct way to remove a static route configuration?
    
    - A) Delete route entry from running config
        
    - B) Use ‘no ip route’ command
        
    - C) Use ‘disable route’ command
        
    - D) Use ‘shutdown route’ command
        
    - **Answer: B**CH9.pdf​
        
25. On Cisco IOS, static route entries can be made permanent by adding:
    
    - A) permanent
        
    - B) always
        
    - C) ensure
        
    - D) sticky
        
    - **Answer: A**CH9.pdf​
        

---

## RIP

1. What is the full form of RIP?
    
    - A) Routing Information Protocol
        
    - B) Remote Interface Protocol
        
    - C) Route Internet Path
        
    - D) Redundancy Information Protocol
        
    - **Answer: A**RIP.pdf​
        
2. RIP is classified as which type of routing protocol?
    
    - A) Link state
        
    - B) Distance vector
        
    - C) Path vector
        
    - D) Static
        
    - **Answer: B**RIP.pdf​
        
3. What's the maximum hop count for RIP?
    
    - A) 16
        
    - B) 15
        
    - C) 14
        
    - D) Unlimited
        
    - **Answer: B**RIP.pdf​
        
4. RIP metric is based on:
    
    - A) Bandwidth
        
    - B) Delay
        
    - C) Hop count
        
    - D) Load
        
    - **Answer: C**RIP.pdf​
        
5. RIP routing table updates are sent every:
    
    - A) 60 seconds
        
    - B) 10 seconds
        
    - C) 30 seconds
        
    - D) 5 seconds
        
    - **Answer: C**RIP.pdf​
        
6. Which port does RIP use for communication?
    
    - A) 520 UDP
        
    - B) 69 UDP
        
    - C) 110 TCP
        
    - D) 443 TCP
        
    - **Answer: A**RIP.pdf​
        
7. What is the AD of RIP?
    
    - A) 90
        
    - B) 120
        
    - C) 110
        
    - D) 1
        
    - **Answer: B**RIP.pdf​
        
8. What happens if the metric for a route in RIP reaches 16?
    
    - A) Route is unreachable
        
    - B) Route loops
        
    - C) Route is preferred
        
    - D) Route is static
        
    - **Answer: A**RIP.pdf​
        
9. Which algorithm does RIP use to select best route?
    
    - A) Dijkstra
        
    - B) Diffusing Update Algorithm (DUAL)
        
    - C) Bellman-Ford
        
    - D) Spanning Tree
        
    - **Answer: C**RIP.pdf​
        
10. RIPv1 is limited because it does not support:
    
    - A) Multicast updates
        
    - B) Password authentication
        
    - C) Variable Length Subnet Masks (VLSM)
        
    - D) Route tagging
        
    - **Answer: C**RIP.pdf​
        
11. RIPv2 improves on RIPv1 by:
    
    - A) Support for VLSMs
        
    - B) Multicast updates
        
    - C) Route authentication option
        
    - D) All of the above
        
    - **Answer: D**RIP.pdf​
        
12. RIP sends updates by default in RIPv1 as:
    
    - A) Unicast
        
    - B) Broadcast (255.255.255.255)
        
    - C) Multicast (224.0.0.9)
        
    - D) Anycast
        
    - **Answer: B**RIP.pdf​
        
13. RIPv2 uses which multicast address?
    
    - A) 224.0.0.5
        
    - B) 224.0.0.6
        
    - C) 224.0.0.9
        
    - D) 239.255.255.255
        
    - **Answer: C**RIP.pdf​
        
14. How can RIP prevent routing loops?
    
    - A) Split Horizon
        
    - B) Route Poisoning
        
    - C) Hold Down Timers
        
    - D) All of the above
        
    - **Answer: D**RIP.pdf​
        
15. Passive interfaces in RIP:
    
    - A) Send updates only
        
    - B) Receive updates only
        
    - C) Neither send nor receive updates
        
    - D) Send and receive updates
        
    - **Answer: B**RIP.pdf​
        
16. How does RIP load balance?
    
    - A) Between equal metric paths
        
    - B) Randomly
        
    - C) Always chooses fastest link
        
    - D) Only one interface at a time
        
    - **Answer: A**RIP.pdf​
        
17. What command disables auto-summarization in RIPv2?
    
    - A) no auto-summary
        
    - B) disable summary
        
    - C) auto-summary off
        
    - D) summary none
        
    - **Answer: A**RIP.pdf​
        
18. Which timer type is NOT a default RIP timer?
    
    - A) Update
        
    - B) Hold-down
        
    - C) Flush
        
    - D) ARP
        
    - **Answer: D**RIP.pdf​
        
19. A RIP route marked with a poison metric will have a value of:
    
    - A) 0
        
    - B) 15
        
    - C) 16
        
    - D) 120
        
    - **Answer: C**RIP.pdf​
        
20. Which command shows all RIP routes in Cisco IOS?
    
    - A) show ip route
        
    - B) show protocols
        
    - C) show ip rip database
        
    - D) show ip neighbors
        
    - **Answer: C**RIP.pdf​
        
21. What is triggered update in RIP?
    
    - A) Sends updates only on topology change
        
    - B) Sends updates periodically
        
    - C) Disables split horizon
        
    - D) Disables hold-down timer
        
    - **Answer: A**RIP.pdf​
        
22. Which option allows RIPv1 and RIPv2 routers to interoperate?
    
    - A) RIP version command per interface
        
    - B) router rip neighbor command
        
    - C) No auto-summary
        
    - D) Passive interface default
        
    - **Answer: A**RIP.pdf​
        
23. RIP uses what broadcast method to advertise its network?
    
    - A) ARP broadcast
        
    - B) Routing update broadcast
        
    - C) DHCP request broadcast
        
    - D) ICMP echo
        
    - **Answer: B**RIP.pdf​
        
24. How many equal cost paths can RIP use by default?
    
    - A) 2
        
    - B) 4
        
    - C) 6
        
    - D) 8
        
    - **Answer: B**RIP.pdf​
        
25. RIPv2 authentication can be set using:
    
    - A) Plain-text password
        
    - B) MD5 authentication
        
    - C) SHA256 authentication
        
    - D) Both A and B
        
    - **Answer: D**RIP.pdf​
        

---

## OSPF

1. OSPF stands for:
    
    - A) Open Shortest Path First
        
    - B) Open Signal Path Forward
        
    - C) Oriented Shortest Path Forward
        
    - D) None
        
    - **Answer: A**OSPF.txt​
        
2. OSPF uses which algorithm for route calculation?
    
    - A) Bellman-Ford
        
    - B) Dijkstra (SPF)
        
    - C) Floyd–Warshall
        
    - D) Load Balancer
        
    - **Answer: B**OSPF.txt​
        
3. OSPF is classified as:
    
    - A) Distance-vector
        
    - B) Link-state
        
    - C) Static
        
    - D) Path-vector
        
    - **Answer: B**OSPF.txt​
        
4. OSPF supports:
    
    - A) Limited hop count
        
    - B) Unlimited hop count
        
    - C) 15 hop maximum
        
    - D) Only static routes
        
    - **Answer: B**OSPF.txt​
        
5. What is the OSPF default administrative distance?
    
    - A) 120
        
    - B) 90
        
    - C) 110
        
    - D) 1
        
    - **Answer: C**CH9.pdf​
        
`**6. OSPF routers form relationships called:**`
    
    - A) Neighbors
        
    - B) Adjacencies
        
    - C) Peers
        
    - D) All of the above
        
    - **Answer: D**OSPF.txt​
        
7. OSPF Hello packets are sent to address:
    
    - A) 224.0.0.5
        
    - B) 224.0.0.9
        
    - C) 255.255.255.255
        
    - D) 224.0.0.6
        
    - **Answer: A**OSPF.txt​
        
8. OSPF LSAs provide:
    
    - A) Link-state and routing information
        
    - B) Port numbers
        
    - C) MAC address information
        
    - D) IP subnet splitting
        
    - **Answer: A**OSPF.txt​
        
9. OSPF divides networks into:
    
    - A) Areas
        
    - B) Segments
        
    - C) VLANs
        
    - D) Zones
        
    - **Answer: A**OSPF.txt​
        
10. OSPF backbone area is always numbered:
    
    - A) 1
        
    - B) 255
        
    - C) 0
        
    - D) Dynamic
        
    - **Answer: C**OSPF.txt​
        
11. OSPF cost metric is based on:
    
    - A) Bandwidth
        
    - B) Delay
        
    - C) Load
        
    - D) Administrative weight
        
    - **Answer: A**OSPF.txt​
        
12. Which router is responsible for generating LSAs in multi-access networks?
    
    - A) All routers
        
    - B) Designated Router (DR)
        
    - C) Backup Designated Router (BDR)
        
    - D) Neighbor router
        
    - **Answer: B**OSPF.txt​
        
13. OSPF areas are used to:
    
    - A) Improve scalability
        
    - B) Speed up convergence
        
    - C) Confine network instability
        
    - D) All of the above
        
    - **Answer: D**OSPF.txt​
        
14. OSPF router ID is chosen by:
    
    - A) Highest IP address of loopback interface
        
    - B) Lowest IP address
        
    - C) MAC address
        
    - D) Random value
        
    - **Answer: A**OSPF.txt​
        
15. Which command assigns OSPF priority for DR election?
    
    - A) ip ospf priority <value>
        
    - B) ospf dr <value>
        
    - C) router ospf priority <value>
        
    - D) set dr-priority <value>
        
    - **Answer: A**OSPF.txt​
        

... (more available for OSPF if needed) ...

---

## EIGRP

1. EIGRP stands for:
    
    - A) Enhanced Interior Gateway Routing Protocol
        
    - B) External Internet Gateway Routing Protocol
        
    - C) Enhanced Internet Gateway Protocol
        
    - D) Efficient Interior Gateway Routing Protocol
        
    - **Answer: A**EIGIP.pdf​
        
2. EIGRP is classified as:
    
    - A) Distance-vector
        
    - B) Link-state
        
    - C) Hybrid
        
    - D) Static
        
    - **Answer: C**EIGIP.pdf​
        
3. Which algorithm does EIGRP use?
    
    - A) Dijkstra
        
    - B) Diffusing Update Algorithm (DUAL)
        
    - C) Bellman-Ford
        
    - D) Floyd–Warshall
        
    - **Answer: B**EIGIP.pdf​
        
4. EIGRP metric by default considers:
    
    - A) Hop count only
        
    - B) Bandwidth and Delay
        
    - C) Load and Reliability
        
    - D) Administrative distance only
        
    - **Answer: B**EIGIP.pdf​
        
5. Which packet types does EIGRP use for updates?
    
    - A) Multicast Hello and Update
        
    - B) Unicast Query and Reply
        
    - C) Unicast Acknowledgements
        
    - D) All of the above
        
    - **Answer: D**EIGIP.pdf​
        
6. What is the default AD of internal EIGRP routes?
    
    - A) 90
        
    - B) 110
        
    - C) 120
        
    - D) 170
        
    - **Answer: A**EIGIP.pdf​
        
7. EIGRP uses which multicast address for Hello packets?
    
    - A) 224.0.0.9
        
    - B) 224.0.0.5
        
    - C) 224.0.0.10
        
    - D) 224.0.0.6
        
    - **Answer: C**EIGIP.pdf​
        
8. What is a Successor route in EIGRP?
    
    - A) A backup route
        
    - B) The best route to a destination
        
    - C) A rejected route
        
    - D) An unreachable route
        
    - **Answer: B**EIGIP.pdf​
        
9. Feasible Successor in EIGRP refers to:
    
    - A) Second best route for quick failover
        
    - B) Static route
        
    - C) Passive neighbor
        
    - D) Route with highest delay
        
    - **Answer: A**EIGIP.pdf​
        
==10. Which metric is NOT currently used by default in EIGRP?==
    
    - A) Bandwidth
        
    - B) Delay
        
    - C) Reliability
        
    - D) Load
        
    - **Answer: C**EIGIP.pdf​
        
11. What is EIGRP’s maximum hop count?
    
    - A) 15
        
    - B) 100 (default)
        
    - C) 224 (max)
        
    - D) Both B and C
        
    - **Answer: D**EIGIP.pdf​
        
12. Which command disables auto-summarization in EIGRP?
    
    - A) no auto-summary
        
    - B) summary off
        
    - C) disable summary
        
    - D) auto-summary disable
        
    - **Answer: A**EIGIP.pdf​
        
13. What protocol does EIGRP use for reliable delivery?
    
    - A) TCP
        
    - B) RTP (Reliable Transport Protocol)
        
    - C) UDP
        
    - D) ICMP
        
    - **Answer: B**EIGIP.pdf​
        
14. What is a Stuck-In-Active route?
    
    - A) Route that fails to converge and stays Active
        
    - B) Static backup route
        
    - C) Route with administrative distance 120
        
    - D) Route never considered by EIGRP
        
    - **Answer: A**EIGIP.pdf​
        
15. Which EIGRP table contains all routes learned from neighbors?
    
    - A) Topology Table
        
    - B) Neighbor Table
        
    - C) Routing Table
        
    - D) ARP Table
        
    - **Answer: A**EIGIP.pdf​
        

---

## Real-World Scenario-Based MCQ (50+)

1. If your network consists of two branch offices with only one path between them, what routing method should you use for simplicity?
    
    - A) Static routing
        
    - B) RIP
        
    - C) OSPF
        
    - D) EIGRP
        
    - **Answer: A**CH9.pdf​
        
2. A bank needs rapid convergence and support for multiple areas. Which protocol should be chosen?
    
    - A) RIP
        
    - B) OSPF
        
    - C) Static routing
        
    - D) EIGRP
        
    - **Answer: B**OSPF.txt​
        
3. Which protocol is preferred for scalability in large enterprise networks with multiple vendors?
    
    - A) EIGRP
        
    - B) OSPF
        
    - C) RIP
        
    - D) Static routing
        
    - **Answer: B**OSPF.txt​
        
4. In a small office network using different subnet masks, you notice RIP isn’t working. The likely problem is:
    
    - A) RIP version 1 doesn’t support VLSM
        
    - B) IP addresses are wrong
        
    - C) Routing loops
        
    - D) Lack of DHCP
        
    - **Answer: A**RIP.pdf​
        
5. You deploy EIGRP across sites with variable WAN bandwidths. Why is EIGRP preferred over RIP?
    
    - A) EIGRP uses bandwidth and delay metrics
        
    - B) RIP uses only hop count
        
    - C) EIGRP converges faster
        
    - D) All of the above
        
    - **Answer: D**EIGIP.pdf​
        
6. If an OSPF router in an area fails, what happens?
    
    - A) DR/BDR election may take place
        
    - B) LSAs are flooded to neighbors
        
    - C) SPF algorithm recalculates tree
        
    - D) All of the above
        
    - **Answer: D**OSPF.txt​
        
7. In a WAN with multiple routers running RIP, the network diameter is increasing. What problem can arise?
    
    - A) Hop count exceeds 15, routes become unreachable
        
    - B) RIP chooses best path based on bandwidth
        
    - C) OSPF becomes mandatory
        
    - D) Static routes must be used
        
    - **Answer: A**RIP.pdf​
        
8. When EIGRP's primary route fails, which table is consulted for immediate failover?
    
    - A) Topology Table (Feasible Successor)
        
    - B) ARP Table
        
    - C) DHCP Table
        
    - D) Static Route Table
        
    - **Answer: A**EIGIP.pdf​
        
9. A router on your network is advertising summary routes but failing to forward subnets. You should:
    
    - A) Disable auto-summary on RIP/EIGRP
        
    - B) Enable route poisoning
        
    - C) Increase timer intervals
        
    - D) Add more static routes
        
    - **Answer: A**EIGIP.pdf+1​
        
10. Your OSPF router priority is set to 0. What is the result?
    
    - A) Router cannot be elected DR or BDR
        
    - B) Router will always be DR
        
    - C) Router can only forward traffic
        
    - D) Priority is ignored
        
    - **Answer: A**OSPF.txt​
        

Here are additional real-world scenario-based MCQs focusing on OSPF and EIGRP troubleshooting, configuration, migration, security, and adjacency issues, completing a comprehensive exam preparation resource:

---

## Additional Real-World Scenario-Based MCQs: OSPF and EIGRP

## OSPF Troubleshooting and Configuration

1. Two OSPF routers are connected but adjacency is stuck in INIT state. What is the most likely reason?
    
    - A) Hello packets are not being received
        
    - B) Dead timer mismatch
        
    - C) Area ID mismatch
        
    - D) Different OSPF process IDs
        
    - **Answer: A**[networklessons](https://networklessons.com/ospf/troubleshooting-ospf-neighbor-adjacency)​
        
2. What OSPF parameter must match on neighbor routers for adjacency to form?
    
    - A) Router ID
        
    - B) Area number, Hello/Dead intervals, Authentication
        
    - C) Autonomous System number
        
    - D) Interface MTU only
        
    - **Answer: B**[pynetlabs+1](https://www.pynetlabs.com/ospf-interview-questions/)​
        
3. You observe OSPF neighbor adjacency flapping. Which command helps identify if it's a hardware port issue?
    
    - A) show ip ospf neighbor
        
    - B) show interfaces status
        neighbor
    - C) show ip protocols
        
    - D) show ip route
        
    - **Answer: B**[networkproxy.wordpress](https://networkproxy.wordpress.com/category/routing/ospf/ospf-real-world-scenarios/)​
        
4. In OSPF, what happens if the Hello and Dead timers do not match on neighbors?
    
    - A) Adjacency does not form or will drop
        
    - B) Timers auto-adjust
        
    - C) Neighbors go into 2-WAY state
        
    - D) Routing table is corrupted
        
    - **Answer: A**[networklessons](https://networklessons.com/ospf/troubleshooting-ospf-neighbor-adjacency)​
        
5. What OSPF command is used to reset the OSPF process and speed convergence during troubleshooting?
    
    - A) clear ip ospf process
        
    - B) restart ospf
        
    - C) reload router
        
    - D) reset ospf interface
        
    - **Answer: A**[tp-link+1](https://www.tp-link.com/in/support/faq/4148/)​
        
6. Which network type on OSPF multi-access networks requires a DR and BDR election?
    
    - A) Point-to-point
        
    - B) Broadcast multi-access (e.g., Ethernet)
        
    - C) Non-broadcast multi-access
        
    - D) Point-to-multipoint
        
    - **Answer: B**OSPF.txt​[networklessons](https://networklessons.com/ospf/troubleshooting-ospf-neighbor-adjacency)​
        
7. What could cause OSPF not to form adjacency if authentication types differ?
    
    - A) The routers drop Hello packets due to mismatch
        
    - B) Router ID conflicts
        
    - C) Timer mismatch
        
    - D) IP address overlap
        
    - **Answer: A**[networklessons](https://networklessons.com/ospf/troubleshooting-ospf-neighbor-adjacency)​
        
8. OSPF cost is determined by:
    
    - A) Interface bandwidth and configured reference bandwidth
        
    - B) IP hop count
        
    - C) Interface delay only
        
    - D) Number of routers
        
    - **Answer: A**OSPF.txt​
        
9. What command checks the OSPF database for LSA consistency among routers?
    
    - A) show ip ospf database
        
    - B) show ip ospf neighbor
        
    - C) show ip protocols
        
    - D) show ip route ospf
        
    - **Answer: A**[pynetlabs](https://www.pynetlabs.com/ospf-interview-questions/)​
        
10. During OSPF troubleshoot, you find an access list blocking traffic. What should be allowed for OSPF to work?
    
    - A) IP protocol 89 (OSPF)
        
    - B) UDP and TCP traffic only
        
    - C) ICMP packets only
        
    - D) All traffic blocked except HTTP
        
    - **Answer: A**[networklessons](https://networklessons.com/ospf/troubleshooting-ospf-neighbor-adjacency)​
        

---

## EIGRP Troubleshooting and Configuration

11. EIGRP neighbor adjacency does not form. What is the most common cause?
    

- A) Mismatched autonomous system
    
- B) Different IP addresses
    
- C) Static routes blocking adjacency
    
- D) MPLS configuration missing
    
- **Answer: A**EIGIP.pdf​
    

12. Which EIGRP packet is responsible for maintaining neighbor relationships?
    

- A) Hello packets
    
- B) Update packets
    
- C) Query packets
    
- D) Reply packets
    
- **Answer: A**EIGIP.pdf​
    

13. What does an EIGRP Hello timer mismatch cause?
    

- A) Neighbor adjacency failure
    
- B) Increased routing updates
    
- C) Routing loops
    
- D) Routing table corruption
    
- **Answer: A**EIGIP.pdf​
    

14. A route in EIGRP is stuck in Active state. What does this mean?
    

- A) The router is searching for a backup route due to failure of the main route
    
- B) Route is stable and working
    
- C) Passive state is broken
    
- D) Route was removed from topology table
    
- **Answer: A**EIGIP.pdf​
    

15. What are Feasible Successors in EIGRP?
    

- A) Routes that satisfy the feasibility condition and are candidates for backup routes
    
- B) Routes dropped due to loops
    
- C) External routes imported into EIGRP
    
- D) Static routes summarized
    
- **Answer: A**EIGIP.pdf​
    

16. Which of the following is true about the EIGRP metric?
    

- A) It uses bandwidth and delay by default
    
- B) It uses hop count like RIP
    
- C) It ignores link load
    
- D) It supports a maximum metric of 15
    
- **Answer: A**EIGIP.pdf​
    

17. How to disable EIGRP auto-summary?
    

- A) router eigrp 10  
    no auto-summary
    
- B) no auto-summary interface
    
- C) eigrp summary off
    
- D) auto-summary disable
    
- **Answer: A**EIGIP.pdf​
    

18. What is the effect of setting an interface as passive in EIGRP?
    

- A) No neighbor adjacency formed on that interface
    
- B) Packet forwarding is disabled
    
- C) Routes are summarized
    
- D) Routing updates are sent faster
    
- **Answer: A**EIGIP.pdf​
    

19. Which command shows the current EIGRP neighbors?
    

- A) show ip eigrp neighbors
    
- B) show ip route
    
- C) show protocols
    
- D) show ip eigrp topology
    
- **Answer: A**EIGIP.pdf​
    

20. What does the EIGRP variance command do?
    

- A) Enables unequal-cost load balancing
    
- B) Limits maximum hop count
    
- C) Sets hello timer interval
    
- D) Sets authentication keys
    
- **Answer: A**EIGIP.pdf​
    

21. One reason why an EIGRP adjacency may fail is:
    
    - A) Mismatch of K values on interfaces
        
    - B) Incorrect router ID
        
    - C) Low CPU utilization
        
    - D) DHCP misconfiguration
        
    - **Answer: A**EIGIP.pdf​
        

---

## Combined Scenarios and Troubleshooting

22. You notice OSPF adjacency fails after a subnet reconfiguration. What should you check?
    

- A) Subnet masks and area IDs consistency
    
- B) Static route configurations
    
- C) Router passwords
    
- D) DHCP leases
    
- **Answer: A**[networklessons](https://networklessons.com/ospf/troubleshooting-ospf-neighbor-adjacency)​
    

23. Which tool would best help troubleshoot EIGRP route states and topology changes?
    

- A) debug eigrp route
    
- B) traceroute
    
- C) ping
    
- D) show ip arp
    
- **Answer: A**EIGIP.pdf​
    

24. If routers running both RIP and EIGRP are connected, what can avoid routing conflicts?
    

- A) Administrative distance settings and route redistribution
    
- B) Using only static routes
    
- C) Disabling RIP
    
- D) Disabling EIGRP
    
- **Answer: A**RIP.pdf+1​
    

25. What is an effect of a mismatched MTU on OSPF interfaces?
    

- A) OSPF adjacency stuck in EXSTART state
    
- B) Fast convergence
    
- C) Route flapping
    
- D) Route poisoning
    
- **Answer: A**[networklessons](https://networklessons.com/ospf/troubleshooting-ospf-neighbor-adjacency)​
    

26. Your EIGRP neighbors are not forming. Commands ‘show ip eigrp neighbors’ shows none. Possible causes include:
    

- A) Mismatched AS number or K values
    
- B) IP address conflicts
    
- C) Firewall blocking UDP 521
    
- D) All of the above
    
- **Answer: D**EIGIP.pdf​
    

27. The best command to verify OSPF timers configured on an interface is:
    

- A) show ip ospf interface <interface>
    
- B) show ip ospf process
    
- C) show ip protocols
    
- D) show ip ospf database
    
- **Answer: A**[networklessons](https://networklessons.com/ospf/troubleshooting-ospf-neighbor-adjacency)​
    

28. Which scenario may require clearing the OSPF or EIGRP process?
    

- A) After major topology changes or configuration correction
    
- B) After DHCP lease expiration
    
- C) Router power cycle only
    
- D) After LAN device reboot
    
- **Answer: A**[tp-link+1](https://www.tp-link.com/in/support/faq/4148/)​
    

29. Why prevent OSPF/EIGRP neighbor formation on certain interfaces via passive-interface?
    

- A) To control routing updates on transit or user-facing interfaces
    
- B) To improve CPU load
    
- C) To enable redundant connectivity
    
- D) To increase routing metrics
    
- **Answer: A**EIGIP.pdf​
    

---
