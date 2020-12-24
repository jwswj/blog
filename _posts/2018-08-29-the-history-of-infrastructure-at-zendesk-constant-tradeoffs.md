
# The history of infrastructure at Zendesk (Part 1) — constant tradeoffs

I think Zendesk’s infrastructure journey is an important story to tell. Our path will always be unique to Zendesk, but our story will probably resonate with companies who were growing around the same time. The story of our growth is one we’ve often told internally, as new engineers have joined the company over the years. We find that while it’s an interesting story in and of itself, it provides invaluable context for engineers who haven’t been here since the beginning. It frees them to question decisions made long ago, and to challenge our current state. This has proven essential to continuing our technological evolution and the rapid growth of Zendesk.

I joined Zendesk in 2012; however, the story starts long before that. To capture the early days, I sat down with the person who was there from the very start, our founding CTO and co-founder Morten Primdahl.

**How did you settle on a language in the beginning?**

It starts in 2005 with Alexander, Mikkel and me in Copenhagen. We had to sit down and build this product, I came from Java/Unix world, Alexander came from .Net world. We had to find some common ground and decide what to build in … not that it was a big deal at the time! I knew David Heinemeier Hansson, the creator of Ruby on Rails; I was following him on the side and thought what he was doing was interesting. You could see even back then a good chunk of mindshare was going in that direction. There were some great minds pushing Rails and web development in general; it felt like we were converging on something. So it was a pretty easy decision to say, “we’re going to go with Ruby on Rails.” We just wanted to build this great feeling product with lots of interactivity and think about what a modern product should look like for customer service. And that’s how we settled on Rails.

**Did you just open up a terminal and type `rails new`?**

Yep.

**Where did the first version of Zendesk run?**

The first production instance was tiny with 645MB of RAM running on Engine Yard. That was the Zendesk production system! MySQL was running on a shared database. We went with Engine Yard because they were experts in deploying Ruby on Rails applications. They had a big chunk of knowledge about the entire Stack, which I felt was a good thing because if there was an emergency, we had someone to take care of it if I was unavailable.

**Did the infrastructure change much in the early days?**

It took a couple of years before the site started to see much serious traffic, a few customers came along, we kept evolving functionality, but infrastructure stayed similar for the first year at least.

Something we’ve always cared about has been database performance. We built product features that customers wanted, but that meant we sometimes asked systems to do things they weren’t very good at. From very early on we were using New Relic (which was mind blowing back then, there was nothing like it). So we were constantly looking into response times and keeping the average response time under 160ms.

**What was an early event that changed the way you thought about our infrastructure?**

In early 2009, we had 600 customers and a single primary database with a couple of replicas. When you have 600 companies using your product, you start to feel like that’s something. Then one of our customers (a large social network) went live. Overnight, our traffic quadrupled and our database started growing like crazy because this company created a Zendesk end-user record for each user who signed up. This is now a common pattern for our customers, but at the time we hadn’t seen anything like it. We scaled vertically to get out of the immediate pain, knowing it was only a short-term option. Their load was pivotal in making us think more strategically about how to scale. They were our big fish, and drove a lot of load, for a long time. We are really grateful to them for that.

**Why Rackspace?**

In late 2009 we started feeling increasing pressure from the instability of the data systems and relatively long lead time on new hardware. All of a sudden a slow query would hit from a Ticket View that someone had made, and when you are on spinning disks, it could take out our entire IO subsystem. We could see this happening more and more. We’d reached the size where the working set would no longer fit in memory, so the database would start swapping and it would kill performance for everyone. So after our growth in 2009 we had to sit down and say “What is the best option for us today? We need more and we needed a hosting partner who can provide hardware when we ask for it.” And that’s what Rackspace did.

