#Our Product Vision
Our product vision describes how we think about building Cloudkeeper over the next ten years.

The name "Cloudkeeper" btw is derived from "Housekeeping for Clouds" - just like a Housekeeper looks after a house, Cloudkeeper looks after your cloud.

##Our Origin and How This Vision Will Evolve Over Time
Our co-founder Lukas started developing Cloudkeeper in late 2019 as an internal project at D2iQ (formerly Mesosphere).

At the time, Lukas was an SRE at D2iQ and needed a tool to give him the big picture of all cloud resources running, automate their documentation, and reduce spend.

Like all start-ups, D2iQ had prioritized growth. Engineering headcount at D2iQ had grown to over 200 people, with some 40+ AWS sub-accounts, and everyone was spinning up resources. A team of just three SREs had to support all this growth, and their priority was to build things that would increase feature velocity. "Let's worry later about that SRE stuff".  

As a result, D2iQ's AWS bill kept creeping up. From the mid 5-figure range to the mid 6-figure range _every month_. D2iQ as a business had grown too, but cloud spend was growing much faster than customers and revenue. There also were outages. Usually because some obscure AWS service in a sub-account had run into quota limit, which brought the entire development pipeline to a halt.

And so the order came down from the CEO and the CFO to reduce cloud spend, and bring order to the chaos.

The scenario probably sounds familiar. And there were plenty of infrastructure tools out there at the time that promised a solution. But they all had the same drawbacks:

- Rule-based. The tools assume that you know what your problem is, and that you know what you're looking for. And they work well in that situation. But not so much if the tool didn't create the resource. You just don't see it in your inventory. You can establish rules for tagging, etc. - but if you have 200 engineers, automated systems, something will aways fall by the way-side and the rules don't work.

- "Columns and rows". The tools produce a long list of resources, sometimes in a pretty UI, but don't show any dependencies. You couldn't understand a resource's "blast radius" if you wanted delete it.

- Context. There's no context for any individual resource. If it's not tagged, it's hard to understand for e.g. Finance why the resource is running. It comes back on the SREs to explain it.

Lukwas wanted a tool that periodically collects a list of resources in cloud accounts, provides metrics about them, and can clean them up. Rather than creating yet another list with "rows and columns", he chose to store information in a graph. The graph reflects dependencies and also stores context.

The first version of Cloudkeeper was deployed in early 2000. And it delivered. Within four weeks, cloud spend was cut in half! Another six months later, cloud spend had been reduced by a total of 70%. The entire infrastructure had become more resilient.

In 2020, D2iQ open-sourced Cloudkeeper, and Some Engineering Inc. took over development in July 2021.

A lesson learned from our history is that the biggest question to ask is always "Why now?". Why is now the right time for something like Cloudkeeper, and why would customers care?

That's what this product vision is about. We're projecting the "Why now?" into the future. For the near term - it's still trends like cloud-native and multi-cloud infrastructure that drive our roadmap.

# Cloud Infrastructure Has Changed

Cloud-native architectures have caused a change in the way companies operate their infrastructure. What used to be manual processes and ITIL practices is now infrastructure-as-code and self-service automation.

Developers are in the driver's seat - they determine what cloud services they want to use, and spin up resources as needed. The goal is feature velocity, and to ship new digital products faster. But - the larger and more distributed an organization gets, the more challenges these new dynamic environments create.

CI/CD pipelines and tear down jobs fail. Things break and don’t get cleaned up - the result is drift, and a rising cloud bill. Despite garbage collection, “stuff” is leaking. Artifacts get left behind, growing the number of orphaned resources. It’s not just servers, databases and VPCs. It’s also things like accounts, SSH keys, IAM policies, roles and certificates, volumes and their snapshots and dynamic IP addresses. It’s a long tail of resources.
