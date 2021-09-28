- AWS Reigons
- AWS Availability Zones
- IAM
	- Recommended using MFA
	- written in json
	![[Pasted image 20210803143842.png]]
	- Least Privlidge Principle
	- Federation
		- Uses the SAML Standard
	- Do not commit IAM credentials to code OR use ROOT account
- EC2
	- Renting virtual machines (EC2)
	- Storing data on virtual drives (EBS)
	- Distributing load across machines (ELB)
	- Scaling the services using an auto-scaling group (ASG)
	- User Data
		- When the instance is started you can pass User Data, This is used for bootstrap automation
			- make sure to start with the Bash shbang
	- instance launch types
		- On Demand (short/elastic workload, predictable prices)
			- Pay for what you use. per second billing. High Cost, no commitment
			- un-interupted workloads
		- reserved (1 year)
			- Traditional IT Model
			- Pay Upfront for long term (1-3 year commitment)
			- reserve a type, IE for a database.
			- long workloads
			- convertible reserved instances
			- can be scheduled
		- Spot Instancces
			- 90% discount to on-demand
			- can "lose" an instance at any point
			- set a max price for your workload
			- use for resiliant workloads **NOT** for critical jobs or database.
				- data analysis
				- image processing
				- batch jobs
		- Dedicated Instances
	- Elastic Network Interfaces
	
		represent a virtual network card. 
		has an IP4 address and MAC address
	- EC2 Hibernate
		an instance can hibernate up to 60 days
