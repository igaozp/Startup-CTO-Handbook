## Onboarding

Onboarding new engineers to the team, in most cases, doesn't strictly require a large investment from the team; a good engineer will figure it out eventually. That said, doing nothing will lead to a poor experience for your newest hire. It will slow down their time to productivity, and it may also make it harder to identify how well you've hired. Stated another way, good onboarding optimizes for three goals:

1. **It respects the employee:** A good onboarding experience helps a new hire to feel integrated into your company and culture and become productive as quickly as possible.
1. **It helps evaluate the quality of the hire:** Good onboarding provides structure for both the new employee and their manager, including clear goals that, when achieved, demonstrate that you've hired well for the role.
1. **It builds your culture:** Good onboarding emphasizes a culture of continuous improvement, helping to streamline the process for future hires and enhance the scalability of your overall processes.

 There are many right ways to do this. What follows are some relatively simple and inexpensive techniques and practices that I've used myself. Feel free to expand on or deviate from these ideas.



### Boy Scout Rule: Onboarding

I encourage you to emphasize to your managers, your new employees, and in your onboarding documentation that successful onboarding is the shared responsibility of all members of your team(s), recent hires included. Depending on how often you are hiring, onboarding documentation has a tendency to get stale. If a new employee encounters something that is unclear, incorrect, or missing entirely from their materials, make it clear to them that you expect them to put in the effort to clarify and improve the documentation for the next person.

#### Onboarding to the Team vs. the Company

There are elements of onboarding any engineer new to your company that should be consistent across all hires. This includes the high-level process, the emphasis on organizational culture, the types of documentation that new hires receive, and the structure of sharing documentation and setting onboarding milestones. You wouldn't want your frontend teams to have a rockstar-smooth onboarding process but your backend teams to be clueless. First impressions count, and onboarding is your opportunity to ensure that all team members get a great first experience of your organization and are introduced in a consistent way to your company's values and your team's best practices.

That's not to say that the nuts and bolts of onboarding will be identical across teams. You can and should have different materials for different teams when it makes sense, and every team and individual hire should have a customized onboarding plan and milestones.

#### Onboarding Documentation

There are two key elements of getting a new engineer onboarded: teaching them about your culture and best practices, and also giving them something to do by way of structure and instructions. I prefer to break these out into two written artifacts: The Engineering Guidebook and the Welcome to [Your Company Name] Engineering, Day 1 Guide.

##### The Engineering Guidebook

The Engineering Guidebook gathers in a single document all of the opinions, best practices, structural elements, and business operations of your engineering team. It should be the single source any engineer can rely on to learn about choices and decisions that are expected to be consistent across the engineering organization. Be deliberate and thoughtful about exactly what practices should remain uniform across the organization.

The larger your team becomes, the more it will make sense for pieces of the team to develop their own specialized way of getting work done. That said, for most small/medium startups of, say, less than seventy-five to one hundred developers, there is a ton of value and efficiency to be unlocked by adhering to a healthy and consistent set of best practices.

The guidebook can take many forms, though my preference is as a slide deck/presentation. Some examples of practices your guidebook should outline:

Software Engineering

- Choice of programming languages
- Opinions/requirements around CI/CD
- Standards for naming (casing in code, casing in contracts)
- Standards for data processing, protection, backup, security
- Opinions on how to use source control (Git Flow, GitHub Flow)
- Opinions on testing (kinds, tools, how much to do)
- Standard patterns for frontend and backend authentication and authorization
- Wire protocol standards (REST, gRPC, GraphQL, etc.)
- Universal requirements (Do we support mobile, responsive, translation?)
- Certification frameworks and related training (e.g., PCI, SOC2, GDPR)
- Other coding logistics: accessing private repos, linting, static code analysis, commit message format/style.

 Engineering Process

