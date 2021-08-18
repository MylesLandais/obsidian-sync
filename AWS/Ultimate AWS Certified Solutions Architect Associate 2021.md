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
	- Horizontal Vs. Vertical Scaling
	- What is load balancing?
		[[EC2 Load Balancer]] 
		Health Checks - Determines if instances are responding to requests
		![[Pasted image 20210818113113.png]]
		If a reply is 200 OK an instance is healthy, health check can be conifgured
		