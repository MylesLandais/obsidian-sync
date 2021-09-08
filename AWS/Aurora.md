Proprietary Amazon database compatible with MySql + Postgres modes (chosen when deployed)

Cloud optimize to provide 3-5x performance increase over traditional database applications

Autoscaling for disk

15 replications, more than mysql, and reduced replication lag

HA native, failover instant.

6 copies across 3 AZ's
	4 copies for writes
	3 copies for reads
	self healing with p2p
	Storage striped accross multiple volumes
	

Clustering
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
		
