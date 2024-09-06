# CAP Theorem

The CAP theorem states that a distributed database system can only guarantee two out of the following three properties:

1. **Consistency (C)**:  
   Ensures that all nodes in the system return the same, most recent data after a write operation.

2. **Availability (A)**:  
   Guarantees that every request to the system receives a response (success or failure), even if some nodes are down.

3. **Partition Tolerance (P)**:  
   Ensures that the system continues to operate even if communication between nodes is lost due to network partitions.

## Partition Tolerance (P) is Preferable

In real-world distributed systems, **Partition Tolerance (P)** is typically non-negotiable, as network failures are inevitable. 
If a system cannot tolerate partitions, it may become unavailable or inconsistent during outages. Therefore, 
systems often choose to balance **Consistency** and **Availability** while ensuring **Partition Tolerance** (P). 
In many cases, partition-tolerant systems focus on either strong consistency (CP) or high availability (AP) based on the application's requirements.