- Opinions on cadence/ceremonies (Agile, Kanban, retrospectives)
- Opinions on technical documentation/specification requirements
- Opinions on how to use the ticketing system (What's an epic? Do we use story points?)
- Any metrics the team as a whole cares about (Are you measuring cycle time?)
- How are production incidents handled (PagerDuty? RCA documents?)
- How new technology gets incorporated into the stack
- Process around bugs, tech debt.

 People Management

- Expectations for how performance reviews are conducted, how individuals are evaluated/promoted
- Expectations for contribution to onboarding/hiring processes.

The guidebook should be clearly labeled as a living document, with a well-defined process in place for proposing, getting feedback on, and incorporating changes to the guidebook. For example, I've used a Request for Comments (RFC) process for updates.

##### Welcome To [Your Company Name] Engineering, Day 1 Guide

Distributing a Day 1 Guide is your opportunity to provide some structure for new employees, giving them a concrete list of things to do on their first day with your organization that will introduce them to the company culture, their teammates, your process, and your software stack. The Day 1 Guide should, of course, reference The Engineering Guidebook as required Day 1 reading. In addition, your Day 1 guide should cover the following:

Instructions on how to get logins/access to required systems, including:

- Source control
- Ticket management
- Any dev/stage/prod logging
- Error tracking
- Any design tools (Figma, Sketch)
- Documentation/wiki (Confluence, Notion, etc.)
- Internal communications (Slack, email)
- Information about company hardware (including whether new hires get to choose a laptop/phone), and expectations for using that hardware
- Instructions on how to set up a local development environment
- An introduction to the team and company organization chart: who their manager is, relevant cross-functional leaders, direct reports, and relevant VPs or executives
- Expectations around transparency and reaching out across the organization chart for help or escalation of concerns
- An introduction to the technical architecture
- Relevant books, blogs, and other written resources you encourage all team members to read

#### Onboarding Milestones aka The Ninety-Day Scorecard

As discussed in the hiring chapter, hiring is very hard. Even the most thoughtful hiring processes will not achieve a 100 percent success rate. Said another way, mis-hires are inevitable.

The best way to handle the potential for unsuccessful hires is first to have the humility to acknowledge that your hiring process isn't perfect, and then to be thoughtful about how to measure the success of the new employees and take swift action to correct any mistakes. The process should be transparent upfront to new employees, clearly explaining expectations. Managers should work with new employees to make sure their role is a mutual fit, that the new employee is starting to feel at home in the role, and that they are delivering at a level commensurate with what they were hired for. At sixty or ninety days, it should be clear to both the new employee and the manager whether those expectations are being met.

If there is disagreement on whether the employee is being successful, that's a good sign that it's not working out, and you should consider relatively quickly whether there is another spot on the team where the new employee might be a better fit, or if both sides might be better off parting ways.

##### The Scorecard

It is the responsibility of the manager of the new employee to identify and document measurable milestones for any new role *before* the new employee starts. On Day 1 the manager should walk through the milestones with the new employee, collect feedback, and collaborate on those milestones to ensure they are fair and clearly measurable. For some roles, these milestones may be easy and clear, such as in a support role measuring escalation tickets with ticket throughput. For other roles you may need to get more creative, for example, features delivered or story points closed. Regardless of the milestones you choose, the scorecard should do the following:

* Establish clear and transparent expectations between the manager and the new employee.
* Provide guidance for the new employee on what they will do and how they'll be measured in their first ninety days.
* Provide obvious criteria for meeting or not meeting the expectations of their role.

The scorecard doesn't have to be lengthy or highly nuanced. The key thing is that, whatever form it takes, after ninety days the employee and manager can look at the scorecard and agree on how the employee has performed and have a shared feeling of confidence on whether this is going to be a good long-term fit.

A quick word on the ninety-day length: ninety days is a commonly used timeframe for onboarding new employees, but it is not a hard rule. A thirty-day interval is generally too short in engineering, where there is a significant learning curve to mastering your technology, tools, and product. On the contrary, waiting a full performance cycle e.g., six or twelve months leaves a potentially poor fit in the role for too long, preventing them from getting the remediation they need to achieve productivity, and costing the company lost time and productivity. The right answer is likely in between, and the exact amount of time is up to you and your managers.

##### Handling A Scorecard Failure

If, after ninety days, the manager and the employee agree things are not meeting expectations, or there isn't agreement on whether expectations are being met, something has to change. This doesn't mean you have to fire the new employee, but it does mean you have to do something. Consider the following options in this scenario:

* Is the problem the manager? Would this person be more successful on another team or with a different manager?

  * If you suspect this is the case, consider a lateral move before moving to termination.
* Is there a cultural misalignment?
  * Realigning an employee to your culture after a misalignment is identified is challenging and rarely successful. If you're concerned you may be in this scenario at ninety days, almost certainly the right option is to part ways, and more likely than not the candidate will be just as relieved as the manager.

* Is it a lack of experience or skill?
  * If you hired someone at a senior level but they're performing at mid-level, you have the option of attempting to down-level them. After all, it's unfair to other employees to keep this person on and pay them as a senior-level performer if they're not delivering at that level. Be warned, however, that down-leveling is very challenging. Unless expectations are very carefully managed, down-leveling will often result in bruised ego and ultimately prove unproductive or even toxic to your team.

##### Letting A New Employee Go

In general, if it's not clear after ninety days that a hire is going to work out, it likely won't magically become better after 120 or 150 days, and it's best to let them go. You should terminate this employee the same as any other, with a full severance package and as much kindness as possible.

I encourage you to take full ownership of the mis-hire. If you hired them, take responsibility; it means your hiring process isn't perfect. Don't penalize the employee for it. An industry-standard severance package at a startup is four weeks salary, benefits if you can extend them, and assistance finding another job in any way you're comfortable offering.

#### Onboarding Timeline

Onboarding begins the second somebody agrees to work at your company and signs their offer letter. You should be thinking about how to make your new employee successful even before their first day. Not every new employee will be eager to spend their own time learning about the company or their role in advance of their start date, but depending on the task or what's offered, many will volunteer to do so.

I encourage you to send candidates your Day 1 Guide as well as your guidebook the day they sign their offer letter. If you have a company reading list, now is a good time to order those books and have them either shipped to the candidate or offer them in eBook/audiobook format. Most candidates are not at all interested in reading/writing code before Day 1, but learning about your culture or reading high-caliber books on business/culture/ engineering is rarely perceived as a burden. You shouldn't require this activity, but by making it available you'll likely get fairly healthy volunteer participation.

On their actual start date, the candidate should meet with their new manager first thing in the morning and check in. If they haven't read through the materials you sent them in advance of their arrival, set the expectation that they are to do so on Day 1. They should schedule follow-up time to review the ninety-day scorecard after the candidate has had a chance to review the introductory materials and set up their environment/logins. This is also a good time to reinforce the idea of continuous improvement and encourage the candidate to take ownership of any hiccups in their onboarding and contribute to improving the documentation and process for whoever follows them next onto the team.

## Performance Management

One of the keys to improving employee morale and promoting a positive workplace culture is ensuring that everyone has a clear understanding of how they are perceived in the workplace and has reliable guidance on how to level up within the organization. The goal of any performance management system is to, as objectively and fairly as possible, provide that transparency and structure to employees. A bad performance management system will result in unwanted surprises or awkward and demotivating situations, while a strong performance management system motivates your team and encourages everybody to level up together.

Poor performance management often results in negative outcomes. Here are two examples:

Person A is promoted and, as a result, Person B is surprised and feels skipped over. The situation worsens if the manager can't provide concrete justification for the decision when subsequently challenged by Person B, resulting in a sense of distrust, oversight, and cratered morale.

Person X, having been at Level 4 for too long, feels exasperated and demoralized not knowing how to make it to Level 5 and get the associated raise.

Your performance management system should give everyone clarity on exactly where they stand, what they need to improve upon (and how), when they'll be evaluated, and how those evaluations are considered for promotions and compensation adjustments.


#### Competency Matrix and Leveling

Performance management and compensation design should not be done entirely by you, the technical leader. There are plenty of ways to make mistakes here that could expose your company to legal liability. These are easily avoided by ensuring that your HR lead is heavily involved in the process. In fact, ideally, your HR lead would do most of the blueprinting and lean on you only for help defining technical competencies. Regardless of who takes the lead, HR is your partner here.

##### Overview

The core of a performance management system is a document, spreadsheet, or other workable artifact here I'll call it a competency matrix (sometimes it's also called an impact matrix or an advancement plan) that lists skills and areas of impact for each role. The competency matrix provides granularity, specificity, and expectations for what each skill/ impact area looks like at various levels.

