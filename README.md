# Company_file_service
This repository will contain an infrastructure diagram describing bottlenecks of the whole service with estimated costs.

# Problem
- Provide an infrastructure diagram describing bottlenecks of the whole service with estimated costs for 1,000, 1,000,000, and 1,000,000,000 users with 10gb files -- %40 video -- and 1000 requests per user/day.

# Solution
*Note: Since I don't have clear information about the develpment of the application, I am assumming everything on my end. Also note that this is a general high level overview on how this solution could be implemented, just for guidance.*

For this approach, since I don't a long track doing architecture for an environment like this, I will use an approach similar to what Netflix does for their video streaming application. They are the best in this field and I think it's a good idea to learn from them.

In order to release some of the infraestructure managemente, we will place everything in the cloud, being AWS the one we will use for this case but I think any major cloud provider will do.

### Diagram

![Diagram](infrastructure.jpg)

1. The Client sends a Play request to Backend running on AWS. That request is handled by AWS Load balancer (ELB)

2. AWS ELB will forward that request to API Gateway Service running on AWS EC2 instances. 

3. Application API component is the core business logic behind the application operations.

4. Play API will call a microservice or a sequence of microservices to fulfill the request.

5. Microservices are mostly stateless small programs and can call each other as well.

6. Microservices can save to or get data from a data store during its process.

7. Microservices can send events for tracking user activities or other data to the Stream Processing Pipeline for either real-time processing of personalized recommendation or batch processing of business intelligence tasks.

8. The data coming out of the Stream Processing Pipeline can be persistent to other data stores such as AWS S3, Hadoop HDFS, Cassandra, etc.


### Estimated Cost



# Problem
- How would you assure developer happiness for this service. Please send details about how local development environments are set, what are the rules for submitting code to
production?

# Solution
*Note: I would need to have a bit of more input about the application hosting this service, in order to design the proper dev env so, let's say this is a containerized app and will setup an agile containers based development environment*

For this case, I would deploy a coulple of kubernetes clusters in order to host 

- Which best practices should be applied while working with a team of 20 developers?

- Describe how the CI/CD infrastructure should be for this kind of service.
