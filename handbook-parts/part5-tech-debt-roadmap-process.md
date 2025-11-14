## Tech Debt

San Francisco's Golden Gate Bridge is made out of steel, which is not actually golden in color. The bridge is painted, and maintaining the iconic color of the bridge is so important to San Franciscans that they paint it continuously (ctohb.com/painting). Once repainting is finished, the process immediately restarts. This form of continuous investment or perpetual maintenance is what's required to keep the most important and sophisticated systems performing to expectations, from the Golden Gate Bridge to your team's software project. Only for your project, the maintenance doesn't require paint buckets; it comes in the form of technical debt.

Every feature a software development team delivers brings with it some level of need for future work, or debt. That debt can take the form of bugs that need fixing, fast-follows to the feature to deliver incremental customer value, or sloppiness in the code that should be fixed to improve maintainability, performance, or security. A certain amount of debt naturally accrues even if your team is out on vacation: security vulnerabilities in dependent software are found, packages go out of date, new versions of tools are released, third-party APIs are deprecated or changed, etc. Debt is unavoidable and you need to account for it.

### Tech Debt And The Product Lifecycle

Another way to think of tech debt is like financial debt, such as a mortgage on a house. When you take out a mortgage to buy a house, you're making a deliberate decision to take on debt, knowing the consequences (interest), to enable you to do something you want now (get a house). Then you pay down that debt on a consistent basis over an extended period of time (monthly payments).

The same happens with technology debt. Your startup may accumulate it deliberately as part of a conscious tradeoff, and part of that tradeoff is establishing a realistic plan for paying it down. You should apply the same kind of logic you would to pay down financial debt to addressing your technical debt: either pay it off upfront because you have extra resources (and no better place to put those resources), pay it off continuously over time, or pay it all off down the road but perhaps at a higher total price that includes interest.

However you choose to pay down your tech debt, the key to doing so successfully is to recognize that debt is an inevitable part of the software engineering process, and proactively paying down debt is a necessary investment in overall engineering health.

#### Defining Tech Debt

Another way to define technical debt is as a technical decision, implementation, or nuance that actively reduces the efficiency or effectiveness of the business today or in the future. The point is that tech debt has a consequence that matters. Some of your code might be objectively ugly or inefficient, but if that inefficiency has no impact on the business and There's no need to modify that code in the future to maintain quality, performance, or iteration, then that code isn't costly in terms of tech debt. After all, the goal of software development, especially at a startup, is not to write the perfect codebase, but to build software that enables the business.

Don't be afraid of debt. It can serve a purpose. For example, when building Version 1 of a product that's not yet been validated in the market, a technical team may decide on an architecture that will not scale past a hundred users. If that decision allows the team to rapidly validate the product and determine whether or not a hundred users will ever use the product, that path may be worthwhile especially given the fact that it may take several versions of these prototypes to find one that users love.

There are at least seven types of technical debt:

1. **Architecture** or **Design Debt** arises when the design of the software is not capable of meeting the near-term or future needs of the business. For example, the design makes it too challenging to build the features the business needs, or the design won't scale to the number of users or performance requirements of the business.
1. **Code Debt** accrues when the implementation itself was done without paying attention to best practices, yielding code that's difficult to understand and maintain.
1. **Test Debt** accumulates when you've run insufficient automated tests to provide the team confidence in the correctness of the codebase.
1. **Infrastructure Debt** occurs when the infrastructure, observability, and supporting systems are not robust or have been poorly maintained, leading to difficulty scaling or deploying updates, or poor uptime and reliability.
1. **Documentation Debt** results when There's insufficient documentation, or the documentation is stale/inaccurate, which can make it difficult for team members to onboard a project.
1. **Skill Debt** rises when the team members lack the needed skills to maintain or update the code or surrounding infrastructure.
1. **Process Debt** accrues when the team is inconsistent in how it solves problems, leading to mistakes, delays, or increased costs.

#### Tech Debt Bankruptcy

If your startup neglects or ignores tech debt for long enough, it can become a major impediment to future progress. Teams can unintentionally find themselves spending 80 or even 100 percent of their time sorting through system problems or inefficiencies as a result of tech debt, a state known as tech debt bankruptcy.

Some signs your team may be tech debt-bankrupt:

* You are regularly dealing with production outages to the point of material business impact.
* You receive constant pushback or exaggerated timelines on new features due to the need to deal with debt.
* The team complains that a codebase is too complex to get work done.
* New features cannot be shipped without accidentally breaking old features or introducing an unacceptably high level of defects.

