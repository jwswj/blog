
# 10 tips for growing a globally distributed engineering team

Zendesk has built out a global engineering team spread across four continents, nine countries and 10 cities around the world. We started the journey relatively early in our company’s life, it’s been difficult, and we’ve learned lessons along the way. Many of the things we got right, came from key people who had run global teams before (and knew the mistakes they didn’t want to repeat). Many of the things we got wrong, were based on assumptions that Zendesk would work as another business did. We’ve learned there’s no perfect strategy for expanding beyond head office, but we have been able to refine down some of the core beliefs that anchor us. These seem applicable beyond Zendesk, so I wanted to share. To do that, it’s worth spending a little time talking about how Zendesk grew up, so you can understand the incremental decisions we made to get to where we are today.

**Our backstory**

Born in non-stereotypical Copenhagen we hired our first engineer remotely in Argentina (he’s still making Zendesk better today). Over time we moved to Boston at the request of our first venture capital investor and energetically embarked on a mission to build a team in a *single* location. We actually still believe in the importance of physical co-location today. Being able to talk things through face to face, or drop by someone’s desk, builds relationships and trust.

But life doesn’t always turn out as planned. In Boston the team survived a harsh winter and were pleasantly surprised to get funding from a San Francisco based firm. It wasn’t a hard decision to move everyone to the up-and-coming SF end of Silicon Valley. Quite quickly, Adrian McDermott joined as our head of engineering and we were getting serious about building a pretty big engineering team. We needed to hire engineers, specifically Ruby engineers if possible. We had all these positions open … and we just couldn’t hire at the rate we needed.

All our candidates were saying they liked us, but they were getting offers from the likes of Google, Twitter and Netflix. These companies were a few years ahead of us, growing faster and had more to offer. Recruiting was pretty demoralizing during this time. It got to a point where we said to each other, “Can we hire engineers anywhere else? We’ve already got Anibal in South America. We need to look outside of San Francisco.”

**Finding our people around the globe**

Mikkel, Morten, and Alexander knew some of the Ruby community in Copenhagen. They flew home to spend some time there and leveraged their existing network to recruit two people! Copenhagen had the added benefit of being a place the founders wanted to visit. When you expand to new locations, it’s rather helpful to have a dual benefit when you visit. This approach worked! We found great people in Copenhagen and very quickly had a team of three! There weren’t many product companies in this part of the world, so to our potential hires, Zendesk presented an opportunity to work for a Silicon Valley tech company, without having to relocate across the world.

Even though the Copenhagen office was growing, we were still behind from a hiring perspective. We thought, “this model could probably work in other places around the world.” Opportunistically, Zendesk’s first employee had just moved to Melbourne. His name was Michael. He had grown up in Copenhagen, but prior to Zendesk had followed his wife’s work to Melbourne. After a stint in Boston & SF, they had decided to move back. They probably didn’t realize how significant that decision would be for engineering at Zendesk.

Australia was our third biggest country at the time, and Michael used the move to accelerate that growth and set up a structure for Zendesk to operate in Asia. While in Boston and SF, he had observed the value of physically sitting engineers next to Sales and Support. He found a local engineer and pitched that he should build a Zendesk engineering team in Melbourne. He pitched without Adrian’s knowledge as I understand it, then convinced Adrian it was a good idea … within 2 months we had an engineering team in Melbourne. It is now our biggest engineering office globally outside of San Francisco. That local engineer was me :)

A few months later, we decided to launch a data center in Dublin. We thought it would be a good opportunity to have product and engineering on the ground. Another new office was born. At that point, the organization had reached about 100 engineers, up from 15 when we opened Copenhagen. We had dramatically changed our recruiting profile and now had four different markets we could recruit people into. We just started recruiting in all those different places and seeing where we could find great people!

**How we scaled**

A common question is: “how did you scale a global product and engineering team?” The short answer is: hire great people in locations around the world, give them ownership, partner with them, build trust, repeat. The longer answer is: we were like new parents with Copenhagen, there was a lot of trial and error. The time zones also made it difficult (often only one hour of business hour overlap).

