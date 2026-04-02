# redis-cluster-aws
Redis Cluster on AWS (Key-Value Store Project)
Overview

This project demonstrates how to build and test a distributed key-value store using Redis on AWS. The goal was to understand how real-world systems handle large-scale data using techniques like sharding, replication, and failover. A Redis cluster was deployed across multiple virtual machines, and its performance and fault tolerance were tested.

What this project does
Deploys a distributed Redis cluster on AWS EC2
Stores data using a key-value model
Automatically splits data across nodes (sharding)
Uses replication for backup and reliability
Supports automatic failover when a node fails
Simulates real-world usage using a workload generator
Measures latency and throughput
Architecture
6 EC2 instances (Amazon Linux)
3 Master nodes (store actual data)
3 Replica nodes (backup copies)
All nodes connected inside a private network (VPC)
Technologies Used
AWS EC2
Redis Cluster
Python (for workload generator)
Linux (Amazon Linux 2023)
Steps Performed
1. Cloud Setup
Created 6 EC2 instances in AWS
Configured security groups to allow:
SSH access (port 22)
Redis communication (6379, 16379)
Ensured all nodes can communicate using private IPs
2. Redis Cluster Deployment
Installed Redis on all nodes
Updated configuration:
Enabled cluster mode
Allowed external connections
Created cluster using:
3 masters
3 replicas
Verified:
All nodes joined
All 16384 hash slots assigned
3. Failover Testing
Stopped a master node manually
Observed:
Replica automatically became master
Cluster remained operational
Restarted node:
It rejoined as a replica
4. Workload Generator
Built a Python program to simulate real usage
Performed operations:
SET, GET, DEL, INCR
Used multiple threads to simulate multiple users
Measured:
Latency per operation
Overall throughput
Key Results
Cluster successfully handled node failure
No major downtime during failover
Data remained accessible
Load distributed evenly across nodes
System showed strong high availability and fault tolerance
What I Learned
How distributed systems manage data using sharding
Importance of replication for reliability
How failover ensures system availability
How to deploy and manage systems on AWS
How to test performance using workload simulation
Important Note

Sensitive files like .pem keys are not included for security reasons.

Future Improvements
Add automatic scaling (add/remove nodes)
Improve workload generator with more realistic patterns
Automate deployment using scripts or Terraform
Conclusion

This project shows how a distributed key-value system can be built and tested using Redis and AWS. It demonstrates important concepts like scalability, fault tolerance, and high availability, which are used in real-world systems.
