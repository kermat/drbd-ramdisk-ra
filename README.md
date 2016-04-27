# drbd-ramdisk-ra
Pacemaker resource-agent for managing a ramdisk. Optionally, 
this ramdisk can be replicated using DRBD9; which is the real 
reason this RA was created. 

Since DRBD9 v9.x can natively support 64 replicas and the 
licensed version of DRBD9 supports RDMA transport, using a 
ramdisk backed DRBD device sounded like a "neat" idea. DRBD v8.x 
can only support 2 replicas (without device stacking) leaving 
data on a volatile ramdisk vulnerable during a resync. Also, 
the TCP transport was a huge bottleneck in throughput/latency of 
a DRBD device sitting on a super fast ramdisk. With 3+ replicas 
of our ramdisk connected via RDMA transport the aforementioned 
risks/bottlenecks are somewhat mitigated.
