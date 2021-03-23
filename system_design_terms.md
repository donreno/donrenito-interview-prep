# System design Terms
Multiple System Design or Distributed Systems Terms.

## Client Server
A client - Server model is a model where clients requests data or services to servers.

### Client
A machine or process that requests data or service from a server.

### Server
A machine or process that provides data or service requested by a client.

### DNS
Domain Name server, a server that provides ip addresses for given hostnames.

## Network Protocols

### IP (Internet Protocol)
**I**nternet **P**rotocol, mostly every other protocol is build on to of it.
(TCP, UDP, HTTP, etc...)

### TCP (Transport Control Protocol)
Built on top of IP allows ordered and reliabla data delivery between machines, a socket server runs over *TCP*.

### HTTP (Hypertext Transport Protocol)
Built on top of TCP, it's based on a request response model where both are composed of different attributes.
- Request: Host, Port, Method, Headers and Body
- Response: Status, Headers and Body

### IP Packet
Internet Protocol Packet, is composed of 2 parts:
- IP Header:Network info for source and destination
- Payload: Data being sent

## Latency and Throughput

### Latency
Time that takes an operation to be completed.
**e.g**:
- Reading **1mb** from **memory**: `250 microseconds`
- Reading **1mb** from **SSD**: `1 milliseconds`
- Transfer **1mb** over **Gigabit Network**: `10 milliseconds`
- Reading **1mb** from **HDD**: `20 milliseconds`
- **Intercontinental** round trip: `150 milliseconds`

### Throughput
The number of operations that a system can hgandle per time unit. **e.g**:
- **RPS**: Reads per second, request per second.
- **TPS**: Transactions per second.
- **QPS**: Queries per second.

## Availability

### Availability
Odds for a service to be available, e.g: 99.99%

### Nines
Numer of nines representing uptime o availability of a service.

| # of Nines | Percentage representation |
|    ---     |         ---               |
|     2      |         99%               |
|     3      |         99.9%             |
|     4      |         99.99%            |
|     5      |         99.999%           |

### Redundancy
The process of replicating parts of a service/system.

### SLA
Stands for Service Level Agreement, are guarantees given to a customer can be composed of 1 or many SLO's.

### SLO
Service Level Objective, typically an SLO will be the availability of a Service.

## Cache

### Cache
Hardware or service that stores data to be retrieved faster, the catch is that cached data can become *stale* quickly.

### Cache Hit
When requested data is found on cache

### Cache Miss
When requested data is not found on cache

### Cache Eviction Policy
The policy by which values are evicted (or removed) from the cache. **e.g**: *LRU, FIFO, LFU...*

### CDN
Content Delivery Network, it's a cache that is tipaclly used to store blobs, media or files that might be used frequently or needs to be accesed from other regions, then is replicated on those region's CDN.

## Proxies

### Forward Proxy
Server that sits between a client and a server, it act's on behalf of a client, usually to hide client information.

### Reverse Proxy
A server that sits between a client and a server and acts on behalf of a server. Typical reverse proxies would be a load balancer, a cache like varnish, etc...

### Nginx
Web server often used as reverse proxy or load balancer

## Load Balancing

### Load Balancer
A type of reverse proxy that distributes traffic across servers.

### Server selection strategy
How a load balancer chooses servers when distributing traffic. **e.g**:
- Round Robin
- Random
- Based on performance metrics
- Ip Based
- etc...

### Hotspot
When distributions falls more oftenly on a single server this one becomes a hotspot.

## Hashing

### Consisten Hashing
A type of hashing that minimizes the number of keys that need to be remapped, oftenly used by load balancers.

### Rendezvous Hashing
A type of hashing also coined as "highest random weight" allows minimal redistribution.

### SHA
Stands for Secure Hash Algorithms, collection of cryptographic algorithms used in the industry like SHA-3, SHA-256, etc...


## Databases

### Relational DB
Tabular formatted stored data that relies on relationships between tables, relys on SQL as Query language.

### Non-Relational DB
DB's that not necessarily imposed on tabular struct, oftenly refered as NoSQL (Not Only SQL)

### SQL
Structured Query Language

### SQL DB
DB's that support SQL

### NoSQL DB
An not SQL compatible DB

### ACID Transaction
Transactions with 4 important properties
- Atomicity: All succeeds or all fails.
- Consistency: The transaction does not end on an invalid state on a DB.
- Isolation: The concurrent execution will have the same effect if runned concurrently.
- Durability: Any commited transaction will be stored on permanent storage.

### DB Index
Auxiliary data structure that helps to find data faster.

### Strong Consistency
Refers to ACID consistency

### Eventually Consistent
Could return stale views of a system, but at times or maybe most of the time, data will be consistent.

## Key-Value Stores
Flexible NoSQL db oftenly used for caching or dynamic config.

### etcd
Strongly consistent and highly available Key value store, also provides leader election.

### Redis
In memory key-value store, tipically used as cache or rate limiting solution.

### Zookeper
Strongly consistent and Highly available key-value store from Hadoop ecosystem, oftenly used for leader election. 

## Specialized Storage

