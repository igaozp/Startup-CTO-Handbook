## Team Makeup

The key difference in impact between junior and senior talent is the consistency with which they can reliably solve different kinds of problems. As engineers become more experienced, their judgment and decision-making improve on larger and larger surface areas. Similarly, you should expect that more senior talent will develop solutions that have fewer defects, last longer, and are more durable to requirements change along the way. That's not to say everyone has to be senior; in fact, it's rare that a majority of projects involve architecting brand-new greenfield solutions.

The right blend for any given team considers the types of work to be done and staffs the team thoughtfully as a result.

### Seniority Makeup

Your team should be more heavily weighted with senior engineering talent if your codebase is:
* Very new, requiring lots of architecture and foundational contract creation
* Is very old, poorly maintained, or poorly thought up and considered difficult to work in - in short, a brownfield codebase
* Is meaningfully changing in requirements, especially if new requirements do not look very much like old requirements
* Is using new tools, techniques, or patterns that require validation for your problem
* Requires establishing new patterns/ways of doing work, especially with ecosystems that don't provide tight guardrails that encourage healthy patterns.

### Technical Specialization


On Day 1 of most startups, the team will consist of a small handful of engineers, typically two or three. Having a team of three leaves limited opportunity for specialization. There are twenty categories of technical work to do and only three people, so by the pigeonhole principle, at least one person and more likely all three will be doing many types of technical work. Said another way, early on at your company, everyone is expected to wear many technical hats. As your company grows and you add more people to the team, you and your employees will find more opportunities for specialization.

So, you've raised a round of funding and you're looking to expand your team for the first time. How do you decide whether you need frontend engineers, backend engineers, DevOps engineers, etc.? Here are some general guidelines:

**Listen to your team:** The people currently doing engineering are very likely to be vocal about where the biggest sources of inefficiency are, and where the most help is needed. Your job as a manager is to take in that perspective and extrapolate going forward. Is the team pointing out a problem that will disappear in two months, in which case hiring somebody wouldn't be appropriate? Or is the issue systemic in nature and likely to continue for the long haul?

**Look for factors that are hurting productivity:** If your team is mostly frontend engineers and you're struggling with backend reliability, then that should be a sign that you need backend or DevOps engineering help. This same principle applies to testing, developer experience, etc.

**Specialize with scale:** Until your team is north of a dozen people, chances are high that you're better off with a team of primarily generalists.

Here are some rough numbers for team composition based on startup experience:

* Team size 1 5
  * Your team is all generalists, specialized at most between frontend, backend, and mobile.

* Team size 5 15
  * Your team is specialized by product or general skill area such as backend, frontend architecture, frontend design, DevOps, and testing.
  * You'll likely want to start thinking about dedicated resources in testing and DevOps when you've grown to (or past) fifteen engineers.
* Team size 15 30
  * You should have real specialization by this point and be hiring only people with expertise in a subfield of software engineering.
  * At this point, any inefficiencies in how work gets done are likely to start getting very expensive across the team, so make sure you're investing either headcount or time in ensuring that developers are able to get work done, their tools work, and operational logistics are streamlined.

* Team size 30-plus
  * At this stage there are many methodologies for breaking out teams into smaller units to ensure work stays efficient. If you have multiple product lines, aligning team members with specific product lines is a fairly natural place to start organizing.
  * Many companies at this stage use a concept of pods, where a pod has a focus area and is made up of a diverse/cross-functional team capable of independently executing tasks in that area.

### Project Maintenance: The Two Crews Philosophy

If you are shipping end-user software, your engineering team has to strike a balance between doing new work and handling support tickets that come in from active customers. Left unchecked, the need to handle support tickets can become a major distraction to the team, hurting efficiency, draining morale, and burning out your best people. There are many right answers to solving this problem; the important thing is that you recognize its effect on your team and architect a solution to help them be productive and drive great customer outcomes.

Microsoft has published a great article on this topic titled Building productive teams (ctohb.com/teams) describing what they call the two crews model. The two crews model outlines a feature crew and a customer crew.

The feature crew focuses on the future, building new features. The customer crew focuses on the present, working on active customer issues, diagnosing bugs, and prioritizing site health.

Other names for customer crew might be a maintenance team, or a Tier 2 support team (where Tier 1 is your non-technical customer support staff).

Splitting maintenance work off into its own team has many benefits:

* It allows for a dedicated team to monitor the customer queue at all times, triaging and resolving anything important and urgent.

* It allows your feature team to remain 100 percent focused on the future, undistracted by customer support work.

* It allows for developing specialization within the customer crew, building tooling and expertise at handling issues, making issues less expensive to handle over time.

* It provides another career path for individual engineers, especially junior engineers, to learn and level up on your team.

The first question I get asked about the two crews approach is: how long does somebody stay in the customer crew? There are four approaches to determining customer crew tenure:

* Make the customer crew a permanent, distinct team or department.

  * You have published job descriptions for engineers focusing on support and debugging. Note that for many engineers, a job focused only on debugging may sound undesirable. To me, a job description that emphasizes data entry or accounting sounds very unpleasant, and yet there are many people who enjoy and even pursue those jobs.

  * Don't assume that just because you wouldn't do that job, there are not others who might be excited by the prospect. In particular, working on a customer crew exposes an engineer to a huge amount of code, often offers opportunities to talk to customers, and involves less product-driven deadline pressure all things that might appeal to the right candidate.