In the early days, we asked Copenhagen to be an extension of the team in SF. That worked horribly. We had a release cycle where we only deployed the main application once a week (on a Thursday). Copenhagen would put changes in, those changes would get deployed while they were sleeping, and something would break. It wasn’t a healthy way to work. Eventually, we realized we needed to give Copenhagen the ability to control their own destiny, to *own* something themselves. We said, “Copenhagen, we are giving you Forums (now Guide). It’s a critical product. We trust you with it. Make it awesome.” This worked! They took ownership, extracted it from our monolith, started to deploy it multiple times a day and pumped out new features.

As more offices came onboard, this ‘gifting’ of products became a successful pattern. The core team in SF had built all this stuff over the five years Zendesk had been alive. They were working frantically, firefighting, dealing with scaling problems (and a complete rewrite of our user interface). There were many extra products that needed love. One-by-one, we took a product area and transitioned it out to a region. We said, “Dublin you can take Zendesk Chat, that can be your responsibility.” That went well, so we said “Dublin you take Talk as well!” The same was true for Melbourne, “you can have integrations and our developer platform.” This meant the SF team was free to move onto the next thing, stabilize existing systems, enhance the agent experience or build the core critical components that everyone else depended on.

This was an idyllic, organic way to grow. We incrementally built trust and gradually moved responsibility and ownership. It was a very successful model, also allowing our offices to grow at different paces … then, we made our first acquisition. That company was based in Singapore and was a whole new ball game! There is close to a 12 hour time difference, it was already a fully-fledged team and we couldn’t ramp it up slowly. Quite often, acquisitions are duplicative services because you’re running a ‘build, buy or partnership’ strategy (concurrently trying to build the product you end up acquiring). In these cases, international expansion becomes that little bit more difficult especially when you have to reconcile the broken hearts of your existing engineers.

Since then we’ve acquired companies in Montpellier (France), Krakow (Poland) and Montreal (Canada). We have also organically added another office in Madison (Wisconsin). This gives us a total of ten full engineering centers around the world. And it’s amazing! We would do the same again in a heartbeat: we would expand outside SF, we would acquire the best teams globally, we would make it work from a management perspective.

**Benefits**

This model has allowed Zendesk to continue to hire at an incredible rate, especially juniors. There are wonderfully talented engineers coming out of universities in every country around the world. There’s a high density in SF, but realistically they’re everywhere. We now have access to incredible talent in eight cities that aren’t default tech cities. That gives us a real advantage for recruiting. We also see a higher retention rate for engineering teams outside of SF, which is a great thing.

There are also financial benefits. Governments around the world are excited to increase the number of tech workers in their economies. It has a wonderful compounding effect: we can hire more people, in more markets, at less cost. It means we can have more people improving Zendesk products. That being said, we never let this be a driver for expansion.

Then, there are the practical benefits of having a globally distributed team. It makes on-call easier and has been incredibly helpful when large scale incidents have hit and we’ve needed response teams working around the clock for multiple days. We instantly know we can grab people who know our systems, know our standards, and run a 24-hour incident response over a sustained period of time.

As you can imagine, there’s also plenty of challenges but, “for every problem, there is a solution”. With that in mind, here are our tips on what worked, what didn’t, what we’d do again.

**Tip 1 — Have business hours overlap**

From early on, we understood it was best to avoid locations that were difficult from a time zone perspective. Many of the new Zendesk leaders had previously been at companies where there was a ‘follow the sun model’ (12 hours of difference between the two offices). In reality, that’s no good for anyone: you’re either on a video call at 9pm at night, or 6am in the morning, neither of those are good for health. That’s where Melbourne worked well for SF. We have three hours of business hours overlap for the majority of the year so it’s more likely we’re going to talk. That’s a really important thing.

Having said this, we’ve now got more offices in time zones that don’t work well together. For example, projects between Dublin and Melbourne are really difficult. We avoid getting those offices to work together where we can. Sometimes we need to compromise, when we do, we make sure people are in a position to travel frequently to the other side of the world. We know we can do it for three months, but we can’t sustain it for twelve. It impacts family too much, it burns people out, and that’s not worth it for us.

