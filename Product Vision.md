# Our Product Vision
Our product vision describes how we think about building Cloudkeeper over the next ten years.

Some Engineering Inc. is a new company. As we learn new things, we will update our vision on a rolling, quarterly basis, in particular the short term 1-year vision.

The name "Cloudkeeper" btw is derived from "Housekeeping for Clouds" - just like a Housekeeper looks after a house, Cloudkeeper looks after your cloud(s).

## Our Origin and How This Vision Will Evolve Over Time
Our co-founder Lukas started developing Cloudkeeper in late 2019 as an internal project at D2iQ (formerly Mesosphere).

At the time, Lukas was an SRE at D2iQ and needed a tool to give him the big picture of all cloud resources running, automate their documentation, and reduce spend.

Like all start-ups, D2iQ had prioritized growth. Engineering headcount at D2iQ had grown to over 200 people, with some 40+ AWS sub-accounts, and everyone was spinning up resources. A team of just three SREs had to support all this growth, and their priority was to build things that would increase feature velocity. "Let's worry later about that SRE stuff".  

As a result, D2iQ's AWS bill kept creeping up. From the mid 5-figure range to the mid 6-figure range _every month_. D2iQ as a business had grown too, but cloud spend was growing much faster than customers and revenue. There also were outages. Usually because some obscure AWS service in a sub-account had run into quota limit, which brought the entire development pipeline to a halt.

And so the order came down from the CEO and the CFO to reduce cloud spend, and bring order to the chaos.

The scenario probably sounds familiar. And there were plenty of infrastructure tools out there at the time that promised a solution. But they all had the same drawbacks:

* Rule-based. The tools assume that you know what your problem is, and that you know what you're looking for. And they work well in that situation. But not so much if the tool didn't create the resource. You just don't see it in your inventory. You can establish rules for tagging, etc. - but if you have 200 engineers, automated systems, something will aways fall by the way-side and the rules don't work.

* "Rows & columns". The tools produce a long list of resources, sometimes in a pretty UI, but don't show any dependencies. You couldn't really understand a resource's "blast radius" if you wanted to delete it.

* Context. There's no context for any individual resource. If it's not tagged, it's hard to understand for e.g. Finance why the resource is running. It comes back on the SREs to explain it.

Lukas wanted a tool that periodically collects a list of resources in cloud accounts, provides metrics about them, and can clean them up. Rather than creating yet another list with "rows and columns", he chose to store information in a graph. The graph reflects dependencies and also stores context.

The first version of Cloudkeeper was deployed in early 2000. And it delivered. Within four weeks, cloud spend was cut in half! Another six months later, cloud spend had been reduced by a total of 70%. The entire infrastructure had become more resilient.

In 2020, D2iQ open-sourced Cloudkeeper, and Some Engineering Inc. took over development in July 2021.

A lesson learned from our history is that the biggest question to ask is always "Why now?". Why is now the right time for something like Cloudkeeper, and why would customers care? That's what this product vision is about. We're projecting the "Why now?" into the future.

For the near term - it's still trends like cloud-native and multi-cloud infrastructure that drive our roadmap.

# Cloud Infrastructure Has Changed

Cloud-native architectures have caused a change in the way companies operate their infrastructure. What used to be manual processes and ITIL practices is now infrastructure-as-code and self-service automation.

Developers are in the driver's seat - they determine what cloud services they want to use, and spin up resources as needed. The goal is feature velocity, and to ship new digital products faster. But - the larger and more distributed an organization gets, the more challenges these new dynamic environments create.

CI/CD pipelines and tear down jobs fail. Things break and don’t get cleaned up - the result is drift, and a rising cloud bill. Despite garbage collection, “stuff” is leaking. Artifacts get left behind, growing the number of orphaned resources. It’s not just servers, databases and VPCs. It’s also things like accounts, SSH keys, IAM policies, roles and certificates, volumes and their snapshots and dynamic IP addresses. It’s a long tail of resources.

## The problem is getting worse.

Drift can cause all sorts of downtime issues. Today’s infrastructure management tools don’t offer a solution. They do a good job of managing resources they know about. But they do a poor job managing resources they didn't create.

For SREs in charge of maintaining cloud infrastructure, it’s a drag. They are typically outnumbered by developers by a factor of 50-80x. At the same time, SREs are expected to build features that increase development velocity. Over time, that widens **“the gap”** between the desired state and the actual state of the infrastructure.