* Create an explicitly discussed career trajectory for engineers to start on the customer crew and, after a period of time (usually twelve-plus months), transfer to the feature crew.

* Engineers rotate between the crews on a regular basis. The Microsoft blog post referenced above recommends swapping some team members between the two crews every week.

* Define the customer crew as a temporary team. This can mean either that the customer crew itself doesn't exist full-time (perhaps for only one week per month), or that team members are constantly rotating between the customer and feature crews.

I recommend creating a dedicated, permanent customer crew only for teams or products where customer issues are costly enough for the team to warrant it. If you're in a high-support business, a dedicated customer crew can be a force multiplier for both engineering productivity and customer satisfaction.

### Team Organization

In general, you'll find technical organization charts organized in one of two ways: functional organization and product organization. A functional group is organized around the type of work team members do, such as frontend engineering, testing, or a particular internal service. Product groupings, sometimes called business units, are organized around a particular business-related/product focus, such as the enterprise core application team or the consumer mobile app team. How you choose to organize your team can have a significant impact on team collaboration, productivity, and morale. Product-organized teams, often called pods, are the right answer most of the time.

When you're designing an organization chart you should consider what you're optimizing for. For a startup, the primary goal of an organization chart is to ensure that different people who need to collaborate closely with one another are enabled and encouraged to do so by the organizational structure. The best way to achieve that is to have all the people who directly contribute to the feasibility and success of a product be organized together, to hold them accountable to a common set of goals, and to develop a shared sense of ownership over that product.

When your team is small, and you have just one product, the question of how to organize is moot it's one cross-functional team all working on the same product. By the time your team has grown to 12 or more people, you'll need to start being more deliberate about defining what a pod is, and finding a method that is easy to understand and grounded in your product reality, before breaking your team out into pods.

The advantages of pods are greater team cohesion, autonomy ownership, accountability, and overall execution velocity. This approach is not without tradeoffs, however. Having a long-lived group of engineers work on one product can create knowledge silos. As organizations scale, it's also more likely for a product team to make architectural decisions that might optimize locally and lead to duplicate work or inefficient use of compute resources. If you anticipate and plan for these issues arising, the pain they induce when well-managed will be far outweighed by the benefits of autonomous, high-performing pods.

### Managing Remote Teams

There are a sufficient number of successful 100 percent remote software engineering teams that it is incontrovertible that remote organizations can work. That's not to say all remote teams are successful, or that it's necessarily easy to build an entirely remote culture. I've spent nearly a decade managing remote teams. Below are some recommendations that should apply to most remote management scenarios.

#### Documentation

Being remote means that there's nobody sitting next to you to answer questions, but that doesn't mean the questions go away. Those questions still get asked, only now social context is lost and so perhaps the question goes unanswered for a while. Or, rather than holding questions until the other person takes a break, now they get asked immediately, prompting various kinds of notifications and distracting from focus work. Having a robust set of internal documentation with an effective search feature can speed up time-to-answer and reduce the number of one-on-one context switches that become barriers to getting work done.

#### Asynchronous Work

A great way to turn remote work into an asset rather than a liability is to lean into asynchronous working practices. A strong asynchronous culture reduces the burden of time zone mismatches and reduces the amount of time spent in remote meetings/dealing with remote context switches. (See Benefits of Overcommunication, page 20, for more on asynchronous communication and the value of asynchronous work.)

#### In-Person Meetups

As useful as they are, video calls are no substitute for sitting down and having a meal as a team. The bonds that are formed by in-person meetings tend to endure over a long period of time, so an investment in even infrequent in-person meetings can improve the quality of social relationships between team members for months. As a general rule, it's healthy for a team to meet in person once per quarter to maintain these relationships and minimize remote social frustration.

#### Time Zone Overlap

My overall recommendation is for teams that are working on the same project to have a minimum of four working hours of overlap. That leaves a sufficient window for any regularly scheduled meetings and an opportunity for ad-hoc conversation and questions.

#### Create Social Opportunities

In general, people's default mode with video calls is to multitask during the call and then get off the call as fast as possible. Once a work conversation is over, everyone hangs up. That isn't how people interact in person; for example, the meeting ends and then you talk about sports in the hallway when walking back to your desks. That bit of social time before/after meetings is a valuable way for people to build relationships and trust, and it won't happen unless the leadership and culture actively support it. A cheap and easy way to do that on a regular basis is to ask a lighthearted, round-the-room, ice- breaker style question on a regular basis, such as What's one bit of good news personally, and professionally, you can share?

You can support remote social building with remote happy hours, or virtual team dinners and social activities. Post-COVID-19, there are many online social facilitators who run remote events ranging from digital casino nights to virtual escape rooms.

#### Camera On

Depending on which article you read, 70 90 percent of communication is nonverbal. Using a webcam during a video call doesn't replace all of that 70 percent, but it is unquestionably an improvement over having no video at all. Since webcams are so cheap now, there's really no justification for not having that additional social communication bandwidth within your company. The common objection is that employees are worried that others may judge their appearance on camera. If that's a concern you are facing, I encourage you to walk through the business justification for wanting as high-quality communication as possible in a remote setting, and have a zero-tolerance policy for any employee who makes inappropriate remarks on another's appearance. It can also be helpful to create a space for people to do whatever they feel appropriate to get themselves ready, such as allowing/encouraging background blurs, and occasional video-off to deal with something in reality or to tidy up.