If you find yourself in tech debt bankruptcy, it's time to raise the alarm, reset expectations with stakeholders, devise a plan to consolidate the debt, and begin paying it down immediately.

If you've been honest with your peers in leadership (see Delivering Bad News, page 46), you should have the necessary credibility to explain the tech debt problem and develop a common understanding of the ROI for an investment in resolving tech debt.

#### Measuring Debt The Debt Inventory

Unlike with a mortgage or car loan, There's no website you can visit that will give you a statement of your exact amount of tech debt and remaining payments. Some forms of debt can be measured quantitatively, but most of the analysis is qualitative. For healthy and responsible debt management at scale, I recommend a debt inventory survey.

The survey should be taken at regular intervals. Somewhere from one to four times per year, do a sober analysis across the varying kinds of debt, producing an honest assessment of where the team is operating. Don't take the survey independently; rather, do so in collaboration with other engineers on the team who are working in the code every day and interacting with the debt on a regular basis.

A survey can be as simple as this: for each of the following types of debt, rate how much we have on a scale of 1 to 10, then provide a few sentences justifying the score.

Use the results of the survey to inform how your team spends its energy paying down debt, and compare results between surveys over time to ensure debt stays at a reasonable level and your team is regularly solving its biggest debt pain points.

#### Strategies For Paying Down Debt

In order to decide when to pay down tech debt, you should first consider how much of your team's time is worth spending on it. Key considerations include:

* How much debt exists, as indicated by your most recent debt inventory survey
* How much it is hindering your company's ability to run day to day i.e., via outages, customer churn, or defect rates
* How much it is hurting your team's ability to deliver on new projects How difficult it will be to pay down the debt

If you are not in tech debt bankruptcy and your goal is to maintain a healthy level of debt, I recommend allocating somewhere between 10 20 percent of your team's time to investments in non-feature engineering (e.g., paying down debt, exploring new patterns/proofs of concept, improving developer experience, etc.). The more severe your current debt impact, and the higher the effort to pay down the debt, the higher the percentage of your team's time you should allocate.

##### Just-In-Time Payment

The most common way to handle tech debt is to pay it off on a Just-in- Time basis, meaning the debt is paid off as part of a business-driven project. This will often look like a team adding tech debt tickets that relate to the stories that have been selected for a sprint in a planning meeting. This is a low-overhead and low-planning-effort approach, and it can work out well. But be mindful of some potential pitfalls:

* Just-in-time payments, by virtue of being less visible to the broader team, can lead to systemic underinvestment in tech debt. Make sure you are being honest and transparent with the team as you do just-in- time-payment about what total percentage of team time you're expecting to be in debt.

* Adding tech debt as part of a sprint can imply that investing in tech debt is a secondary objective to the sprint goals, and thus likely to get cut from scope if a team runs low on time.

* Tackling tech debt in a sprint may be perceived as slowing down the sprint or causing delays, rather than as an investment in velocity and overall system health.

##### Periodic Paydown

Periodic paydown is akin to how one might pay down a car loan or a mortgage. The team makes space to pay off debt on a fixed interval (e.g., a day per sprint, a couple of days per month, or a couple of weeks per quarter). Google famously allowed their engineers 20 percent time to work on whatever they wanted, including paying down debt or innovating on new projects and tools. The idea here is the same: as a manager, you explicitly make time and encourage the team to make investments into the tools and processes used to do engineering.

For example, the Shape Up method (see Tech Process, page 157) describes a two-week cooldown period after a six-week cycle, or 25 percent of an eight-week period, for making technical investments. Keep in mind that 25 percent isn't a magic number; the right percentage will depend on your team's debt inventory.

#### Continuous Paydown

Depending on how expensive debt is for your team, you may want to dedicate more resources to overall system quality than a periodic strategy allows. This looks like having a dedicated team what I call a customer crew in a two-crew scenario (see Project Maintenance: TheTwo Crews Philosophy, page 113) pay down tech debt as part of their everyday work and objectives.

It's important to ensure that any team whose primary objective is internal efficiency, such as a tech debt team or a customer crew, has clear and measurable goals for their work. For example, if your debt inventory ranks test debt as your highest debt category, then measure defect rates and code coverage and hold the customer crew accountable for improving those metrics. If your infrastructure debt is the largest, then focus on uptime and Mean Time to Recovery metrics.

### Communication of Tech Debt

Non-technical leaders don't expect perfection from their technical teams. But they do expect high performance and consistently met expectations.

When it comes to debt, that means clearly communicating your strategy for keeping debt at a manageable level, and also providing upfront and honest communication about when debt may get in the way of business goals, as well as your strategy for paying it down so it's no longer a blocker.

