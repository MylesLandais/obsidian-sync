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
	- 