**Tip 2 — If you can’t hire the leader, don’t do it**

Over time, it became clear that the successful offices had one pivotal thing in common — a great engineering leader. That person was many things: they were local to that city, they were experienced, they had a network, they knew how to recruit, they knew how to deal with government, they would host meetups, they could assist sales teams locally and they could build an engineering team without much oversight. These types of people are difficult to find, and ways to find them are varied. Governments can play a good role in connecting to the talent (both our first hires in Dublin and Melbourne were introduced by their respective governments). You will find good individual contributors anywhere in the world. But until you find the one person who can recruit all those great people … don’t do it.

I personally learned this lesson the hard way. In Manila, I saw we had built out a Support team. It was going really well, but there was a distinct lack of engineers. I thought, “here’s a great opportunity to enter a new market and reach a new talent pool”. I couldn’t find an experienced engineering leader … but I could find a couple of fantastic engineers. They were hungry to learn and excited to work for a company like Zendesk. I decided to try it. I hired two engineers and planned to manage them remotely, while they continued to interview for a manager … we never found that manager, one of them turned into the manager and did a good job. I feel like their career growth was limited because they didn’t have a local manager helping them grow day to day. In retrospect, I wouldn’t do it again. I would say to myself, “it’s not worth it, even though we will miss out on working with some talented engineers and fantastic people.”

**Tip 3 — Make ‘Head of Engineering’ also ‘Head of Office’**

As I mentioned above, that first engineering hire must be many things. Suddenly, they are responsible for working with legal and finance to get the region online and running healthily. This means finding office space, making sure there’s a legal entity in the country, ensuring stable internet, working with government, being the face of the company at local universities and meet ups. It takes 30–40% of their time, and is the stuff some engineers don’t have fun doing. But these things are critical if you want to grow a team of 20–50 pretty quickly. This person is going to establish your engineering brand in a location, choose carefully and give them plenty of guidance about the culture and brand you want to project locally. Your local head of engineering is new to the company, so this is hard. Making the Head of Engineering also the Head of Office worked really well in the early days and gave the tenured people we hired a broad enough scope while the engineering team was still growing.

**Tip 4 — Align, at least every 3 months**

The other important piece was ensuring alignment between all our engineering leaders around the world. As teams became more autonomous there was more chance of misalignment. It was impossible to get everyone on a video call at the same time. We decided we may as well have one chance every quarter, and condense it all down to a single week in person. Every 12 weeks the heads of engineering still meet somewhere in the world to align, share what their teams have done, plan for the next quarter, work through globally relevant topics, then return to their teams and execute. This cadence was really important and remains important today. Travel expense is a necessity not a luxury — we joked that “Zendesk is a Travel Agency for Engineers that also make software”. This sends the wrong message, your CFO has two choices: Pay SF wages or buy a few airline tickets every quarter — the travel is not negotiable.

**Tip 4.5 — Total Product Ownership**

We do not outsource or offshore — we hire talented, multi-disciplinary teams to build SKU’s and features in global locations. These teams need near-total control over the execution of short term roadmaps and product strategy. That means that Product Management and Product design also need to be on the Global Workforce bus. They need a distribution strategy and they need local management and individual contributors. SaaS software is a team sport and everyone needs to be playing the same game with the same tactics and understanding of distributed authority.

**Tip 5 — Commit to fast iteration cycles**

Having just engineering outside of SF didn’t work. We needed product and design team members sitting side-by-side with the engineers to decrease delays and increase velocity. Once you commit to having engineering somewhere, there’s incredible value in committing all three to that location. If even one is remote, it slows down iteration cycles. Whereas HR, finance, legal and sales can follow later.

**Tip 6 — Build a bridge for acquisitions**

In Copenhagen, Melbourne and Dublin the Zendesk culture was organically absorbed as we grew those teams (plus SF was responsible for most of the interviewing). Acquisitions are a completely different experience. When we acquire a company, they have already built a unique culture of their own due to charting their own course.