# A new approach
This is why we’ve built Cloudkeeper.

Cloudkeeper is “housekeeping for clouds”. It automatically cleans up drift that shouldn’t be there and closes **“the gap”**.

Cloudkeeper indexes resources, captures dependencies and maps out your infrastructure in a graph so that it’s understandable for a human. The graph contains metrics for each resource. Developers and SREs can search the graph with a query language, and create alerting and clean-up workflows.

## 1-Year Vision: Make clean-up and search in multi-cloud infrastructure easy for developers and engineers

Cloudkeeper is the one place where developers and site reliability engineers go to search for resources in their cloud infrastructure. They create event-based workflows that automate high-value but also high-effort tasks such as deleting unused resources or documenting cloud inventory for audit purposes.  

Cloudkeeper is a horizontal product that supports AWS and GCP. That is more for historic reasons than for market share reasons. Cloudkeeper started as an internal D2iQ project, and D2iQ runs on AWS and GCP.

Cloudkeeper is an expert tool for engineers that runs on top of the Keepercore graph platform. They interact with Cloudkeeper via a command line interface (CLI), a tool all engineers are familiar and comfortable working with.

* We keep their cloud infrastructure permanently clean.

* The Cloudkeeper Query Language offers an abstraction layer for engineers to query and collect metrics from their infrastructure. Think `> match is(instance) and tags.owner ~ jane` e.g. to find all compute instances across AWS and GCP owned by Jane.  

* We collect bare metal information. Hardware specs differ, even for the same type of instance. Pre-deployment we give developers estimates about the fastest / cheapest hardware per region, and once they have the instance let them know exactly what they got.  

* We integrate with Terraform and show the difference between the planned state and the current state of infrastructure in our CLI.

* On top of the CLI, we will build a UI/UX that makes navigation with the resource graph intuitive. Someone can search, navigate and click on resources in the graph. They can annotate and build workflows across all resources.

* Users receive notifications when resources relevant to them change, via integrations with popular “ChatOps” tools like Slack, Teams and Discord.

* We offer an approval workflow within these tools (“Cloudkeeper will delete these resources. Are you ok with that?”).

* We start with collecting metrics from AWS and GCP cloud services most relevant for users, and expand the number of supported services with each sprint based on what the community is telling us.

* Because Cloudkeeper is extensible and open source, the community can build plug-ins and collect metrics from any AWS or GCP service that we do not support yet. Our SDK makes building new, custom plug-ins to collect data easy.

## 3-Year Vision: Anyone in a company can search their digital infrastructure and build workflows

We make it easy for engineers and all other company stakeholders (Finance, Legal, Product, Customer Success, etc.) to explore and navigate a company’s entire digital infrastructure. They can build workflows, dashboards and reports in a browser, relevant for their business needs, and export metrics to their favorite tools. They don’t need to talk to an engineer anymore, which saves everyone time.

For example, Legal builds an inventory of workflows that verify ongoing infrastructure compliance with regulatory frameworks such as HIPAA, SOC or FedRAMP. Finance pulls cloud cost metrics down to the individual product and user level and exports them to their Snowflake data warehouse. For a sustainability report, engineering calculates a company’s annual carbon footprint based on the hardware profiles of their cloud servers.

By now, Cloudkeeper covers the major global (AWS, GCP, Azure, Alibaba), specialized (Digital Ocean, Oracle, IBM, etc.) and private / hybrid clouds such as VMWare and Red Hat.

We’ve expanded beyond the cloud, and also collect metadata from other infrastructure such as IoT devices - Raspberry Pi, industrial appliances, etc. Either directly, or through community-supported plug-ins. If something has an IP address, we can collect metadata and metrics - and that opens up new (vertical) use cases. Cloud computing is not the only infrastructure where it’s useful to be able to search, query resources, build workflows or have metrics and have event triggers. In short, reacting to changes. Something changes, and you want to be able to react to it. That’s useful for any digital infrastructure.

Say the valves of a fertilizer plant have embedded sensors. The sensors only have an analog serial interface and are not connected to the Internet. If the plant operator retrofits each valve with a Raspberry Pi, then Cloudkeeper collects data from both the Pis and the sensors, and integrates them into the overall company infrastructure graph. The plant operator builds the Cloudkeeper plug-in for the valves and defines the valve-specific primitives / attributes (e.g. ``pressure``, ``throughput``, ``temperature``) to collect, in addition to any applicable common attributes (e.g. ``atime``, ``ctime``). Cloudkeeper provides an MQTT bridge that integrates with existing IoT infrastructure and allows attribute updates via an industry standard protocol.