## Technology Roadmap

### Timeframes

I find it useful to think of a technology roadmap in three timeframes, sometimes labeled as short-, medium-, and long-term or horizon one, two, and three. Each timeframe should be managed by a different process and is often owned by different stakeholders.


#### Short-Term/Horizon One

Your short-term roadmap is what your team is working on now. This includes any in-flight features, actively worked-on defects, tech debt, or urgent work items. For more detail on managing your short-term roadmap, see Workflow in the Tech Process section, page 157.


#### Medium-Term/Horizon Two

If you're the only technical manager on the team, then you are responsible for both the medium- and long-term roadmaps. If you have directors or senior managers reporting to you, you'll likely be collaborating on the medium-term roadmap. The medium-term roadmap is a very useful artifact not only for your own planning and organization but also as a tool to communicate with other departments/stakeholders on what the engineering team is doing.

Typically, a medium-term roadmap is implemented as a spreadsheet where teams or individuals are rows, and columns are time periods often weeks or sprints and the contents of the table are high-level work items or work areas. The purpose of the roadmap is not to predict precisely when any given task will be completed; doing so would require accurate and precise estimates of work which is tenuous at best (even at a granularity of weeks) and never a guarantee. Instead, the idea is to outline an order of operations and set a direction for the team.

You can and should expect to update the actual duration of any given activity as engineering progresses. Updating the number of weeks on a given task is a great point in time to evaluate whether continued investment in a project makes sense, and also to update external stakeholders on current completion estimates. Finally, the roadmap is helpful as a retrospective tool for tracking how long major initiatives took, and also to assess where a team is investing time at a very high level.

#### Long-Term/Horizon Three

As the leader of your team, it falls on you to focus on the long-term health and productivity of the team. You should spend time designing these goals and producing a well-thought-out, clear document (or slide deck, video, wiki article, etc.) that explains the goals to the team. Once you've set initial goals, revisit them infrequently as changing strategic goals causes churn in an organization. Just as problematically, frequent changes in direction can be confusing and demotivating for the team. I encourage you to provide an update on progress towards long-term initiatives on a quarterly basis, both to the entire engineering team as well as to other executive leaders.

Some examples of long-term initiatives:

*Architectural tech debt*

- Moving from a deprecated framework to something actively maintained
- Migrating from one hosting environment to another (e.g., onboarding to Kubernetes)

*Language debt*

- Consolidating usage of programming languages
- Moving from older to newer versions of languages (Python 2 to 3, or .NET 4 to .NET 5+)

*Platform/architecture adoption*

- Having multiple teams adopt or migrate to new versions of internal services
- Moving to/from serverless environments
- Adopting new paradigms (e.g., server-side rendering, edge computing)

*Hiring plans*

- Growing or reorganizing teams
- Hiring specialists or building new technical departments

#### Timeline Communication

Every leader in sales, marketing, product, or support I've worked with has been appreciative of transparency in the technical process and technical roadmap. By contrast, I've spoken to leaders at some companies who describe their technical teams as a black hole. It goes without saying that you don't want to be called a black hole. Not being a black hole is simple; it looks like somewhere in your organization having a regular process to provide transparency to other leaders. Ideally, you're also helping other departments feel heard by having a forum, or a mechanism, to take input and incorporate that into the roadmap process. You can and should close the loop with other departments in your process by communicating back to stakeholders where their request is in the development process and manage expectations for when it will be completed.

## Tech Process

Conway's Law states that Organizations, who design systems, are constrained to produce designs which are copies of the communication structures of these organizations. Said another way, how you structure your teams, and importantly the process of work within and between those teams, will have a significant impact on the product you make. Teams working in information silos are unlikely to produce products that beautifully integrate with another team's designs, so it's up to you, as the overseer and ultimate architect of these communication structures, to ensure those structures meet the needs of the product you're developing.

### Workflow

Technical work is a highly nuanced matter with thousands of minute decisions that will affect how things ultimately interoperate and behave. To have any hope of maintaining productivity within your organization you need a set of standards and guiding principles to ensure the everyday technical decisions are broadly consistent and thus manageable for the team. That means you need to actually set those standards, train the team on them and have a day-to-day process to enforce and modify them as necessary.

The pattern a team follows to determine how to decide what to build and how work gets done is referred to as a workflow. The five most popular workflow patterns are:

* Agile
* SCRUM
* Kanban
* Waterfall
* Shape Up