For example, an individual contributor software engineer's competency matrix may include a row for coding/feature output velocity. In a Level 1 to Level 5 system, the matrix would specify that for a Level 1 engineer, expectations on code velocity are X pull requests per week or the ability to close Y story points per sprint, whatever makes the most sense for your team. Ideally, each description is either directly measurable and specified quantitatively, or qualitatively tangible and interpreted in a consistent way by the team. The expectations for the remaining levels would increase incrementally and culminate in a very high bar for coding velocity at Level 5. In this way, with a complete competency matrix, any given team member should be able to rank themselves within each category and produce a set of rankings that would closely match those provided by their manager or peers.

Once you've got the descriptions for each level written out, all that's left is to publish a formula to summarize rankings of individual skills into a single job level. With that, you've got yourself a transparent, objective, measurable system any employee can use to understand their on-the-job performance and exactly where they can improve to level up. I provide a sample formula for this summation process in Performance Reviews, page 101.

Keep in mind that different roles should be evaluated for different contributions to the team and should have different (though perhaps overlapping) competency matrices. It is especially important to create a separate matrix for management as distinct from individual contributing engineers to encourage managers to grow their skills beyond coding.

##### Creating the Competency Matrix

The details of the competency matrix impact every member of the team, so it stands to reason that the team should be included in specifying those details. Referring to the Team-Based Decisioning Models section of Mini Management Frameworks, page 33, this is definitely a job for either the straw man or the codevelopment model.

