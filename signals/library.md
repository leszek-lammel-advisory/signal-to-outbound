# Signal library

30 buying signals in three levels. Each one says what it usually means, how long it stays fresh, whether it's a pitch or a touchpoint, how to find it with Clay and without, and an angle for the first message.

Angles are starting points, not templates. Replace every [bracket] with a real fact you found, or don't send the message.

The same list as a file for your AI: [library.csv](library.csv).

| Level | Signals |
|---|---|
| Industry level | [I1](#i1-a-regulation-with-a-deadline-applies-to-the-segment), [I2](#i2-a-vendor-announces-the-end-of-a-product-the-segment-relies-on), [I3](#i3-a-competitor-shuts-down-is-acquired-or-raises-prices), [I4](#i4-a-cost-or-market-shock-hits-the-segment), [I5](#i5-a-trade-fair-or-conference-the-segment-attends) |
| Account level | [A1](#a1-a-job-post-for-the-function-you-serve), [A2](#a2-a-job-post-that-names-a-tool-or-a-problem), [A3](#a3-the-first-hire-in-a-new-function), [A4](#a4-headcount-grew-20-or-more-in-6-months), [A5](#a5-a-funding-round), [A6](#a6-expansion-to-a-new-country-or-a-new-office), [A7](#a7-a-new-product-or-product-line-launched), [A8](#a8-an-acquisition-they-bought-someone-or-were-bought), [A9](#a9-a-tool-was-added-to-or-removed-from-their-stack), [A10](#a10-uses-a-competitor-or-a-complementary-tool), [A11](#a11-a-new-executive-joined-the-company-ceo-cro-cmo-cfo), [A12](#a12-layoffs-or-a-restructuring), [A13](#a13-an-award-ranking-or-certification), [A14](#a14-website-traffic-jumped-or-dropped), [A15](#a15-a-public-tender-or-request-for-proposals), [A16](#a16-public-complaints-about-their-current-vendor) |
| Prospect level | [P1](#p1-new-in-the-role-first-90-days), [P2](#p2-a-past-champion-changed-companies), [P3](#p3-promoted-internally), [P4](#p4-posted-about-the-problem-you-solve), [P5](#p5-engaged-with-posts-about-the-problem-or-a-competitor), [P6](#p6-spoke-at-an-event-on-a-podcast-or-in-a-webinar), [P7](#p7-visited-your-website), [P8](#p8-engaged-with-your-own-content), [P9](#p9-asked-for-help-in-a-community-or-forum) |

## Industry level

Something hits a whole segment at once. Use it to choose the segment, then rank companies inside it by account signals.

### I1. A regulation with a deadline applies to the segment

- **Type:** trigger. **Fresh:** From announcement to the deadline; strongest 3 to 12 months before it
- **What it usually means:** Every company in scope must change a process, document something or buy a tool by a fixed date. Many start late.
- **Good for sellers of:** Compliance and security software, finance and HR tools, consultancies
- **Usually a:** pitch
- **Find it with Clay:** Company search by the industries, sizes and countries the rule covers. Then a Custom data point: 'Does this company say publicly that it is preparing for [regulation]? Quote the source.'
- **Find it without Clay:** The regulator's scope definition, industry association pages, news. Ask your AI who is in scope and by when.
- **Message angle:** The [regulation] deadline is [date] for companies like yours. Who owns getting ready for it?

### I2. A vendor announces the end of a product the segment relies on

- **Type:** trigger. **Fresh:** From the announcement to the end-of-support date
- **What it usually means:** Every user has to migrate. They will compare alternatives anyway.
- **Good for sellers of:** Direct alternatives, migration and implementation services
- **Usually a:** pitch
- **Find it with Clay:** Company search with technographics.any(product = "[product]") or vendor = "[vendor]".
- **Find it without Clay:** The vendor's announcement, then BuiltWith or Wappalyzer, case studies and job posts that name the product.
- **Message angle:** [Product] stops being supported on [date]. Have you picked what replaces it?

### I3. A competitor shuts down, is acquired or raises prices

- **Type:** trigger. **Fresh:** 0 to 90 days after the announcement
- **What it usually means:** Its customers reconsider whether to stay. Some are already unhappy.
- **Good for sellers of:** Direct alternatives
- **Usually a:** pitch
- **Find it with Clay:** Company search with technographics.any(vendor = "[competitor]").
- **Find it without Clay:** News, the competitor's own customer logos and case studies, G2 and Reddit threads about the change.
- **Message angle:** Saw [competitor] [changed pricing / was acquired]. Are you staying, or looking at options?

### I4. A cost or market shock hits the segment

- **Type:** leading. **Fresh:** 0 to 90 days
- **What it usually means:** Budgets tighten and anything that saves money or time gets a hearing. Growth projects get paused.
- **Good for sellers of:** Products that cut cost or replace headcount
- **Usually a:** touchpoint
- **Find it with Clay:** Company search by industry and region, then Recent News per company to see who is affected.
- **Find it without Clay:** Industry news and association reports.
- **Message angle:** How is [shock] showing up in your numbers so far?

### I5. A trade fair or conference the segment attends

- **Type:** trigger. **Fresh:** 30 days before to 14 days after the event
- **What it usually means:** People are travelling, meeting suppliers and open to conversations. Exhibitors have spent money and need it to pay off.
- **Good for sellers of:** Anyone selling to exhibitors or attendees, especially products for sales and marketing teams
- **Usually a:** touchpoint
- **Find it with Clay:** Paste the exhibitor list into your chat, then a Custom data point per company: 'What is this company presenting at [event]?'
- **Find it without Clay:** The exhibitor directory on the event website. Most list company, stand and category.
- **Message angle:** Are you at [event] next week? Happy to stop by your stand at [hall].

## Account level

Something changes at one company. Find the company first, then the person who owns the problem the signal points to.

### A1. A job post for the function you serve

- **Type:** leading. **Fresh:** 0 to 30 days full, 31 to 90 partial, over 180 expired. Drop it once the role is filled.
- **What it usually means:** They are investing in that area, and soon there will be a new person who needs onboarding, tools and process.
- **Good for sellers of:** Tools, training and services for that team
- **Usually a:** pitch
- **Find it with Clay:** Company search: jobs.exists(job_title is_similar_to ("[role]") and job_posted_date >= today() - interval 30 days and job_still_open = true). Then verify with a Custom data point that asks for location, date and link.
- **Find it without Clay:** Job boards that show dates (in Germany: arbeitnow.com), then the company's own careers page. For companies on Ashby, https://api.ashbyhq.com/posting-api/job-board/[company] lists every open job with its publish date. Search engines often ignore site: searches on job platforms.
- **Message angle:** Saw you're hiring a [role] for [market]. [What that usually means]. Who's [owning that part]?

### A2. A job post that names a tool or a problem

- **Type:** leading. **Fresh:** 0 to 30 days full, 31 to 90 partial
- **What it usually means:** The description shows their stack, their pain or the project the hire is for. Recruiters write it in plain words.
- **Good for sellers of:** Anything the job description names: a tool you replace, a process you fix
- **Usually a:** pitch
- **Find it with Clay:** Company search: jobs.exists(job_description contains ("[tool or phrase]") and job_posted_date >= today() - interval 30 days). Add company_size and industry filters: without them this returns the biggest employers first (SAP, Bosch). Read the posting for tools they already use: a post that names a competitor needs a different message.
- **Find it without Clay:** Search the phrase on job boards: "[tool]" "[role]" site:jobs.ashbyhq.com, or ask your AI to read the careers page.
- **Message angle:** Your [role] posting mentions [project]. Are you building that in-house or with a partner?

### A3. The first hire in a new function

- **Type:** trigger. **Fresh:** 0 to 60 days
- **What it usually means:** They are building the function from zero. No tools, no process, and the new person wants quick wins.
- **Good for sellers of:** Tools and services a new team needs on day one
- **Usually a:** pitch
- **Find it with Clay:** Company search with a job post for the role, then a Custom data point: 'Does this company already employ anyone in [function]? Is this the first hire?'
- **Find it without Clay:** LinkedIn people search at the company for the function. If nobody holds it, it's a first hire.
- **Message angle:** Looks like [role] is a new team at [company]. What's the first thing they need to get running?

### A4. Headcount grew 20% or more in 6 months

- **Type:** trigger. **Fresh:** 0 to 90 days full, 91 to 180 partial
- **What it usually means:** Processes that worked at the old size are breaking: onboarding, tooling, reporting, management.
- **Good for sellers of:** Ops, HR, onboarding, IT and infrastructure tools
- **Usually a:** touchpoint
- **Find it with Clay:** Company search: employee_growth_6mo >= 1.2 (1.2 means +20%). Or the Headcount Growth data point on your own list.
- **Find it without Clay:** The employee count on the company's LinkedIn page over time, or the number of open jobs on its careers page.
- **Message angle:** You've grown about [x]% since [month]. What broke first?

### A5. A funding round

- **Type:** trigger. **Fresh:** 0 to 90 days full, 91 to 180 partial, over 365 expired
- **What it usually means:** Money plus a plan to hire and grow. On its own it's weak: everyone writes to funded companies. Combine it with another signal.
- **Good for sellers of:** Hiring, scaling and growth tools; recruiting; agencies
- **Usually a:** touchpoint
- **Find it with Clay:** On your own list: the Latest Funding data point. In a search, combine with a job post or headcount growth.
- **Find it without Clay:** Crunchbase, Dealroom, Tech.eu, EU-Startups, TechCrunch, or ask your AI: 'Series A rounds in German B2B software announced in the last 60 days'.
- **Message angle:** Saw the [round] on [date]. With [plan from the announcement], how are you handling [problem you solve]?

### A6. Expansion to a new country or a new office

- **Type:** trigger. **Fresh:** 0 to 90 days full, 91 to 180 partial
- **What it usually means:** A new market means a new go-to-market: hiring locally, localising, finding first customers, setting up legal and payroll.
- **Good for sellers of:** Market entry, localisation, local hiring, payroll and legal, outbound agencies
- **Usually a:** pitch
- **Find it with Clay:** Company search: jobs.exists(location contains "[new country]" and job_posted_date >= today() - interval 60 days) plus a headquarters country that is not the new one and a company_size filter, then a Custom data point: 'Has this company announced expansion into [country]? Is it new for them? Link the source.' Without a size filter this returns big multinationals first. Expect many to fail: companies that have been in the country for years, and roles copied across many countries.
- **Find it without Clay:** Press releases, job posts in the new country, new office addresses on the website.
- **Message angle:** Saw you're hiring your first people in [country]. Who's building the pipeline there?

### A7. A new product or product line launched

- **Type:** trigger. **Fresh:** 0 to 60 days
- **What it usually means:** They need demand for something new, fast. The product and marketing teams are under pressure to show traction.
- **Good for sellers of:** Demand generation, marketing services, analytics, sales enablement
- **Usually a:** touchpoint
- **Find it with Clay:** The Recent News data point, or a Custom data point: 'What did this company launch in the last 60 days? Link it.'
- **Find it without Clay:** The company's changelog, blog, press page, Product Hunt.
- **Message angle:** Saw [product] went live in [month]. Who are you trying to get it in front of first?

### A8. An acquisition: they bought someone or were bought

- **Type:** trigger. **Fresh:** 0 to 90 days
- **What it usually means:** Two sets of systems, teams and tools have to become one. Contracts get reviewed.
- **Good for sellers of:** Integration, consolidation, data migration, change management
- **Usually a:** pitch
- **Find it with Clay:** The Recent News data point, or a Custom data point: 'Has this company acquired or been acquired in the last 90 days?'
- **Find it without Clay:** Press releases and business news.
- **Message angle:** Congrats on bringing [company] in. Are you merging [system] or running both for now?

### A9. A tool was added to or removed from their stack

- **Type:** leading. **Fresh:** 0 to 30 days full, 31 to 90 partial
- **What it usually means:** They just changed how they work in that area. Adjacent tools are next.
- **Good for sellers of:** Tools that integrate with or replace the one that changed
- **Usually a:** touchpoint
- **Find it with Clay:** The Tech Stack data point, or company search with technographics.any(vendor = "[tool]").
- **Find it without Clay:** BuiltWith, Wappalyzer, job posts that mention the tool, the company's integration pages.
- **Message angle:** Saw you moved to [tool]. Has [adjacent process] moved with it?

### A10. Uses a competitor or a complementary tool

- **Type:** structural. **Fresh:** No decay. It is fit, not timing.
- **What it usually means:** They already pay for this category, so they understand the problem. It tells you who, not when.
- **Good for sellers of:** Competitors (displacement) and add-ons (integration)
- **Usually a:** touchpoint
- **Find it with Clay:** Company search with technographics.any(vendor = "[tool]"). Tested: technographics.any(vendor = "HubSpot") works.
- **Find it without Clay:** BuiltWith or Wappalyzer, the competitor's customer logos and case studies.
- **Message angle:** Combine with a timing signal before writing. Alone: 'How is [tool] working for [use case]?'

### A11. A new executive joined the company (CEO, CRO, CMO, CFO)

- **Type:** trigger. **Fresh:** 0 to 60 days full, 61 to 90 partial
- **What it usually means:** New leaders review vendors, set new goals and want early wins. Budgets get reshuffled in the first 90 days.
- **Good for sellers of:** Anything in the new leader's area
- **Usually a:** pitch
- **Find it with Clay:** Company search: people.exists(is_current = true and job_title is_similar_to ("[title]") and start_date >= today() - interval 3 months). Dates are by month.
- **Find it without Clay:** LinkedIn 'started a new position' posts, press releases about the appointment.
- **Message angle:** See the prospect-level version (P1) for the message to the leader.

### A12. Layoffs or a restructuring

- **Type:** leading. **Fresh:** 0 to 90 days
- **What it usually means:** Fewer people have to do the same work. Cost cuts, but also openness to tools that replace manual work. Be careful with tone.
- **Good for sellers of:** Automation and efficiency tools, outsourcing
- **Usually a:** touchpoint
- **Find it with Clay:** The Headcount Growth data point (a negative number), or the Recent News data point.
- **Find it without Clay:** News, layoff trackers, LinkedIn posts from affected employees.
- **Message angle:** Avoid mentioning the layoff. Lead with the workload: 'How is [team] covering [work] right now?'

### A13. An award, ranking or certification

- **Type:** leading. **Fresh:** 0 to 180 days full, 181 to 365 partial
- **What it usually means:** They are proud and visible, and often about to grow. A certification such as ISO 27001 also tells you about their process maturity.
- **Good for sellers of:** Mostly a reason to talk; a pitch if you sell to certified or fast-growing companies
- **Usually a:** touchpoint
- **Find it with Clay:** A Custom data point: 'Has this company won an award, made a ranking or earned a certification in the last 6 months? Link it.'
- **Find it without Clay:** Ranking lists (for example growth rankings in trade press), certification announcements on LinkedIn.
- **Message angle:** Saw you made [list]. What's the next bottleneck at that growth rate?

### A14. Website traffic jumped or dropped

- **Type:** leading. **Fresh:** 0 to 30 days full, 31 to 90 partial
- **What it usually means:** A jump means a campaign or a launch is working; a drop means something broke (search ranking, a migration, demand).
- **Good for sellers of:** SEO, web, conversion and analytics
- **Usually a:** touchpoint
- **Find it with Clay:** The Website Traffic data point on your list.
- **Find it without Clay:** Similarweb's free view, or ask your AI to compare with last quarter if it can see traffic data.
- **Message angle:** Looks like traffic to [site] changed a lot since [month]. Is that planned?

### A15. A public tender or request for proposals

- **Type:** trigger. **Fresh:** Until the submission deadline
- **What it usually means:** They have budget, a scope and a date. This is the most explicit buying signal there is.
- **Good for sellers of:** Anyone selling to the public sector or to companies that tender
- **Usually a:** pitch
- **Find it with Clay:** Not a Clay search. Find the tender first, then use Clay to find the people at the buying organisation.
- **Find it without Clay:** TED (ted.europa.eu) for the EU and national procurement portals. Ask your AI to search them by category code or keyword.
- **Message angle:** Saw the tender for [scope], closing [date]. Are you open to a short call on [one requirement] before then?

### A16. Public complaints about their current vendor

- **Type:** leading. **Fresh:** 0 to 90 days
- **What it usually means:** They are unhappy with what they use now. The complaint tells you exactly which pain to lead with.
- **Good for sellers of:** Direct alternatives
- **Usually a:** pitch
- **Find it with Clay:** A Custom data point: 'Has anyone at this company publicly complained about [vendor] in the last 90 days (G2, Reddit, LinkedIn)? Quote and link it.'
- **Find it without Clay:** G2, Capterra, Trustpilot, Reddit, LinkedIn posts. Search "[vendor]" with words like 'switching', 'alternative', 'frustrated'.
- **Message angle:** Quote the pain, not the person: 'Teams moving off [vendor] usually mention [pain]. Is that on your list too?'

## Prospect level

Something changes for one person. Write to that person about what changed for them.

### P1. New in the role (first 90 days)

- **Type:** trigger. **Fresh:** 0 to 60 days full, 61 to 90 partial, low after that
- **What it usually means:** They are assessing what they inherited, setting a plan and have room to change vendors. The first 90 days are when they decide.
- **Good for sellers of:** Anything in their area of responsibility
- **Usually a:** pitch
- **Find it with Clay:** Contact search at your target companies: experiences.any(is_current = true and job_title is_similar_to ("[title]") and start_date >= today() - interval 3 months). Or company search with people.exists(...) as in A11.
- **Find it without Clay:** LinkedIn Sales Navigator's 'changed jobs in the past 90 days' filter, LinkedIn 'started a new position' posts.
- **Message angle:** You started as [role] in [month]. What did you inherit that you'd change first?

### P2. A past champion changed companies

- **Type:** trigger. **Fresh:** 0 to 90 days after the move
- **What it usually means:** Someone who used or bought your product before now has a new team, a new budget and a reason to bring tools they trust.
- **Good for sellers of:** Anyone with past customers or users
- **Usually a:** pitch
- **Find it with Clay:** Contact search with your customers' domains, companyTenure "past", and experiences.any(is_current = true and start_date >= today() - interval 3 months) to see who just started somewhere new.
- **Find it without Clay:** LinkedIn: check the profiles of your past users and buyers. Sales Navigator can save them as leads and alert you on job changes.
- **Message angle:** Congrats on the move to [company]. Want to set [product] up there the way you had it at [old company]?

### P3. Promoted internally

- **Type:** trigger. **Fresh:** 0 to 60 days
- **What it usually means:** Bigger scope, new team, and a mandate to show results at the new level.
- **Good for sellers of:** Tools and services for the bigger scope
- **Usually a:** touchpoint
- **Find it with Clay:** Contact search at your target companies: experiences.any(is_current = true and job_title is_similar_to ("[new title]") and start_date >= today() - interval 3 months). Then check that the previous role was at the same company.
- **Find it without Clay:** LinkedIn profiles: a new title at the same company.
- **Message angle:** Congrats on taking over [scope]. What's the first thing you want to fix?

### P4. Posted about the problem you solve

- **Type:** leading. **Fresh:** 0 to 14 days full, 15 to 30 partial, over 60 expired
- **What it usually means:** They are thinking about it right now, in public, in their own words. Use their words.
- **Good for sellers of:** Anything that solves the problem they described
- **Usually a:** pitch
- **Find it with Clay:** The Find Thought Leadership contact data point, or a Custom contact data point: 'Has this person posted about [topic] in the last 30 days? Quote and link the post.'
- **Find it without Clay:** LinkedIn search for posts with the topic, filtered to the last week. Ask your AI to search '[topic]' site:linkedin.com/posts.
- **Message angle:** Your post on [topic] last week stuck with me, especially [their point]. How are you handling [specific part] today?

### P5. Engaged with posts about the problem or a competitor

- **Type:** leading. **Fresh:** 0 to 14 days
- **What it usually means:** They are following the topic. Weaker than writing a post, but there are many more of them.
- **Good for sellers of:** Anything in that topic area
- **Usually a:** touchpoint
- **Find it with Clay:** Collect the people who liked or commented on a relevant post, then use Clay to find their company and check fit.
- **Find it without Clay:** Open the post and read the reactions and comments. Several tools export the people who engaged with a post.
- **Message angle:** Saw you weighed in on [author]'s post about [topic]. Where do you land on [question from the post]?

### P6. Spoke at an event, on a podcast or in a webinar

- **Type:** leading. **Fresh:** 0 to 60 days
- **What it usually means:** They have a public point of view and like talking about it. Referencing it shows you listened.
- **Good for sellers of:** Anything their talk was about
- **Usually a:** touchpoint
- **Find it with Clay:** The Find Thought Leadership contact data point, or a Custom contact data point: 'Has this person spoken at an event or on a podcast in the last 60 days? Link it.'
- **Find it without Clay:** Event agendas, podcast directories, YouTube. Ask your AI to search '[name] podcast' or '[name] [event]'.
- **Message angle:** Heard your point on [podcast] about [topic]. Does that also hold for [related question]?

### P7. Visited your website

- **Type:** leading. **Fresh:** 0 to 7 days full, 8 to 30 partial
- **What it usually means:** They looked at you. Which pages matter: pricing and case studies mean more than one blog post.
- **Good for sellers of:** You, the owner of the website
- **Usually a:** touchpoint
- **Find it with Clay:** Send website visitor data into a Clay table (a webhook) and research the company there. The connector doesn't read visitor data.
- **Find it without Clay:** Website visitor identification tools (for example RB2B, Dealfront, Snitcher) or your analytics. Be careful with privacy rules in the EU.
- **Message angle:** Never say you saw them on your site. Lead with the topic of the page they read.

### P8. Engaged with your own content

- **Type:** leading. **Fresh:** 0 to 14 days
- **What it usually means:** They know who you are. A cold message becomes a warm one.
- **Good for sellers of:** You
- **Usually a:** touchpoint
- **Find it with Clay:** Export the people who engaged with your posts, then use Clay to check fit and find their company.
- **Find it without Clay:** Your LinkedIn post analytics and company page followers.
- **Message angle:** Thanks for [reacting to / commenting on] the post on [topic]. Curious how [topic] looks at [company]?

### P9. Asked for help in a community or forum

- **Type:** trigger. **Fresh:** 0 to 14 days
- **What it usually means:** They have the problem right now and they are looking for answers.
- **Good for sellers of:** Anything that answers their question
- **Usually a:** pitch
- **Find it with Clay:** Not a Clay search. Find the question first, then use Clay to find the person and their company.
- **Find it without Clay:** Reddit, Slack and Discord communities, LinkedIn groups, Stack Overflow. Search the problem in their words.
- **Message angle:** Answer the question in the community first. Then: 'Saw your question about [problem]. Did you solve it?'