### Blob Storage
Sort of key value store for large binaries, DB Snapshots or images.

### Time Series DB
Stores time indexed data, influx, prometheus or graphite.

### Graph DB
Stores data using graphs (Neo4j)

### Cypher
Cypher query language, it's originally from Neo4j.

### Spatial DB
DB specialized on a Map, oftenly relies on Quadtree data struct.

### Quadtree
It's a kind of tree where each node has 0 or 4 child nodes, that is required to represent quadrants.
Operations runs on `log (x)` time (Where **log** is base **4** because of the 4 child nodes).

### GSC
Google Cloud Storate, a blob store provided by google.

### S3
Blob storage provided by Amazon.

### InfluxDB
Popular time series DB.

### Prometheus
Popular time series DB, oftenly used for monitoring and dashboards (Similar to Graphite)

### Neo4j
Popular Graph DB.

## Replication and Sharding

### Replication
The act of duplicating data from one DB Server to another, oftenly used to increase redundancy or moving data closer to clients (Regions)

### Sharding
Also called Data Partitioning, is the act to partition data into 2 or more pieces, there might be different criteria to shard a DB, here are some examples:
- Sharding based on **region**.
- Sharding based on **time**.
- Sharding based on the **hash of a column**.
- Sharding based on **business rule**.

### Hot Spot
When distributing load across a set of server that load might get spreaded unevenly causing one of the servers to get heavy loaded, oftenly this happens because a suboptimal sharding key.

## Leader election

### Leader Election
The process by which nodes in a cluster elect a so called leader responsible for the primary operations of the supported services.

### Consensus Algorithm
Complex Algorithm used to have multiple entities agree on a single data value (like leader election).

### Paxos & Raft
Two consensus algorithms that when implemented  correctly allows sync of certain operations like leader election.

## Peer to Peer network

### Peer to peer networks
Is a collection of machines refferred as peers that divide workload between themselves.

### Gossip Protocol
When a set of machines talk to each other in an uncordinated manner to spread info through a system without requiring a control source of data. **e.g**: BitTorrent.

## Polling and streaming

### Polling
Fetching data at a given interval making sure data that you receive is not too old or stale.

### Streaming
Continuously getting feed from a server by keeping an open connection the whole time.

## Rate limiting

### Rate limiting
Limiting request sent to/from a server, oftenly used to prevent DOS attacks.

### DOS Attack
Denial of service attack, normally done by flooding a service with loads of traffic.

### DDOS Attack
Distributed denial of service, in this case flooding comes from many sources.

## Logging and monitoring

### Logging
Collecting and storing logs from applications.

### Monitoring
Having visibility of a system's key metrics.

### Alerting
Process trough which a system admin or team will get notified when critical issues occur.

## Publish and subscribe

### Pub/Sub
Messaging model that consists of publishers and subscriber, in this model publishers will publish a message to a topic or channel where subscribers will read. Normally it guarantees at least once delivery.

### Idempotent Operation
An operation that has same output regardless of how many times is executed.

### Apache Kafka
Distributed messaging system created by linkedIn, useful when streaming over polling.

### Google cloud Pub/Sub
Highly scalable messaging system created by Google, guarantees **at least once delivery** and **rewinding**.

## Map Reduce
Popular framework for processing large datasets in a distributed manner, meaning that most operations are done on nodes where data is stored (On a Distributed file system).

### Map
Transforms chunks of data into an intermediate key-value pairs.

### Shuffle
Reorganizes key-value pairs so pairs with same key are routed to the same machine.

### Reduce
Runs a reduce function on the newly shuffled key-value pairs transforming into meaningful data.

### Distributed file system
Abstraction of a file syste that runs on multiple machines, couple of popular ones are GFS (Google File System) and HDFS (Hadoop Distributed File System).

### Hadoop
Popular opensource framework that supports MapReduce on top of HDFS.

## Security and HTTPS

### MITM Attack
Man In The Middle Attack, attack where the attacker intercepts comunications between a client and a server or two servers, these are the main threat that encryption and HTTPS aim to protect from.

### Symmetric encryption
Type of encryption that relies on a single key to both encrypt and decrypt.

### Asymetric encryption
AKA Public Key encryption, relies on 2 keys Public and Private keys, data encrypted with public key can be decrypted only with private key.

### AES
Advanced encryption standards has 3 symetric algorithms **AES-128**, **AES-192** and **AES-256**

### HTTPS
HTTP Secure, it requires servers to have trusted SSL certificate issues, uses TLS on top of TCP.

### TLS
Transport Layer Security, security layer on top of TCP.

### SSL Cert
Digital certificated issued by an authority, used on TLS Handshake.

### Certificate Authority
Trusted Authority that signs and issues digital certificates.

### TLS Handshake
Process through which a client and server communicating through https exchange encryption related info.

1. Client sends client hello to server.
2. Server responds with server hello and the SSL Cert (which contains public key).
3. Client verifies that cert was issued by a Certificate Authority and sends a premaster secret.
4. Then the client and the server uses client hello, server hello and premaster secret along with public key and private keys to generate the same symetric encryption.
