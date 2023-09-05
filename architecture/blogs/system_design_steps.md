# Overview

Building software isn't just about following instructions; it's like combining science and art while staying flexible as the software is used more.

First, let's talk about the science part. By science, we mean:

- Understanding computer science.
- Knowing the basic building blocks and how they fit together.
- Turning customer requests into technical plans.
- Thinking beyond just the basics.
- Picking the right tools and using them effectively.
- Analyzing and communicating well.

Now, let's talk about the art part! It's not just about using computer science; it's about making a system that people find easy to use. Some skills you might need:

- Dealing with humans who is going to build the system
- Making it user-friendly.
- Understanding what users want, even if they can't express it clearly. Imagining how people will use it today and tomorrow
- Thinking creatively but staying practical.
- Staying on track, even if time is limited.

There's a lot to learn about each of these aspects, so we won't cover everything here. This sets the stage for how we approach designing a system. Let's define the problem:

> "I've been given a task: design a system that does what's asked, and also make sure it can handle lots of users, run smoothly, and be easy to monitor. And we should explore different solutions instead of sticking to just one."


Certainly, here are some examples of system design:

1. Develop a system for generating short URLs.
2. Create a system to track and manage the inventory of collected garbage.
3. Design a system to evaluate job seekers' qualifications based on various internet data sources.
4. Implement a distributed caching system for improved data access


# Approach

In simple words, it's essential to plan things out carefully before diving into a project, rather than jumping straight into using all your tools and techniques. You should also be willing to make changes and improvements along the way instead of sticking to one fixed path. Think of it like using Agile Engineering methods.From my perspective, we can break the whole process down into these steps:

- Step 1: **_Grasp the problem_**
- Step 2: **_List requirements_**
- Step 3: **_Specify assumptions and constraints_**
- Step 4: **_Define system interface_**
- Step 5: **_Architecture_**
- Step 6: **_Define system interaction_**
- Step 7: **_High-level Design_**
- Step 8: **_Operability and Observability_**
- Step 9: **_Enhancing Efficiency, Building Resiliency, and Protecting Digital Assets_**


After iterating through steps (1)-(9), repeat the process to establish a transition architecture. Transition architecture is crucial because of the following real-life truths:

* _Rome can't be built in a day._
* _Today's priorities can change._
* _Technology keeps evolving._
* _Executives prefer avoiding reinventing the wheel._
* _Resources, including money and time, are limited._
* _Striving for the best can hinder system evolution._

Let us deep-dive into each of the above step.

# Step 1: Grasp the problem

To truly grasp the problem, engage with it actively and analyze it from different angles. Remember, no two minds think exactly alike. It's not just about focusing on what's explicitly asked; it's equally important to consider what's not being asked. Here are some thought-provoking questions to guide you:

- What is the specific request or problem statement?
- How does the system under consideration interact with other systems, if any?
- Who will be the primary users of the system? Are they human users, automated bots, or other systems?
- Which 2-3 vital processes or flows within the system are indispensable for resolving the issue?
- What input does the system receive?
- What is the expected output of the system?

# Step 2: List requirements

You've understood the problem in plain language. Now, it's time to translate it into engineering terms. It's time to identify high-level epics, avoiding diving too deeply into specific stories. Additionally, pay attention to non-functional aspects that might not have been initially mentioned. Here are some guiding questions:

1. **Functional**:

    - What interfaces need to be developed?
    - What resources (or nouns) does the system require to support?
    - What functions (or verbs) must the system support that non-resource elements (or nouns) want to execute?

2. **Non-functional**:

    - What availability requirements should be met?
    - What performance requirements are needed for normal, low, and high traffic scenarios?
    - Are there any resource constraints, such as computing power, storage, or network capabilities?
    - What scalability expectations exist? Note that scalability considerations are closely 	related to other requirements.
    - Are there any security constraints to consider?
    - Who is going to access the system from where and when?

# Step 3: Specify assumptions and constraints

Once you've completed this process, don't hesitate to further refine the following: (1) **_Assumptions_** and (2) **_Constraints_**. Here are some guiding points:

### Assumptions:

1. **Input**

    - How we gather input data?
    - Different types of input: **_User Input**_, **_Collaborating Service Input, **_Closed Loop Input**_.
    - Formats of input data: **_JSON**_, **_Database Tables**_, **_Files**_.
    - The frequency of collecting input data.