At that time we considered AWS, but we couldn’t use it because we had huge throughput requirements on our databases. Their offerings at the time just did not make any sense for us. So we ended up at Rackspace with brand new servers and FusionIO SSD drives for our MySQL databases. At that time, those drives were a game changer in terms of stability and performance. They had 100,000 IOPS versus a 24 disk RAID that had like 3000. We knew eventually we would run out of disk space, and those drives are super expensive. But it bought us some time to think about how to evolve our architecture.

**The legendary MySQL crash?**

During the early days on Rackspace, and with our shiny new FusionIO drives, we ran into a serious problem. At that time we had two replica databases because when we did a database backup the replica would slow down so much that it couldn’t replicate fast enough from the primary and we’d be stuck with lag on the replica that was the fallback. We basically had a primary, a read-replica and a backup-replica.

Then, all of a sudden we started having massive MySQL crashes. When it crashed it would just not come back up, then when it did come back it was corrupted and we’d have to do a full restore to repair it. It tooks us hours. One night the primary went down, we did a fail over, then the new primary went down and we ended up running production on our backup-replica. It’s one of those moments you always remember because you never want to be back there.

We eventually found a work around and managed to replicate it, and we sent it to the MySQL team (which is the great thing about Silicon Valley, you can get hold of anyone). And they had a patch for us the next day. Essentially only us and Facebook had ever seen that specific issue. *But when the database that is the cornerstone of your technology business just disappears on you, you’re really in a bad spot. *So we had to prioritise this at a much higher level.

As an aside, the episode shell shocked us to an extent that we operated with three replicas for the following two years.

**Today we heavily shard MySQL. Tell me about sharding?**

8–10 years ago there weren’t that many people who had done sharding, especially in Denmark where we came from. No one had done sharding there! But Facebook and Google had shown it was a proven model, and in 2009 it was just what you had to do if you were running out of capacity in your MySQL instance. You had to have a way to distribute load and storage.

We knew it was going to be a departure from the easy world of working on the monolith and Rails. Sharding is not necessarily pleasant; it creates a lot of organisational pain because just running database migrations becomes difficult and engineers need to understand the new database topology. But it worked. And the amazing thing is that it still works. It’s not ideal compared to what can be done today, but it took us from where we had customers with tens of millions of tickets, to now where we have customers with hundreds of millions of tickets. It kept our head above water while we were waiting for the technology to be created that would allow us to do it better.

**Was there any thought at the time of moving away from a single Ruby on Rails application, with a single database, and towards a microservices pattern?**

We had 3 big entities at the time: Tickets, Ticket Events and Users. Sure we could split that up, but the rest were nothing in comparison, which meant we wouldn’t have won much. We were really thinking, “what’s the biggest pain we can address?” And that was the growth of those entities. Relative to that, it seemed pretty insignificant what we would gain at the time by splitting up the codebases.

**We’ve talked a lot about the technology, but so much of building great infrastructure is about the people you have and the teams you create. How did the team grow?**

In 2009 we had enough capital to hire our first Ops guy and a couple of engineers with great minds for infrastructure. But these guys weren’t just doing infrastructure; they were doing all sorts of automation and deployment.

This was a crazy time of growth and we were constantly balancing building our product with the next thing that was going to kill us, the fires. We knew if we didn’t isolate people to look at those fires, they would get dragged into Product and suddenly all our feet would be burning! So we had to allocate engineers to it, even if it isolated them from Product at the time. We ended up with a team focused on features, an Infrastructure team and an Operations team. Then I also created an Office of the CTO team (nicknamed OCTO) too to focus on Ruby scaling issues.

**Zendesk has engineering teams in 9 offices all around the world. How did that happen?**

We arrived in the US shortly after the 2008 global financial crisis and as such had a relatively easy time hiring. That changed over the next couple of years as the large technology companies ramped up again and a bunch of new startups entered the stage. So rather than accepting to compete against them, we started to look elsewhere, and that’s when we hired some people in Denmark. They were the first engineering team outside Zendesk headquarters to join the company. They were super smart, they were 9 hours ahead of us, they weren’t sitting next to us to see how we did things, and didn’t have the historical understanding of our systems. Soon after it became pretty clear we needed to give them their own application and vision to work on.

