1. A customer relationship management (CRM) application runs on Amazon EC2 instances in multiple Availability Zones behind an Application Load Balancer.
	a. The load balancer will stop sending requests to the failed instance
	b. The load balancer will terminate the failed instance.
	c. The load balancer will automatically replace the failed instance.
	d. The load balancer will return 504 Gateway Timeout errors until the instance is replaced.
	**Answer**
		An Application Load Balancer (ALB) sends requests to healthy instances only. An ALB performs periodic health checks on targets in a target group. An instance that fails health checks for a configurable number of consecutive times is considered unhealthy. The load balancer will no longer send requests to the instance until it passes another health check
2. A company needs to perform [asynchronous processing](https://aws.amazon.com/blogs/compute/understanding-asynchronous-messaging-for-microservices/), and has Amazon SQS as part of a decoupled architecture. The company wants to ensure that the number of empty responses from polling requests are kept to a minimum.
		A) Increase the maximum message retention period for the queue.
		B) Increase the maximum receives for the redrive policy for the queue.
		C) Increase the default visibility timeout for the queue.
		D) Increase the receive message wait time for the queue
		**Answer**
			D - When the ReceiveMessageWaitTimeSeconds property of a queue is set to a value greater than zero, long polling is in effect. Long polling reduces the number of empty responses by allowing Amazon SQS to wait until a message is available before sending a response to a ReceiveMessage request.
3. A company currently stores data for on-premises applications on local drives. The CTO wants to reduce hardware costs by storing the data in Amazon S3 but does not want to make modifications to the applications. To minimize latency, frequently accessed data should be available locally. What is a reliable and durable solution for a solutions architect to implement that will reduce the cost of local storage?
	A) Deploy an SFTP client on a local server and transfer data to Amazon S3 using AWS Transfer for SFTP.
	B) Deploy an AWS Storage Gateway volume gateway configured in cached volume mode.
	C) Deploy an AWS DataSync agent on a local server and configure an S3 bucket as the destination.
	D) Deploy an AWS Storage Gateway volume gateway configured in stored volume mode.
	**Answer**
		 B – An AWS [[Storage Gateway volume]] gateway connects an on-premises software application with cloud-backed storage volumes that can be mounted as Internet Small Computer System Interface (iSCSI) devices from on-premises application servers. In cached volumes mode, all the data is stored in Amazon S3 and a copy of frequently accessed data is stored locally
4. A company runs a public-facing three-tier web application in a VPC across multiple Availability Zones. Amazon EC2 instances for the application tier running in private subnets need to download software patches from the internet. However, the instances cannot be directly accessible from the internet. Which actions should be taken to allow the instances to download the needed patches? (Select TWO.)
	A) Configure a NAT gateway in a public subnet.
	B) Define a custom route table with a route to the NAT gateway for internet traffic and associate it with the
	private subnets for the application tier.
	C) Assign Elastic IP addresses to the application instances.
	D) Define a custom route table with a route to the internet gateway for internet traffic and associate it with
	the private subnets for the application tier.
	E) Configure a NAT instance in a private subnet.
	**Answer**
		A, B – A NAT gateway forwards traffic from the instances in the private subnet to the internet or other AWS services, and then sends the response back to the instances. After a NAT gateway is created, the route tables for private subnets must be updated to point internet traffic to the NAT gateway
5. A solutions architect wants to design a solution to save costs for Amazon EC2 instances that do not need to run during a 2-week company shutdown. The applications running on the instances store data in instance memory (RAM) that must be present when the instances resume operation. Which approach should the solutions architect recommend to shut down and resume the instances?
	A) Modify the application to store the data on instance store volumes. Reattach the volumes while restarting them.
	B) Snapshot the instances before stopping them. Restore the snapshot after restarting the instances.
	C) Run the applications on instances enabled for hibernation. Hibernate the instances before the shutdown.
	D) Note the Availability Zone for each instance before stopping it. Restart the instances in the same Availability Zones after the shutdown.
	**Solution**
		C – Hibernating an instance saves the contents of RAM to the Amazon EBS root volume. When the instance restarts, the RAM contents are reloaded