I recommend the straw man model: Outline the key skills and impact areas you'd like to see for any given role and take a stab at filling out most of the competency matrix. Then introduce the idea to your tech team and let them know you'd like their input on how to flesh out that first draft. Set aside fixed time as a team and make it safe and encouraged to workshop the matrix together, perhaps using breakout groups to workshop individual categories.

Whatever structure you choose, make it explicit, provide at least a few hours of safeguarded time for working on it, and set a deadline by which to receive final feedback to incorporate and turn into a candidate final draft for the team.

Aim for at most five general categories, and no more than three areas within those categories. Any more than roughly fifteen skill/impact areas will make the matrix too unwieldy to use as an effective performance evaluation tool (and would certainly prove too cumbersome to collect timely team feedback).

Each level should have its rating system and performance expectations clearly described and/or can share a description with an adjacent level, where appropriate.

I've provided a sample advancement plan on my website for this book at (ctohb.com/templates)[https://ctohb.com/templates]/templates. Codeacademy.com also has a great template at ctohb.com/competencies.

##### Compensation and Leveling

I recommend tying compensation to the competency matrix leveling system, as doing so prioritizes two goals: fairness and incentivization for high performance.

Regarding fairness, if any two employees in the same role and level are compensated equally, then it stands to reason that the fairness of that compensation will depend on how fair the leveling is. If the team as a whole contributed to and believes in the fairness of the competency matrix, then by and large they will also believe that the compensation tied to that matrix is fair.

As for incentivizing high performance, tying compensation to leveling financially incentivizes everyone to level up. If the competency matrix is designed well and democratically, your team will focus on skills/areas of impact that actually help the business, which will earn them higher levels (and higher compensation) while also accelerating your team.

Translating levels into fair compensation is slightly more nuanced than most might assume. The easiest thing to do is create a transparent spreadsheet that says everyone at Level X gets paid $Y per year, but a few issues arise from such a strict system: cost of living adjustments (also known as local rates) and non-performance-based compensation bonuses.

GitLab published a great blog post explaining why they pay local rates (see ctohb.com/local. eir compensation calculator is also public at ctohb. com/gitlabcompcalc). That said, There's no one correct way to handle local rates, and you should consider whether or not paying them makes sense for your business. If it does, calculate those rates in a way that is both transparent and data-driven.

Having a performance level translate to a specific pay range, rather than an exact compensation amount, solves many compensation problems. Any given job will want to be calibrated to market rate, but how are market rates determined? Generally speaking, the tools and data that are available to determine a market rate will be somewhat imprecise, and at best give a range within 10-20 percent. The reason it's not more precise is simple: a software engineering role at your company is unlikely to be 100 percent identical in requirements to the same role at a different company. After all, your codebase and tooling aren't 100 percent the same.

Having a pay band also leaves room to increase compensation outside of the performance management system. Non-performance changes include tenure-based increases and inflation-based adjustments. You can also use pay bands as a rough stand-in and leave space for cost-of-living adjustments before your organization formalizes a more sophisticated local rate system.

