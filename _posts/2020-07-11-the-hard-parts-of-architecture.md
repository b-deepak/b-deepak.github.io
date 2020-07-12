---
layout: post
title: "O'Reilly Training: The Hard Parts of Architecture"
date: 2020-07-11 20:20 -0700
---

## Goal

![architecture hard parts summary]({{ site.url }}/assets/architecture_hard_parts_summary.jpg)

## Decisions

- It Depends. Decisions are a trade-off!
- Why > How
- Use Architectural Decision Record (ADR)
  - Title
  - Status
  - Context
  - Decision - **Justification (Technical and Business)**
  - Consequences - **Trade-offs**
- Example:

```
Title
----
Single consolidated payment service

Context
----
A customer can use any payment type combination (credit card, paypal, store credit, and gift cards) when placing an order.

Payment is required when pacing an order (synchronous activity). The payment logic can be either a single consolidated service or a separately deployed service for each payment type.

Decision
----
We will use a single consolidated payment service for all payment types.

Separating the services would require orchestration, which incurs both network and security latency. A single payment service will be more responsive since it does not require orchestration of each payment, therefore improving customer satisfaction when placing orders.

Consequences
----
The tradeoff of this decision is that maintenance, testing, and deployment will be impacted when changes are made to any of the payment types or another payment type is added. Testing scope is increased, requiring more time for complete testing. Deployment risk is increased as deploying a single service requires deployment of all payment types. Error handling and transactions are maintained in a single consolidated service, improving overall data integrity, data consistency, and performance when errors occur. This also improves overall customer satisfaction when placing orders.

The maintenance impact tradeoff was accepted by the business stakeholders in favor of better performance and data consistency when customers
```

## Architecture Characteristics

1. Synergistic
2. Ill-defined
3. Numerous Categories
4. Voluminous

## The 9's of Availability

Availability is usually expressed as a percentage of uptime in a given year.

| Availability %         | Downtime per year | Downtime per month | Downtime per day    |
| ---------------------- | ----------------- | ------------------ | ------------------- |
| 90% ("one nine")       | 36.53 days        | 73.05 hours        | 2.40 hours          |
| 99% ("two nines")      | 3.65 days         | 7.31 hours         | 14.40 minutes       |
| 99.9% ("three nines")  | 8.77 hours        | 43.83 minutes      | 1.44 minutes        |
| 99.99% ("four nines")  | 52.60 minutes     | 4.38 minutes       | 8.64 seconds        |
| 99.999% ("five nines") | 5.26 minutes      | 26.30 seconds      | 864.00 milliseconds |
| 99.9999% ("six nines") | 31.56 seconds     | 2.63 seconds       | 86.40 milliseconds  |

# Connascence / Coupling

> _[Connascence](https://connascence.io/) is a software quality metric & a taxonomy for different types of coupling._

Types:

1. **Static** - name, type, meaning, position, algorithm
2. **Dynamic** - execution, timing, value, identity

Axes of Measure:

1. **Strength**
2. **Degree**
3. **Locality**

## Architectural Quantum

> An architectural quantum is an independently deployable component with high functional cohesion and synchronous dynamic quantum connascence.

## Choosing an Architecture

![choosing an architecture]({{ site.url }}/assets/choosing_an_architecture.jpg)

## Service Granularity

Get granularity right by iteration!

### Drivers

> _When should I consider breaking apart a service?_

- Functionality or Domain
- Code Volatility
- Scalability and Throughput
- Fault Tolerance
- Data Security

### Factors

> _What factors influence service granularity?_

- Database Transactions
- Data Dependencies
- Communication Pattern i.e. Orchestration (Workflow) vs Choreography

## Evolutionary Architecture

An evolutionary architecture supports **guided, incremental change** across multiple dimensions.

### Fitness Functions

> _Any mechanism that provides an objective integrity assessment of some architectural characteristic(s)._

Examples:

- Cyclic Dependency Function in Code Quality Tools
- Zero Day Security Check Function in Build Pipeline
- Contract Fitness Function using [Consumer Driven Contracts](https://www.martinfowler.com/articles/consumerDrivenContracts.html)
  - Tool: [Pact](https://docs.pact.io/)

Architecture Governance Tools:

- Java - [ArchUnit](https://www.archunit.org/)
- .NET - [NetArchTest](https://github.com/BenMorris/NetArchTest), [SonarQube](https://www.sonarqube.org/)

## Coupling

> _Aim for **High Semantic Coupling** & **Low Syntactic Coupling**_

**Contract Types and Trade-offs**

| Strict Contracts                          | Value Based Contracts      |
| ----------------------------------------- | -------------------------- |
| Method Signatures. Ex. SOAP, gRPC etc.    | Name-Value Pairs. Ex. JSON |
| better control of exact parameter passing | requires fitness functions |
| brittle architecture coupling             | requires documentation     |
| better documentation via type signatures  | extremely loose coupling   |

## Managing Data in a Distributed System

- Inter-Service Communication
- Data Replication
- In-Memory Replicated Cache
- Data Domains (Shared Tables)

## Achieving Scalability and Elasticity

Patterns to leverage in Microservices:

- Cache
- Sidecar Containers with Service Mesh
