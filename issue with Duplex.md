Duplex modes:
One end set to full and the other set to half results in a mismatch.
One end set to full and auto negotiation set on the other end:
 Auto negotiation fails, and that end reverts to half.
 Results in a mismatch.
One end set to half and auto negotiation set on the other:
 Auto negotiation fails, and that end reverts to half.
 Both ends at half; no mismatch.
Auto negotiation on both ends:
One end fails to full, and the other end fails to half.
Example: A Gigabit Ethernet interface defaults to full, while a 10/100 defaults to half.
Auto negotiation on both ends:
Auto negotiation fails on both ends, and they revert to half.
 Both end at half; no mismatch.Bandwidth modes:
One end set to one speed and the other set to another, resulting in a mismatch.
One end set to a higher speed and autonegotiation enabled on the other end.
 If autonegotiation fails, the autonegotiation end reverts to its lowest speed.
 Results in a mismatch.
Autonegotiation on both ends:
Autonegotiation fails on both ends, and they revert to their lowest speed.
Both end at half; no mismatch.


https://chatgpt.com/share/693266f1-b708-8010-ae2b-59fb410fc652