##### Competitive Rates & Market Rate Data

So, you've designed your competency matrix and decided to translate levels into pay bands. Now, you just need to calculate your pay bands. This is an area you'll definitely want your HR lead partnering with you on closely to ensure you're meeting any regulatory requirements that may exist. Defining pay bands should be as data-driven as possible, and thanks to a handful of existing platforms (both paid and those that just require data-sharing), that data is relatively straightforward. Platforms like Pave, Option Impact by Advanced-HR, Levels.fyi, and Glassdoor can provide rich data sets that can be filtered to match the size/shape/stage of your company to determine a relevant pay band for a particular role.

#### Job Titles

Many startup founders will tell you their organization is very flat and that titles don't mean anything. That may actually be true from time to time in isolation, but it's the exception, not the norm. At the vast majority of companies, startups included, there are consistent trends in how titles are used. Assigning titles creates an expectation for level and scope of responsibility. Titles are also easily given and hard to take away, so it's worth being thoughtful and considerate about exactly what title you put on a job description or a promotion.

For non-executive roles, before you decide on titles I first encourage you to decide what your levels are using only numbers, e.g., Level 1, Level 2, etc., via a competency matrix (See Competency Matrix and Leveling, page 95). Once you know what to expect from each of those levels, you can map levels to titles. Don't be afraid to add a numeric suffix to titles as well; it's easier and clearer to use titles like Junior Engineer 1 and Junior Engineer 2 than it is to invent a new adjective that means slightly more experienced than junior but not yet mid-level.

##### Engineering Individual Contributor Titles

Titles for individual contributing engineers are pretty straightforward, using descriptive adjectives that convey seniority and size of responsibility. Most startups will use the primary three titles: junior, mid-level, and senior engineer. Beyond senior, phrases such as principal, fellow, and architect are often used, though they have a less consistent definition and hierarchy.

Senior individual contributors often have the informal title of tech lead. Tech lead implies that some of the individual contributor's time is spent on management-style responsibilities, but their primary responsibility is still doing engineering. Rarely is the notion of a tech lead something that is noted in a title on a résumé or organization chart; it's simply an added responsibility for more senior employees and is part of the expectation at that level of seniority. If a tech lead's primary output is management, not code, then they should be on a management track with a manager's expectations, title, training, coaching, etc.

##### Manager Titles

Management titling has more nuanced implications than individual contributors. The most common titles are software development manager (SDM) or software engineering manager (SEM), with appropriate seniority decorations e.g., mid-level software engineering manager or senior software engineering manager. An SDM or SEM is usually responsible for a single team of engineers, who in turn work on a single feature or product.

The next level is typically a director of engineering. Directors are accountable for the performance, alignment, and output of multiple teams within single or highly adjacent products. In most organizations, a director is not expected to be a strategic role. In other words, a director isn't setting foundational technical direction or product strategy.

Beyond director is the role of vice president of engineering (VPE). There isn't a universal implementation of VPE. It varies from being the organizational lead of all engineers at the company (in place of a CTO) to being the strategic technical lead across multiple product areas. Sometimes the VPE reports to the CTO, and other times the CEO. What VPEs have in common, though, is the expectation of being technically very senior, experienced, and skilled at people management a great communicator and strategic thinker.

#### Performance Reviews, Surveys and Promotions

Not all skill areas in a competency matrix can be evaluated quantitatively by a manager or spreadsheet, so every team needs a performance review process that can also collect qualitative feedback from managers and peers.

The challenge is to collect qualitative feedback in such a way that it can be used to align with your leveling. In this chapter, I present a methodology I've used to collect feedback that ultimately results in a relatively easy-to-understand scoring system that can produce individual performance levels.

##### Review Cadence

Performance reviews require a considerable amount of time, can be emotionally exhausting, and are very costly to your team, all of which push management to do them less often. The competing incentive is the fact that employees want tighter feedback loops and more opportunities for promotion. The balance is struck at scheduling reviews once every six or twelve months (more immediate feedback can and should be done with regular employee/manager 1:1 meetings). Remember, a sufficient amount of time between reviews is needed in order for individuals to grow and demonstrate that growth. Generally, six months is a safe lower bound that balances these concerns.

##### Reviewer Selection

