## Testing

Imagine that, instead of testing software code, your job was to be the inspector for a municipal bridge. The bridge is built and now it's your job to inspect it and decide whether or not to allow it to open to the public. Do you inspect every single bolt and rivet on the bridge? Doing so would probably give you high confidence the bridge was safe, but it would also take a long time and derail the mayor's plans to open the bridge next week.

Another reasonable strategy would be to decide exactly which elements of the bridge are essential to meet the designated safety factor and test/ inspect those. Maybe that's only every other rivet, plus all the cables and structural concrete.

Similarly, in software engineering testing, the goal isn't coverage for coverage's sake, but coverage that provides confidence that the software does what it is intended to do.

Effective software testing is not always about 100 percent code coverage. The bar for a good software test suite is that it gives your team confidence that, when the build is green and all tests pass, the software is ready to be released to end users. That may mean 100 percent code coverage, or it may mean 30 percent code coverage. The exact number is up to you to determine and monitor, and that amount of effort may change over time if you find the tests are not providing the same confidence they once were (and, conversely, if you find you're overinvesting i.e., you're spending a lot of resources on a test suite, yet bugs are still making it out too often).


### Testing/Quality Assurance Teams

Depending on the size of your team, you'll either have no dedicated test team, one test team working on one or many types of tests, or many test teams working on various kinds of software testing. No matter who is doing the test it's important to recognize that software testing is a complicated process, and nuance matters. To test software effectively, the tester, whether they wrote the code or it was thrown over the fence to them, has to deeply understand what the code/software should be doing. Your role is to set up your teams so that they can empathize with each other. To do this, ensure that the teams share goals/KPIs, that your process has robust and continuous communication between the developer and tester, and monitor that the teams have a healthy, productive relationship.

### Test Quality

Before jumping into the nuts and bolts of the different software testing paradigms, it's worth thinking about what the purpose of software testing is, and thus what makes a good test, and conversely what makes a bad test.

Defining bad tests is simple. Bad tests have a higher cost than benefit to your team. Some common characteristics of bad tests:

* It takes more time to maintain and fix tests for legitimate code changes than the pain you save by bugs found.

* The test has a high false positive rate or is inconsistent, which slows down CI and causes developers frustration and context-switching cost to re-run spurious failures.

* The test is poorly thought out and literally validates that the code does the wrong thing.

* The suite tests that the code does the right thing and has low false positives, but it's so convoluted and hard to understand that only the person who wrote the test can add a new one, and every other engineer who looks at it gets a migraine.

* The test does not instill confidence that the code under evaluation is ready to be shipped to end users.

With that picture in mind, it's relatively easy to see by contrast what attributes good tests should have. Good tests are:

* Easy and fast to run both locally and in a shared CI environment

* Capable of running reliably and consistently producing the same result Easy to augment

* Easy to refactor or update for underlying logical changes

* Appropriately coupled to the underlying code patterns, testing at the right altitude (so to speak) to capture breakages that matter

* Easy for any engineer to understand and work on

One of the best ways to evaluate your testing approach is also the most obvious: ask how your team feels about the tests with a simple sentiment analysis. The results tend to be very binary either tests are a source of security that teams rely on, and naturally augment them because they obviously are a net value-add; or teams passively, or even actively, hate their tests because they're a drain on productivity with not enough obvious value.

### What To Test

Your team should be adding testing in ways that boost confidence that the system works correctly while minimizing the additional burden of maintaining those tests long term in the face of organic system growth. A general pattern to minimize this pain is to test the public interface. Public interfaces should be well thought out and comparably stable over time.

They are also the happy path that consumers of the software will actually experience.

Tests on public interfaces should therefore change little over time and also provide confidence that the parts of the code that matter are working correctly.

The public interface for your software may vary from project to project. For many projects, it'll be an actual HTTP-based API; for some, it'll be a set of functions/classes in a library or internal service. For other projects it may be a user interface.

### Testing Type Comparison

Software testing can be broken down into the following categories/ paradigms:

* Unit testing
* Integration testing
* End-to-end testing
* Manual testing
* Semi-automated testing

The attributes that differentiate these types of testing are as follows:

**Code planning:** How much forethought is required in the actual writing of the code to ensure it's testable under this test paradigm.

**Test scope:** How much each test can evaluate at once.

**Change granularity detection:** What size of, or type of, code change a test is likely to detect and cause a failure.

**Run cost:** How quickly or how costly it is to run the tests, in time or in dollars.

**Addition effort:** How much effort is required to add additional coverage.

**Setup effort:** How much effort is necessary to set up an effective test suite.

The following chart summarizes how the five paradigms map to these metrics. Note that there is no one perfect test paradigm; each has tradeoffs, and I encourage you to think carefully about which tradeoffs make sense for your company and codebase. The right answer is usually a blend of different test paradigms, using each type of test where it adds the most value in your application.

TODO: Insert the table from the book


### Unit Tests

Unit testing is often the first thing that comes to mind when somebody talks about software testing. It's widely what's taught in school and included in textbooks, and it usually gets the most effort in the real world. Given all this, you'd think unit tests were the best type of test, though I'd argue that's not always the case. Let's begin by clearly defining unit tests so as to differentiate them from other testing paradigms.

Unit tests run entirely in memory on a machine, in a shared memory space with the code under evaluation, without requiring any network connectivity or dependency on external services. Most unit tests are very fast to run, test very small amounts of code at a time, and are relatively easy to get started with. Unit tests are usually also tightly coupled to your code contracts and often require new code in the form of mocks to enable code- under-test to execute without normally available external dependencies.

