# M1
### Replication & Consistency 
The replication of data increases reliability, improves performance and scales (numbers and geographic zones)

Benefits in distributed systems: 
- reliability 
- fault tolerance 
- accessibility 
- performance 
- scalability

Problems in distributed systems: 
- cost 
    - computational resource
    - bandwidth 
- consistency

# Distributed Systems. Principles and Paradigms - book 
Definition of distributed system: 
> A distributed system is a collection of independent computers that appears to its users as a single coherent system.

Meaning that distributed systems are composed of autonomous components and create the illusion of a single system for the user.
In order to provide the same experience to all users there are layers between application and middleware.
A distributed system should:
- make resources easily accessible: it's cheaper to share  resources and make collaboration easier
- it should reasonably hide the fact that resources are distributed across a network
- it should be open (?)
- and it should be scalable

### Goals for distributed systems 

*Transparency* means hiding that the process and resources are distributed throw multiple computers.

Different types of transparency:
    - access: hide difference in data rapresentation and how resources are accessed
    - location: hide where resources are located
    - migratio: hide that a resource may move to another location
    - relocation: hide that a resource may move to another location while in use 
    - replication: hide that a resource is replicated 
    - concurrency: hide that a resource may be shared by several competitve users 
    - failure: hide the failure and revcovery of a resource 

Degree of transparency: 