#### Recording Meetings

Recorded meetings provide a great way to allow employees to get up to speed on a topic without requiring a work stoppage for a calendared meeting. In general, you'll find that very few employees or candidates are opposed to the idea of recording video calls. Recordings are also a great way to expose more people to some content than is perhaps comfortable in the moment. For example, you may want a hiring team of four or five people to watch an interview with a candidate, but having five people in the room at the time may be intimidating. Making a recording of a 1:1 interview is an excellent way to ensure everyone has the opportunity to evaluate the candidate without creating an uncomfortable or unfair situation by overloading the interview meeting itself.

## Leadership Responsibilities

As an executive, your leadership responsibilities extend beyond the technical components of developing and growing an engineering team. You should be looking to help the company be successful as a whole, with a particular bent toward how technology contributes to that success. Doing that means keeping an eye on how technology is working with the rest of the company by facilitating healthy collaboration with other teams, both in-house and external, as well as putting into place good process and management practices surrounding technology and product development.

### Product and Design Teams

It's your responsibility as a technical leader to ensure that your engineering team is working efficiently with the product and design teams, even if those teams report to somebody else. When designing this process, as a general rule, throwing things over walls between groups isn't efficient. Good interaction between product, engineering, and design teams requires empathy and understanding. What does the other team do, what challenges do they face, and how can you and your team make their lives easier? Below I'll provide a little background on these other functions and some concrete suggestions on how to work together efficiently.

### Design Systems

Design teams would ideally like their work to be implemented faithfully, pixel-perfect, by the software engineering team. Absent any sort of structure or set of constraints, actually achieving pixel perfection is expensive or even impossible; however, a bit of shared understanding and a design system can make the task dramatically cheaper.

A design system is a set of standards for managing design at scale using reusable components and patterns. Large companies tend to create their own design systems. Atlassian, for example, makes theirs available publicly (ctohb.com/design). As a small startup, innovating on design systems is likely not key to your success, so it follows that you should use an off-the-shelf design system. Nowadays you can choose from a plethora of off-the-shelf systems with rich feature sets and a variety of aesthetic styles that, more likely than not, can be customized to match your brand.

Not only do design systems provide a time-saving set of guardrails and components used by designers, they often come with out-of-the-box support for various frontend languages and frameworks. Material Design, for example, has a published design system in Figma (ctohb.com/figma), as well as a set of JavaScript react components (mui.com) and angular components (material.angular.io).

By adopting a system like Material (or AntD, Chakra UI, Blueprint, Bootstrap, Semantic UI, etc.) you not only get a suite of prebuilt technical components but you also get a system that integrates neatly with designer tools. By integrating the same system with the tools of both engineers and designers, you'll ensure that what your designers create will map cleanly to the components available to engineers. This cuts down or even eliminates the need for engineering to do custom styling or frontend UI, and makes it easy to match a design down to the pixel.

Beyond the efficiency gained by having consistency between design and engineering, most design system component implementations also take into account or automatically solve for other design priorities, such as accessibility (both for screen readers and color contrast management for the colorblind), adherence to UI standards, and even out-of-the-box dark mode support.

### PRDs and Specs

A Product Requirements Document (PRD), sometimes also called a product specification, or just a spec, is an essential part of the product development process. Note that a product spec has a different purpose and is a distinct document from a technical spec (see Technical Planning and Specifications, page 164). There are many methodologies and templates for PRDs. Sources like lennysnewsletter.com regularly catalog some of the most common and thorough ones. PRDs have a shared purpose, which is to describe the problem background as well as the why that justifies a project or feature. PRDs often include lists of requirements that need to be met to meet a business objective. Most PRDs leave the how of a feature to a technical spec.

A PRD, like a technical spec, is a living document. As your team learns more about the problem, or as factors in the outside world change, these documents can and should change and be updated to match. I encourage you and your team to use these documents as a continually updated source of truth to document your considerations and ultimate decisions made during the product development process.

### EPD

EPD is an industry acronym for Engineering Product and Design. The implication is that all three departments are essential to the product development lifecycle and need a healthy way of working together to produce great results. From the business's perspective, all three departments together are responsible for producing a product the customers love, so it's helpful to have a single person with a single set of business goals setting the direction for all three units.

### Product vs. Project Management

Product and project management are industry terms with distinct meanings. A product manager is accountable for the design and creation of the product as well as the key performance indicators (KPIs) the product should meet for the business. Melissa Perri's *Escaping the Build Trap* is a phenomenal resource that dives deeply into the role and impact a great product manager can have on your organization. A project manager is accountable for guiding the internal organization of the team, managing internal communication, and adhering to the roadmap and deadlines.

Early on in your startup, as CTO you may be filling both of these roles. Very early in your hiring roadmap you should plan to have a great product manager who can take some of these responsibilities from you. Some product managers excel at project management, while others don't find joy in it and therefore don't put time and attention into it. Arguably, early on at your startup, it's okay either way; with a small team, the consequences of lax project management are minimal. However, as you get larger, formalizing project management becomes more important, and if your product manager isn't filling the role, you should aim to augment them with a project manager.

My general recommendation is to formally delegate project management when EPD has grown to around twenty people. That will mean formally assigning yourself that role, having the product manager do it, or hiring a dedicated project manager. you'll want to be involved early on in setting up project management processes, ensure that the mechanisms being put in place for project management support the kind of culture you're looking to build, and are empathetic to all parties involved.