The key tradeoff made by unit tests and their primary downside is that they are tightly coupled to the code under test. It's altogether too easy to have unit tests be deeply intertwined with actual function calls and internal data objects. This deep dependency means any refactor of the code even simple and benign changes will require considerable unit test updates as well. The creation of mocks and test data fixtures often also requires a considerable amount of code to create and maintain to allow unit tests to run, adding unexpected cost to the unit testing framework.

### Integration Tests

An integration test relaxes the in-memory and zero-dependency constraints of unit tests. As a result, integration tests tend to run slower and integrate with code-under-test at a higher level. When they run in a different process from code under test, they're usually exercising an externally exposed contract, such as an API. This means that internal refactors that don't change API behavior tend to go unnoticed by an integration test, making these tests overall less brittle but also less likely to detect smaller side effects.

In addition, integration tests require the creation of fewer or no mocks and, as a result, can be less code to implement.

### End-To-End Tests

An end-to-end (e2e) test exercises code in the same manner as the end user. For backend code, end-to-end tests and integration tests may function in the same way, running code via an external contract. For user-facing frontend code, an end-to-end test usually involves mechanizing the client interface, often a web browser or mobile phone. I would not encourage any tech leader to write their own client mechanizing code this is a particularly gnarly problem that downloadable tools like Selenium, Cypress, and Puppeteer can take off your hands. For mobile, there are tools like HeadSpin and Detox.

The key tradeoff of end-to-end tests, in the real world, is reliability. At least at the time of writing, reliable web end-to-end tests are still somewhat elusive; the nature of how the browser renders means race conditions occur very easily by accident. Building a reliable web end-to-end test suite requires considerable care, attention to detail, and maintenance.

The payoff, though, is not insubstantial, as it's possible to create very high test coverage and very high confidence in functionality of user-facing flows with e2e test suites. There are several companies, including testim.io and rainforestqa.com, that are exploring using AI and ML to solve this problem. These solutions deploy fuzzy visual testing instead of relying on the presence or absence of CSS selectors, for example, to try and improve test reliability. Hopefully by the time you read this, the state of the art will have advanced a bit further, and the value proposition of end-to-end tests will be even stronger than at the time of this writing.

#### Visual Regression Testing

Visual regression testing is a relatively new paradigm that aims to detect defects in user-facing applications by performing deltas on rendered visuals. There are frameworks that do that at various levels of granularity, ranging from capturing screenshots of entire pages to rendering individual components, and producing deltas to detect defects. The obvious drawback is that every intentional change to any visual tested component will require a change to a test.

Fortunately, these test frameworks often make it simple and painless to reproduce the set of correct visuals for comparison, which opens up another pitfall: with easy tooling to overwrite the testing target, it becomes very easy to produce false negatives, accidentally accepting a visual delta that is, in fact, erroneous.

#### Manual Testing

Manual testing, as the name implies, is run by humans and not machine code. For humans testing code, we can further subdivide this category into specialized and unspecialized testers.

#### Specialized Manual Testing

Specialized manual testing is an in-house manual testing team. Beyond the traditional benefits of an in-house team, such as aligned incentives and a long-term working relationship, the value of being in-house is that the team can build expertise in your product and deeply understand your users. This allows the team to identify defects that an untrained or unfamiliar tester would miss. A high-quality testing team can not only serve as a resource for catching software defects but also contribute valuable feedback on a product level, identifying inconsistencies in design, and asking provocative questions about how or why something works the way it does.

A great in-house manual testing team can provide a huge improvement in overall software and product quality.

Specialized manual testing teams should be creating detailed test plans for product functionality and storing those plans in an easy-to-retrieve/ repeat fashion, ideally with a tool like TestRail that allows creating full test suites of manual test plans which can be rerun by the team manually on demand. Another benefit of a tool like this is integration with other developer and product tools for example, linking a TestRail run to a Jira epic to show how many manual and regression tests were run for the release of a given feature. Not only is this valuable as a launch checklist item, but it also aids in retrospectives for any released defects, allowing you to revisit what manual tests were run before releasing any given feature, and adding additional manual tests to catch any defects that made it through.

#### Unspecialized Manual Testing

Unspecialized manual testing is often referred to as crowdsourced testing. There are several proprietary platforms for sourcing testers, such as Rainforest QA, Pay4Bugs, 99Tests, and Testlio. The pricing model for these platforms usually varies based on the number of validated bugs submitted. Depending on the nature of your product and the types of defects you're looking to optimize for, crowdsourced testing can be a very cost-effective and low-effort way to improve product quality.

### Semi-Automated Testing

Semi-automated testing is a relatively new category of software testing. These tests are created by non-technical staff perhaps your specialized manual testing team and then run in either a completely automated or supervised environment.

The major pitfall of these tests is reliability. Because they're created by non-technical staff, they may not be quite as precise as fully automated tests, making them more prone to false positives and false negatives. That said, this space is rapidly evolving with new companies and tools launching every year, such as Rainforest QA and Testim, with strategies to improve reliability and lower overall cost.

## Source Control

The industry standard used by the vast majority of companies for managing source control is Git. There would need to be a very compelling reason for your organization to use anything else; most of your current and future team members will arrive already knowing the basics of Git. By not using it, you'd likely be inflicting an unnecessary learning curve on them by forcing them to learn your chosen alternative.

There are three main cloud Git hosting platforms: GitLab, GitHub, and Bitbucket. These three have the lion's share of the market and, again, you should think carefully before deviating from these standards.