6. A company plans to run a monitoring application on an Amazon EC2 instance in a VPC. Connections are made to the instance using its private IPv4 address. A solutions architect needs to design a solution that will allow traffic to be quickly directed to a standby instance if the application fails and becomes nreachable. hich approach will meet these requirements?
	A) Deploy an Application Load Balancer configured with a listener for the private IP address and register the primary instance with the load balancer. Upon failure, de-register the instance and register the secondary instance.
	B) Configure a custom DHCP option set. Configure DHCP to assign the same private IP address to the secondary instance when the primary instance fails.
	C) Attach a secondary elastic network interface (ENI) to the instance configured with the private IP address. Move the ENI to the standby instance if the primary instance becomes unreachable.
	D) Associate an Elastic IP address with the network interface of the primary instance. Disassociate the Elastic IP from the primary instance upon failure and associate it with a secondary instance
	**Solution**
		C – A secondary ENI can be added to an instance. While primary ENIs cannot be detached from an instance, secondary ENIs can be detached and attached to a different instance.
7. An analytics company is planning to offer a site analytics service to its users. The service will require that the users’ webpages include a JavaScript script that makes authenticated GET requests to the company’s Amazon S3 bucket. What must a solutions architect do to ensure that the script will successfully execute? 
	A) Enable cross-origin resource sharing (CORS) on the S3 bucket. 
	B) Enable S3 versioning on the S3 bucket. 
	C) Provide the users with a signed URL for the script. 
	D) Configure a bucket policy to allow public execute privileges.
	**solution**
		A – Web browsers will block the execution of a script that originates from a server with a different domain name than the webpage. Amazon S3 can be configured with CORS to send HTTP headers that allow the script execution
8. A company’s security team requires that all data stored in the cloud be encrypted at rest at all times using encryption keys stored on-premises. Which encryption options meet these requirements? (Select TWO.) 
	A) Use Server-Side Encryption with Amazon S3 Managed Keys (SSE-S3). 
	B) Use Server-Side Encryption with AWS KMS Managed Keys (SSE-KMS). 
	C) Use Server-Side Encryption with Customer Provided Keys (SSE-C). 
	D) Use client-side encryption to provide at-rest encryption.
	E) Use an AWS Lambda function triggered by Amazon S3 events to encrypt the data using the customer’s keys.
	**solution**
		C, D – Server-Side Encryption with Customer-Provided Keys (SSE-C) enables Amazon S3 to encrypt objects server side using an encryption key provided in the PUT request. The same key must be provided in GET requests for Amazon S3 to decrypt the object. Customers also have the option to encrypt data client side before uploading it to Amazon S3 and decrypting it after downloading it. AWS SDKs provide an S3 encryption client that streamlines the process
9. A company needs to maintain access logs for a minimum of 5 years due to regulatory requirements. The data is rarely accessed once stored, but must be accessible with one day’s notice if it is needed. What is the MOST cost-effective data storage solution that meets these requirements? 
	A) Store the data in Amazon S3 Glacier Deep Archive storage and delete the objects after 5 years using a lifecycle rule. 
	B) Store the data in Amazon S3 Standard storage and transition to Amazon S3 Glacier after 30 days using a lifecycle rule. 
	C) Store the data in logs using Amazon CloudWatch Logs and set the retention period to 5 years. 
	D) Store the data in Amazon S3 Standard-Infrequent Access (S3 Standard-IA) storage and delete the objects after 5 years using a lifecycle rule
	**solution**
		A – Data can be stored directly in Amazon S3 Glacier Deep Archive. This is the cheapest S3 storage class.
10. A company uses Reserved Instances to run its data-processing workload. The nightly job typically takes 7 hours to run and must finish within a 10-hour time window. The company anticipates temporary increases in demand at the end of each month that will cause the job to run over the time limit with the capacity of the current resources. Once started, the processing job cannot be interrupted before completion. The company wants to implement a solution that would allow it to provide increased capacity as cost-effectively as possible. What should a solutions architect do to accomplish this? 
	A) Deploy On-Demand Instances during periods of high demand. 
	B) Create a second Amazon EC2 reservation for additional instances. 
	C) Deploy Spot Instances during periods of high demand. 
	D) Increase the instance size of the instances in the Amazon EC2 reservation to support the increased workload.
	**solution**
		A – While Spot Instances would be the least costly option, they are not suitable for jobs that cannot be interrupted or must complete within a certain time period. On-Demand Instances would be billed for the number of seconds they are running