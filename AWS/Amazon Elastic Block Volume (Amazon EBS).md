Volume Types
	- GP2 General Purpose SSD
	- IOI High performance for low latency high throughput (databases)
	- STI Low cost, through put optimized (streaming, kafka, logging)
	- SCI Lowest cost Scenario when cost optimizing over performance.
	
EBS Snapshots - not recommended to run during high traffic time. IO intensive

Create Snapshot, Copy snapshot to encrypt or move region, Then you may restore from encrypted snapshot

Encryption uses KMS

Local Ec2 instance store - physical block strange attached, cannot be scaled

ephemeral, generally /dev/nvme0n1 ~50gb.

Raid 0 - Increase performane; no fault tolerance
Raid 1 - Increase fault tolerance; Writes both drives togther. Data is replicated between drives (mirroring)
Raid 5 - not recommended for cloud performance
Raid 6 - Not recommended for cloud performance

Raid does not live in the AWS console, must be configured by host

<iframe width="649" height="365" src="https://www.youtube.com/embed/LW7x8wyLFvw" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