Git has an interestingly shaped learning curve. Most people reach a plateau where they operate with a rudimentary understanding that gets them by for most happy path testing scenarios. However, sometimes things go wrong, and a developer loses a commit or makes a mess with a merge. When this happens, their failure to climb the rest of the Git learning curve will cause frustration and slowdown. I encourage you, as the team lead, to invest the effort to climb the back half of the curve. Use Git exclusively on the command line to become familiar with what is actually happening. Learn about the reflog, interactive rebases, bisect, and the various built-in merge strategies. Armed with this knowledge, you can bypass an entire class of productivity-draining problems and train your team to become Git experts as well.


### Peer Review

In general, experts recommend implementing a robust peer review process for all code changes. (As I write this in early 2023, there is a growing movement challenging this recommendation, or at the least adding nuance to it, which I'll discuss in the next section.) Most peer review is done with what is called depending on your code hosting solution a pull request, code review, or merge request. Here are some suggestions for keeping code review productive and efficient:

* Keep reviews small! Set a maximum size for code reviews, something like ten files and 200 lines. Anything else should be broken out into multiple stacked/incremental reviews. (A stacked review is a code review that is based on or dependent on a prior review. When completed, the reviews are merged sequentially to add up to a complete change.)

* Establish the goals for code review upfront with your team and bake them into your culture. Code review is not for style or petty semantics; that's what your auto code formatter/linter and static analysis are for. Code review's purpose is to ensure clarity, identify architectural concerns, flag defects and deviations from patterns, note edge cases, and guarantee adherence to business rules.

* Require the author to make the reviewer's job easy. Authors should include a description of the change, a link to relevant requirements and tickets, and a video walkthrough (using a tool like loom.com) of the code and the code working as intended.

* Encourage the author of any given code review to do a self-review before asking others to review. A few well-placed comments from the author to guide readers can save a lot of time.

* Set aside dedicated review times/windows to minimize disruptions.


### Ship, Show, Ask

The common wisdom is that every code change should be reviewed by two people before being shipped to customers. As with everything, there are tradeoffs. Manual code review is not free, nor is it a guarantee of software quality. Given that manual code review comes at a cost, it's worth thinking about when that cost provides the highest return and using code review as a tool for the highest-ROI scenarios. This general idea was popularized by a 2021 blog post by Rouan Wilsenach titled Ship/Show/Ask (ctohb.com/ssa).

Let's examine the cost of code review. A code review requires two people call them the Author and the Reviewer to experience a number of context switches. A common asynchronous code pattern might be as follows:

**Context Switch #1:** Author stops coding on Project 1, sets up code review, and tags Reviewer. Author starts working on Project 2.

**Context Switch #2:** Reviewer gets a notification, stops their work on Project 3, and begins review of Project 1. Reviewer leaves feedback for Author, résumés work on Project 3.

**Context Switch #3:** Author is notified of feedback on Project 1, stops work on Project 2, and addresses comments from Reviewer. Then Author résumés work on Project 2.

**Context Switch #4:** Reviewer stops work on Project 3 and best-case scenario Reviewer is now satisfied with changes in Project 1 and approves the code review. Reviewer résumés work on Project 3. Worst case, Author and Reviewer must repeat Context Switches #3 and #4 several times.

**Context Switch #5:** Author is notified of approval, stops work on Project 2, merges Project 1, then résumés work on Project 2.

There are ways to minimize these context switches, but they too involve tradeoffs. A common alternative is to do all code reviews as a synchronous pair programming exercise; however, that strategy trades context switches for synchronous meeting time, which is still a drag on productivity. No matter how you slice it, human code review is expensive.

My suggested alternative is to classify types of work by their level of risk, and the expected benefit from code reviews. A sample classification system:

 Trivial changes no approval required

- Copy/translation updates
- Minor UI changes, ideally submitted with visual evidence of the change
- Test-only changes
- New code that is explicitly not yet used or is disabled behind a feature toggle
- Code that no customer or user is able to access (e.g., hidden pages)

 Minor changes minimal review or after-the-fact review

- Code changes that come with tests and involve augmentation of existing patterns and functionality
- Code that has limited or no real-world usage (e.g., an undeployed product)
- Refactors that can be proven are correct via reliable testing

 Major changes careful upfront review

- Anything involving new tools, frameworks, patterns, or architecture
- Significant new features
- Anything involving sensitive data or PII or with potential impact on security posture

Although I believe this system improves overall team efficiency, I concede that it's not an option for everyone. Many compliance regimes (such as PCI or SOC 2) require a policy of 100 percent human code review. The best you can do in that scenario is comply and perhaps carve out products or feature areas that are not governed by the compliance framework to experiment with a more nuanced and efficient process.

### Branching Models

There are many ways to deal with source control branching, though the industry as a whole is building momentum around the concept of trunk- based development. As this seems to be the most effective and commonly used pattern at this time, it's what we'll discuss here. If you're seriously considering a different pattern, you'll find plentiful resources online discussing methodologies and best practices for alternative approaches.

There are many blog posts with helpful graphics covering git branching models, such as this one from Reviewpad: ctohb.com/branching. If the following description doesn't make sense to you, I urge you to consult any of these posts and their associated visuals.

In a traditional branching model sometimes referred to as GitFlow there are two long-lived branches, a main and a develop branch. Work is done based on develop in feature branches and then is often forked to another release branch for any given release, and then finally back merged to main. Hotfixes are then done off of main while further development is done off of develop. This system involves no less than four branches for every change to get to production, and involves maintaining many branches simultaneously. For these reasons and others, GitFlow has largely fallen out of favor and is no longer considered best practice.

Trunk-based development, and its slightly more sophisticated cousin, GitHub Flow, are models of managing source code that aim to minimize the number and duration of branches. The exact implementation of GitHub Flow and trunk-based development will vary, but what they have in common is that there is a single branch whose name varies and doesn't matter much. Here we'll call it production. Production is always deployable. In fact, I recommend that you set up automation so every commit to production can actually be deployed to production. Work can then be done in feature branches off of production, reviewed in the feature branch, and merged when ready. That's it one long-lived branch and many short-lived (and ideally small) feature branches.

For this model to work well, you need a handful of prerequisites:

* Continuous Integration that runs a robust test suite to ensure that feature branches are safe to merge.

* A culture and an implementation of using feature toggles so branches can be merged quickly and then features deployed/enabled at a later date when it makes sense for the business.

* Robust monitoring of production to detect changes.

* The ability to rapidly deploy, with zero downtime, code changes to the production environment. Similarly, an ability to rapidly revert individual changes in response to an incident.

* A culture that is disciplined about small and short-lived feature branches. The GitHub Flow model loses its efficiency and simplicity if feature branches become large, long-lived and unwieldy. As discussed in the 3.3.5 Feature Branch Environments, small commits, small branches. and small pull requests are a key driver of productivity.

### Long-Lived Vs. Short-Lived Branches

The key to maintaining a smooth system of branches and merges with your team is to keep branches short-lived. Nearly all of the problems associated with code merging come from code branches being open too long or the branch containing too large a diff (ctohb.com/diffs). In general, a short-lived branch should be open just a few days, or two weeks at the absolute most.

Keep in mind that a feature doesn't necessarily have to be implemented in a single branch. For example, you can have an initial branch with just tests that is reviewed and merged, and then followed up by a branch with the implementation. Alternatively, you can build an implementation that isn't connected to the main application, have it reviewed and merged, then build the connection and tests in a subsequent branch.

With a bit of thought and practice most implementations can be broken down into independently mergeable pieces. This is a skill that with your guidance teams can develop over time.

Benefits of keeping branches short-lived:

* Limits the amount of time for new code from other branches to be merged into trunk, thus limiting the scope for code conflicts. Smaller branches also inherently have less surface area for conflicts.

* Keeps the feature branch code relatively small, thus making it easier for reviewers to read and limiting the scope for breakages.

* Encourages faster feedback in reviews, and allows for course corrections sooner in the process of implementing features.

* Encourages your team to have a reliable Continuous Integration system. Frequent merges will highlight deficiencies in your build/test environment, making it painful if the systems are unreliable and motivating improvements to those systems.

## Production Escalations

An escalator is a tool that takes in incidents and manages an on-call rotation, paging the on-call engineer and then escalating to others if pages go unacknowledged. PagerDuty is likely the most popular of these tools.

### Implementing Escalators

Before you implement an escalator and set up a rotation, make sure the engineers on your team have opted in to being on rotation, and that everyone knows and understands expectations for creating exceptions (e.g., trading an on-call window with somebody else during a vacation).

You'll also want to ensure that you have adequate documentation in place, and that everyone understands the standard procedures for what to do when receiving a page. Some considerations for establishing these procedures:

* Note where the recipient should post an acknowledgment of receipt of the page (maybe in the escalator tool itself or a shared group chat dedicated specifically to handling escalations).
* Enable easy access to the playbooks that are used to help diagnose particular kinds of problems.
* Determine whether to, and where to, set up any kind of site down notice (e.g., a company status page needs updating).
* Decide where and how often to post updates on the status of the investigation, impact estimate, and restoration estimate.
* Determine what to do once an incident is closed, scheduling a root cause analysis exercise and ensuring the particular incident does not recur.

### Root Cause Analysis (RCA) Exercises

Any time there is a system issue that has measurable user impact, your team should perform some level of root cause analysis (RCA). The goal of

an RCA is to understand where your systems had a failure that allowed an impactful defect to make it to production and to end users.

To be crystal clear, the root cause analysis *must not* be about identifying fault or assigning blame. That needs to be true in every part of the RCA process and embedded into the culture of your team. The RCA attacks systemic problems (not human errors) in your system that allow a failure to occur.

Without that safety and willingness for team members to be forthright with their feedback and documentation, you'll miss out on key opportunities to improve the system.

#### RCA Documents

Your team should produce documentation in some form for every RCA. Depending on how often issues occur with your system, and the nature of those issues, you may wish to create a classification system for RCAs, with low-impact incidents getting a lighter-weight RCA process than high-impact incidents. It should be acknowledged that a thorough RCA on a high-impact incident is an expensive effort, taking considerable time and thoughtfulness, and that it may prove too heavy-handed for trivial defects.

That said, for most companies it's better to err on the side of overspending in this area and ensuring greater reliability. You should start with a thorough RCA on everything, and transition to a stratified RCA system once you've got a good understanding of the landscape and impact of the kinds of issues your team will face.

For issues that merit a full, thoughtful analysis, here is a template that will get you started and asking your team the right questions: ctohb.com/ rca. It is a good practice and in fact a requirement for most compliance frameworks to create a new document like this for every incident and to organize them in an internal company document store for later reference.

#### RCA Meetings And Timeline

As soon as it is practical after you've resolved an incident, designate an appropriate person to serve as the lead on an RCA. The lead should clone the template and begin filling in relevant data about the incident and beginning to explore the Five Whys (ctohb.com/5whys) for the incident.

They should complete an initial draft of the RCA and circulate it to relevant peers before scheduling a time as a group to explore and try and improve the analysis and future prevention steps.

The meeting attendees should read the RCA draft in advance and come prepared to explore the nuts and bolts of the incident and ideate on future prevention steps.

#### Choosing the RCA Lead Author

The RCA lead need not necessarily be the person who responded to the incident. The ideal RCA lead should be someone who is very familiar with the systems involved and can ask insightful questions about where tools and processes failed and generate ideas for improvement.

Note that we re not throwing anyone who made a human error under the bus. That person may be the RCA lead if they fit the prior criteria, but their error does not on its own make them the right person to lead the RCA. They should certainly contribute and take the opportunity to learn through the process. But again, they are not punished for their mistake as part of the process. Authoring an RCA is not a punishment; it's an important responsibility and element of system maintenance.

#### Scheduling RCA Remediation Work

A good RCA process will often identify many work items for the team to improve the system and make future incidents less likely. The natural next question is: do we do them now? For the engineers involved, the answer is likely yes; for a manager concerned about hitting deadlines and a roadmap, the answer will be less clear.

There is no one right answer to the question, but here is some general guidance:

Never let a good crisis go to waste. Motivation to remediate issues will be at its peak around the incident and the RCA meeting, and highly motivated engineers are often most efficient. It's also easy to underestimate the overall cost to your team of system reliability issues and thus under prioritize reliability improvements. The fact that a production incident occurred should remind you and your team that these investments are critical to limiting distractions and enabling teams to focus on productive feature work and delivering consistent high velocity.

The level of effort for many remedial issues is likely to vary widely. Some typical tickets might be add more logging or change a setting in our CI provider to ensure PRs with failing builds cannot be merged. These types of trivial tickets cost more to maintain and groom in a backlog than they'd take just to do in the moment, so just do them. The chances they are the wrong thing to do are pretty low, and if negative consequences result, they can be easily reversed.

For high-effort remediation steps, I encourage you to triage those and put them through your regular planning process. Often, high-effort remediation steps can be simplified with the benefit of time and planning. Said another way, the identified right way to solve the problem on day one may not be the ideal solution, and only by putting the issue through the regular paces of technical scrutiny can a better, perhaps less costly, solution emerge.

## IT

Here I refer to IT, information technology, as internal company tooling and technology used to conduct business on a daily basis. This is in contrast to the technology your company is building for its customer product.

IT usually comprises tools like company hardware (desktops, laptops, and phones), VPNs, email, antivirus and monitoring software, etc. As a startup in the modern world, whether you're an in-person or remote team, if you make a few wise decisions, you should not need to spend very much time or capital on IT.

Some key decisions that will help you minimize IT cost at most small tech companies:

Use a cloud-based system for company email, data, and documents. Most startups are using Google Workspace, but if your team members (and prospective future hires) are more comfortable with an alternative, go with that. There's no benefit at this stage in setting up your own in-house mail server, document storage, data access, networking, etc.

Early on, unless required to by a compliance system, don't requireemployees to use company hardware. At small scale purchasing (especially pre-product market fit), provisioning and managing company hardware is a non-trivial effort (and cost!) that provides only marginal or rare real-world benefits.

It's perhaps painful to acknowledge, but properly securing your product and IT system is a considerable task, and unrealistic for a young startup to do exhaustively early on. I encourage you to be pragmatic and focus on securing your system from the most likely sources of breach or data theft: human error by your employees. It's far more likely your engineering team forgot to put authentication in front of an API, or somebody leaves their laptop unlocked at a coffee shop, than an attacker manages to man in the middle your data or hack into your cloud infrastructure using an exploit.

Even following best practices to minimize IT effort, you'll still have some IT tasks you cannot avoid, primarily around activating and deactivating user accounts and password recovery for employees. I encourage you to document for and train other coworkers, perhaps in HR, in how to do these tasks so they do not interrupt you or the engineering team on a regular basis.

## Security and Compliance

In this section, I will provide a brief overview of the subject of security and compliance for startups. You can and should put in the effort to find in-depth resources beyond this book on these topics.

### Auth Security Terminology

Especially with security, it's important to be precise and exact with language. Some definitions of commonly misused terms:

**Authentication, or AuthN**: Validating that a user or client is who they say they are. Your login system performs user authentication.

**Authorization, or AuthZ**: Validating that a user or client has permission to do what they're trying to do. Your role-based access control (RBAC) or permission system does authorization.

**2FA or MFA**: Two-factor authentication and multi-factor authentication is the process of authenticating with a service using more than one type of credential. This is typically done with a password (first factor) and some kind of proof-of-ownership, e.g., an emailed one-time password (proving you own the email), SMS (proving you own a phone number), or timed one-time-password (TOPT) (proving you own a device/ passkey). Note that due to the prevalence of SIM Porting attacks, where an attacker has the ability to intercept or reroute SMS, using SMS as a second factor is generally discouraged.


### Security At Startups

Startups are often defined by the extent to which they are resource-constrained. As a result, security posture and compliance are often the first things deprioritized on the to-do list, as they are less likely to represent an existential threat to the business than other pressing concerns. If you have no users or revenue, what is there for a hacker to steal?

Taking security into account can also become a drag on productivity or an expensive task, especially if your mission is to secure a system that already exists. But if you're starting from day one, you have the opportunity to make good decisions at the start that create a strong security posture with minimal additional cost.

Some ways to incorporate security at your startup that won't cost you much:

* Establish security as a priority in the mindset of your team in your onboarding and training materials.

* Enroll all engineers in onboarding and recurring basic security training things like the OWASP Top Ten or various gamified security training that take a few minutes a month to keep security top of mind.

* Rely on proven and well-maintained tools for anything related to authentication or authorization.

* Don't waste time building a login page yourself; in 2023 There's really no reason to. Tools like Auth0, SuperTokens, and AWS Cognito provide secure user signup, login, social login, forgotten password management, email authentication, two-factor authentication, and session management. Some of these tools also offer robust authorization systems. Dealing with auth is a substantial project; it's very complex and mistakes are expensive. There's no reason your startup needs to solve that problem.

* Don't be lazy about IT security. Regardless of whether you're using Dropbox, Box, Google Drive, SharePoint, etc., take a few minutes and set policies to help avoid human error, such as default sharing permissions to being internal only. Set up regular data-sharing reports and appoint an employee to do a quarterly audit of permissions settings on any particularly sensitive documents or spreadsheets.

* Use an enterprise password management solution, such as 1Password, and ensure all employees are using robust passwords for important tools. Similarly, use Single Sign-On (SSO) as often as possible and ensure your SSO provider is configured with high security (at least requiring Multi-Factor Authentication).

* Don't commit secrets in your codebase. Leverage a secure secret manager such as Google Cloud Secret Manager or AWS Secret Manager, and commit the name/location of a secret in code and resolve that name to a value in production, either at bootup time using a tool like Berglas or Whisper, or at runtime directly with the secret manager APIs.

### Compliance

Whether it's due to the industry you are in, the size of your business, or the nature of your customers, most startups need to comply with at least one formal compliance framework. If your users are in Europe, then you need to comply with GDPR. If you're taking in user data, it's wise to understand the CCPA. If you're working with enterprise clients, you'll be asked for your SOC 2 or ISO 27001 certification. In healthcare, you've got HIPAA, and if you're in payments, you've likely heard of PCI DSS.

For a startup, staying in compliance with any or all of these frameworks can be unacceptably expensive. Here are some tips for staying compliant and anticipating the cost:

* Don't try to get a compliance certificate at the last minute. Preparing for and conducting an audit such as for PCI DSS or SOC 2 from start to finish is a lengthy process, ranging from six to twelve months for most startups. Starting early and maintaining compliance is cheaper than starting late and doing rework.

* Use as much automation to enforce or provide evidence of compliance as possible. There is a thriving sector of SaaS companies who specialize in automating these compliance frameworks; companies like Vanta, Tugboat Logic, Secureframe, Laika, and Drata all have offerings that will reduce your time-to-certification and total cost significantly.

* If you're lucky enough to have a formal compliance person or department, lean into that relationship. The more proactive you can be in sharing plans with a compliance department, and the earlier you incorporate their feedback, the less costly and frustrating staying compliant will be.

# Conclusion: Measuring Success

You've put together a great hiring process, the team is happy, you're running sprints like a pro, and your architecture is withstanding the growing demands of the business. That feels good, but how do you know if it's enough? How do we measure our own success and performance as a technical leader or CTO?

One way to look at defining greatness in this role might be from a CFO's perspective: how efficiently can a CTO deploy an R&D budget and convert that into engineering and product output?

Or perhaps one might look at it from the CEO's viewpoint: how quickly can the team the CTO leads deliver on certain business objectives?

Or, given how important people leadership is to excelling in this role, we could view it through a humanistic lens: is your team doing their best work? After all, a great CTO's mission is to build an organizational culture that allows individual engineers to do their best work and achieve the impossible with technology.

Or, rather than trying to define a single objective, maybe the best definition of CTO greatness is a sum of all the skills that a CTO might exercise on a daily basis. Perhaps great is when you take the sum of architecture, performance management, vendor management, executive leadership, cultural contributions, public evangelism, mentorship, and DevOps, put it through a formula, and you end up with a number bigger than 42.

Try as we might, it seems that great leadership even great *technical* leadership isn't something we can precisely quantify or measure. Smart minds will struggle to agree on a common description of greatness, but we will all agree that the role is diverse and ever-changing, requiring constant learning and adaptation.

There are few universal truths in engineering leadership, but one of them is that becoming a good engineering leader is a never-ending journey of self-improvement, discovery, and growth. Proceeding down this path requires humility, willingness to make mistakes, and, above all, curiosity and a desire to learn.

I hope this handbook has been a helpful reference guide for you with the challenges you face on your leadership journey. The handbook covers many of the challenges that I myself have faced over the years as well as those of the many wonderful leaders I've had the pleasure of interacting with.

I've done my best to provide some structure on meeting those challenges, though every situation is unique, and ultimately the path you take is yours to devise and the results are yours to own.

At some point in life, one gets asked: What advice would you give to the younger version of yourself? This handbook is my answer to that question.

I hope it helps you in your journey to build powerful technology, motivated and empowered teams, and successful businesses, and, most of all, have fun and do some good for the world.


# Book References

*Getting Things Done* by David Allen

*Extreme Programming Explained* by Kent Beck

*Work Rules!* by Laszlo Bock

*How to Win Friends and Influence People* by Dale Carnegie

*Agile Estimating and Planning* by Mike Cohn

*Good to Great* by Jim Collins

*The 7 Habits of Highly Effective People* by Stephen Covey

*Domain-Driven Design* by Eric Evans

*Patterns of Enterprise Application Architecture* by Martin Fowler *High Output Management* by Andy Grove

*Scaling Up* by Verne Harnish

*The Hard ing About Hard ings* by Ben Horowitz

*Immunity to Change* by Robert Kegan

*The Phoenix Project* by Gene Kim

*The Five Dysfunctions of a Team* by Patrick Lencioni

*Managing Humans* by Michael Lopp

*Team of Teams* by Stanley McChrystal

*Escaping the Build Trap* by Melissa Perri

*Good Authority* by Jonathan Raymond

*Good Strategy/Bad Strategy* by Richard Rumelt

*Radical Candor* by Kim Scott

*The Art of Agile Development* by James Shore and Shane Warden

*Scrum: The Art of Doing Twice the Work in Half the Time* by Jeff Sutherland

*Extreme Ownership* by Jocko Willink and Leif Babin

## Digital References

**VSCode's Setting Files** (ctohb.com/vscode): https://code.visualstudio.com/docs/getstarted/settings

**Key to Gmail** (ctohb.com/keytogmail): https://techcrunch.com/2010/03/14/key-to-gmail

**Shit Umbrella** (ctohb.com/umbrella): https://medium.com/@ rajsarkar/word-of-the-month-shit-umbrella-33e3182a0f1b

**Liar's Paradox** (ctohb.com/liarsparadox): https://en.wikipedia.org/wiki/Liar\_paradox

**Gitlab Compensation Calculator** (ctohb.com/gitlabcompcalc): https://about.gitlab.com/handbook/total-rewards/compensation/

**Five Whys** (ctohb.com/5whys): https://en.wikipedia.org/wiki/Five\_whys

**Take the DORA DevOps Quick Check** (ctohb.com/dora): https://www.devops-research.com/quickcheck.html#questions

**Netflix Keeper Test** (ctohb.com/keeper): https://empowerment.ee/wp-content/uploads/2021/05/NETFLIX-%E2%80%93-THE-KEEPER- TEST.pdf

**Why GitLab Pays Local Rates** (ctohb.com/local): https://about.gitlab.com/blog/2019/02/28/why-we-pay-local-rates/

**What is the topgrading interview process?** (ctohb.com/interview): https://www.greenhouse.io/blog/ what-is-the-topgrading-interview-process

**Topgrading** (ctohb.com/topgrading): https://en.wikipedia.org/wiki/Topgrading

**Painting the Bridge** (ctohb.com/painting): https://www.goldengate.org/bridge/bridge-maintenance/painting-the-bridge/

**Dare to Lead: e BRAVING Inventory** (ctohb.com/braving): https://brenebrown.com/resources/the-braving-inventory/

**Root Cause Analysis Template** (ctohb.com/rca): https://docs.google.com/document/d/1GuRZgDpMVg\_Qf3sR7r8tZqRx6Re0oBrwIcnj-ekgJ60/ edit#

**Ship Small Diffs** (ctohb.com/diffs): https://blog.skyliner.io/ship-small-diffs-741308bec0d1

**GitHub Flow, Trunk-Based Development, and Code Reviews**(ctohb.com/branching): https://reviewpad.com/blog/ github-flow-trunk-based-development-and-code-reviews

**Ship/Show/Ask** (ctohb.com/ssa): https://martinfowler.com/articles/ship-show-ask.html

**Thoughtworks Technology Radar 27** (ctohb.com/techradar): https://www.thoughtworks.com/en-us/radar

**Feature Toggles (aka Feature Flags)** (ctohb.com/hodgson): https://martinfowler.com/articles/feature-toggles.html

**Multi-stage Builds** (ctohb.com/docker): https://docs.docker.com/build/building/multi-stage/

**Choose Boring Technology** (ctohb.com/boring): https://boringtechnology.club/

**Technology Radar** (ctohb.com/radar): https://www.thoughtworks.com/en-us/radar

**e Waterfall Model** (ctohb.com/waterfall): https://en.wikipedia.org/wiki/Waterfall\_model#History

**e Pragmatic Programmer** (ctohb.com/tpp): https://en.wikipedia.org/wiki/ e\_Pragmatic\_Programmer

**Rubber Duck Debugging** (ctohb.com/rdd): https://en.wikipedia.org/wiki/Rubber\_duck\_debugging

**FrequencyReducesDifficulty** (ctohb.com/fowler): https://martinfowler.com/bliki/FrequencyReducesDifficulty.html

**Figma Material Design** (ctohb.com/figma): https://www.figma.com/@materialdesign

**How to Design with the Atlassian Design System** (ctohb.com/design): https://atlassian.design/get-started/design

**Building Productive Teams** (ctohb.com/teams): https://docs.microsoft.com/en-us/DevOps/plan/building-productive-teams

**GitHub Compensation Calculator** (ctohb.com/calc): https://about.gitlab.com/handbook/total-rewards/compensation/

**Codeacademy Engineering Competencies** (ctohb.com/competencies): https://github.com/Codecademy/engineering-competencies

**e Multitasking Myth** (ctohb.com/myth): https://blog.codinghorror.com/the-multi-tasking-myth

**Acronyms Seriously Suck: Elon Musk** (ctohb.com/acronyms): https://gist.github.com/klaaspieter/12cd68f54bb71a3940eae5cdd4ea1764

**How We Work Without Meetings at Levels** (ctohb.com/async): https://medium.com/levelshealth/ how-we-work-without-meetings-at-levels-a6a525e21aa5

**Collaborate with kindness: Consider these etiquette tips in Slack** (ctohb.com/slack): https://slack.com/blog/collaboration/etiquette-tips-in-slack

**How to Use Skip-Level Meetings Effectively** (ctohb.com/skip): https://www.managementcenter.org/resources/skip-level-meeting-toolkit/

**From Founder to CTO** (ctohb.com/founder2cto): https://calv.info/founder-cto

**How to Prioritize the Developer Experience and Improve Output** (ctohb.com/dx): https://www.harness.io/blog/developer-experience



# Glossary

**Agile ceremony**: Agile ceremonies are meetings where a development team comes together at various stages during the development process for discussions on planning future work, communicating ongoing work or reviewing and reflecting on past work.

**Applicant Tracking System (ATS)**: An applicant tracking system (ATS) is software for recruiters and employers to track candidates throughout the recruiting and hiring process.

**Boy Scout Rule**: Leave things better than you found them. As applied to a technical team, whenever you work in an area of code, always make even a small improvement, maybe to tests, or documentation, or otherwise improve clarity, readability or maintainability.

**Brownfield development**: e opposite of greenfield development: working with existing legacy systems, often heavily impacted by tech debt. You're stuck with the high-level decisions that have been made in the past and you have limited flexibility for large change.

**Business Intelligence (BI)**: Business intelligence (BI) is software that ingests business data and presents it in user-friendly views such as reports, dashboards, charts and graphs.

**ClickOps**: ClickOps is the error-prone and time-consuming process of having people click-through various menu options in cloud providers websites, to select and configure the correct automated computing infrastructure.

**Containerization**: Containerization involves packaging software that contains all the necessary elements to run an application into a container environment. This allows organizations to run applications from anywherein a private datacenter, public cloud or even a personal laptop.

**Context switching**: Changing from one task to another. For engineers that means setting aside the problem being worked on and starting to work on another. The act of switching is generally time consuming and less efficient than working on one problem at a time.

**Direct report**: Direct reports are employees who report directly to someone who is above them in the organization chart, often a manager, supervisor, or team leader.

**Engineering Product and Design (EPD)**: e idea of combining together into a single department what traditionally has been three separate departments: Design, Product and Engineering. The order of the acronym is often changed, EDP, PDE.

**Greenfield solution**: Greenfield software development refers to development work in a new environment with minimal pre-existing legacy code and free choice on tools, patterns, and architecture.

**Horizon One/Two/Three**: Each horizon represents a different timescale. Horizon one is generally short term (days/weeks), two is medium (months) and three long term (years). Often used as a planning tool to ensure you're accommodating each horizon.

**Idempotent**: A technical operation is idempotent if subsequent executions of the operation do not change the output.

**Kaizen**: Kaizen is the philosophy of continuously improving all processes in an organization.

**Key Performance Indicator (KPI)**: KPIs are the critical quantifiable indicators of progress toward an intended result. Sometimes referred to as input metrics.

**Objectives and Key Results (OKRs)**: Objectives and key results is a goal-setting framework, originating at Intel in the 1970s, used by individuals, teams, and organizations to define measurable goals and track their outcomes.

**Pigeonhole principle**: Describes a circumstance where there is a fixed number of outcomes and a larger number of trials. If you flip a coin three times then at least one of heads or tails must come up twice.

**Product Requirements Document (PRD)**: A PRD is a document that gathers into one place the background, references, justification for and articulation of the requirements for a product.

**Reproducibility**: The ability to reproduce a given outcome on demand. Generally in software development it takes the form of a user pushes button X, then the application crashes. If pushing the button is a complete and reliable description of how to cause the application crash then this is a reproducible crash with understood reproduction steps.

**Request for Comment (RFC)**: A document that outlines an idea, philosophy, proposal or methodology that is intended to collect feedback and ultimately become a long-lived reference material.

**Root Cause Analysis (RCA)**: An approach, and generally a document, that attempts to dig below the superficial to truly understand why an event occurred. Generally used as an investigative tool, and then reference documentation, for why an incident occurred in a software project.

**SaaS Management Platform (SMP)**: A SMP provides a single location to review, manage, optimize and govern SaaS tools used across an organization.

**Service-Oriented Architecture (SOA)**: e phrase Service-Oriented Architecture (SOA) originated in the 1990s and is used to refer to some fairly specific technology choices. Nowadays, the phrase is used to more broadly describe a system where information moves between parts of the system over a network

**Standup meeting**: (aka Daily Scrum) A regular meeting as part of the scrum/agile ceremonies. Generally intended to be short, less than 30 minutes, to facilitate communication, updates, conflict resolution and decision making within a team.

**Straw Man Model**: A first draft proposition that can be put together rapidly with incomplete data. Often used as a starting place proposal with a team to accelerate the process of collecting feedback and getting to a solution.

**Synchronous/Asynchronous Workplace Culture**: e idea of an asynchronous workplace culture is that communication flows are encouraged to asynchronously, that is, without needing both sides of the communication to participate at the same time. For example, a written document facilitates asynchronous communication, the author need not be present when the readers consume the document. Asynchronous cultures de-emphasize meetings and emphasize written or recorded audio/video documentation.


# About the author

Zach Goldberg graduated from the University of Pennsylvania magna cum laude with a degree in Computer Science and Engineering. He's been the CTO of six startups including WiFast, Sticks and Brains, AutoLotto, Trellis Technologies, GrowFlow (acq. Dama Financial, 2022), and Towards Equilibrium Inc, as well as an Entrepreneur-in-Residence at Tencent and an Associate Product Manager at Google. After Dama acquired GrowFlow in 2022, Zach sat down and poured all of his experience into this book. Learn more about Zach's work at zachgoldberg.com.


# About the publisher

Founded in 2021 by Bryna Haynes, WorldChangers Media is a boutique publishing company focused on Ideas for Impact. We know that great books change lives, topple outdated paradigms, and build movements. Our commitment is to deliver superior-quality transformational nonfiction by, and for, the next generation of thought leaders.

Ready to write and publish your thought leadership book with us? Learn more at www.WorldChangers.Media.
