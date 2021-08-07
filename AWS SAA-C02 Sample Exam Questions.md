1. A customer relationship management (CRM) application runs on Amazon EC2 instances in multiple
Availability Zones behind an Application Load Balancer.
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
			When the ReceiveMessageWaitTimeSeconds property of a queue is set to a value greater than zero, long polling is in effect. Long polling reduces the number of empty responses by allowing Amazon SQS to wait until a message is available before sending a response to a ReceiveMessage request.