The who reviews whom question has no easy answer. Many companies simply have the manager do the review, and that's it. While the manager's feedback is valuable, it can also leave too much room for bias and neglect the equally important perspective of peers and direct reports. The easiest (though slightly more costly) way to run a fair and comprehensive process is to have every employee receive multiple reviews that include these other perspectives, often called a 360 review.

Here I recommend using the straw man technique (see the Team-Based Decisioning Models section of Mini Management Frameworks, page 33): Each manager should create a list of direct reports and peers who have enough exposure to that team member to write a valuable review, then have a conversation with the employee and get feedback before finalizing the list. Managers should also keep track of how many reviews each employee is being asked to complete to keep the requests manageable.

##### Review Questions

Your questionnaire should mirror your competency matrix, and reviewers should be encouraged to make explicit references to the matrix.

The same set of questions can apply to each matrix category:

* What are some examples of this person excelling in this area?

* Where does this person demonstrate room for improvement in this area? What level do you think this person is performing at in this area?

Note that from an unconscious bias perspective, it's better to ask the reviewer to enumerate the examples before asking for a level. The alternative may encourage reviewers to choose a level, then cherry-pick examples to justify the level they've already chosen.

It may make sense to include some higher-level/softer questions at the end:

* How eager and excited are you to work with this person? (Scale: Not excited at all to Very excited. This question is from Netflix's Keeper Test [ctohb.com/keeper])

* This person is currently at Level X. Do you feel they are ready for promotion to Level X+1?

* Are there any other strengths this person brings that you want to highlight?

* Are there any other areas for improvement that you want to highlight?

##### Review Format

You can conduct reviews with or without the aid of a formal review tool (also known as performance or culture management tools, like Culture Amp and 15Five). Of course, a purpose-built tool will save time and scale this process quickly for larger teams. It's crucial to keep all individual feedback anonymous, with the exception of noting which scores came from management (we'll use those scores separately as a sanity check against peer reviews later in the process).

##### Result Calculation

Once the reviews have been submitted, a set of scores should be reflected for each person in each category of the competency matrix, ideally broken out between scores from peers, direct reports, and managers. Here is an example matrix of scores:

<TODO: Insert Table Here>

The challenge now is how to aggregate those scores into a final job level calculation. Some key considerations in this calculation:

* Protect the integrity of the process (e.g., that an employee didn't collude with their peers to artificially inflate or deflate anyone's scores)

* Ensure the formula is fair and can be calculated consistently

* Confirm that the manager's perspective of the employee's impact aligns with peer/subordinate feedback

* Decide whether all categories in the matrix are weighted equally or unequally.

Here's the method I recommend to determine a level: Assign the level at which the Cumulative Score is 66 percent or higher. The cumulative score for a given level is the percent of all scores that are at that level or higher. The lowest level will always have a cumulative score of 100 percent, Level 2 will be 100 percent minus the percentage of votes from Level 1. Level 3 is 100 percent minus the percentage from Level 2 and Level 1, and so on.

In the example above, the individual would be a Level 2. At Level 2, their cumulative score is 90 percent. Using the 66 percent rule, they are very close to a Level 3 (which is at 60 percent) a mere two votes away. That they are so close can be used in coaching to encourage further improvement before promotion, or used to justify an adjustment within a pay band.

When you've completed your overall calculation, if you've managed to track a manager's scores separately, you can apply the same formula to the manager's scores in isolation and calculate the difference between the level resulting from the cumulative score of the manager's reviews and the level from the cumulative score of all peer reviews. A large delta there anything more than one level warrants close attention and additional review as it means the manager and peers have significantly different perspectives on an individual's performance. Or it might indicate some irregularity in the voting/scoring process.

##### Result Discussion

I encourage managers to provide performance review data ahead of an actual 1:1 performance review meeting to maximize the value of the meeting itself. It's best to give the individual the data and some time to process, so they can be fully engaged when the meeting occurs.

The agenda for the performance review meeting should be simple:

1. Discuss any strengths or weaknesses that were identified that are unexpected or otherwise not regularly covered in 1:1s.
1. Synthesize a small list of focus areas to work on before the next review period. Many leaders advocate for a single focus area, but I've seen several individuals grow in more than one way during the given period, so two or three focus areas is a reasonable upper limit, as applicable.
1. Establish a schedule for the manager and employee to regularly check in on those focus areas and ensure there's advancement before the next review.