There are entire books written on these patterns, and my favorite is *Scrum: The Art of Doing Twice the Work in Half the Time* by Jeff Sutherland.

There are some fundamental strengths and weaknesses of these approaches that I'll discuss in this chapter; however, in the real world, the differences between the processes are dwarfed by the impact of how well the manager implements the chosen process. Your job as tech leader is to pick a process and ensure it's implemented well and iterated on.

A good development process respects the following truisms about software development:

* Nobody can perfectly predict how long it will take to complete any given engineering task.
* Engineering is rarely a straight line; building feature X may require putting time into problem Y before X can be built.
* There is no such thing as a perfect specification; there are always gaps and things to be discovered along the way in building technology.

Generally, the goal of a workflow process is to ensure that a team is well organized and delivering at an acceptable pace. In a roundabout way, some workflow processes even attempt to quantify engineering team velocity, allowing for reporting on how velocity changes over time to non-technical stakeholders.

#### Waterfall

The oldest workflow process, dating back to the 1950s, is waterfall (see ctohb.com/waterfall). The waterfall model breaks down project activities into sequential steps, where each step is dependent on and starts after the prior step is completed. In software engineering that looks something like first having a product vision, then doing product concepting, then product design, then software development, and finally testing, deployment, and maintenance. The most common criticism of waterfall is that this structure is rigid, inflexible, and doesn't promote iterative development.

#### Agile/Scrum

Agile and SCRUM process is a more nuanced and prescriptive methodology than waterfall. There are many great resources that cover these nuances in detail, including Sutherland's *Scrum*, *Agile Estimating and Planning* by Mike Cohn, *e Art of Agile Development* by James Shore & Shane Warders.

The key thing to realize about these processes is that they are guidelines, not scripture. To get the best out of your engineering team, start with a process and see how well it works for your particular group of people with your particular type of technical challenges. Some teams have work that lends itself much more to estimation and story pointing, while others have much more ambiguous brownfield projects where estimation is near impossible. Pay attention to whether any particular ceremony from the process is really adding value to the engineering team, or if it's just a lengthy meeting everyone dreads.

Do not hesitate to skip ceremonies that are not obvious wins for the team. For example, I find SCRUM's prescription for planning poker to be inefficient for most teams.

#### Shape Up

Shape Up is a methodology formalized by the company Basecamp and published in an eBook available at basecamp.com/shapeup. The core cycle in Shape Up is six weeks long, a much longer sprint than espoused by SCRUM. This cycle uses fixed-time and variable scoping. The idea is that a longer time period provides more space to produce clear pitches (specifications) and do good work on a project. Shape Up places considerably less emphasis on estimation than other models which, as I'll soon discuss, is a good thing for engineering teams.

### Engineering Estimates

According to Google, the technical definition of accuracy is the degree to which the result of a measurement, calculation, or specification conforms to the correct value or a standard. That is to say, accuracy is an indicator of overall correctness. When you're throwing darts at a dartboard and aiming for the bullseye, an accurate set of throws is a set of throws that tends towards the center.

Precision, by contrast, is defined technically as refinement in a measurement, calculation, or specification, especially as represented by the number of digits given. In other words, precision indicates a level of exactness. When throwing darts, if all of your throws, regardless of their target, are tightly grouped together, that can be said to be a precise grouping.

As this description should help you visualize, something can be accurate without being precise (a broad grouping of darts around or near the bullseye but not hitting it), precise without being accurate (a tight grouping of darts that misses the bullseye), and, of course, both accurate and precise (a tight grouping of darts that does hit the bullseye).

You should expect and hold your team accountable for accurate but not necessarily precise estimates for completing software development tasks. If today is the first of the month, reasonable guidance from your team is, We'll ship the feature this month. If the team says, We'll ship the feature on the 23rd, they're more likely to miss that deadline.

There's no need to try to estimate hours or days per ticket if you plan your work/resource allocation out by week, month, or quarter. Pay attention over time to whether or not your estimates are actually giving you the planning capability you hope for. If they're not, don't punish the team by continuing the process, or worse, using it as a contributing factor in performance reviews. Instead, adjust the estimates so they help instead of hurting you. Change your expectations, and instead of reacting to missing estimates, react to the challenges the team is facing as they struggle to meet the estimates.

A final note on estimates: don't conflate missing estimates with poor total output/velocity. Some teams will be highly effective, have high output, and still miss estimates. Velocity is the more important metric, and a high output but imperfectly estimating team should not be punished. Conversely, a team that regularly misses estimates *and* has trouble delivering new value is underperforming and needs to change.

### Burndown Charts

