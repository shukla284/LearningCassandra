# Cassandra Operations

* There is interface node which is handling the operations for the cluster commodity systems. These systems are running the instances for storing the data for cassandra, since the data is distributed across these nodes. 

* Now the thing is the data is distributed so there should be some component which handles the queries for the database and how the results would be collected out of the different systems which are containing the actual data. 

* For the above purpose there is something which needs to communicate and fetch the queries from the actual data sources. So the interface with which the application talks or which acts as the proxy for the clusters so that the application needs not to perform the result aggregation for the query is quite simplified. 

* Now the interface handles the queries like update/read/write from the application and gets the results for the same easily, now since this node might go down and create SPOF in our application. Now to avoid this the coordinator decision takes place in case the current node goes down. 

* The database application is decentralized in a way so that application may not fall apart in this case of failure. The cassandra architecture is decentralized which provides with the correct required configuration in that respect. 

* Another database which is similiar to this is HBASE which is part of Apache Hadoop is also column oriented database & distributed in nature. While cassandra is de centralized so that there may be lesser point of failures for that, while the HBase is not as such it is more of kind of dependent on the name server which creates a SPOF. 