Because of this abstraction via the primitives and our declarative query language - the Pis and valves are each just one more infrastructure component that users can discover, query and build workflows for. As the Valves get replaced over time, their spec and even their brand may change. All the plant operator needs to do is write a new plug-in for a new spec / brand, and collect the same primitives. That means existing queries, workflows and automation for the entire plant will keep working.

We also collect metadata from popular SaaS / software tools, e.g. for identity (Okta, OneLogin), source code management (GitLab, GitHub) or ERP (Netsuite, SAP). These tools are now sources, not just destinations / integrations where we export to.

That way - Cloudkeeper is one powerful abstraction layer across the entire digital infrastructure - cloud, hybrid, IoT, SaaS, software. We collect their attributes and do not care what those are - we store them in the graph, document dependencies, make them searchable, aggregatable, and then actionable by triggering alerts and workflows on events for those metrics.

* We’ve launched a no-code UI/UX for non-technical users. They can explore a company’s digital infrastructure and build workflows in a browser.

* Running infrastructure is a collaborative effort. We’ve built functionality so users can share and discover workflow templates that other people have built. This raises overall productivity.

* The productivity benefits of Cloudkeeper are so high and so useful that Cloudkeeper is among the first three tools any engineer uses for a cloud project:
  * GitHub to maintain versions of their infrastructure config as code
  * Terraform to deploy infrastructure
  * Cloudkeeper to maintain infrastructure.

* Because we’re open source, anyone can contribute and build plugins for company- and industry-specific digital infrastructure.

* Customers share their basic graph structure with us. We can train a model with that data set, infer typical ways of architecting cloud native services and help customers detect anomalies in their infrastructure.

* Once a day we collect the latest pricing and open benchmarking data for all cloud providers, and share that part of our graph with everyone else.
Our users have started to adopt Cloudkeeper as their “source of truth” to document their digital infrastructure, instead of e.g. their existing CMDBs.

## 5-Year Vision: The platform for universal search and workflows for digital infrastructure.

Cloudkeeper is the established tool to collect metadata from millions and millions of resources. Keepercore is the underlying graph platform to store, annotate and navigate the resources.  

As our use cases have expanded, our users want to start offering the benefits of universal search and workflow for digital infrastructure to their customers. They embed Cloudkeeper and Keepercore into their own products.
In the example of the valves and the fertilizer plant, the plant operator retrofitted the valves by connecting them via Raspberry Pis and writing the plug-in.

Now, it’s the valve manufacturers themselves who standardize and expose attributes of their valves, write the Cloudkeeper plug-ins, and define standard workflow templates. A workflow template could be a maintenance alert and dispatch when the valve achieves a certain age or total lifetime throughput.

Instead of “just” selling valves, a manufacturer bundles valve, Raspberry Pi, Keepercore, plug-in and workflow templates into a subscription for a “digital valve” or a “valve cloud” that carries the manufacturer’s own brand. The valve manufacturer also maintains connectivity to all valves across its customer base, collecting the aggregate data set. Because Cloudkeeper is open, standardized and abstracted - the “valve cloud” is plug-and-play and integrates with a plant operators’ existing digital / cloud infrastructure. The valves and Raspberry Pis again become searchable, discoverable and programmable.

By turning a physical product into a programmable infrastructure resource, companies open up new types of business models and income streams, such as subscription revenue. There are benefits for all parties. With the subscription, the plant operator has the benefit of turning upfront Capex into an operating expense. As the maintainers of the project, Some Engineering contributes with certifications, training and support.

* We keep our customers’ entire digital infrastructure clean.

* We’ve launched a development platform, to build and publish custom-branded infrastructure workflow apps via the web and cloud marketplaces. These stores offer distribution and commercialization options for our customers and partners. We build the integrations to automate onboarding and listing for these marketplaces.

* Customers use Cloudkeeper to maintain their entire digital infrastructure - across cloud, edge, IoT, SaaS, data, software. We hear from customers how they are replacing their “rows and columns” CMDBs with a graph maintained in Keepercore.

* Our customers consider us like their Air Traffic Control, to supervise their infrastructure and act before something catastrophic happens, e.g. when a user starts a database that's not encrypted. 