One of the things we’ve learnt with acquisitions is that it’s critical to have multiple Zendesk employees relocate for at least a year and a half, if not two years. They must be the bridge between the acquisition and the Zendesk world. They must unblock from a product perspective, unblock from a technical perspective and help navigate the organization. This has been a hard thing to always do, yet we still believe it.

Welcoming acquisitions also caused us to start to define integration standards to give teams a clear sense of what we expected to be completed within the first year.

**Tip 7 — Everyone needs a friend**

As Zendesk grew in every location, many looked to leverage our global structure. At the time we had a centralized SF Operations team who were responsible for running (and being on call) for all our services. As the global offices grew, we said “This will be great! We don’t have to be on call outside business hours anymore. We can hire one person in Melbourne, they can hand off to Copenhagen, they can hand off to SF!” Everyone in SF said, “brilliant, this will be great.” So we hired one person in Copenhagen, and one person in Melbourne.

Looking back, that was a mistake. When committing a new function in any office, we suggest a minimum of two people. Those lone Operations hires needed someone with context to talk through ideas with, and to rant to occasionally. They needed someone to cover for them when they were sick and didn’t want to burden someone in SF to go without sleep. They needed someone to give a +1 on their pull requests and peer review in the same time zone to keep iteration cycles fast. Both those first Ops hires ended up leaving Zendesk. It’s worth noting, one has recently returned now we’ve moved away from a global Operations team.

**Tip 8 — Avoid juniors reporting across an ocean**

The same concept is true for junior employee reporting lines. It always seemed like a good idea at the time: “Let’s put two security and two design people in each office. We’ll have all those people report to a manager in SF.”

We’ve found junior employees grow significantly faster in their careers if they have a local manager who can help them day to day, observe their actions and provide in-person feedback. We’re now at a size where we aim to only have senior managers reporting across an ocean. They can handle having a remote manager because they’ve been a manager before, often don’t require as much from their manager to make them successful. Similarly, we’ve also had our best success with remote employees who are senior.

**Tip 9 — Standardize And Write Everything Down**

Tools are important, keep a tight grip on technology sprawl and proliferation. You need a relatively consistent development process, culture, tool chain, onboarding process and technology stack. Our engineers need to be team Zendesk first, team location second. As a single site development team, most of the information and culture is passed by oral tradition, cave paintings on white boards and consulting the local engineering shaman for advice. None of those things work across oceans, so you need to write everything down so that expectations are understood and there is a written record for remote employees to consult. It’s a great exercise because through the process of documentation, you will often discover what is important versus what we do just because we’ve always done it that way.

**Tip 10 — Be global by default when communicating**

It’s easy to be HQ-centric when you’re trying to appeal to a live audience, yet it dramatically weakens the message for people outside of the location. For example, in the early days we’d often have a San Francisco-centric section in our Town Halls (HR benefits, office update, an amazing happy hour, introduce new employees). Employees around the world would watch the recording and feel like they were missing out or second-class in some way. It was never the intent, but it happens, and we still catch ourselves doing it occasionally. We now try to be global by default with all communication, then focused with our locally relevant content.

Beyond town-halls, over the years we’ve tried all sorts of strategies for improving global communication. We have weekly engineering meetings, monthly managers and leaders meetings, podcasts, 2-pager updates from teams and more to keep everyone up to date. With all the time zones that are involved, we often do meetings twice (APAC & EMEA friendly) and ensure that they recorded shared for asynchronous consumption. This year, we’ve had success with a weekly engineering meeting that is remote-by-default and we provide a 5min summary video for easy consumption.

**Conclusion**

These are just some of the key lessons we learned as we scaled a global engineering organization. Many seem obvious in retrospect, yet are still difficult to action when lured by a fantastic potential hire or pressured to deliver faster or decrease spending. I’m sure there’s still a lot to learn, but if you cornered any Zendesk engineering manager or technical contributor, they would probably start to tell you stories that related back to these tips. We hope other companies can learn from them, and internally, we hope to refine the list as we move on to our next stage of growth.

Our engineering team is getting to over 1000 people across our global offices, and we’re pretty happy with how things have turned out so far.

—

Thanks to Adrian, Soren, Dennis, and Jesper for contributing to the tips and reading drafts.