- High Availability
	Horizontal Vs. Vertical Scaling
	What is load balancing?
		[[EC2 Load Balancer]] 
		Health Checks - Determines if instances are responding to requests
		![[Pasted image 20210818113113.png]]
		If a reply is 200 OK an instance is healthy, health check can be conifgured
		SECURITY - Configure EC2 instances to allow access from load balancers 
		-  Network Load Balancer
				- Internet Facing
				- can exsist in multiple AZ's
				- targeting a grouop
				- Can be assigned an elastic IP (must be done at creation)
		- Application Load Balancer V2
				- Route based on path in url
				(example.com/users or example.com/post)
			- Additionally routing on query string and headers
			- port mapping feature
			![[Pasted image 20210824112817.png]]
			- can direct to lambda functions
			- Client IP information contained in x-forward- http headers
		- Classic Load Balancers (v1)
			- TCP (layer 4)
			- HTTP (layer 7)
			- Health cheack at either level
			- fixed hostname
		Stickiness - The client will continue to connect to the same instance behind the load balancer. Used to maintain session data. May cause an imablance. (duration up to 7days)

		Cross Zone Balancing - Each load balancer will distribute across all AZ's
		![[Pasted image 20210825105223.png]]

		SSL/TLS Certificates
			Secure Socket Layer - used to enctrypt connections
			Transport Layer Security - newer version, mainly used.
			Public certs and issued by Certificate Authorities
				- Comodo, Symntec, LetsEncrypt
				- Have an expiration date, must be re-newed regularly
			Load Balancers uses a X.509 cert.
			managed using AWS Cert Manager, where you can upload your own certs
			Server Name Indication - Solves the problem of loading multiple certificates onto one web server to server multiple websites
			Multiple Certs is supported by ALB and NLB (Not v1 classic)

		Connection Draining or Deregistration Delay
			Time to complete requests while un-healthy. Stop sending new requrests to the instance while de-registering
			![[Pasted image 20210825111212.png]]
			Disabled with value 0, max time 1 hour
			
	Auto Scaling Groups
		Scale out or in to match load demands while registering new machines with load blanacers
		Attributes
			Launch configuration
			AMI + instance types, User Data, EBS Volumes, Security Groups, SSH Key Pairs
			Alarms - Can notify through cloudwatch monitoring metrics to scale
			Scaling patterns can be time based (ie. reports run every sunday and monday)
		IAM roles can be applied through scaling
		Can replace terminiated instances
		Cool Down period ensures doesnt add/remove before the previous activity takes place.
		Default Termination Policy, Find AZ with most instances, deleted the oldest configuration
		Lifecycle hooks - Perform pragmatic actions when scaling [Amazon EC2 Auto Scaling lifecycle hooks - Amazon EC2 Auto Scaling](https://docs.aws.amazon.com/autoscaling/ec2/userguide/lifecycle-hooks.html)
		Launch Templates - Versions, Parameters, t2 burst
- Cloud Storage
	-  EBS Root volumes deleted on terminiation.  Do not keep data on this volume
	-  EBS is a network drive has latency and locked to an AZ
	-  Unexcpected terminations can hapen
	-  IOPS ratio based on size allocation
	-  Snapshots can be AMI, Managed by Data life cycle management (snapshot lifecycle policy) can automate your backup process.
	-  To move to another reigon, snapshop, copy, re-create on new az
	-  Data at rest can be encrypted. Minimal impact on latency
	-  [[Elastic File System]]
	-  EBS can be snapsnots and restored to migrate
	-  EFS can be mounted to many, and has the performance for that
-  Databases
	-  [[Relational Database Service]]
	-  Automated provisioning and patching
	-  Point in time restore
	-  Monitoring dashboard
	-  Multi-AZ disaster recovery
	-  Using elasticache infront of RDS
	![[Pasted image 20210907113806.png]]
	- Elasticache can be used as a user session store
	- elasticache does not have IAM auth
	- IAM used for API-level security
	- Redis by default can be accessed
		- Reommended to configure Redis Auth
	- Patterns for ElasticCache
		- Lazy Loading
		- Write Through (no stale data)
		- Session Store (TTL Feature)
[[Route53]]
	Routing Policies
		Simple
		Weighted
		Latency
		failover
		geolocation
		geoproxmity - Can assign a bias value to get more traffic to a certain reigon
		Multiple Value - Associated with health checks, up to 8 healthy records can be returned
	Health Checks
	Traffic Flow
		Start point (A: IPAddr) connects to rules.
		Visual route 53 flow charting
		Traffic policy has a monthly fee ~50$
	Registrar Vs. DNS Service
[[Solutions Architecture]]
	Understand how all the pieces fit together
	Statelesss web application - whatisthetime
	Whatsthetime (stateless - case study)
		Public vs. Private IP and EC2 instances
		Elastic ip vs Route 53 vs Load Balancers
		Route 53 TTL, A Records, and Alias Records
		Auto Scaling Groups
		multi az disasters
		ELB health checks + Security policy
		capacity cost saving
	MyClothes (case study)
		ELB sticky sessions
		ElasticCache
			Storing sessions data (alternative dynamoDB)
			Caching data from rds
			multi-az
		RDS
			Data Store
			Scaling with Read Replica
			multi-az
	wordpress (cms - case study)
		aurora db
		storing data in EBS vs storing data in EFs
[[Elasstic Beanstalk]]
	Supports Go, Java, .Net Core, Python,  Php, Ruby, Docker
	Web server tier v. Worker Tier
		Workers can be processing messages from a queue
	Presets
		Free Tier
		Single spot
[[Amazon S3 - Cloud Object Storage]]
	object files have a key, this may be the filename and it may include the directory structure
	contains
		metadata
		tags
		versioning
	deleting objects creats a delete marker
	Encryption
		SSE-S3 keys used and managed my AWS
		SSE-KMS keys handled and managed by KMS (auditable)
		SEE-C aws does not know what keys, must be done through cli, sdk, or API
		Client Side Encryption you encrypt + you manage keys
	Security Pollicy
		IAM users/policy can be authorized for specific access
		Resource Based bucket pilcies, wide rules allow cross account
		Object ACL - Fine grain control
		Bucket ACL
		IAM Principal can access and s3 object if user allow or the resource policy allow and no deny.
		Bucket Policies are JSON based
			Blocking public access through ACL's
			Support for VPC endpoints
			Logging and Audit stored in s3 buckets
			api calls can be monitored in cloudtrail
			MFA delete can be required
		S3 Websites
			bucket policy needs public reads
			host static websites
		CORS
			Define Origin, Scheme, Host, Port
			Cross Origin Resource Sharing
AWS SDK, IAM Roles & Policies
	[aws policy simulator]
	ec2 instance metadata
		169.254.169.254/latest/meta-data - internal IP address for AWS
		Retrieve IAM Roles
	AWS SDK allows your to program your infrastructure
		Available in Java, .NET, Python, Go, C++, Ruby
		CLI uses BOTO3 sdk 
		default reigon to us-east-1
Advanced S3 & Athena
	MFA-Delete to delete/suspend versioning, versioning must be on
	Must be enabled by the root account
	Can only be enabled with the CLI
	S3 Logging to another bucket
	S3 replication
		enable versioning on source & destination
		Cross-Region Replication - CRR
		Same Region Replication - SRR
		Requires IAM permission
		Only after replicating new objects will be copied.
		Delete marker options may not be replicated.'
	S3 Storage Classes
		S3 Standard - General Purpose
			content distribution and application data.
		S3 Standard-Infrequent Access (IA)
			disaster recovery and backups
		S3 One Zone-Infrequent Access
			secondary backup copies
		S3 Intelligent Tiering
			auto tiering fee
		Glacier
			90 day minimum, long term retention (10/years, no access)
		Glacier Deep Archive
			Long term cheap storage
	S3 Lifecycle Rules
		Transition Actions - Arcive old data
		Expiration Actions - Remove old data
	S3 - KMS limitation
		SSE-KMS has a per second quota and to raise it you must make a request through amazon
	S3 Byte-Range Fetches can be used to download a single file in parallel
	S3 event notifications can update lambda functions, SNS or SQS
	Requester Pays can be setup for large enterprises that can force the requester to pay the cost of downloading from buckets
[[AWS Athena]]
	Servless analytics platfrom

	
	