SCRUM burndown charts show team progress against estimates and can be a great tool for measuring sprint productivity. However, estimates are imperfect and, for various reasons, a burndown chart may show a flat line or even burn up. This can be because a team legitimately is not making progress, or it could be an artifact of estimation issues or bad data collection.

A burndown chart that burns up consistently, despite teams shipping and doing good work, is demoralizing and not achieving the intended benefit. If there are easy adjustments that will help you better capture data and fix the chart, make that change. But if you find a particular way of measuring output still isn't working, just get rid of it. It's okay to admit that your method of estimating these particular types of stories with this team isn't precise enough and move on to other methods of monitoring and improving performance.

In my experience, only a small percentage of teams find success with burndown charts, so don't be disheartened if that one technique isn't helpful for your engineering team.

### Choosing A Workflow

I contend that which workflow you choose will not be a significant factor in the ultimate success and velocity of your engineering team. The key factor is that you are paying attention to your team's workflow and continuously iterating on the workflow itself to ensure your patterns are adding value and are a good match, both for your team and the types of problems your team faces.

That said, here is a rough model for thinking about which type of workflow is likely to be a better starting place: well-understood work (i.e., tasks that are concrete, greenfield, and easy to explain) is easier to manage and will generate more benefit with a more nuanced or prescriptive planning process. Said another way, if your work is ambiguous and hard to estimate, it's likely better managed with Kanban than SCRUM.

Well-understood stories that tend to work well with SCRUM are:

* Greenfield that is, new code that doesn't depend on perhaps legacy or difficult-to-work-with external modules
* Not dependent on new patterns/tools/technologies, relying instead on the existing (boring) tech stack
* Easily broken down from stories to smaller tasks Familiar to the team from previous work

Conversely, you're perhaps better with Kanban if your work is:

* Brownfield, or heavily impeded by tech debt with unclear paths for paydown/refactoring
* Regularly changing or saddled with unpredictable priorities
* Dependent on adopting new and different tools and patterns that can introduce unexpected costs in the first few implementations
* Assigned to a brand-new team that doesn't have a history working together or on these types of projects

### Cooldown/Innovation Sprints

When using a regular cadence like sprints, the major peril teams find themselves in is the expectation that a sprint will finish, features will be shipped, and the team can immediately shift to the next set of features. Due to the accumulation of debt and need to iterate on product features, that is simply not possible to sustain. There has to be either continuous or periodic time set aside to pay for debt.

A common practice for periodically paying down debt is the notion of a cooldown sprint. Sometimes called a tech debt sprint, or innovation sprint, the idea is the same: give the team time to clean up their digital workspace, do some code-housekeeping and ensure that they and the code are in a good place for high velocity work going forward. As discussed in Strategies for Paying Down Debt, page 150, it's reasonable to dedicate anywhere from 5 20 percent of your total development time on cooldown work.

If you're doing two-week sprints, that might mean that one in four or five sprints is dedicated to cooldown.

### Technical Planning And Specifications

When discussing the process for writing tech specs with engineers, I'm often asked, How do you have time to write specs? Usually I counter with, How do you have time *not* to write tech specs? Implied in my response is that taking time to think through what you're building before you build it is a net time saver.

Software engineering is inherently a creative process, meaning we re not doing the same thing every time and there is more than one way to do any particular story. A great planning process recognizes that there is value to be gained in thinking through a story in advance but balances that emphasis on pre-planning with the knowledge that the only real way to truly know everything about a feature is to actually build it.

A great tech planning process can accomplish several goals:

* Reduce the amount of rework in a feature
* Identify ways to do less work to achieve the same functionality
* Decrease the chance that important non-business visible considerations are forgotten, such as error handling/negative cases, testing, logging, monitoring, analytics, security, scalability, launch planning, and tech debt payoff
* Increase the chance that work from multiple people/teams is done in a compatible way
* Provide valuable documentation for how and why a feature was built a certain way for future maintenance, improvement, or expansion
* Keep the team thoughtful and aligned on irreversible/expensive technical considerations (e.g., tooling and architecture), as well as unlikely-to-forget key details
* Prove lightweight enough that it is completable in reasonable time and doesn't force decisions on minor details that either don't matter or don't have enough information upfront

#### Tech Spec Leads

I recommend that you designate a lead for any project that needs planning: a single person to be accountable for producing the technical specification and getting that specification through your approval workflow.

That doesn't mean they're the only contributor. On the contrary, if other team members are available during the planning window and have helpful knowledge, they can and should contribute.

