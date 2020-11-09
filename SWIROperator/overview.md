
 * Three microservics Helpdesk, Magazines and Books are a part of a bigger Library solution
 * Helpdesk makes HTTP REST calls to obtain data from Magazines and Books services
 * Helpdesk doesn't know where the Magazines and Books APIs are exposed or what protocol to use
 * SWIR Sidecars are used to discover services, call APIs and secure transport layer
 * SWIR Operator is used to detect when SWIR Platform deployment is used and configure SWIR Sidecars appropriately
 
![Service Discovery and Invocation](https://raw.githubusercontent.com/swir-rs/swir/master/graphics/example-solution-sdi.png)