2. **Output**

    - How we generate output data.
    - Formats of output data: **_JSON_**, **_Feeds_**, **_Notifications_**, **_Database Tables**_.
    - The frequency of generating output data.
    - How the output is produced (or used?: **_Sync_**, **_Async_**, or **_Both_**.


### Constraints:

- **Scale vs. Time**. Dealing with scalability limitations.
- **Performance**. Performance considerations under specific loads.
- **Security**. Ensuring security measures are in place.
- **Data Consistency**. Ensuring how we will make data consistent by when.
- **Fail-over Scenarios**. Dealing with availability aspect.


# Step 4: **_Define system interface_**

In the system design document, it's essential to adopt a top-down approach and consider the user's perspective, whether they are human, bots, or other systems. Designing the right interface is crucial to understanding how our system will be accessed. There are primarily two key aspects to address:

1. Communication Protocol: Choosing the appropriate communication protocol, which can be one of the following:
    - REST
    - GraphQL
    - gRPC
    - Message Queue
2. Request and Response Payload for the Communication Interface: Defining the structure of the data transmitted through the interface, which can be in the form of:
    - Messages
    - JSON Schemas
    - Feed data

These considerations help ensure that the system's interface is well-designed to meet user requirements. For any interface style, it's crucial to focus on the following specific details:

1. Request Traceability: Ensuring that requests can be tracked and monitored effectively to understand their flow and status.

2. Request Processing Mechanism: whether requests are processed synchronously or asynchronously, depending on the system's requirements.

3. Handling Response Data: Establishing mechanisms to handle responses that may contain both small and very large datasets efficiently.

4. Handling Failed Requests: Implementing mechanisms to address scenarios when a request in transit crashes or fails midway to ensure data integrity and appropriate handling.

5. Idempotency of Requests: Ensuring that repeated requests, even if executed multiple times, have the same outcome, preventing unintended side effects or data corruption.

# Step 5:  Architecture

Now is the crucial moment to select the components that will serve as the fundamental building blocks in crafting the system. It's important to acknowledge that there are countless ways to address challenges by arranging and combining these building blocks in various configurations. For instance, one could employ Cobol for Machine Learning, use SQL to manage extensive datasets, or employ polling mechanisms to gather change data. However, it's essential to pause and reflect: is this the right strategy? Also, all depends upon what architecture style you want to pick for specific portion of the system. Few choices you might have are:

1. **Layered Architecture**. Few patterns are:
    - LAMP
    - n-tier architecture
2. **Service Oriented Architecture**. Few patterns are:
    - Microservices
    - FaaS
    - Broker
    - SOA
3. **Event Driven Architecture**. Few patterns are:
    - Pub-SUB
    - Even Driven
4. **Data Centric Architecture**. Few patterns are:
    - Kappa
    - CQRS
    - Kappa
    - Lambda
    - Event Sourcing
5. **Component Based Architecture**. Few patterns are:
    - Microkernel
    - Plug-in
    - Object Oriented
6. **Concurrency Architecture**
7. **Orchestration Architecture**. Few patterns are:
    - Choreography
    - Pipeline
    - Primary-Secondary
    - Orchestration
8. **Interpreter Architecture**, takes high level instruction and translates to low level code
9. **Distributed Systems**, resolves the issue of large scale data and its consistency
10. **Domain Driven Design**, focus on domain complexity than technology


In my opinion, I don't believe that Domain Driven Design is a suitable fit for the list mentioned above. This is primarily because it focuses on breaking down a large system into smaller systems rather than zeroing in on specific technologies, which is the primary focus of the styles mentioned earlier. Instead, I view Domain Driven Design as an overarching approach to identify domains and then utilize one or more combinations of the styles mentioned above to implement specific domains. This topic warrants a separate blog post to delve into further detail. For now, it's important to ensure that you select the right approach for the specific service you're designing within the system.

Defining a foolproof strategy can indeed be challenging, but one is likely to make sound decisions by following this approach.

1. **Identify the Business Domain**, divide into multiple if required.
2. **For a Given Domain, Identify the Services** (Primarily the Starting Point):
    - API Service
    - Storage Service
    - Data Collector Service
    - dentify the Interactions Among Respective Services
3. **Identify the Interactions Among Respective Services**
4. **Identify Building Blocks (or Technology Choices) for Each Service**
5. **Sketch the Overall Picture**. This step involves creating a comprehensive overview of the entire system, ensuring that all components and interactions are captured in a clear and concise manner.


# Step 6:  Define system interactions


Now, it's time to select 2-3 critical flows and define system interactions. We'll categorize interactions into the following scenarios:

1. **Day-Zero**: This step may require dealing with specific circumstances such as:

    - Pre-loading data.
    - Establishing communication with other systems.
    - Initializing application infrastructure.

2. **Everyday Operations**: This involves the routine execution of defined flows, including:

    - Executing flows in the presence of misbehaving neighbors.
    - Handling flows in the presence of misbehaving users.
    - Executing flows when encountering invalid inputs.

3. **Recovery from Failure**: This scenario deals with handling failures and includes:

    - Addressing half-processed solutions.
    - Managing live request processing versus processing backlogs.


# Step 7:  High-level Design

It's indeed the right time to choose the components that will serve as the building blocks in constructing the system. It's important to note that almost any problem can be addressed through various permutations and combinations of these building blocks. However, the correct strategy is key. Here are some aspects to consider:

1. **Input and Output Processing**

    - Choosing between REST, GraphQL, or gRPC.
    - Selecting between Webhooks or Websockets.
    - Deciding between Polling and Event-Driven Architecture.
    - Balancing between Synchronous and Asynchronous communication.

2. **Application Infrastructure**

    - Computing resources: Container vs. Virtual Machine (VM).**
    - Storage options: Block, Object, or Object Storage.
    - Network accessibility: Local, Regional, or Global.

3. **Storage**

    - Determining consistency or eventual consistency
    - Considering data size and types: Content, Index, User.
    - Choosing between SQL, NoSQL, or Time Series databases.

4. **Service-to-Service Communication**

    - Opting for REST or gRPC for communication.
    - Deciding between direct calls or utilizing a Message Broker.
    - Balancing between Synchronous and Asynchronous communication.

5. **Performance**

    - Scaling options: Segmented or Horizontal scaling.
    - Deciding on Distributed Cache or Local Cache usage.
    - Utilizing appropriate data indexing data structures.
    - Selecting data transfer protocols: Binary or JSON.

6. **Scalability**

    - Implementing auto-scaling based on load.
    - Managing 24x7 services versus scheduled tasks (cron jobs).

7. **Security**

    - Implementing Authentication and Authorization.
    - Ensuring proper auditing mechanisms.
    - Considering Single Sign-On solutions.
    - These choices will play a crucial role in shaping the system and its capabilities.


Absolutely, in this step, it's important to consider these aspects as well:

1. **ER Diagram**: This diagram is often influenced by the Domain Model and helps in visualizing the structure of the data and how different entities and attributes are related.

2. **Database Schema**: Defining the schema of your database is crucial for organizing and storing data efficiently, ensuring data integrity, and enabling effective querying.

3. **In-Memory Data Structures**: If specialized processing requires in-memory data storage for rapid access and manipulation, you should define and implement the necessary data structures to support these operations.

4. **Indexing Strategy**: Developing a well-thought-out indexing strategy is essential to optimize data retrieval and query performance, ensuring that the database can efficiently handle various types of queries and operations.

# Step 8: Operability (includes Observability)

Addressing non-functional aspects, especially operability, from the very beginning is crucial. An operable system should have a well-defined strategy that includes:

1. **Correct Telemetry**: Comprehensive logs, metrics, and alerts that provide visibility into system behavior and performance.

2. **Auto-Detection of Failure**: Implement mechanisms that can automatically detect failures, notify relevant parties, and, if possible, take corrective actions.

3. **Resilience to Bursty Traffic**: Design the system to withstand sudden spikes in traffic or load without significantly degrading performance.

4. **Resilience to Cyber Attacks**: Incorporate security measures to protect against cyber attacks, noisy neighbors, and unauthorized access.

5. **Auto-Scaling**: Implement auto-scaling mechanisms to dynamically adjust system resources to handle varying workloads effectively.

Taking these aspects into account helps ensure the system's stability, reliability, and ability to adapt to changing conditions and challenges.


# Step 9: Enhancing Efficiency, Building Resiliency, and Protecting Digital Assets

Now that we have the initial design ready, let's explore how we can make it even better.This section focuses on ensuring that the system is resilient, optimized for performance, and safeguarded against potential threats to digital assets.

1. **Availability**: This involves ensuring that the system is consistently operational and accessible.

    - Active-Passive / Active-Active Deployment: Implementing a redundant system setup where there are either backup systems (active-passive) or multiple active systems (active-active) to ensure continuous service in case of failures.

    - Auto-Start on Failure: Setting up mechanisms that automatically restart components or services in case they fail, reducing downtime.

    - Availability SLO (Service Level Objective): Defining and adhering to specific availability targets, often expressed as a percentage (e.g., 99.9% uptime).

    - Multiple-AZ / Multiple-Region Deployment: Deploying the system across multiple Availability Zones (AZs) within a region or across multiple regions to enhance redundancy and fault tolerance.

    - Degraded Availability even if Failure Occurs: Designing the system to gracefully degrade its functionality, allowing it to continue operating in a limited capacity even in the event of a failure.

2. **Performance**: Making the system faster and more efficient. For example:

    - Separating the paths for reading and writing data.
    - Automatically adjusting resources based on demand (auto-scaling).
    - Handling storage read and write operations separately.
    - Using indexes for frequently accessed data.
    - Implementing caching mechanisms.
    - Utilizing load balancers.
    - Implementing single sign-on for security.

3. **Security**: Enhancing the system's protection. For instance:

    - Enabling HTTPS for secure communication.
    - Implementing OAuth 2.0 for authorization.
    - Setting up a Dead Letter Queue for handling undeliverable messages.

4. **Operability**: Ensuring that the system is easy to operate and maintain. This includes:

    - Adding message codes to application messages for easier debugging.
    - Establishing a support channel based on Logging, Log Monitoring, and Alerting (LLM).
    - Implementing auto-remediation to automatically resolve issues.
    - Each of these areas deserves its own in-depth discussion to fully understand and implement the optimizations effectively.

5. **Backup and Restore Strategy**: This plan involves regularly making copies of your data (backups) and having a plan in place to put things back to normal (restore) in case something goes wrong. It's like creating copies of important documents so that if you lose one, you can retrieve it from your copy.

6. **Disaster Recovery Strategy**: This strategy is all about being prepared for the worst-case scenario. It includes plans and actions to ensure that your systems and data can be quickly recovered and made operational again after a major disaster, like a fire or a severe hardware failure. Think of it as a safety net for your digital assets in case of a catastrophe