Planning can be synchronous (i.e., everyone is in a room for the whole time period) or asynchronous. I recommend asynchronous planning as much of the work in planning will involve research (e.g., reading product documentation, reading code, prototyping/proof of concepting, evaluating tools and APIs, etc.) which can be done fine independently.

#### Time For Planning

Your tech planning process should save you time in your initial implementation. It should also save time in the future by minimizing tech debt and leaving behind documentation that can accelerate future improvements.

The wrong amount of time to put into planning doesn't meet these goals, either because it's too short and doesn't save you time/produce good documentation, or is so lengthy that it doesn't pay for itself in savings.

There is no universal formula for the correct amount of time, but I'll provide a rule of thumb: allocate one day to technical planning for every week of work you estimate the project to take. In general, this will lead to between half-day and three-day planning windows. If your project requires less than two days of work, it likely needs very minimal planning effort and has low risk. Conversely, if you're looking at a project that is expected to take more than three solid weeks of development effort, you may not be able to efficiently plan something that large all at once and should consider breaking it down.

If your team refuses to invest time into planning, you're likely pushing too hard for results over process. The way to ensure the engineering process produces good results for the business is not to crack the whip harder, but to establish a healthy process that enables good results. You wouldn't speed up a structural engineering team designing a bridge by having them work longer hours. You would make sure they have the best bridge-designing tools available to them with the best possible information about the span being bridged. Software engineering is no different. But instead of using CAD software or real-world measurements of soil/rock, we have product specifications, design process, and software tools.

Conversely, an overly lengthy planning process where team members insist on getting every minute detail upfront can be an indicator of a serious cultural problem, where team members are paralyzed by fear of making a mistake. Effective planning won't eliminate risk, but thinking through important, high-level decisions in advance can minimize it. A team that obsesses over details may be afraid of making mistakes or unwilling to iterate on their work both symptoms of overly results-driven management. Individuals should not be punished for reasonable mistakes or planning oversights. It's fine if a tech spec isn't perfect upfront; expect your team to find mistakes or gaps during implementation, and update the spec when those issues are found.

### Prototyping as Part of Spec Writing!

Often when writing a technical specification you'll have multiple options for how to achieve a goal without any overtly compelling arguments on paper to go one way or another. Or you'll discover unknowns about the effectiveness of a particular option, which makes the decision ambiguous. If possible especially if it can be done efficiently I encourage you to give your engineering teams space to prototype one or more of these solutions to gain data to make better decisions in planning. Half a day devoted to building a toy with a new tool to validate that the tool will achieve the desired results upfront is half a day well spent.

### Tech Spec Content

Having a template that your team uses when starting to write a technical specification is a great way to speed things up and ensure important topics are not neglected. I recommend your template primarily be a sequence of headings with topic areas to be covered, perhaps with a bit of instruction or reminder for tech spec authors. I've included a sample tech spec at (ctohb.com/templates)[https://ctohb.com/templates].

A quick aside before jumping into content: technical documents can be a bit dry and serious. If it aligns with your culture, I encourage you to inject lightheartedness where it's appropriate and not distracting. A good example is a clever meme at the top of the document that references the subject of the specification. In my experience, it takes only a manager/leader making a meme once in a spec to encourage others on the team (read: open the floodgates) to add their own.

Some suggested components to include in the template:

* A reminder that the document is in fact a template, and authors should make a copy before starting writing (this mistake is easy to make!)
* Guidance for how a specification should be thought about/a reference to company specification guidelines and approval processes
* A background section explaining the business rationale for the project
* Any particularly standout areas of technical risk this project has (e.g., it touches sensitive PII, or involves previously unused tools/architecture)
* A glossary/definition of any non-obvious terms
* Any explicit business goals the spec aims to achieve/correlation with previously stated goals (i.e., quarterly KPIs or OKRs)
* A solution architecture overview (the bulk of the document)
* Tech debt specifically discuss why or why not addressing any required/adjacent debt
* Data modeling, including required updates to a database or data pipelines
* Internal and external reporting or analytics and measurement requirements
* Testing
* Deployment
* Feature toggles/flags
* Implications on overall system reliability or disaster recovery Security and privacy
* Deliverable milestones

### Tech Spec Approval

To achieve the goal of ensuring consistency and alignment across projects and between team members, you must ensure team members are reading and contributing to each other's planning process. My recommendation to achieve this is to have a lightweight approval process for a specification before it can be considered complete.

#### Review Goals

Your tech spec review goals should include the following:

* Ensure all teams/projects are aligned on technical direction and building consistently.
* Review and educate the team on important data concepts/technical contracts.
* Ensure universal and consistent understanding of the problem at hand.
* Minimize chance of missing important edge cases or other non-business visible requirements.

