
# The history of infrastructure at Zendesk (Part 3) — Foundation team forming and evolving

Desire path, photo by perrine_dethier via flickr (CC 2.0)

**Introduction**

In [Part 2](https://medium.com/zendesk-engineering/the-history-of-infrastructure-at-zendesk-part-2-the-messy-middle-59f16a959b7f), I wrote about our adventures moving from physical data centers to the Cloud. Let’s move on to how we transformed our organizational structure to take advantage of being in the Cloud and enable self-service.

**Building the foundation**

In early 2018, our organizational structure was stereotypically old school, with operations completely separate from engineering. As we were racing to migrate to AWS, we saw an opportunity to align our organizational structure with our future architecture. We needed to plan for a future where our engineering teams would more than double in the span of a few years, our products would become more integrated, and reliability would be paramount. We needed to design an environment where we could move quickly and reduce bottlenecks and dependencies. In short, we needed a reliable foundation to support our product engineers as Zendesk scaled.

We did our research, looking at how bigger companies were structuring themselves, including companies born in the Cloud. We talked to infrastructure leaders at companies like Facebook and Stripe, and sought out Zendesk employees who had previously been at companies like CA Technologies and Autodesk. By combining these great insights with our anticipated 2020 architecture, we started solidifying our approach.

Then the changes began! We broke the team down into practical sub-groups, assigning each an area of responsibility. We set up teams to fully own services, while also dramatically increasing the number of people with local management … the Foundation team was formed!
> # Our mission: provide the infrastructure for Zendesk engineers to safely and efficiently deliver reliable products at scale.

Though it was chaotic for a couple of months, everyone eventually landed on their feet and it felt great! I am still somewhat awed that our team had the drive and agility to pull off a restructure where 36% of people changed direct managers.

Of course, we recognize that no organizational structure is perfect. We expect our organization to evolve as new technologies rise and teams grow. Already, Cloud has taken on a new name, Configuration and Secure, and Analytics has expanded to Analytics & Machine Learning. The current teams are:

**ZENDESK FOUNDATION TEAM**

Config: *Configuration management*
Secure: *Security and compliance automation, e.g. IAM, OS platform*
Edge: *Routing and protection, from DNS to Nginx*
Compute: *Service container orchestration platform, e.g. Kubernetes*
Storage: *Performant and highly-available data storage*
Analytics & ML: *Data platform: batch and streaming. ML platform*
Network: *Efficient and secure internal routing*

**Growing pains**

In the early days at Zendesk, we didn’t really think about providing automation or self-service for our own engineers. We just had this model where Operations was separate from Engineering! Operations were constantly considered a bottleneck for product innovation — mostly due to being a small team who had full responsibility for running and maintaining all the systems engineers built, while dealing with a stream of ad-hoc requests. The pain was compounded by customers pushing the scalability limits of our systems. As a result, Operations was constantly context-switching and reprioritizing.

The context-switching was taxing us heavily. We had gone with a follow-the-sun strategy, meaning each team member was expected to maintain an incredibly broad knowledge base. Consequently, it was incredibly difficult for them to build future-focused platforms when responding to incidents outside their current focus.

Layered on top of this was a number of delivery problems causing a lack of predictability. Firstly, the request process for infrastructure changes (e.g. new route, database, network configuration) differed by team and requests could take 1 day to 3 months to fulfill. Some things required manual fixes that needed to be scheduled, whereas others seemed easy initially, but turned out to be very difficult — like provisioning a new host group or data store. Others, though *truly easy*, were blocked by big projects. To make matters worse, the automation we had in place (mostly Chef) worked well when we had ~100 servers but not at 10,000+ servers.

Clearly something needed to change. Indeed, we had no choice. Having dramatically increased our reliability target, manual intervention was not even feasible; no human could ever respond quickly enough. Instead, our infrastructure would have to live, breathe and respond to different signals on its own.
> # We had this crazy dream: to enable any new Zendesk engineer to take a service to production in their first week.

To do this we would need to leverage a self-service model. But to transition from a request-based interaction model we needed two things: standards that would span across the entire organization and a golden path leading to launch. Our team’s services would form the foundational layers, building the platform that would pave the way. First, though, we had to talk to engineering teams to understand what the golden path should be.

**The golden path**

I remember a beautiful curved path at my high school, leading from one building to another … no one used it! Everyone preferred taking a shortcut across the grass. Worn down over time, a small dirt track was the easiest way to get from Building A to Building B — a desire path. We don’t want to build curved paths that no one uses. We want to identify the shortcut in our infrastructure and pave it smooth. We want to point our users to the easiest route to their destinations — our golden path.

The term “golden path” is thrown around a lot in this space. It’s all about creating standard tools that are appealing. The work of maintaining and extending a well-worn path is never finished. The path will expand as we improve it and possibly change course altogether as technology evolves or new obstacles are thrown in its way. There may be special cases where it’s better to diverge, and we’ll support our engineers should they do this. But we’ll primarily focus on using the carrot not the stick. We’ll direct our engineers to the easiest path, and it will be the one paved with our standards.

So how do we know which path is golden? We leverage our collective wisdom. We look into each of the teams and learn about the technologies and tools they use. We listen to their tales about roadblocks encountered when deploying new features or hardening existing infrastructure.

**Making it real with personas**

With over 500 engineers at Zendesk, 100 of them on the Foundation team, we reached a point where we wanted a product management function, to keep us focused on bringing value to our customers. Much of this had previously fallen to our engineering managers and technical leads. We felt product management could help us leverage tooling and infrastructure effectively to build scalable, long-term technology architecture. It was a great plan … however hiring for this specific skill set was difficult. So we moved onto Plan B, seeking guidance from Zendesk’s existing Product Managers and marching onwards.

As a geographically dispersed group of deeply technical people, some with expertise in operating systems and others in building systems, we did not have experience talking directly to customers. Without the benefit of product management in our midst, taking a user-centered approach to prioritization would call for something different. One solution in particular fitted the bill: personas.

We brought together representatives from every Foundation team and defined our proto-customers (the product engineers at Zendesk), their journeys, and the tasks they were trying to accomplish. Now, when we talk about whom we’re building for, we have *real* use cases. Real Zendesk engineers who are experiencing the real pain of real problems. In other words, people who could potentially move faster because of things we build. These personas gifted us a shared understanding of the problems Zendesk engineers are facing and a shared language around who we are trying to assist. They transformed our ability to prioritize our efforts.

**Our vision for self-service and automation**

We are aiming to significantly reduce the time it takes to provision and update resources — from weeks to minutes. Aggressive automation is the first step. This will dramatically reduce the human assistance required to perform a task, making its execution more predictable. Yet automation alone will not address the issues inherent to our complex organization. Zendesk engineers are a large and geographically distributed group, with interdependent teams and resources. Automation will only slightly move the needle towards our required velocity. To reduce cycles significantly, we need to move beyond automation and onto *self-service*, so that our infrastructure is not susceptible to human error and our engineers can move even faster.

Self-service is paramount to achieving our higher-level goals like increasing team velocity, reducing tedium, and enabling simple access to resources that are approved and compliant. Ultimately our goal is to empower our engineers to scale their processes in lock step with the scaling of Zendesk teams. By giving our engineers the power to work more efficiently, Zendesk can deliver and innovate more quickly.

**Common interface**

So how do we make self-service happen? When a Zendesk engineer wants to build something new or modify something, they need to know where to go and how to get started. We must provide them with a common interface that allows any engineer to easily pick and provision their required resources across all of Foundation’s offerings, e.g. data stores, Kafka topics, container orchestration, proxy routing, etc. Using a single, consistent tool minimizes learning time and maximizes efficiency. Engineers can focus on getting their job done, while we work behind the scenes to make all the infrastructure come together. The current plan is to use a YAML file within a service’s git repository and be tightly integrated with our future build pipeline. We are in the middle of staffing a team to own this lightweight interface and [choreographic](https://specify.io/concepts/microservices#choreography) system.

**Trusted advisors**

In addition to offering a common interface, we offer our expertise. We hope to be trusted advisors. If a team wants to use a data store like MySQL, we can provide Aurora MySQL. If a team wants to make the best use of a storage engine or improve performance, we can help them design their schemas or suggest changes to indexes. Should they run into problems, we’re there to assist and help them debug. The Foundation team spends all day working with these systems, learning exactly how they work and maintaining relationships with our vendors and Open Source communities. We work with both to understand how we can best leverage various options. We hope our specific deep knowledge can help other Zendesk engineers when they need it.

**Our technical choices**

Our teams have made a number of technology choices that support our work.

Config: *Secrets-Hashicorp Vault; Service Discovery-Hashicorp Consul; Infrastructure as code: Hashicorp Terraform/Atlantis, AWS Cloudformation.*

Secure: *IAM accounts: AWS, LDAP, GCP; Security and Compliance as code-AWS Config; EC2 and Container OS Base Platform (and associated pipelines.)*

Edge: *Cloudflare for our default edge providers, DDoS mitigation, and all the other functionality that Cloudflare provides; Standardizing on Nginx as our routing mechanism.*

Compute: *All in on Kubernetes for general needs except for those cases where Lambda offers a tighter, most convenient interface to AWS services.*

Storage: *Shifting from self-managed data stores (MySQL community edition, Riak, Cassandra and MongoDB) to Managed AWS data stores (MySQL Aurora, DynamoDB, S3, Kafka) and making them easy to provision and maintain using Kubernetes Operators.*

Analytics & Machine Learning: *Streaming data into S3 using Bin Logs via Kafka and Kafka Connect; Using Apache Spark for batch & Apache Flink for streaming; For ML platform, AWS Batch and Sagemaker.*

Network: *Implementing a service mesh (which one? TBD); Continuing to use our home-built routing networking solution, called [Medusa](https://youtu.be/KGKrVO9xlqI?t=3582), until something else becomes available.*

**Reaching our destination**

While we need to evolve our architecture, we can’t just drop everything to pursue the shiny stuff. We need to keep supporting the existing technology that enabled us to build a business on track to reach 1 billion dollars of revenue by 2020. As always in tech, we’ll need to make constant tradeoffs based on evolving data and insights.

With all our accounts now migrated out of the data centers, we’re entering the next stage of our journey. We will dramatically improve the automation of our infrastructure, use self-service to create a golden path, act as trusted advisors, and continue to support the evolution of our overall architecture.

There will be challenges along the way. We’re experiencing them already, especially around how we evolve our compliance controls and offer initial self-service while building out the Foundation Common Interface. We’re working through each of those challenges with the intent of ensuring our early adopters aren’t burdened as we evolve our offering, and always keeping in mind the importance of protecting our customers’ data.

It will be a journey, with bumps along the way — no organizational structure or golden path is ever perfect. We’ll have to listen, learn, and adapt. At the moment, I’m confident we’re moving in the right direction to allow our engineering organization to rapidly scale through the next 5+ years.

Onwards :)

*The Zendesk Foundation Engineering team is located all around the world. Config & Secure are based in Madison; Compute in SF; Edge in Dublin; Storage in SF, Melbourne and Dublin; Analytics & ML in SF and Melbourne; and Network in SF and Madison. If you live in any of these cities, or want to live in one of these cities and work with these technologies, then reach out to Alireza who leads our Foundation team: jsmale@zendesk.com*