##### Compensation Adjustment Rollout

At many companies, review feedback and compensation changes are handled at different times. I don't believe it is critical, or even advantageous, to discuss compensation changes in a performance review meeting, as this can distract from what can otherwise be a challenging but important discussion. The key thing is to set expectations for when compensation changes will be decided, communicated, and implemented before the performance review process, so they know what to expect before they walk into the meeting.

### Performance Improvement Plans (PIPs)

Performance improvement plans, commonly referred to as PIPs, are a tool that provides structure to either improve an employee's performance or fire them. Some key aspects of PIPs:

* Everyone on your team should understand your company's PIP process.
* Many people go into work with the same searing questions at the back of their minds: Will I be fired today? or Am I doing well enough?
* Knowing that their company has a formal process for firing employees that includes an opportunity for correction can help reduce these anxieties.
* PIPs should only be used in a genuine attempt to address *and* improve underperformance, as they demand a significant effort from both the employee and the manager.
* The manager should take time to thoughtfully complete the PIP document, making sure that it clearly articulates the underperformance, provides quantitative, clear evaluation criteria and structure wherever possible, and offers support and mentorship to help the individual improve.

* PIPs should allow a reasonable time period to demonstrate improvement say, thirty days for individual contributors and sixty days for senior staff or managers.

PIPs should always include a complete written version, not only to ensure clarity between employee and manager but also to provide documentation for HR/legal to have on record for any subsequent inquiries.

There are a few situations in which you should bypass a PIP process and proceed straight to termination:

* Breaks in company policy, HR violations, inappropriate workplace behavior, etc., are not correctable with a PIP and should be met with zero tolerance.
* Certain skill gaps are not correctable with a PIP, such as general lack of good judgment on a certain topic, poor culture fit, or lack of experience in critical skill areas. This is most commonly a consideration for management or very senior staff positions where good skill judgment is critical to the role.

### Changing Seats

Before developing a PIP or terminating an underperforming employee, it's worth asking the question of whether that person might be a better fit for a different team or role in the company. If the nature of the underperformance is skill-based, and the employee has skills that might be better applied in a different role, then changing teams can be very productive. If the underperformance is culture-based, then you'll likely find neither side has the motivation to attempt an internal transfer.

#### Brilliant Jerks

A brilliant jerk is an industry-standard term used to describe an individual who is highly productive on their own, but whose presence hurts the morale or productivity of the people around them. They are often described as toxic personalities.

Due to their sometimes extraordinary individual productivity, choosing to fire a brilliant jerk can often feel difficult or wrong. The nearly universal recommendation is to fire them anyway. Each day that you, as a manager, allow toxic behavior to persist can increase your team's resentment toward you for allowing it to continue. There's no amount of individual productivity that makes up for the hit to company culture and to your credibility as a manager that retaining a toxic individual entails.

### Firing

Your company should have a clear procedure for how to actually terminate an employee. My best advice: follow it. This is an area that, if handled incorrectly, can become a substantial liability to the company. Key considerations include:

**Documentation:** Ensure you have sufficient documentation to justify the decision to let this individual go and to prove that the termination is based on performance or another for-cause reason.

**Timing:** Once you've decided to let somebody go, do so as soon as possible. The common wisdom is that, after letting somebody go, managers typically worry less about whether or not that person should have been let go and more about whether they waited too long to do so. Mechanically, it doesn't make much of a difference what day of the week you decide is best to let somebody go, but if you are able to save it for the first day of the month instead of the last, you are offering the employee the benefit of an extra month on the company healthcare plan.

**Witnesses:** Ensure that the manager and HR are present to witness the actual termination meeting. The meeting should be very short and to the point, and HR should answer most follow-up questions concerning termination logistics.

**Offboarding:** Develop a plan in advance of termination for how and when to turn off the employee's access to company systems and recover any company hardware.

**Severance:** Letting an employee go is most often just as much a failure of the company/management as it is the employee. Letting someone go is not a place to be spiteful or petty; that person has invested time and energy into your company, and you should do everything you can to set them up for success at their next role, including an industry-standard severance package (the range is somewhat broad, from a few weeks for an individual contributor up to two to three months for a senior executive, with packages also often factoring in tenure).

