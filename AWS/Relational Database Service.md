Managed database services

Provisioned on [[amazon EC2]] instances and [[Amazon Elastic Block Volume (Amazon EBS)]]

Engine options
	- postgres
	- maria/mysql
	- Oracle
	- Microsoft

Free Tier mysql + postgres

Templates
	- Free tier
	- Production
	- Dev/Test
	
Storage Autoscaling

Availability & Durability
	Create a standby instance for production
	
Connectivity
	Default VPC 
	publically accessible?
		you only want to expose to your application
Security through IAM, Security Groups, KMS
Backups and Snapshots
Monitoring through CloudWatch
