## Architecture

There are many excellent resources that explore various architectural patterns deeply; one of my favorites is Martin Fowler's *Patterns of Enterprise Application Architecture*. In this chapter, I'll provide a summary of some key phrases you'll hear so you have context when exploring these topics in depth elsewhere.

### Domain-Driven Design

Domain-driven design (DDD) is an approach to software development that focuses on understanding and modeling the problem domain in order to design better software solutions.

The core concepts of DDD include:

**Domain model:** A representation of business concepts as objects in your technical system;

**Ubiquitous language:** A common, consistent vocabulary and language that is used across your company to minimize confusion;

**Bounded context:** The boundary within which the domain model applies and where the ubiquitous language is used.


#### High-Level Patterns

When somebody uses the phrase technical architecture, they are usually referring to how code is executed and how information moves around in a system. Most descriptions of architecture involve the phrases services, monoliths, or message transports. This is in contrast to coding patterns, in which phrases such as object-oriented, functional programming, or dependency injection appear frequently. Coding patterns may sometimes be called code architecture and are discussed in Coding Patterns, page 188.

The highest-impact decision in technical architecture is whether code runs as a monolith or as a set of services (commonly referred to as microservices). I'll start here with a description of what each pattern looks like, and then provide some guidance on the tradeoffs between them.

##### Monolithic Architecture

The monolithic architecture pattern is one in which all code is executed as a single process, where information moves between pieces of your system entirely in memory, modeled as simple function calls. If you've ever sat down and built a simple application in an afternoon, chances are good it would fall into the category of the monolith. Monoliths come in all sorts of shapes and sizes, from very small to massive, multi-million-line projects.

The key to building a successful monolith is to carefully design the data flows within the application, using domain-driven design. You can measure this pretty easily; you want to ensure that when a developer goes to change the functionality of the application, it is obvious where in the monolith they should be working. They should only need to change code in an obvious and well-defined or confined area to achieve their goal. Every additional area of the codebase that needs change to meet a functional requirement adds additional complexity or opportunity for error, and in general slows down development.

Key features of a monolith:

* Code is deployed as a single unit.
* Code is managed in a single source-code repository.
* Deployed code is scaled as a single unit up and down.
* Information moves between parts of the system in memory, usually with function calls.
* Domain-driven design and clear information flow design are not enforced by the system, leaving it up to the engineers to do design well.

##### Service-Oriented Architecture (Soa)/Microservices

The phrase service-oriented architecture (SOA) originated in the 1990s and is used to refer to some fairly specific technology choices. Nowadays, the phrase is used to more broadly describe a system where information moves between parts of the system over a network. The main tradeoff with an SOA is that, in comparison to a monolith, it can be very complex to think about and requires a team to do a lot of setup and thoughtful design to truly ensure that the benefits outweigh added complexity.

Microservices are a subset of service-oriented architecture where each service is as the name suggests very small. There are system implementations with thousands of microservices, each of them only a few lines of code. That said, you do not need to have thousands of microservices to experience the benefits of a service-oriented architecture. Even breaking out a system into four or five smaller services, in the right circumstances, can provide major improvement to code health.

You may have heard that microservices are the only good architecture pattern; this is untrue. The perception stems from the fact that many monoliths are poorly designed or haven't received the attention and investment in tech debt required to unlock productivity. The idea that all microservice architectures are a joy to work in is also untrue. There are many microservice implementations that for one reason or another fail to realize the benefits as well.

Key features of an SOA or microservices system:

* Different services are independently deployable and scalable.
* Code is managed by either a single source-code repository or many code repositories.
* Information moves between parts of the system over a network, often via HTTP, RPC (Remote Procedure Call), or queuing systems.
* Data contracts must be intentionally designed and well thought out, as contracts are implemented as APIs and communicated over a network.

##### Choosing Between A Service-Oriented Architecture And A Monolith

In general, a monolith is easier to set up than an SOA and requires considerably fewer technical logistics to manage. For this reason, a monolith is the right answer on day one for the vast majority of problems. If the team is very disciplined and thoughtful about designing a monolith, it can scale with the team forever. This won't be the case for everyone, however. For many teams/projects, a monolith's lack of enforced contracts, inability to scale as separate components, and lack of enforced separation of concerns will become a barrier to productivity.

If you do find yourself contending with an unruly monolith, this doesn't mean your engineers are bad at their jobs. The nature of software engineering is that requirements change and systems evolve. Maintaining a monolith may mean, at times, investing considerable resources into updating the system design to evolve as well, and it is when a team fails to make this investment that monolith complexity becomes a barrier to productivity.

There are some circumstances where moving to a service-oriented architecture is clearly the right choice:

Your service has elements that need to be scaled independently. For example, one feature consumes lots of CPU resources and you don't want that to interfere with other features, or you prefer not to pay to scale up all features when it's more cost-effective to scale that one piece independently.

You're working on functionality that needs to expose its own independent API and has its own exclusive data domain apart from the main system. Especially if this API is meant to serve external customers, then having this functionality live as its own service is an obvious good choice.

For some reason, you need to use another programming language as part of your application. A good example might be because there is a robust and high-quality framework for solving a certain kind of problem in Python, but the rest of your application is in Java. Bridging these two languages in memory is possible, but clunky. The easier option is to bridge them via an API, leaving them naturally hosted as separate services.

Deploying your monolith is overly expensive, slow, or risky. In this case, you can enable additional productivity and reduce time to deploy by deploying new code as an independent service. Just ensure that the new service operates independent of the monolith and you're not creating new deployment dependencies.

##### Source Control for Service-Oriented Architectures: monorepo and manyrepo

Managing source code for a monolith is fairly straightforward because it lives in a single repository with a single-build system. Once you start to break out your code into different packages, projects, and services, you're faced with a decision: do you manage multiple services in a single code repository, or do you make multiple repositories? is tradeoff is referred to as monorepo vs. manyrepo.

If you choose to manage multiple services as a monorepo you'll likely want to look for a workspace management solution (e.g., yarn workspaces for JavaScript ecosystem) to manage building the projects separately. Here are some basic differences between the monorepo and manyrepo approaches:

**Pros and cons of monorepo
TODO: Put the chart here

it's easy to ensure every service or package dependency is up to date with the latest version.

Many CI systems do not support multiple packages in a single repo natively, so you have to build a harness manually to support this.

Having all the code in a single repository improves discoverability, making it easier for developers to find the module or reference they're looking for. IDEs have robust support for this kind of search.

**Manyrepo, by contrast**

Requires using a central package manager with version control. This isn't necessarily a bad thing, but it can lead to significant overhead when working on a project and its dependencies simultaneously.

Integrates cleanly with CI/CD pipeline systems (Bitbucket pipelines, GitHub actions, etc.).

