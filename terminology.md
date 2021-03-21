 AWS region or regions where your application is hosted. 
 In the background, 
 Amazon’s DNS service (called Route 53) :
 will successfully connect you to your hosted application at AWS.
 
 Route 53 can also assist in connecting you to your hosted application when it’s running in multiple regions, connecting you to the closest location.
 
 
 If you’re planning to move applications from your corporate data centers to the AWS cloud, the location of your place of business might influence the AWS region that you want to utilize if you are planning to operate in a hybrid model (with some resources remaining in the corporate data center and some resources hosted in the cloud).

Selecting a location closest to your corporate data center may not matter at all if all your applications are moving to the AWS cloud.

If you’re creating a public-facing SaaS application, you may think that you need to choose a region closest to where most users are located. The reality is, you’ll solve this issue by using Amazon’s content delivery network (CDN), called CloudFront. You can find more details on CloudFront in Chapter 6, “Cloud Storage.”

Region Isolation
As mentioned, each AWS region is an isolated entity; AWS regions are physically and securely separated from each other, as shown in Figure 2-4. Depending on the scope of your design, the region that you choose to operate in at AWS may always remain separate from the other regions. Or you may decide to use a database service such as DynamoDB, AWS’s managed NOSQL database solution and utilize a feature called global tables, which are hosted and replicated across multiple regions. Perhaps over time, you will decide to operate in multiple regions and use Route 53 for geo-load-balancing your applications hosted in different regions.

Separation of Essential AWS Services
Within each region, AWS has a variety of cloud services designed to support the customers’ needs for storage, load-balancing, DNS services, managed database services, and more. Would it really make sense to have all AWS cloud services offered within a region contained within data center facilities? Amazon doesn’t think so. All AWS cloud services have been designed to be durable and redundant and to retain the ability to fail over when disaster strikes to other backup services contained within the region.

We also don’t know how many separate regional buildings contain these supporting cloud resources and services, but it’s handy to visualize a large cluster of strategically placed buildings as shown in Figure 2-5 wired together with high-speed private networking that supports the nested availability zones contained within each region. A private AWS networking campus spread across each region is designed for fault tolerance and failover.

AVAILABILITY ZONES
An availability zone (AZ) is defined as one or more data centers inside a region. Each region is sliced up into multiple AZs, as shown in Table 2-1. Each AZ is linked to the other AZs in the region through dedicated, redundant, low-latency fiber connections. Internal AWS private network speeds are in the 40 Gbps range. All AZs within a region are linked to each other with redundant private network links that AWS owns.

Region Code : ca-central-1
Region Name : Canada
Availability Zones: ca-central-1a ca-central-1b

A failure of an AZ (typically a single physical data center located within the AZ) will not affect and derail the operation of the AWS services that are specifically designed to live outside the AZs. For example, Amazon’s S3 storage and Elastic Load Balancing (ELB) services are specifically designed to integrate with the data centers within each AZ; but each of these services functions as a standalone entity that will continue to function even if one or all the data centers located within an AZ have failed.

In addition, services defined as global services are designed to sit outside the regions themselves at the perimeter of AWS, defined as the edge location—specifically, DNS services such as Route 53, and CloudFront, AWS’s CDN. You can find more about Route 53 in Chapter 3; for CloudFront, you can find details in Chapter 6.

Even though each AZ is backed by a cluster of multiple data centers, it’s important to also grasp that no two AZs share the same single data center. Each AZ is also isolated from the other AZs within the region.



