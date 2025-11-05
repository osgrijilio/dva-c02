# Availability

The availability of a system is typically expressed as a percentage of uptime in a given year or as a number of nines. In the following table is a list of availability percentages based on the downtime per year and its notation in nines.

|Availability (%) | Downtime (per year)
|-|-
|90% (one nine of availability) |36.53 days
|99% (two nines of availability) |3.65 days
|99.9% (three nines of availability) |8.77 hours
|99.95% (three and a half nines of availability) |4.38 hours
|99.99% (four nines of availability) |52.60 minutes
|99.995% (four and a half nines of availability) |26.30 minutes
|99.999% (five nines of availability) |5.26 minutes

To increase availability, you need redundancy. This typically means more infrastructure—more data centers, more servers, more databases, and more replication of data. You can imagine that adding more of this infrastructure means a higher cost. Customers want the application to always be available, but you need to draw a line where adding redundancy is no longer viable in terms of revenue.

## Add a second Availability Zone

The physical location of a server is important.

However, when there is more than one instance, it brings new challenges, such as the following:

- __Replication process__: The first challenge with multiple EC2 instances is that you need to create a process to replicate the configuration files, software patches, and application across instances. The best method is to automate where you can.

- __Customer redirection__: The second challenge is how to notify the clients—the computers sending requests to your server—about the different servers. You can use various tools here.
  - __Domain Name System (DNS)__, where the client uses one record that points to the IP address of all available servers. However, this method isn't always used because of propagation — the time frame it takes for DNS changes to be updated across the Internet.
  - __Load balancer__, which takes care of health checks and distributing the load across each server. Situated between the client and the server, a load balancer avoids propagation time issues. You will learn more about load balancers in the next section.

- Types of high availability – The last challenge to address when there is more than one server is the type of availability you need: active-passive or active-active.

  - __Active-passive systems__

    With an active-passive system, only one of the two instances is available at a time. One advantage of this method is that for stateful applications (where data about the client’s session is stored on the server), there won’t be any issues. This is because the customers are always sent to the server where their session is stored.

  - __Active-active systems__

    A disadvantage of an active-passive system is scalability. This is where an active-active system shines. With both servers available, the second server can take some load for the application, and the entire system can take more load. However, if the application is stateful, there would be an issue if the customer’s session isn’t available on both servers. Stateless applications work better for active-active systems.