### Managing Managers and Manager Training

There's an industry expression that your company is ultimately run by your middle managers. The implication is that, despite whatever strategies and processes executives put in place, it's the middle managers who ultimately have the highest impact on the quantity and quality of output. Middle managers hire individual contributors, set their day-to-day objectives, and hold them accountable for quality standards. The best middle managers are mini executives, focused on culture, building collaborative teams, and working to enable them to do their best work. It follows then that, as an executive, you should put a lot of effort into hiring, managing, and training those middle managers.

The complicated topic of training managers deserves an entire book on its own, and it's a skill that takes time to master. That said, the top two lessons I can offer you that will provide leverage to all other skills here is to set an example yourself and build a culture of continuous management learning. The minute you hire or promote somebody into management you should make it clear that your expectation is that they will commit to putting time and effort into refining their craft of management. you'll go out of your way to make that easy for them by including management training in their personal goals and development plan, providing them resources to level up on management skills, helping them work through management problems, and teaching them everything you know.

Management training doesn't have to be over-the-top burdensome and expensive. If budgets permit, I highly recommend hiring outside management coaches for your managers. An internal manager monthly book reading/review can also be effective at kickstarting the continuous development flywheel.

### Finances and Budgeting

Part of your role is likely shouldering accountability for the present and future cost of the software engineering department (and sometimes design and product departments). As a responsible steward of that budget, you should know how much was spent on various items in the past, and how much your company as a whole has allocated in the future. Most importantly, you'll need a plan to justify spending that allocation wisely.

In general, you'll find the two largest line items in a technical department are people (payroll) and infrastructure/SaaS. Keep in mind that the actual cash cost of an employee is higher than just their salary, as it will include benefits and payroll taxes. A good rule of thumb is that the cash cost of an employee is 20 percent above their salary; this percentage is referred to as the burden rate.

### The Budget

Most finance teams use sophisticated accounting and budgeting software to manage the company's books. If not, they'll have a company-wide spreadsheet that's far larger and more complex than you need as CTO. In my experience, finance departments are not usually willing to let people outside of finance make changes to the core budgeting system, so unless they give you something to start with, it's on you to make a financial model for your department.

Given that your department's costs are fairly predictable, and centralized in a few line items, the model you make doesn't have to be very sophisticated. My recommendation is that you maintain a spreadsheet that includes the following:

* Payroll tab
* SaaS/Costs of Goods Sold (CoGS) tab
* Infrastructure tab
* Other tab (including travel, hardware) Summary tab