For a long time we were only going to have a single database at Zendesk. We were still feeling some pain from scaling the database systems and we were wary of saying “Hey Copenhagen, set up your own database and run it yourself” because we hardly had a DBA. But it meant we could get these guys working right away. And then came Melbourne, and then came Dublin. The speed of hiring and having teams in multiple regions changed the way our infrastructure evolved quite dramatically.

**Why did we move beyond Ruby on Rails?**

However productive Ruby on Rails is for building software, the relatively slow execution speed of Ruby can get in the way. The first introduction of a new language was Node.js, because we were building chat functionality and needed a language with good high level abstractions and async IO. But we were still very purposeful at this point. Honestly back then there weren’t that many languages to choose from.

Then we made some acquisitions and we got Python and Scala. I think you have to use the tools that are there for you, but that can also result in things becoming a little rough around the edges. You have to clean things up every once in a while and have standards.

**In 2012 we decided to again move our hosting. Why did we then do hardware ourselves?**

We were sitting in a middle ground where we were growing fast enough to face real pain, but not fast enough to take on the infrastructure and build it ourselves. We weren’t the size Facebook or Google, but we got better at building things all around the world. For business continuity reasons, you can’t just be in one place. It was about economy of buy in. Also denial of service attacks. We had to figure out a place where we could have a bigger say in the network infrastructure, so we could take our own path.

People often ask why not AWS at that point? We had conversations with AWS way back then but they didn’t ship provisioned IOPS until late 2012, and even then the throughput on the EBS volumes couldn’t meet our needs. We couldn’t deliver our product without an IOPS guarantee. A big part of me wishes we had the mentality to challenge that and solve the Ticket Views problem back then. On the other hand I think, it’s exactly what makes the Zendesk product magical and appreciated — it’s not just a static table with tickets that can be sorted by this column or that column. Businesses can define their Views in a way that makes sense to them. So we had to ask ourselves what is it that makes us successful as a company and how can we not kill that technology just because it’s complicated? So, long story short, AWS was just not an option for the throughput we had at the time. How times have changed!

**Can you talk about the pain of trade offs?**

We know the development of our infrastructure has in some ways been a painful journey. At many times I could see exactly what the engineers wanted and I agreed with them. But we had to remember, what is this about? This is about survival, we can’t scale if we don’t survive. There were times where we were saying “OK should I put out this fire? Or work out how to speed up that container for you? I think the fire is more pressing.” All those work arounds were the result of us giving our customers a super flexible system, a system where they can look at things that are complicated. We did things we knew were not going to scale indefinitely. So this is self-inflicted pain, and however frustrating for an engineer to see, it’s about picking our battles.

For better or worse, Engineering has been really good at isolating its problems from the rest of the business, as it should be. They’ve provided our customers with what they needed, even though it was not the easiest path. What I am excited about is that we’re now starting to make use of this new, now accessible technology and reimagine some of the Zendesk infrastructure that kept us in business for more than 10 years.

**The future?**

In the future I think there will always be a different set of problems. We’ll continue to evolve our infrastructure as our business grows and morphs, focused on the value we provide to our customers. We’ll also evolve our infrastructure to ensure that our organisation can remain productive, so we can react to a changing market and take advantage of new technologies.

I’m excited that we’ve now scaled to a size where we have a Foundation Engineering team, which is a unification of Infrastructure and Operations, and can be very purposeful in the way we build our Infrastructure. We’re making fantastic progress migrating to AWS, Kubernetes, Aurora, Kafka and moving to a service-oriented architecture.

**Thanks Morten!**

*Zendesk is hiring engineers to work on evolving our Infrastructure in Dublin, Melbourne, San Francisco & Madison. Find out more on our [careers site](https://www.zendesk.com/jobs/).*