#### Review Process

My recommendation for a lightweight review process is an asynchronous conversation in the document followed by a synchronous conflict resolution meeting (see Meetings and Time Management, page 28, for more on conflict resolution meetings). The author of the technical specification should, once they've made some progress on the key elements of the project, circulate the document with other engineers who have sufficient context. The idea is for others to read the document and leave comments and questions in their own time. Many of these issues can be resolved quickly and asynchronously by the lead author, but some may be contentious or highly nuanced, requiring higher bandwidth communication.

To close out the process, the author should schedule a meeting whose attendees are only those who have read the document and contributed in advance. The purpose of the meeting is to review open questions and conflicts and come to a resolution. The purpose of the meeting is not for the author to simply read the specification out loud to a bored or disinterested audience. If there are open questions that require further diligence to learn about and resolve, then do that offline and review the results with only the interested parties afterward.

Once all open questions are resolved, document who contributed to the specification (so a future reader knows to whom they should direct further questions), and consider the document approved.

#### Leaders In Specification Review Meetings

The technical leader or manager does not have to be the approver for all technical documents. I encourage you to build a culture where the team as a whole feels safe to contribute and doesn't rely on you to provide technical guardrails or support. Early on, when the department is relatively small, you should be heavily involved in most or all specifications, but that approach won't scale. As soon as you've hired other senior individual contributors, architects, or managers, empower them to be lead reviewers and defer to them, allowing them to do the job you hired them for. If you find a senior member is not guiding the team well in these reviews, don't walk all over them in a public forum. Discuss and course-correct with them in private.

#### Technical Specifications As Documentation

Your tech team is now spending time creating thoughtful documents that cover how you're engineering your product, and the team should be making fewer mistakes as a result. The last way that technical specifications help you is by providing useful resources for future engineers who need to augment or modify the work that's been done. I recommend that you create a well-organized and searchable directory (e.g., an internal wiki such as Confluence or Notion, or document storage like Google Drive), and that your team be diligent about ensuring all specification documents are added to the directory. It may also be helpful to link or refer to the specification in code comments to explain why something is implemented the way it is.

## Developer Experience (DX)

DevOps tooling company Harness (harness.io) defines Developer Experience (DX) as the overall interactions and feelings that the developer feels when working towards a goal. It is similar to the definition of User Experience (UX), except in this case the primary user is a software engineer.

Developer experience may not always be measured on a dashboard, but when it's designed poorly, the team knows it, and they may complain loudly about it. Bad developer experience can derail an engineer an entire afternoon for example, an attempt to boot up the microservice to test it throws a cryptic traceback and the maintainer of the service is on vacation, so a mid-level engineer spins their wheels for hours just trying to get to a reliable build-execute-test loop.

Multiply this inefficiency by all the engineers on your team and all the various types of repositories, services, and projects that exist at your company and it can quickly spiral into losing person-months of productivity in direct time. Add in additional context-switching time spent bringing in others to help solve the problems, and poor DX quickly goes to the top of the list of areas that, when left unaddressed, can tank an otherwise high-performing engineering team.

There are two prerequisites to a great developer experience:

1. Tools that make it easy to have highly reliable and reproducible environments and dependency chains
1. Documentation and consistency in practices for how things are done

Thankfully, nowadays, many readily available tools and ecosystems can help with #1. Most programming languages have an ecosystem with standardized tools for dependency management and reproducible environments. It's up to you to identify and use them (e.g., npm, pipfile, etc.). Many of these systems produce a file called a lock file.

The lock file is not for concurrency management to avoid deadlocks; it's designed to lock in place a specific instance of the dependency graph. You should be committing these lock files and making sure other developers and any build systems use them. The lock file helps guarantee that everyone on the team has installed an identical set of dependencies.

If your chosen programming language does not provide those tools, then it's up to you to build that reproducibility perhaps by using docker containers, makefiles, or the like.

Often the difference between good DX and bad DX is twenty or thirty minutes of upfront effort from somebody familiar with the codebase.

It doesn't take long to ensure that basic build commands work in a fresh install, and that those commands are documented in a local README.

One opportunity for you as CTO to make this easier is to ensure that the build commands used across repositories and codebases at your company are consistent. Maybe it's always docker compose up or always yarn run. Whatever it is, any developer should be able to git clone any repository, and then the first command that comes to mind to build and run the software works.

### Prioritizing Developer Experience

Anything not on the product roadmap can be difficult to prioritize.

