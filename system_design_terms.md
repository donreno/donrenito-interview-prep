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