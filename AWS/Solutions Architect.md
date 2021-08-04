Domain 1: Design Resilient Architectures
	1.1 Design a multi-tier architecture solution
> Determine a solution design based on accesspatterns.
	> Identify how data will be queried
		> Access patterns matrix
		> Priority queries usually are the most used or most relevant queries. It is also important to identify queries that require lower response latency.
	> Determine a scaling strategy for components used in a design.
		> Auto Scaling Stratgies
			> availability
			> balanced (cost + availability)
			> cost
	> Select an appropriate database based on requirements.
		![[Pasted image 20210801213737.png]]
	> Select Compute
	> Select storage services

**Access pattern**

Provide a name for the access pattern.

**Description**

Provide a more detailed description of the access pattern.

**Priority**

Define a priority for the access pattern (high/medium/low). This defines the most relevant access patterns for the application.

**Read or write**

Is it a read access or write access pattern?

**Type**

Does the pattern access a single item, multiple items, or all items?

**Key attribute**

What is the key attribute used to access data?

**Filter**

Does the access pattern require any filter?

**Sort**

Does the result require any sorting?

[source](https://docs.aws.amazon.com/prescriptive-guidance/latest/dynamodb-data-modeling/template-access-patterns.html)