Thankfully, DX rarely requires a large enough investment of time that it needs triaging on the roadmap. In the early days of your company, I prefer follow the Boy Scout Rule leave the codebase (or developer experience) better than you found it. Any time a developer encounters a problem building, running, or testing something, it is their responsibility to fix, document, or otherwise ensure that whoever comes to that code next has an easier time of it.

As systems start to get larger it can become an increasingly sizeable chore to get everything running locally together to test functionality. At this point it may be worth investing in DX more formally on the roadmap, or even with dedicated headcount, to ensure that tools are working and developers don't lose large chunks of time fighting the system instead of writing productive code.

### Easy Developer Experience Wins

Here are a few easy wins to upgrade DX across your software engineering team:

* Have a README file with instructions to run a codebase ideally a one-liner to install dependencies then build and run the code.
* Enforce that all code be linted with a strict set of linting rules that is consistent across all usages of that language at your company. Fail your builds if linting doesn't pass. If all developers have their IDE configured to auto-lint, builds should rarely fail for lint issues.

* Ensure that lint configuration is checked into source control where possible (i.e., by investing in setting up something like VSCode's settings.json file, found at ctohb.com/vscode).

* Invest time in making sure that local test data can be set up in local databases from scratch. Often a quick data generator or seed data script can short-circuit a lot of developer headaches. Better yet if the seed data can be easily augmented to add additional corner cases/use cases as the system evolves, so that the base set of test data can be as comprehensive/representative as possible.

* Develop a plan for how to either mock or actually spin up dependent services locally to test multiple-service interactions when necessary. Ideally, with good contracts and domain-driven design, the need for this will be rare, though it should still be easy when necessary.

### Changing Tools For Developer Experience

In 2022, Stripe, the fintech decacorn (i.e., a company valued at more than $10 billion), decided that Flow, its current programming language, had become too expensive to use. It was using too much memory, locking up laptops, and integrated poorly with developer IDEs.

TypeScript, like Flow, is an optional type language built on top of JavaScript. TypeScript has seen far wider adoption than Flow, and thus has solved many of the problems the Stripe teams were encountering with Flow, which had become more painful to work with over time. It was increasingly clear that TypeScript offered a major DX improvement over Flow. The only problem is, how do you convert millions of lines of code from one language to another?

The answer, it turns out, is an eighteen-month project by a team of engineers to prepare for a single, massive merge commit to update the entire codebase all at once. On Sunday, March 6, 2022, Stripe's mega- merge landed, and on Monday, March 7, the team came back to work and started using a new programming language. One developer described the change as the single biggest developer productivity boost in their time at Stripe.

The lesson here is that if the pain of poor developer experience is severe enough, then almost no cost is too high or any project out of reach to make improvements. Your team is almost certainly smaller than Stripe s, and you're likely not dealing with millions of lines of code, but the same calculus applies: if your team is encountering friction in DX that is slowing it down, you must invest the necessary developer time and effort to improve it to gain that efficiency back.

Another problem teams often face is changing tooling too often. In certain tech ecosystems (particularly the JavaScript world), it seems something new and shiny comes out every month that could provide a productivity boost for your team. I encourage you to be disciplined about adopting new tools, make sure you've spent the time to really understand the pain that exists, diligence the new tool, see if it meets *all* your requirements not just the shiny headline and make decisions accordingly. For more on my recommended process here, see Implementing Internal Technology Radar, page 204.

# Tech Architecture

One of your key responsibilities as a tech leader is to make good decisions on your architecture and tools. Good architecture aligns the strengths of the tools and patterns you choose with the needs of your organization now and in the foreseeable future. That requires understanding the strengths, weaknesses, and tradeoffs inherent in each choice. My goal in this section of the book is to make you aware in general of the landscape of options in various domains, and help you recognize the general tradeoffs that different strategies entail.

One thing to keep in mind when discussing tools and tool choice with your team: engineers can be emotional about tool choice. Tools are reviewed as good and bad, and people have personal likes, dislikes, and biases. As the leader and decision-maker, I strongly caution you against adopting this style of language when discussing tools. Not only can it potentially alienate team members if you're disparaging their personal favorite tool; it's also unproductive and can distract from the goal of identifying a good solution for your problem.

Some individual tools are genuinely poorly designed and overshadowed by superior alternatives. However, more often than not a more nuanced evaluation will reveal that a given tool isn't inherently bad, but rather appropriate or inappropriate for a particular company or project. Don't let one bad past experience of trying to use a tool that was inappropriate for solving one problem prevent you or your team from using it another time when it may prove a better fit.