My general advice is to keep things simple. For small-to- medium-sized projects, a monorepo will be simpler to set up and maintain. Transitioning to manyrepo means being willing to make an investment in tooling to ensure manyrepo works smoothly for your developers; it's a significant cost. For a small startup, that cost is likely not worth it. On the flip side, if you're growing rapidly or are passing fifty-plus developers, and monorepo is becoming unwieldy, and you've got a dedicated internal platform or DevOps team that can do the heavy lifting of making manyrepo easy to use, then transitioning to a manyrepo pattern may be the right choice.

##### The Distributed Monolith

A distributed monolith is a system deployed as multiple services that are not designed with sufficient independence or isolation and thus are not independently deployable. To be clear, this is the worst of both worlds. Rather than enabling a developer to go to any service and to work on it in isolation, not thinking about any other service, this setup requires that developer to reason about how that service affects other services. Not only that, but they have to then make changes potentially in multiple services and coordinate deployments in a particular order between services to ensure compatibility during releases. This development and deployment complexity negates the key benefits of a microservice system.

If you notice your team falling into these patterns or complaining about coordinating releases between services, this should be a red flag for you to look closer and consider paying down some tech debt to get back to independently deployable services. That tech debt is usually located in your contracts, the design of your APIs, and how data is handled in your system.

### Writing Readable, Good Code

In a professional environment, the principal audience for any given line of code is not the computer but the developer who has to read that code at some point in the future for further development. This is the golden rule of programming: engineers should be writing code with the same level of readability that they expect of anyone else's code.

#### Choice Of Language And Ecosystem

Per the golden rule of programming, your choice of language should enable your team to write code that is highly readable and maintainable. In general, a good engineer can do that in any language; however, some languages make it easier than others to do so consistently. Some other considerations for what language or ecosystem to choose:

* How large is the talent pool that is familiar with that language, and more specifically is familiar with that environment and also interested in startups like yours?
* Are there existing implementations that you can use as a starting point?
* Do you have particular performance or scaling requirements? Some languages are much faster than others for specific types of tasks. Haskell is famously inefficient at string manipulation, and C is famously fast at most things, though there are other languages that, for certain problems, approach or exceed the speed of C while providing an easier and more friendly coding environment.
* Is there a particular framework that might be a good starting point in a particular language? React Native, for example, is a powerful cross-platform mobile language that requires JavaScript or TypeScript.

In the enterprise setting, I recommend languages with static type systems, such as Golang, TypeScript, Rust, etc.  With a static type system the compiler does more of the heavy lifting for ensuring code correctness. You should strive for a local development environment where the tools are finding errors before your code is executed. Fixing a compile time issue is in general much faster and cheaper than fixing a runtime issue.

#### Code Style And Formatting

