Proprietary Amazon database compatible with MySql + Postgres modes (chosen when deployed)

*Amazon Aurora connection management*; Aurora uses *Endpoints* as a handler abstraction for connections for routing and load balancing connections. For example - a primary instance can handle all the data manipulation.

Endpoint Types
-	Reader; Provides load balancing support for read-only connections
-	Custom; Examples may include using a low capacity instance for ad-hoc reporting
-	Instance; Specific instance of a database within the cluster
-	
Cloud optimize to provide 3-5x performance increase over traditional database applications

Features

Autoscaling for disk

15 replications, more than mysql, and reduced replication lag

HA native, failover instant.

6 copies across 3 AZ's
	4 copies for writes
	3 copies for reads
	self healing with p2p
	Storage striped accross multiple volumes
	
Clustering
	A cluster has a single-master configuration
	Or a Multi-Master can be configured
	Shared storage volume
	Master volume writes
	Writer endpoint, pointing to master write node
	read replicas can be auto-scaling.
	reader endpoint exposes replicas and load balances

Aurora Serverless
	Automated instances
	good for unpreditctable or iternmittent workloads
	Cost effective cost per second
	
Global Aurora
	Cross reigon read replicas
	Aurora Global
		Primary Reigons
		5 secondary reigons with minimal replication lag

<iframe width="1138" height="640" src="https://www.youtube.com/embed/iwS1h7rLNBQ" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

