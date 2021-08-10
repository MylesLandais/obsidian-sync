
# Frequently Asked Questions
- What are the benefits of Amazon SQS over homegrown or packaged message queuing systems?
	- Development overhead, Scalability, high message durability, maitnence costs
- How is Amazon SQS different from Amazon SNS?
	- SNS is for time critical applications by pushing otifications. SQS uses a polling model allowing for decoupling of services
- How Is SQS different from MQ
	- [[MQ]] is recommend if your already using messaging with existing applications as it extends functionality of [apache activemq](https://activemq.apache.org/) , and [rabbitmq](rabbitmq) If you are building an application cloud first it would be advised to use a managed query service
- Does Amazon SQS provide message ordering?
	- SQS uses a loose-FIFO attempts to preserve the order messages are sent in
- Does SQS quarentee delivery of messages
	- Messages will be sent "at-least-once". Each message is on the queue once, no duplicates allowed, deleted when processed by consumer.
- How is SQS different from [[Kinesis Data Streams]]
	- SQS is a FIFO queue while Kinesis is a real time stream
- 
# Refrences
- https://aws.amazon.com/sqs/faqs/
- 