In any widely used language, there will be either a published standard for how code should be formatted (e.g., PEP8 in Python) or a configurable tool that can enforce a particular code style and formatting (e.g., ESLint or Prettier in JavaScript, or ReSharper in C#). Most of these tools are very good at ensuring that code, regardless of who wrote it, is stylistically identical. In the spirit of ensuring your codebase is readable, there is no excuse for not using one of these tools and ensuring 100 percent of your codebase is formatted according to the same rules. Which rules you use is entirely you and your team's preference, but just make sure it's consistent and produces a readable result.

I recommend you have a set of configuration options or instructions for the integrated development environments (IDEs) your developers use on how to auto format code when a file is saved. You should then, in your continuous integration system, ensure that all new code is formatted correctly.

Be careful: enforcing style in your continuous integration system without automatic formatting is very frustrating for engineers, so make sure to train everyone in setting up their IDE correctly on day one to avoid consistent surprises and wasted cycle time from lint failures in CI.

#### Static Code Analysis

Modern static code analysis is capable of identifying and alerting on a wide range of common code issues, ranging from security gaps to outright bugs to stylistic inconsistencies. These tools are fairly inexpensive and integrate neatly with a wide range of commonly used continuous integration systems and developer IDEs. From experience using these tools on a range of projects and programming languages, the signal-to-noise ratio is very good, and the output is a net gain in productivity and software quality. Relatively early on in your software project's life, you should integrate static code analysis. I encourage you to look at tools that are specific both to your programming language of choice e.g., ESLint for JavaScript as well as generic analysis platforms such as SonarCloud, Codebeat, Scrutinizer-CI, Code Climate, or Cloudacity.

#### Greenfield vs. Brownfield

Greenfield software development refers to development work in a new environment with minimal pre-existing legacy code and free choice on tools, patterns, and architecture. This has the obvious advantage of allowing the thoughtful choice of the right architecture and tooling for the job, and no distraction from existing tech debt. The subtle downside is that, with so much choice and so few constraints, the risks of making poor decisions are higher. There is also usually a considerable bootstrap cost for new projects that is underestimated things like setting up testing, build systems, static code analysis, etc.

Brownfield software development refers to the opposite of greenfield, working with existing legacy systems. The tradeoffs are essentially inverted: for better or worse, you're stuck with the high-level decisions that have been made by those before you.

The largest risk in brownfield development is not invented here syndrome. Not invented here is the tendency for individuals to avoid taking responsibility for or paying sufficient attention to things they did not create themselves. In brownfield software development, this can lead to systematic underinvestment in understanding existing work, causing frustration and inefficiency in augmenting or modifying existing systems. I strongly encourage managers to make explicit space for a team to read and understand an existing system before asking them to modify it in any way. The time spent in comprehension upfront will be paid back by fewer surprises and faster velocity down the road.

### Coding Patterns

The subject of what style of code to write is a religious discussion for many coders. My intention in this chapter is to provide a brief description of what the most common phrases in coding patterns mean, and refer you to more extensive resources on each practice.

If you're faced with what feels like an emotional conversation on this topic, keep in mind that many successful companies exist that use each of these patterns. Everything is a tradeoff. A bad programmer can make a mess with any tool, and conversely a great programmer will find a way to make a readable solution even with suboptimal tools.

#### Object-Oriented Programming (OOP)

Object-oriented programming (OOP) is a methodology of designing code to mirror real-world nouns and verbs. A typical example would be to model an interaction between two people as two Person objects, and any actions for people, such as talking, would be functions on those objects. Many languages are inherently object-oriented, such as Python, Ruby, and C#. Some, like JavaScript or C++, are Object-Optional (supporting to an extent both object-oriented and functional styles) and others are something else entirely.

#### Purity

Code that is pure has no external dependencies or side effects. Said another way, given the same inputs, a pure piece of code will always produce the same outputs. The advantage of pure code is that it is easily testable and requires no external setup or mocking. Pure code is also easier to read and understand, as it does not require reading any additional code to understand what it does. A simple example of pure code would be a function that sums together two numbers; given any two input numbers, the sum function always produces the same output.

Some code is inherently impure for example, code that interacts with the outside world, such as a filesystem, network, or database. For most other scenarios it's possible to model business logic in a pure way. Where possible, I encourage you and your team to write pure code.

#### Functional Programming

To stick with the parts-of-speech model for describing coding patterns, functional programming treats verbs (functions) as a first-class part of the system. Most functional programming starts with very tiny pieces of functionality and composes it together to create more sophisticated and complex systems. When it's done well, the benefit of functional code is that it tends to be more pure, and thus easier to read, reason about, and test in isolation. Academic examples of functional code even exist that can be formally reasoned about, meaning one can produce a mathematical proof that code runs correctly.

Functional programming, done poorly, can create very verbose and hard-to-read code. For example, when composing together multiple functions, it's important to consider how many functions are being composed, and how obvious the behavior of each function is in the composition chain.

A worst-case scenario: Imagine a function chain of ten functions in a row, each with names that have no meaning to you (e.g., a(b(c(d(e(f(g(h(i(j(input))))))))))). The only thing worse would be if the definitions of these alphabet functions were in ten different files in different places of the codebase, or worse, came from different imported libraries.

#### Extreme Programming And Test-Driven Development (TDD)

Extreme programming is a development methodology, akin to Agile or SCRUM. It may be used to reference the formal methodology described in the book *Extreme Programming Explained* by Kent Beck, or more informally to address some of the coding practices espoused by the methodology. The informal usage of the phrase describes the testing practices in the methodology, specifically the idea of test-driven development.

Test-driven development (TDD) is a process where tests are written before functional software, as opposed to writing functional code first and tests after. Behavior-driven development (BDD) and acceptance-test driven development (ATDD) are similar practices.

#### Dependency Injection

Dependency injection is a pattern where the service dependencies of a particular object, module, or block of code are passed in, rather than instantiated. For example, a data object can instantiate its own connection to a database by looking up a connection string in a configuration file and creating the database client. Alternatively, a parent-calling block of code can create the database service, then pass the single database service into each instance of the data object.

The main advantage of dependency injection is that it decreases the coupling between a service and its dependencies, effectively adding a documented interface between them. This interface allows, for example, other implementations of the interface to be used, such as a mock service in a testing context.

There are subtleties inherent to doing dependency injection cleanly. I encourage you to adopt frameworks or patterns that are commonly used and well thought out for your programming language.

#### Domain-Driven Design

The term Domain-Driven Design comes from a book by Eric Evans, *Domain-Driven Design*, published in 2003. The core idea is to create a model be it for objects in object-oriented design or for a schema for your database that models the nouns in your business domain. This may seem simple and intuitive; however, with complex business domains, it's easy for code either to inconsistently model the domain, or to model it in a way that hinders comprehension by the team. Especially with larger and more complex problems, I always insist that the team sit down and agree on a consistent way to model the problem, using consistent terminology to refer to the same concepts across the entire system.

### API Contracts

An application programming interface (API) is not unlike a legal contract.

It is designed, tweaked, and agreed upon in advance of implementation, and both parties expect the other to conform to the contract to achieve a desired outcome. When you design and implement an API, you're making a commitment to the consumers of your API that it will work in a certain way. Like a legal contract, you may have a specific idea of how your API will function, but if the nuances are interpreted differently by the other party, you may be unable to achieve your purpose. API details truly do matter, and as a technical leader it's your role to ensure that your team is designing and building APIs in a consistent, efficient manner.

All that said, building a high-quality API is a surprisingly complex task. It requires taking into account many things: designing the interface, implementing the code that handles the logic/data, testing the functionality, building the documentation, addressing versioning/change management, keeping the documentation up to date as the API changes, and making it easy for developers to interact with the API. Doing these things well can mean the difference between building an API that developers love and an API that stymies implementation and slows down time to launch important projects. There are two main levers at your disposal as a leader to ensure you're handling these things well: governance and architecture.

#### API Design Governance

Countless decisions go into every element of building an API. What separates good APIs from bad APIs is the consistency, predictability, and correctness of those decisions. As a technical leader the job falls on you to make sure that, across your organization, you have a structure in place to help developers build APIs that are consistent with one another, predictable in that they use common patterns that are appropriate for the problem at hand, and correct.

Achieving these goals requires some form of governance system. This can range from a set of clearly documented guidelines and standards to a group of people who are responsible for reviewing and approving all APIs on a regular basis. The larger your team, the more time and effort you'll need to invest in process and governance to maintain a high standard.

#### API Architecture

Out in the wild you're likely to encounter two main types of APIs: HTTP- based and non-HTTP based. As with any tool, HTTP has its tradeoffs and isn't ideal for every job, so if your business requirements dictate ultra-low latency, or ultra-high throughput/low overhead, or real-time streaming applications, you'll likely be looking for something beyond HTTP. Below I discuss a handful of HTTP API types and then briefly cover some non- HTTP APIs you're likely to run into.

#### HTTP-Based APIs

If you're building a web or mobile application, or even most system backends, chances are very high you'll primarily be dealing with HTTP APIs.

*XML and SOAP APIs*

In the early 2000s, the most common API pattern was the XML-based Simple Object Access Protocol (SOAP). SOAP and other XML-based API styles are well and truly out of fashion with startups in the 2020s, but they are still prevalent in legacy systems, especially from larger companies in technologically slow-moving industries. You should not be building new SOAP or XML-based APIs.

*REST*

REST (Representational State Transfer) is a generic phrase that describes using JSON over HTTP as an API. REST is sometimes augmented with a pattern called HATEOAS, which provides a more formal set of standards to the content/payloads of a REST API. Absent HATEOAS (which isn't all that common), REST does not include formal or branded guidance for how JSON data is modeled. REST APIs commonly model a single noun as an endpoint and use HTTP verbs (GET, PUT, POST, DELETE, etc.) to determine actions on nouns. For example, GET `/users` would list users, POST `/users` would create a new user, and DELETE `/users/123` would delete the user with ID 123.

REST is likely the most common form of API you'll encounter. REST has a broad and robust tool ecosystem and nearly every engineer is familiar with it.

*GraphQL*

GraphQL is similar to REST in that it's JSON over HTTP; however, it does not rely on HTTP verbs. Nearly everything on GraphQL is a POST, and it uses a structured schema of queries and mutations.

I like to think of GraphQL as REST with types and a self-documenting schema. As a result, GraphQL APIs tend to come with automatically generated documentation and schema explorers. GraphQL also, by virtue of its schema system, allows for the composition of multiple schemas from multiple services to form a larger, more powerful, and more complex data graph, sometimes called a federated schema. The company Apollo provides sophisticated solutions for managing and scaling a graph.

There's a lot to be said for the benefits of building a graph to model your company's data, and the good habits that being forced to design a schema bring about. That said, no system comes without tradeoffs. Because GraphQL forgoes standard HTTP verbs, it does not play nicely with some elements of the web stack. GET request caching and developer tooling are still catching up to deal nicely with GraphQL requests. If those drawbacks are not a significant concern for your business, I strongly encourage you to check out apollographql.com and consider using GraphQL especially for internal use cases for your APIs.

#### Non-HTTP APIs

In general, for traditional synchronous request/response- (aka remote procedure call or RPC-) style APIs, you'll want to use an HTTP API due to its ubiquitous nature. However, there are several API patterns especially for asynchronous operations that don't map neatly to HTTP and have commonly used alternative implementations.

*Queueing systems*

A queueing system maintains an inbox (or set of inboxes) to receive messages and an interface for a consumer to read messages with certain guarantees.

A typical queueing system can guarantee message order (either first in first out, FIFO; or last in first out, LIFO) as well as at least once or at most once delivery. Most cloud platforms have hosted implementations of queues, such as AWS Simple Queue Service (SQS) or Google Cloud Task queues.

Queueing systems often have a notion of *explicit* invocation, which is to say that when a publisher creates a message, it explicitly specifies how the request should be handled or executed. By contrast, most publisher subscriber systems support *implicit* execution. This means publishers do not necessarily know beforehand what system will handle the message, only that the pub/sub system will deliver it.

*Publisher-Subscriber (pub/sub) Pattern*

The publisher-subscriber pattern, abbreviated as pub/sub, allows for designing a system where messages are created by potentially multiple sources and delivered via various patterns to potentially multiple subscribers. Publisher-subscriber relationships are modeled as one-to-one (direct), one-to-many (fan-out), many-to-one (fan-in), and many-to- many. Various pub/sub implementations can provide guarantees that messages are delivered to all subscribers, at least one subscriber, at least one time, etc. Similar to queues, there are off-the-shelf solutions, such as RabbitMQ, as well as easily scaled cloud-hosted options like Amazon Simple Notification Service (SNS) or Google Cloud Pub/Sub.

The pub/sub pattern and the guarantees it provides are extremely powerful. However, the tradeoff is that implementations require some care and attention to detail to realize the advertised guarantees. Implementing a subscriber, for example, requires paying close attention to message acknowledgement semantics and carefully managing topic subscriptions to ensure the right messages go to the right place.

If you're torn between implementing a solution with queues, pub/sub, or an HTTP API, my general recommendation is to keep it simple and go with the synchronous HTTP API. The fact that you are torn between implementations indicates that the guarantees offered by the asynchronous systems are not critical to your implementation, and therefore the added complexity is likely not worth it for your startup project.

*Job Systems*

Jobs, or cron jobs, are a type of backend API that are rarely triggered by a publisher or client, but instead by some form of timer. Common examples include nightly data cleanup tasks, or sending weekly email summaries/ notifications. Some best practices for jobs:

* Use a job system maintained by somebody else, don't build one yourself.
* When choosing a job system (or building one yourself, if you must), ensure that it:
  - has logging for every job execution;
  - allows for configuring the retrying of jobs that fail;
  - provides notification when jobs fail. It's very common for engineers to set up a scheduled job, watch it work on day one, and then on day fifteen it fails and nobody notices until day thirty;
  - provides an interface to view jobs and job status;
  - allows for job configuration to be stored as code or configuration in source control;
  - allows for jobs to be run inside your environment/private networks/security groups as necessary to access other internal system APIs/resources;
  - integrates with your secret management system.
  - allows for easily setting up jobs locally in development and production environments, and easy testing in each of those environments.

### Documentation

Having thorough, clear, and current documentation for your API is just as critical as how you build and maintain it. Some key characteristics of great API documentation:

* Always up to date with the implementation
* Documents all possible inputs and their types Documents all possible errors
* Easily read and navigated by other engineers

It's always a good idea to build your API using a system that includes API documentation generation. Doing otherwise means it'll be practically impossible to meet all of these goals on a consistent basis. If you're building a REST API, I strongly encourage you to design your API using OpenAPI (a YAML or JSON document that describes your API). In most languages there are SDKs to consume an OpenAPI spec and automatically generate controllers/routes to match the spec and/or generate a test harness to ensure the implemented API matches the spec. In addition, there are online tools, such as stoplight.io and readme.com, that can consume OpenAPI documents and generate aesthetically pleasing and easy-to-navigate documentation.

If you're using GraphQL, the GraphQL Playground or Apollo Studio explorer can provide a reasonable stand-in for extensive type documentation. I do recommend you still build a separate API documentation page, either using a tool like readme.com or creating something by hand, to act as a primer or getting started guide. The built-in GraphQL documentation lacks a description of how authentication works, and it also does a poor job of providing space to explain the relationships between data in your API.

These are gaps you need to fill elsewhere.

Another benefit of using either OpenAPI or GraphQL is that the resulting API specification is portable not only to documentation generators and test frameworks but also to developer IDEs such as Insomnia or Postman. These IDEs enable developers to quickly interact with an API to validate functionality without writing code. Formal specifications can also be used with code generation tools to ensure typing consistency in code.

### Idempotency

An API request is said to be idempotent when making the same request multiple times has the same effect as making it a single time. Idempotency is an important concept in building robust systems and avoiding data corruption. As with all things, idempotency gives you useful guarantees about a system but it comes with a cost: implementing idempotency adds complexity to backend systems.

In REST APIs, it is widely assumed that every HTTP verb except POST should be idempotent. GET requests, for example, by definition should always return the same result for the same input (unless the underlying data changes, of course). In general, PUT requests are modifying existing objects and should naturally be idempotent. Multiple calls to a POST request, however, in most systems signal the intention to create multiple objects.

#### Idempotency Keys

For HTTP POST requests in REST and for GraphQL mutation APIs, idempotency is not provided by the standard/specification. If you want a client to be able to retry these kinds of requests and have idempotent behavior, you should implement the idempotency key pattern. An idempotency key is an arbitrary string, provided by the client (either as an HTTP header or perhaps in GraphQL as an input variable), that backends use to de-duplicate incoming requests. This requires the backend to store the idempotency key, and also store the response to a request with that key, to be provided to clients later on.

Note that implementing an idempotency key is non-trivial, as it will require additional database writes, logic around capturing request responses, and dealing with concurrency/locking issues for duplicate requests that arrive at the same time. If idempotency is important in your application say, if you're dealing with financial transactions I encourage you to adopt a backend API implementation that provides a robust idempotency system out of the box rather than building it yourself from scratch.

## Data And Analytics

Most startups have at least three different kinds of data they use as part of their business:

* Transactional data

* Analytical business intelligence data

* Behavioral data

Each of these types of data will come in different volumes, have different read/write patterns, and require different tools to visualize and glean insights.

A quick note on the phrase big data. As a startup, the chances are very good that you do *not* have big data in the sense that it needs to be architected with infinity-scale (or web scale) in mind. Typical off-the-shelf databases with reasonable quantities of hardware and half-decent data model design are more than capable of handling tens of millions of rows and hundreds of gigabytes of data with acceptable performance. Most big data solutions, such as data pipelines or data warehouse appliances, involve significant added setup complexity, latency, and cost, and they're likely overkill for your startup. For the sake of simplicity, big data solutions should only be considered if you can make a compelling argument that a regular (e.g., PostgreSQL) database cannot do the job. Said another way, don't prematurely optimize your database architecture.

### Transactional Data

Transactional data is the data that powers your application itself, typically your primary NoSQL or SQL database. Transactional data requires very low latency and high availability, and is modest in total size compared to the other forms of data. My recommendation is to choose an off-the-shelf SQL or NoSQL solution, preferably something hosted for you such as MongoDB Atlas or Google Cloud SQL. Some nice-to-haves in your production database:

* One-click point-in-time restore
* Regular backups with one-click restore
* Read-only replicas for load shedding
* Multi-zone replication and hosting for availability
* Event-based audit logging
* Automated disk expansion/contraction
* Connection/IP-level security
* Resource (CPU, RAM, Disk, Network) monitoring and alerting One-click scaling up/down for CPU/RAM
* Slow query monitoring

### Analytical Business Intelligence Data

Business intelligence (BI) is data that is used to gain insight into behaviors of your users, usually sourced from your transactional data. Early on, you can often get away with running business intelligence queries directly on your transactional database. As the size of data and query complexity increase, this becomes more problematic as it adds additional load to a system that requires high availability and low latency. The natural solution then is either to query a read-only replica of your transactional database, or copy/transform the data to another data storage system via a data pipeline.

Building data pipelines and data warehousing is an entire book unto itself, and the state of the art is always evolving. I have just a few high-level bits of advice:

Consider looking at enterprise data solutions like Snowflake, Databricks, or Google BigQuery for your primary business intelligence data warehouse. These tools are game changers. The serverless warehouses in particular (BigQuery, Aurora) are trivial to set up, have fairly consistent latency regardless of data size, and are highly cost-effective for early/mid-stage startups.

In modern times, a startup doesn't need to build and host sophisticated data pipeline architectures. ELT (Extract, Load, Transform) and ETL (Extract, Transform, Load) tools can now run entirely inside an enterprise database data lake/warehouse, and tools such as dbt provide reproducibility, testability, and pipeline-as-code capabilities, making running data pipelines much more manageable.

Consider using hosted or cloud-native solutions for visualizing data such as Looker, Domo, or Preset.

Make sure your engineering and product teams are collaborating closely with whichever member of your team owns data and business intelligence. Bringing in data's perspective early in the product process will save a lot of headache down the road with a measure twice, create-data-schema once mindset.

### Behavioral Data

Behavioral data also called behavioral analytics events describes how users have used your application. Behavioral data is often fairly high volume, with a somewhat limited schema, and is best used in combination with powerful visualization software.

Overall, you'll want behavioral data from your application to go to multiple sources. This presents a bit of a routing problem: you have a single data source (your application), but you want events to go to many places. The nearly universally adopted solution to this problem is Twilio's Segment platform, though there are some up-and-coming alternatives called Customer Data Platforms (CDP) such as RudderStack. A CDP can ingest data from your application, then send it to your data warehouse and to as many other SaaS platforms as you like.

One important distinction between behavioral data generated by your application and transactional data is its precision. Most behavioral data is lossy users have ad blockers, requests get dropped, or firewalls get in the way. There are many reasons why events might not make it from a client device to your CDP. That doesn't mean behavioral data is not useful, but being aware of its lossiness should inform your expectations for the data and limit the use cases when querying it. If you need exact numbers, expect to derive those from your BI platform and your transactional data.

### General Tips And Best Practices For Architecture Design

Let's close out this section with a few overall recommendations for designing your architecture.

#### Put Business Logic In The Backend

As you build out your application you're often confronted with the choice of where logic should live: on the client (e.g., web browser, mobile device, physical hardware) or some form of backend server. For certain types of logic, such as anything related to authentication, value calculations, anti-cheating/tampering mechanisms, this is a firm requirement. For most other logic it's still a good idea for the following reasons:

Backends are often easier to test than clients, so you can more confidently confirm the correctness of business logic on the backend.

More logic on the backend means thinner clients, and also means you can produce clients for multiple platforms that can leverage a single source for logic, reducing code duplication.

Logic on the backend can't be tampered with or modified by the client.

#### Make Services Externalizable

The APIs from your backend to other backends, or your backend to frontends, should be thought of as generic-purpose APIs that could be consumed by third parties. This forces you to maintain several good design habits, including ensuring that interfaces are comprehensible on their own (domain-driven design), and using sensible authentication mechanisms and appropriate high-level ownership abstractions in data design. And, on the off chance you do one day wish to externalize a service, the road to doing so will be much shorter.

#### Use As Few Languages As Possible

With every programming language comes an associated build system, dependency management system, programming best practices, and interfaces. Your team should be putting in considerable effort to ensure your primary language and ecosystem are well integrated and working well for local developers, test environments, and production environments.

For every additional language you add to your stack, you'll need to replicate all of that effort, and you'll suffer from an inability to share code between the runtimes. Before allowing an additional language in your stack you should be able to build a robust and bulletproof argument that the benefits of the new language dwarf the operational and maintenance burdens that the new language adds. Otherwise you're better off without it.


## Tools

The tooling ecosystem and patterns for software engineering are constantly evolving and changing. You will inevitably be tempted either on your own or by members of your team to change something about how you're doing engineering, such as adopting a new library, framework, language, or pattern. Adopting each of these changes quickly leads to a patchwork quilt of poorly thought-out architecture. Conversely, ignoring all change leaves you with a stale codebase that, over time, will be less efficient and harder for newly hired talent to work on. The right approach is to formalize the process

of changing your tech stack and provide some guardrails to motivate your team to be curious and thoughtful about tooling changes.

### Implementing Internal Technology Radar

Thoughtworks, a leading software consultancy based out of San Francisco, publishes a tool called the Technology Radar (ctohb.com/radar) that evaluates the hundreds of projects Thoughtworks sees every year. They put new tools, techniques, patterns, and languages (which they call blips) in one of four categories based on how effective they are in the real world.

The categories are hold, assess, trial, and adopt.

If you've never read through a Thoughtworks Radar, I highly recommend it as a general primer on what's going on, and also as inspiration for your own team's process.

My preferred way to balance the challenge of keeping engineers motivated and a codebase relevant with tool churn is to follow Thoughtworks lead and implement an internal technology radar. Rather than weigh something new for its universal appeal as Thoughtworks does, my approach evaluates blips for their fit and effectiveness for our organization using the same four levels. To be concrete:

1. Somebody proposes using a new tool, technique, platform, or language (blip). That proposal at first is categorized as "assess". The proposer has to make the case in a technical document that the new blip would provide a material benefit to a project that was already selected by the business (or as an experiment in an innovation sprint see Cooldown/Innovation Sprints, page 163). Then, if approved, it moves to a trial.
2. The new blip is used by the developer in a project, either selected by the business or in their innovation sprint window. At the end of the project, the author produces a follow-up written document describing their experience with the blip, including pros and cons and how well the blip plays with the rest of the tooling ecosystem at the company.
3. Based on the results of the trial, the team as a whole will move to either adopt the blip, unlocking that blip to be used by the rest of the team without further ceremony, or move it to hold, which would require a new trial and a new evaluation for it to be used again. If a trial fails in a business project, the team is advised to think carefully about whether to remove the blip from that implementation to avoid future maintenance concerns.

In most cases, I find that when a blip trial fails, it fails relatively early on and the engineer leading the project doesn't include the blip in the final delivered implementation.

### Boring Technology

Boring Technology is a phrase coined by Dan McKinley and outlined at ctohb.com/boring. The key idea is that your team's job is to deliver functionality to support the business, and most of the time that doesn't depend on using fancy new tools. In fact, using something that's not boring often has many hidden costs, and only if your team is fully cognizant of those costs and believes the benefits are larger, should the new tool be adopted. As Boring Technology describes it, total cost = maintenance costvelocity benefit. Some hidden costs to consider:

* Incomplete, inaccurate, or immature documentation
* Not fully developed ecosystems around the tool/technology, including SDKs and integrations with other tools
* A higher likelihood of encountering defects or missing functionality/features
* Additional training cost for members of your team to adopt the new tool
* Burden in keeping that tool or package up to date, patch ing security holes, etc.

### Tool Cost

It's a fact of life that modern startups will spend a lot of money on Software As A Service (SaaS). Your company is likely no exception, so don't be surprised when you find you are spending an entire headcount or more on infrastructure and tools before your Series B fundraise.

### Budget

There are a handful of published benchmarks for SaaS and tool spend at various company stages as a percentage of either company revenue or total spend.

There's not a single precise benchmark, but it seems that typical SaaS Costs of Goods Sold (COGS) fall somewhere between 10 and 30 percent of revenue.

Know your spend and keep an eye on cost growth. It's very easy to accidentally leave a couple of machines running in AWS and add $10,000 to your annual cloud hosting bills. Most cloud platforms have built-in budgeting features, so There's no excuse to not use them. If you're using infrastructure as code, it's easy to set up a module that, for every new cloud system deployed, will automatically apply a cloud budget at the same time that will monitor and alert on cost for that particular system.

It's typical for SaaS costs to grow over time, be it because your infrastructure is growing, or because you discover a new SaaS vendor that can save your team time. I recommend not using cost as a reason to avoid adopting a typical SaaS tool (with a cost range in the hundreds per month). Instead, I'd advise factoring regular growth into your SaaS cost forecasts.

### Tracking

You should be tracking how much your organization spends on engineering tools, including IDEs, SaaS, and infrastructure (cloud platforms). You can do this manually in a spreadsheet or using a SaaS Management Platform (SMP). Available from various vendors such as BetterCloud, Zluri, and Vendr, these solutions link with your credit card or bank and automatically categorize cash spend.

## DevOps

Wikipedia describes DevOps as a set of practices that combines software development and IT operations. It aims to shorten the systems development lifecycle and provide continuous delivery with high software quality.

To me the key piece of this definition is that devops aims to shorten the software development lifecycle, in other words DevOps is an enabler of broader team productivity.  If you're not already specifically thinking about DevOps, you're likely underprioritizing or underinvesting in DevOps to some degree. It's not just my opinion; it's becoming widely accepted throughout tech industries that high-quality DevOps is a key driver of overall engineering velocity.


### Four Key Metrics (DORA)

The highest-rated blip in 2022 of the Thoughtworks Technology Radar (ctohb.com/techradar) is the Four Key Metrics. These metrics are described by a team within Google Cloud called DORA (DevOps Research and Assessment), and the system of metrics comes from a seven-plus-year research program validating the results and their impact on technology, process, culture, and quantitative results. The four metrics are as follows:

**Lead Time:** How long it takes for code to go from commit to running in production

**Deployment Frequency:** How often code is released to production/end users

**Mean Time to Recovery (MTTR):** How long it takes to restore service after an incident/defect occurs

**Change Fail Percentage:** What percentage of production releases need a hotfix, rollback, patch, etc

Together these metrics quantify the idea of how confidently your team can deploy software. Scoring high on all four metrics requires an investment in automation, DevOps, testing, and culture. As Thoughtworks is quick to point out, drawing value from these metrics doesn't necessarily require highly detailed instrumentation, metrics, or dashboards. DORA publishes a quick check survey (ctohb.com/dora) that your team can take to track its progress at a coarse-grained level. There are also plenty of tools that have fairly low barriers to entry that will yield data quality that's more than sufficient to inform your progress, such as LinearB or Code Climate.

The following subsections on DevOps present concepts, disciplines, and focus areas that contribute in some way to improving these metrics.

### Reproducibility

Deploying code is a highly nuanced activity that requires extreme precision. A single misplaced character in a configuration file can lead to a service failing to start. Worse still, debugging DevOps problems for most engineers is slow and painful, and identifying and fixing that single character error can mean potentially hours of time lost in debugging and fixing. We re all human; these kinds of errors are inevitable. Since they're so expensive in DevOps, it is imperative that we put systems in place to minimize the opportunity for human error. A key component of minimizing the frequency and impact of human error in DevOps is the concept of reproducibility.

Reproducibility implies that we have the capability of doing something a second time that is both inexpensive and guaranteed to be identical to how it was done the first time. Reproducibility in DevOps requires automation and tooling. Arguably, the most important tool in the DevOps tool belt for improving reproducibility and accelerating development time is containerization. A close second is the idea of Infrastructure as Code (IaC). Since these techniques are so fundamental, I'll spend a bit of time introducing each of them here.

### Containerization

The most common way of explaining the role of containers in the DevOps context is to consider where the name originated: from shipping containers. Prior to the standardization of shipping containers, if you wantedto transport goods across the ocean, you would package your cargo in a variety of forms ranging from placing it on pallets, storing it in boxes or barrels, or simply wrapping it in cloth. Loading and unloading goods that arrived packaged in all these different ways was inefficient and error- prone, mainly because There's no single kind of crane or wheelbarrow that could effectively move all of the cargo.

Compare that haphazard approach to deploying a standardized shipping container where the boat and port operator can work with a single form factor, using standardized equipment and shippers and a single, flexible form of packaging for all of their goods. Historically, the usage of standardized shipping containers unlocked a paradigm shift that reduced costs of global shipping by orders of magnitude. Packaging software in a standardized container that can be run on any system in the same way provides an analogous advancement in capability and efficiency.

The most common way you'll interact with containers is through a software system called Docker. Docker provides a declarative programming language that lets you describe, in a file called Dockerfile, how you want the system set up i.e., what programs need to be installed, what files go where, what dependencies need to exist. Then you build that file into a container image which provides a representation of the entire file system specified by your Dockerfile. That image can then be moved to and run on any other machine with a Docker-compatible container runtime, with the guarantee that it will start in an isolated environment with the exact same files and data, every time.

#### Container Management Best Practices

##### Design Containers to Build Once/Run Anywhere

Build the container once (say, in CI) so that it can run in your various environments production, development, etc. By using a single image, you guarantee that exactly the same code with exactly the same setup will transition intact from development to production.

To achieve run-anywhere with your containers, extract any differences between environments to runtime container environmental variables.

These are secrets and configurations like connection strings or hostnames. Alternatively, you can implement an entrypoint script in your image that downloads the necessary configuration and secrets from a central secret store (e.g., Amazon or Google Secret Manager, HashiCorp Vault, etc.) before invoking your application.

An additional benefit to the runtime secret/configuration download strategy is that it's reusable for local development, avoiding the need for developers to ever manually fetch secrets or ask another developer to send them the secret file.

##### Build Images in CI

In the spirit of reproducibility, I encourage you to build your images using automation, preferably part of continuous integration. This ensures the images are themselves built in a repeatable way.

##### Use a Hosted Registry

Once you're building container images and moving them around, you'll immediately want to be organized about managing the built images themselves. I recommend tagging each image with a unique value derived from source control, perhaps also with a timestamp (e.g., the git hash of the commit where the image was built), and hosting the image in an image registry. Dockerhub has a private registry product, and all the major cloud platforms also offer hosted image registries.

Many hosted registries will also provide vulnerability scanning and other security features attached to their image registry.

##### Keep Image Sizes as Small as Possible

Smaller Docker images upload faster from CI, download faster to application servers, and start up faster. The difference between uploading a 50MB image and a 5GB image, from an operational perspective, can be the difference between five seconds to start up a new application server and five minutes. That's five more minutes added to your time to deploy, Mean Time to Recovery/rollback, etc. It may not seem like much, but especially in a hotfix scenario, or when you're managing hundreds of application servers these delays add up and have real business impact.

#### Dockerfile Best Practices

Every line or command in a Dockerfile generates what is called a layer effectively, a snapshot of the entire image's hard disk. Subsequent layers store deltas between layers. A container image is a collection and composition of those layers.

It follows then that you can minimize the total image size of your container by keeping the individual layers small, and you can minimize a layer by ensuring that each command cleans up any unnecessary data before moving to the next command.

Another technique for keeping image size down is to use multi-stage builds. Multi-stage builds are a bit too complex to describe here, but you can check out Docker's own article on it at ctohb.com/docker.

#### Container Orchestration

Now that you've got reproducible images of reasonably small size managed in a hosted registry, you have to run and manage them in production. Management includes:

* Downloading and running containers on machines
* Setting up secure networking between containers/machines and other services
* Configuring service discovery/DNS
* Managing configuration and secrets for containers
* Automatically scaling services up and down with load
* There are two general approaches to container management: hosted and self-managing.

##### Hosted Container Management

Unless your requirements are unique or your scale is very substantial, you'll get the highest ROI from going with a hosted solution that does the bulk of the work of managing production containers for you. A common and fair criticism of these solutions is that they tend to be considerably more expensive than self-managed options and provide fewer features and more constraints. In exchange you get dramatically less overhead and less complexity, which for most startups is a tradeoff well worth making. Most small teams lack the expertise to effectively self-host, and so self-hosting ends up either requiring a substantial time investment for existing team members or forcing you to hire an expensive DevOps specialist early on. Spending an extra $1,000 a month to avoid either of those problems is likely to deliver very good ROI.

Some common hosted container platforms include Heroku, Google App Engine, Elastic Beanstalk, Google Cloud Run. Vercel is another popular hosted backend solution, though it does not run containers as described here.

##### Self-Managed/Kubernetes

The most popular self-management solution for containers is called Kubernetes, often abbreviated K8s. Kubernetes is an extremely powerful and flexible, and thus complicated, system. The learning curve is steep, but the benefits and ROI are worthwhile if you're at the point of needing to self-manage your containers.

If you're considering going this route, I strongly advise against learning Kubernetes on the job. Especially for a team leader, it's too much to take on and do well on an ad-hoc basis. Instead, I recommend buying a book on Kubernetes and committing a week or two to reading it and setting up your own sandbox to get up to speed before diving in for a professional project. It's also a good idea to seek out an advisor or mentor who has a good understanding of Kubernetes to act as an accelerator for your learning of the tool.

#### ClickOps vs. IaC

ClickOps refers to the process of configuring your cloud infrastructure using the user interface, as opposed to the provided APIs. As your infrastructure grows, the quantity of nuance and detail in your system will quickly exceed your ability to reproduce it with ClickOps. ClickOps is fine for prototypes or proof of concepts, but when the time comes to actually build a production environment and mirrored development environments, using ClickOps will quickly lead to considerable frustration and cost, as well as limited capability. The alternative to ClickOps is known as Infrastructure as Code (IaC).

There are several tools and frameworks that allow you to define IaC. The leading one is HashiCorp's Terraform. Terraform uses HashiCorp Config Language (HCL), a declarative configuration syntax, to allow engineers to define what resources they want and how they are to be configured. Terraform code can and should then be managed like any other code, using source control and peer review practices. Once approved, Terraform can generate infrastructure change plans and apply those plans for you with your cloud provider(s) of choice. I cannot emphasize enough how easy to use, powerful, and maintainable Terraform is, and how much ROI you're likely to gain by migrating from ClickOps to IaC.

### Continuous Integration

Continuous Integration is the process of automating the incorporation of new code into a project. That may include running static analysis on new code, running tests, building the code, and generating any required build artifacts (such as container images). Most startups use hosted CI platforms such as GitLab runners, GitHub actions, Bitbucket pipelines, Jenkins, or CircleCI to do continuous integration activities.

Some best practices for CI:

* Ensure the team understands the CI system and is comfortable adding to it, updating for new requirements, and troubleshooting when things inevitably cause the build to fail.
* Ensure builds are consistent and deterministic. Unreliable or flaky builds are an extremely powerful productivity drain and time sink.
* Try to keep build times down. For most teams a good target is for CI to take less than fifteen minutes.
* Learn the capabilities of your CI tool that aide in keeping builds fast, including build caches, build artifacts, and running jobs in parallel.
* Builds can get complex. Try to keep your code for CI *dry.* Reuse code between build pipelines where possible.
* Be consistent in how your builds access secrets. Either depend on a cloud secret manager, or build environment secrets where necessary, and try not to mix them. There should be one obvious and consistent way to handle config and secrets.

### Continuous Deployment

In the early stages of a project, it's comparatively simple to deploy new code. At that point, There's not much code or architectural complexity. Before long, however, the need to manage dependencies, dependent services, CDNs, firewalls, build artifacts, build configuration, secrets, and more leads to a complex deploy process. As these requirements accumulate, it's easy to neglect automation, and simply rely on, for example, a dedicated and highly trusted individual as release manager. There are countless teams out there following this pattern, and I guarantee you most of those release managers have release dates circled on their calendar in advance and dread the stress, long hours, and frustration that those days inevitably entail.

Fortunately There'sa cure for the error-prone stress concentration that is the monthly (or longer!) release day. It's to release every day, or heck, every hour! It follows logically from one of the Ten Pillars of Tech Culture (see page 138), Frequency Reduces Difficulty, that more frequent releases will force your release manager, and team, to automate the hard parts of deployments. With enough iteration, releases can become entirely automated, and with sufficient testing giving you confidence in new changes, you can get to the point of triggering new releases for every code change set, referred to as Continuous Deployment.

In addition to eliminating the complexity of the release process via automation, releasing more often means each release is of a smaller amount of code. Smaller code changes are easier for other developers to review. Smaller changes, simply by virtue of being smaller, present fewer opportunities for defects.

An automated release process tends to also imply an improved ability to roll back changes or recover from an issue in production. This is also measured as Mean Time to Recovery (MTTR).

In summary, automating releases means code goes out faster (reducing lead time*)*, means you can deploy more often (increasing deployment frequency), and improves MTTR. That's three of the four key DORA metrics (see page 208) with one initiative!

In the companies I've worked with, either directly or in an advisory capacity, I've seen at least a dozen teams invest effort into either partially or fully moving to continuous deployment. It's not always a straightforward journey, it doesn't happen overnight, and often there are well-reasoned objections. Yet in every circumstance, when the team looks back on the time invested be it three weeks, three months, or two years later the difference is nothing short of transformational to the culture and overall output and velocity of the team by every metric.

### Feature Branch Environments

A feature branch environment is a hosted environment and set of infrastructure that is available internally to your company, running the code from a specific branch. Feature branch environments are incredibly useful for validating that code works in a production-like setting and for enabling team members at your company to use or test changes without having to build and run code themselves. Do not underestimate human laziness; every extra step it takes somebody to test and validate your code means that they'll do the testing that much less often. Checking out code, installing dependencies, and starting servers is significantly more work than going to an automatically generated feature branch URL, and thus the feature branch will get used far more.

Feature branch environments also solve the contention problem encountered by teams that have only a single staging environment. I advocate giving every branch its own staging environment.

Some considerations for feature branch environments:

* Automation is key here; manually setting up feature branch environments is nearly always impractical.
* Where possible, use a system such as Vercel or Firebase that includes feature branch environments as a first-class feature to minimize your setup and maintenance costs.
* Carefully consider how to treat data in feature branch environments. you'll need to answer the following questions:

  - Does each backend feature branch environment get a new database? My recommendation is yes.
  - Does the feature branch environment use production data? My recommendation is no. Instead, use a seed script that generates similar quantities of data to production. It is worthwhile to have a process that copies, sanitizes, and restores production data for developers when necessary for debugging.
  - How are database schema changes/migrations handled in feature branch environments?
  - How does service discovery work in feature branch environments for service-oriented architectures? Often you can get away with having a common set of services and deploy feature branch versions of just the service under test. I recommend that you have an environment for every service that is always running called integration. Have all feature branches reference the integration environment of other services. Each integration environment update should be a production update, but you should also allow developers to deploy feature branch code temporarily to integration environments for cross-service integration testing.

Having looked at this list of concerns, you may be daunted by the burden of setting up and maintaining feature branches. Indeed, a proper feature branch setup is not cheap, but the value it offers is substantial in improving your ability to test, and in reducing the logistical overhead required to verify different kinds of software changes.

### Managing DNS

Knowing how the domain name system (DNS) works, and knowing how to manage DNS and its security implications for your company, is a critical job that often lands on the startup CTO. If you're not already familiar with the basics of how DNS works and the different record types, I recommend you spend a few minutes browsing Wikipedia now to get a grounding on the subject.

You should also know how DNS is used for email in your organization. In particular, become familiar with Sender Policy Framework (SPF) records and DKIM/DMARC.

You should also set up your DNS records using Infrastructure as Code (IaC). I've seen countless companies where DNS is managed exclusively by an executive whose two-factor authentication is the only one allowed to update a zone record, and when that person is on vacation There's no fallback mechanism to manage the site.

A better solution is to set up DNS with Terraform (which has integrations with all the major DNS providers) and then manage DNS records with source control, empowering individual developers to add new records in a responsible way that isn't gated on any one individual.

### Decoupling Shipping Code from Shipping Features (Feature Toggles)

At a high level, a feature toggle is a switch that allows you to change system behavior without changing the actual code. I strongly advocate using feature toggles, in particular because they allow your team to have separate processes and timelines for shipping code and shipping features. Pete Hodgson has a wonderful, in-depth explanation of feature toggles at ctohb.com/hodgson.

The Four Key Metrics advocate for shipping code as frequently as possible. Doing so leads to many great positive benefits for the health of your engineering process. A natural concern, however, is that your business may not be ready for a particular feature to go live the second the code is done. There are many reasons why your development and release schedules might be out of sync in this way, such as the need to coordinate timing with a marketing activation, the creation of customer support documentation, awaiting regulatory approvals, pausing for internal communication, etc. Feature toggles enable your engineering team to focus on shipping as quickly and reliably as possible and delegate the problem of coordinating when features are enabled to an out-of-band process likely owned by other teams.

### System Monitoring: APMs and RUMs

Application performance monitoring (APM) and real user monitoring (RUM) are two types of tools that help teams understand how an application is performing in production and identify or prevent user-facing outages.

An APM tool usually sits inside or alongside your application in the production environment and provides analytics and insights into resource usage and request latency and throughput from the perspective of your backend. RUM is an external tool that pretends to be a user and provides analytics on latency from the frontend's perspective, or the perspective of a real user.

If you had to choose one (and these tools are often very expensive, so you may be forced to go with one or the other), choose the one that covers the blind spot more likely to be problematic for your application. If you have tons of users and you get inundated with real-time complaints for every minor bug or edge case, then an APM monitoring backend load may prove more valuable than a RUM producing redundant alerts to your users. For most startups in seed or growth stages, though, you'll likely have inconsistent application usage, especially covering your edge cases, in which case RUM may be more valuable than an APM on a mostly idle backend.

Some common tools in this space are New Relic, Datadog, and Akamai mPulse.