You can find a sample technical department budget spreadsheet on (ctohb.com/templates)[https://ctohb.com/templates] that will get you most of the way there on the actual modeling.

### Working with your CFO

If your company is like most startups, you'll be the most expensive department, and your CFO should be well aware of that. Some things to consider that are helpful for you and will make your CFO your best friend:

* Help your CFO know how money is and will be spent. Avoid surprises wherever possible. Provide guidance for things like hardware cost, travel/conference cost, and cloud cost upfront.
* Maintain a budget for your department and keep it up to date with changes in your forecast.
* Update your budget regularly with actuals from the finance department and ensure the delta between forecast and actual is understood and managed.
* Establish a plan for hiring and include estimated salaries.
* SaaS bills are often a burden to track. Consider either using a credit card statement analysis tool (i.e., a SaaS Management Platform, aka SMP) or hiring an assistant to regularly categorize and reconcile these expenses with your budget.
* Finance departments often care a lot about cost attribution to differentiate; for example, costs that are part of Costs of Goods Sold (COGS). Indicating in your budget a very coarse-grained why for each line item can win you friends in finance.

### Measuring Engineering Velocity/Health

I have yet to encounter a technical team or leader who has managed to consistently and usefully quantify actual engineering output. This includes measuring velocity as the sum of estimates of completed tasks. (See the Estimates section of Workflow, page 160, for a discussion on the unreliability of technical estimates.)

I have, however, seen many companies effectively measure engineering health and contributing factors to engineering velocity namely, cycle time and work time allocation.

#### Cycle Time

Cycle time is a measurement of how long it takes to go from idea to shipped feature, and is often broken down into these sub-milestones:

* Time spent coding
* Time to start a code review Time until code is approved Time to deployed code

In general, low-cycle teams are more efficient and able to iterate, innovate, and deliver value to customers faster. There are many tools that facilitate measuring cycle time, including LinearB (linearb.io) and Code Climate (codeclimate.com). LinearB has published a set of benchmarks, using data from thousands of engineering teams, on metrics associated with cycle time.

#### Work Time Allocation

The idea of measuring work time allocation is that, while measuring how much work is done is difficult, it's comparatively easy to measure what types of work team members are spending their time on. This resulting information is directionally useful. For example, if a team is spending the majority of its time addressing bugs, then it's a good hypothesis that improving software quality and bringing down that time percentage will result in more time allocated to developing new features, and thus an overall improvement in health and velocity.

Actually measuring work time allocation can be done in a semi-automated way by pulling reports from ticket systems, or it can be measured with regular lightweight pulse surveys to the team.

### Fundraising and Due Diligence

Generally speaking, as CTO, your role in fundraising and due diligence is fairly minimal. At most startups, the CEO and perhaps the CFO do the lion's share of that work. Your involvement likely comes toward the end of the process as investors do due diligence on the company. Many (though sadly not all) of the requests made in due diligence are for information that a well-organized engineering team already maintains as part of doing business. Keep an eye on on the following, and be ready to produce for due diligence:

* Organization chart
* Department budget
* Full description of all products engineering has created and maintains
* Engineering roadmaps (usually they're looking for short/medium-term roadmaps)
* A list of major areas of tech debt, what I've labeled a tech debt balance sheet (see Tech Debt, page 145)
* High-level system architecture diagrams
* Full description of how software is distributed and updated, either as SaaS or as versioned desktop/mobile software packages
* A high-level description of systems, how they're hosted, and your security practices
* Information about software licensing, including code scans of company code confirming no license violations or unlicensed proprietary software are present

It's not uncommon for an investor to hire a third-party firm to conduct a technical diligence audit. These audits may involve interviews or meetings with you and perhaps a few other senior members of the team. Be prepared to discuss your engineering process, assess the general productivity of the team, and do a code walkthrough of parts of your system.

My advice is to be candid with these auditors. They've looked at a lot of tech companies and are well aware that all engineering teams have debt and parts of the system that teams are more proud of than others. The more your investors know about your strengths and weaknesses, the better they can support and hold your team accountable for improving the weaknesses going forward.

### Vendor Management

In general, the responsibility for sourcing, negotiating with, and managing third-party technical vendors will fall to you as the CTO. For most, this is an unenjoyable but necessary part of the job, and consequently, it doesn't get much thought. Performing this responsibility well, however, can provide significant cost savings for a business. Here, I'll walk you step by step through a typical SaaS negotiation/signing process and provide some tips for how to add efficiency and save cost.

#### Self-Service Signup Tools

Typically, either you or a member of your engineering team will highlight a need for a type of tool, and if it's one of your engineers or managers they'll ask either for you to approve the expenditure or for you to sign up for the tool. Many tools are inconsequential in cost and have trivial self-service signup flows. I recommend you work with your budget and finance team and set a threshold below which your managers are authorized to simply sign up for the tool independently. For tools that are above the cost threshold or don't have self-service signup, you'll need to enter into a discovery and negotiation process with an enterprise vendor, which typically has four steps.

#### Enterprise Tooling

You're now facing an enterprise sales process. Before reaching out to the vendor's sales team, be sure that this particular company is the one best suited to solve your problem. In most instances, I recommend starting a spreadsheet, doing some diligence on all the vendors in the space, and filtering down to a top two or three. Even if one of them is by far your preferred choice, it doesn't hurt to have some deeper context on the space and for negotiating knowledge/leverage/BATNA (best alternative to a negotiated agreement).

##### Sales Qualification

When you first reach out to an enterprise vendor you'll almost certainly enter what is called a sales qualification process. At this step, especially as a technical executive, your needs are not yet aligned with the vendor. You're probably looking for pricing, a contract, and the shortest path to getting started. The vendor is looking to make sure you're their target customer and are likely to sign up and not churn for at least a few years.

Most SaaS sales companies will have frontline sales representatives take the initial phone call, and their primary objective is to learn about your company and see if you fit their profile. They might not have much technical knowledge and often they won't be able to discuss pricing with you. As a result, you're not likely to get much value from this first meeting. My advice is to either delegate these intro meetings or try and get the sales qualification questions from the rep via email and answer them sufficiently to skip the intro meeting altogether.

##### Negotiation

Once the vendor has validated that you fit the mold of their target customer, they'll schedule a second meeting with more senior resources on their side. Typically, this would be a sales manager or perhaps a technical sales representative. This is the stage at which you'll start to get answers to more of the technical questions you have about the solution, and you'll get some transparency into the pricing models the vendor is authorized to use.

Here are some general negotiating tips:

* Keep in mind that, at the end of the day, a salesperson's job is to sell you the product, so you're on the same team when it comes to landing on terms that are mutually agreeable. The more transparent you can be about what matters to you, the better they'll be able to craft a sales agreement that meets those needs.

* Don't undervalue factors other than total cost, such as total contract length (longer contracts should come with steep discounts), payment frequency, payment terms (e.g., net 30, net 90), or what happens to contracts in the event of a change in control of either company.

* In general, look for contracts that grow as you grow. Ideally, the initial cost is low and grows over time as the tool is used more heavily and provides more value. Encouraging a we grow together mindset can help reduce those initial costs.
* Keep your finance and compliance teams in the loop. If your CFO is great at negotiating, let them handle this part of the process.

* If your total SaaS budgets are large or you're negotiating a lot of these deals, consider using a third-party negotiator, such as Vendr. Often these negotiators will charge based on how much they save you, and they have data from many more contracts than you do to understand pricing.

* Be aware that end-of-month/quarter quotas are real and discounts around that time are very common.

##### Signing

Once you've agreed on terms and exchanged paperwork, the next step is to find out who the authorized signers are for your company (assuming you're one of them), get the documentation signed, and keep it organized.

Do not lose or misplace these contracts as they'll be useful for future negotiations or due diligence. Ensure you're tracking the costs in your budgets or with your SaaS management platform (SMP).

##### Post-Sales

After the deal is signed you will likely be handed off to a different representative at your vendor, someone whose title is similar to either post-sales support or customer service manager (CSM). These individuals are incentivized by, measured by, and focused on customer retention or product upsells. They're knowledgeable about the product, and at least somewhat technical. Going forward, they'll serve as your advocate for new features and getting defects resolved.

## Which Type of Startup CTO Are You?

Whether you're the CTO, a CEO playing the role of CTO, or a founder hoping to hire a CTO, it's helpful to have a clear understanding of what exactly it is a CTO does in a startup, and how that role differs from executive and leadership roles in more established companies. As with most things, the answer depends on context and will change over time. Calvin French-Owen has

a great article (ctohb.com/founder2cto) breaking down the CTO into four archetypes: People Leader, Architect, R&D, and Marketing/Consumer- facing. I like this breakdown and will refine it a bit here to three types:

* Tech-Focused

* People-Focused

* Externally Focused

### The Tech-Focused CTO *AKA The Chief Architect*

The tech-focused CTO may also be the office of the CTO, leading an internal technical skunkworks whose primary output is forward-thinking strategy, architecture, and sometimes proof-of-concept implementation on how to help the business down the road. This CTO will have fewer reports, with the bulk of the engineering organization reporting to a separate vice president of engineering. In this case, it's not uncommon for the vice president of engineering (VPE) to report to somebody other than the CTO most commonly, directly to a CEO or to a chief product officer (CPO).

The internal tech-focused CTO may also be the chief technical process architect, setting up tools, systems, and processes for how technical work gets done.

As an internal tech-focused CTO, you may also function as a product manager if your company's product is highly technical in nature (i.e., developer tools, API-as-a-service, etc.)

### The People-Focused CTO *AKA the VP of Engineering (VPE)*

A typical startup will not have both a VPE and a CTO, and so it often falls on the CTO to fill the VPE role. This is often also the hardest role for a cofounder CTO to fill, as the responsibilities of the day one technical cofounder don't much overlap with the responsibilities of the internally people-focused technical leader.

The people-focused CTO is responsible for setting internal technical culture, the hiring process, and overseeing internal processes. This CTO spends much of their time actually managing either independent contributors or other technical managers. This is the most critical of the three focus areas to get right. If a company isn't hiring well, or its technical staff is poorly managed, unmotivated, unfocused, or not aligned, it can impact productivity, and even lead to bad decision-making that will hurt the organization in the long term.

### The Externally Focused CTO *AKA The Head of Technical Sales/Marketing*

This is likely the least common focus for a startup CTO, but no less critical at the right time or place. Most often, you see this CTO at companies that build products for a technical audience developer tools, for example. These CTOs spend lots of time writing blog articles or speaking at conferences. Perhaps they are brought into sales meetings to act as an executive technical representative to close large deals. Note that building a brand around the technical team not only has a positive effect on product sales, but also can be a great recruiting tool and can reduce your time and cost of hires.

This is perhaps the easiest role for the founder CTO to step into, as they have the historical context for the company and can most genuinely and passionately tell the company story and evangelize its product and value.

#### Transitioning Between Types

Ideally, a startup CTO will prove adept in all three areas, though most people will specialize in just one or two. If your business needs a focus that isn't your expertise, it may be worth asking yourself if you can execute that task more effectively by delegating it to a coworker. Especially at an early stage startup, most technical cofounder/cofounder CTOs will be internal tech-focused. Usually There's not much other work to be done at this stage!

It's a very common pattern for that person to find themselves stretching into internal people or external focuses as the company grows, and that's not always a desirable transition for that person. It's not a personal failure to admit that your specialty or your motivation is in tech and that people management isn't a great fit, but quite the opposite. Identifying your superpowers and architecting a role in the company to leverage that superpower is how you add the most value, and the company should hire somebody else whose superpower is, for example, people management to fill that role.

If you find yourself stuck in a role you're unhappy with, it's vital that you acknowledge the mismatch both to yourself and to your CEO. This doesn't mean giving up your position as a founder or leader, or as a respected and high-impact person within the company.

Some thoughts on various transitions:

* Your Superpower: Internal Tech
  * Company Needs
    * Internal People: Hire a people-focused VP of Engineering, proactively characterizing the role of CTO as technical.

    * External Focus: If you don't already have somebody in-house who is doing this better than you, then hire a developer evangelist and empower them to fulfill the role. Otherwise, promote from within and ensure it's clear what the role entails.

* Your Superpower: Internal People
  * Company Needs

    * Internal Tech: If you have a senior engineer or architect on the team whom you can empower/elevate to a position of technical leadership, that's worth considering. Otherwise, a technical architect should be near the top of your hiring priorities.

    * External Focus: If you don't already have somebody in-house who is doing this better than you, then hire a developer evangelist and empower them to fulfill the role. Otherwise, promote from within and ensure it's clear what the role entails.

* Your Superpower: External Focus
  * Company Needs
    * Internal Tech: If you have a senior engineer or architect on the team who you can empower/elevate to a position of technical leadership, that's worth considering. Otherwise, a technical architect should be near the top of your hiring priorities.
    * Internal People: Hire a people-focused VP of Engineering.

In many cases, the end outcome may mean hiring a CTO whose superpower is better aligned with what the company needs at the time. In other cases, it might mean hiring a very capable people-focused VP of Engineering to complement a highly technical CTO.

# Technical Team Management

Your output as a technical leader is measured by the output of your team, so

it falls on you to ensure the team as a whole is running well. What running well means will vary by team and circumstance, but there are general patterns and trends that correlate with high performance. In this section, my goal is to provide guidance on situations common to all tech leaders.

## Tech Culture and General Philosophy

I encourage all leaders to adopt the general leadership style known as *servant leadership*. As a servant leader your main focus is on serving the needs of your team. This means focusing on empowering others, building

a culture of transparency, communication, collaboration, and growth. As you think about your team and culture, and about decisions on a day-to- day basis, ask yourself which option enables the team to do their best work and thus deliver the most for the business.


### Ten Pillars of Tech Culture

*1. Spend Team Time on Things That Matter to the Business*

In general, you want your team to be spending time on things that move the needle for the business, and it's your responsibility as technical leader to create an environment where your engineers can focus their efforts in this way with consistency and minimal distractions. This frame may seem obvious, but when used properly, it's a powerful tool for decision-making.

For example, say your team is debating between using an off-the-shelf framework for the backend vs. writing something from scratch. There's a nuanced list of pros and cons one could make that would discuss things like added flexibility from building from scratch vs. shorter time to first deployment with the framework. In this hypothetical reality, what your business really needs is to iterate on the frontend and optimize the customer journey, so every moment spent on the backend is one moment less spent moving the frontend forward. If the out-of-the-box solution is good enough to power that frontend iteration, even if you have to throw away the framework and rewrite the backend in eighteen months with a custom solution, iterating quickly on the frontend now and finding product market fit earns your business the right to do that rewrite down the line.

*2. Use Reliable Tools Where You Can and Innovate Where it Counts*

Also referred to as don't reinvent the wheel, and standing on the shoulders of giants, the idea here is to use off-the-shelf components (libraries, cloud services, applications, packages) whenever possible. There's an inherent tradeoff for using off-the-shelf components between ease of getting started and customizing a solution to match your exact problem. I contend that in most circumstances where a pre-existing implementation already exists, the tradeoff leans heavily towards using the off-the-shelf service, library, or application.

In the rare circumstance where you will ultimately need to rewrite or heavily customize the dependency, the experience you had with the off-the-shelf tool will be very valuable in influencing and speeding up the design of the custom build.

*3. Automation Unlocks Velocity*

Your goal as the architect of your team is to ensure that your team spends as much of its time working on code that produces value for the business as possible. There are a number of time-consuming tasks developers do on a regular basis that are necessary to writing code but don't themselves add business value (e.g., replicating production environments, getting code to run locally, figuring out how to run test suites, provisioning feature branch environments in the cloud, tracking down bugs that are not covered by tests, etc.).

These types of tasks impose a constant tax on overall productivity. You can avoid paying the tax by making an investment in automating these tasks whenever they are identified. Encourage your team to document whenever they are spending more than thirty minutes on nonproductive technical work and provide a space in your process for automating those tasks so nobody loses that hour ever again.

*4. Frequency Reduces Difficulty*

Under the heading of Frequency Reduces Difficulty, Martin Fowler expounds on the phrase, If it hurts, do it more often (ctohb.com/fowler). Any process or task that is painful, error-prone, or otherwise costly for your team, Fowler contends, is a symptom of that task being underdeveloped. Without pressure from you, painful technical tasks tend to be the last ones volunteered for. As a result, they're neglected, and the pain gets worse over time. Alternatively, if your team culture emphasizes prioritizing these painful tasks, then more effort will go into automating, documenting, and improving those tasks, making them ultimately less painful or even entirely automated. As Fowler points out, doing tasks more frequently also provides more feedback on them and builds skill with practice, all of which further reduce the difficulty and pain of the task.

For many teams, releasing code to production is an example of a task that is often painful. Releasing code can require hours of time to actually deploy and so it's done infrequently. If, however, your team subscribes to the If it hurts, do it more often philosophy, then you as the technical leader will push for regular releases at faster intervals. If you start with a weekly release, then the first week the team will feel the pain, and the second week will be just as painful as the first, but perhaps the engineers will notice an opportunity to automate a piece of the deployment. By the third, fourth, or fifth release, you'll likely have an entirely new set of scripts and infrastructure to get code out the door, enabling you to accelerate the release frequency to twice a week. After a while, you'll be able to get code out the door with the push of a button. Releasing more than once per day is referred to as Continuous Deployment (see Continuous Deployment, page 216).

*5. Standardize The RFC Process*

An RFC, or Request for Comment, is a document that outlines a technical idea, process, or specification and is written for the purpose of peer review and subsequent adoption. Most protocols you're familiar with have an associated RFC, such as RFC 2616 for HTTP, or RFC 1035 for DNS. The idea of peer review and subsequent adoption and standardization is a powerful tool for pseudo-democratically making technical decisions and getting buy-in on the results, and it can be a great tool to use with your team.

I recommend that you formalize an RFC process and provide some guidance as to what kinds of decisions should be put through the RFC process.

A formal process can look like a simple checklist and a template document that includes where to put your copy of that document, how feedback/comments are collected, and what the process for voting, finalizing, and standardizing what the document looks like.

My suggestion is to lean into the tools you have and, for example, create a markdown document in source control that acts as the RFC template. A new RFC would then be a pull request on that repository introducing a new markdown file with the proposal. It is then somewhat natural to collect votes as approvals on that pull request, and finalization of the RFC is when the pull request is ultimately merged. Alternatively, if you've set up an internal wiki, you can create an RFC there, and use a wiki's comment system to collect feedback.

You should also set clear expectations for what kinds of decisions get put to RFC. I recommend limiting it to high-level processes, technical opinions, and culture, and not using it for tool choice or system architecture. Some good examples of topics to RFC:

* Standardizing naming conventions (master vs. main, black/whitelist vs. allow/denylist, camelCase vs snake\_case in various contexts)
* Usage of code formatters/static code analysis Meeting cadences/agenda/artifacts
* Monorepo vs. manyrepo
* API Design opinions/philosophies

I encourage you to include a section in your RFC template on how the results of an RFC are institutionalized. For example, if the RFC proposes standardizing a technical opinion for your team, once the RFC is ratified, that opinion should be incorporated into your engineering guidebook and onboarding documentation, so it becomes canon for current and future employees as well.

*6. Make Speed a Goal, Not a Strategy*

In *Good Strategy/Bad Strategy,* author Richard Rumelt defines a good strategy as one that provides three elements: a diagnosis of how to overcome a challenge, a guiding policy or an overall approach, and a set of actions for how the policy is to be carried out. Strategy outlines the journey.

In contrast, a goal is a description of a destination. I've heard countless teams tell me their strategy is to go fast, with no outline of how they get there. I'm entirely in agreement that engineering velocity and speed is a great goal, but it's not a strategy.

Here's a sample strategy for delivering high-velocity engineering:

**Challenge:** We re an unregulated, early stage startup that needs to iterate as fast as possible to find product market fit before we run out of capital.

**Diagnosis:** We have an opportunity to minimize complexity and move quickly. Since we don't yet have product market fit, the value of what we ve built so far is minimal, so we need to ignore sunk cost and opt for fast rewrites while we re still unsure what our product will look like long term.

**Action plan:** We will focus on hiring software engineering generalists, reinforce a culture of curiosity and scrappiness, leave ego at the door, and invest only a modest amount of effort into long-term technical planning. Instead, for now, we'll focus on our ability to ship MVP product experiments to the market.

*7. Participate In Continuous Education And Technology Conferences*

Technology conferences are ubiquitous nowadays, and There'sa gathering of like-minded individuals for nearly every subspeciality of software engineering. Your team, if they haven't already, will likely ask at some point for a budget to attend these conferences. A typical budget request would be for $1,000 for air and hotel, and $500 $1,000 for entry fees and per-diem expenses. All in all, it will cost on the order of $2,000 for an engineer to attend a conference, plus their time out of the office. Both in the spirit of learning and continuous improvement, as well as a host of ancillary benefits, I recommend that you budget for and regularly approve or systematically approve conference requests.

If the only benefit of attending a conference were that the employee learned a bit more about a relevant technical topic that they're passionate about, the cost would be worth it. There are, however, many more benefits.

I encourage you to require conference attendees to produce a written document summarizing key things they learned after they return. You should also consider sponsoring the conferences most relevant to your business and having you or one of your team members host a seminar on a particular topic. These seminars and sponsorships provide excellent branding opportunities for your company, getting your name and message in front of a very targeted audience an audience that likely contains candidates you'd like to hire in the future.

In summary, allocating a budget for engineers to attend conferences is good for individual professional development, good for culture and morale, good for branding, can help with future hiring and with a bit of documentation, an opportunity for continuous education across the team.

*8. Deploy Rubber Duck Debugging*

Have you ever had the experience of trying to work through a problem and, while explaining it to a coworker, figured out the solution? Rubber Duck Debugging (ctohb.com/rdd, ctohb.com/tpp) is a simple practice that attempts to replicate this phenomenon without involving or context-switching a coworker.

Rubber Duck Debugging is the process of working through a problem by first speaking the problem out loud, perhaps at a real physical rubber duck that is sitting on your desk. The idea is that by speaking the problem out loud, often one will hear the flaw, or see a solution to the problem, that they hadn't considered when the problem was only in their head. The rubber duck approach potentially saves a coworker an interruption and gets you an answer faster.

*9. Build An Explainer Video Library*

If a picture is worth a thousand words, a one-minute video of your desktop/IDE/application with your voice discussing a technical topic is worth $1,000 in developer time savings. There are many tools that make it trivially easy to record and share these mini video messages, including tools built into Slack and Loom. Not only can you clearly convey a technical idea more easily with a screen recording and voiceover than text, but you can do it on your own time. The resulting video can be sped up at the viewer's discretion, and the video can be archived and rewatched later as part of an organizational knowledge base.

As the technical leader of your team, I encourage you to regularly make these mini video explainers, especially at times when you're making changes to the architecture of the platform. Organize all the videos in a library in your internal wiki. Make sure they're complete and standalone but short and to the point; if you don't get around to critical content until the end of an overlong video, your team members might never see it. Also, make the approach as consistent as possible so viewers know what to expect.

I guarantee you'll get relatively poor watch rates upfront as you make and distribute the videos, but over time that library will provide tremendous value as a source of reference knowledge and will get views that save you and your team meaningful amounts of time.

*10. Onboarding Is Everybody's Responsibility*

Your team is continuously creating tribal knowledge, be it how to start a service, or how code patterns are used across your codebase. There are two ways to deal with this: you can do nothing, and on a daily basis you'll increase the size of the knowledge gap for new employees, or you can actively work on converting siloed tribal knowledge into scalable documentation for current and future employees. For obvious reasons, I recommend the latter. This means everyone should always be asking themselves, How can I document what I've just created/learned/discovered? And when you have new employees who come across something that they can't find in your knowledge base, it's up to them to seek out an answer and document it.

