title: Bootstrapping Legacy
author:
    name: Emily Stamey
    twitter: elstamey
    url: http://elstamey.com
output: slideshow.html
theme: jdan/cleaver-retro
style: my-style.css
--


### Pulling Up Your Legacy App by Its Bootstraps
by Emily Stamey


-- slide-me

### Emily Stamey
Application Developer @ North Carolina State University

Twitter: [@elstamey](https://twitter.com/elstamey)

Blog: [elstamey.com](http://www.elstamey.com/)

-- slide-me

### Emily Stamey
Application Developer @ North Carolina State University

- Developing PHP applications since 1999.  

- Primarily supporting legacy applications.

- My department supports about 80 applications that support business processes of the College of Engineering

--


### Why Bootstrapping is important

- A lot of web development work involves supporting **legacy** applications

 <blockquote class="twitter-tweet" data-lang="en"><p lang="en" dir="ltr">&quot;It&#39;s harder to read code than to write it. This is why code reuse is so hard.&quot; - Joel Spolsky</p>&mdash; Programming Wisdom (@CodeWisdom) <a href="https://twitter.com/CodeWisdom/status/711858225528901633">March 21, 2016</a></blockquote>
 <script async src="//platform.twitter.com/widgets.js" charset="utf-8"></script>
    <!--- Supporting legacy is a challenge, but it is worthwhile to learn and master!  -->

- It is HARD to justify **refactoring**  

- **Bootstrapping** gives you flexibility to support your application



--



### Let's review some terminology

--



### Legacy 

Software that has been developed using older technologies and practices.  It can be difficult to replace because of its wide use.

Often a pejorative term, referencing a system as "legacy" often implies that the system is out of date or in need of replacement.

--



### Spaghetti Code

The relationships between the pieces of code are so tangled, it’s nearly impossible to add or change something without unpredictably breaking something somewhere else.

--



### Lasagna code

Lasagna code is code that has way too many layers.  

In Object Oriented programming, this means code that has many really small classes when a few slightly larger classes would have done the trick.

--



### Refactor

Technique for restructuring an existing body of code, altering its internal structure **without changing its external behavior**. A series of small behavior preserving transformations.

--



### Technical Debt

http://marketing.intracto.com/paying-technical-debt-how-to-rescue-legacy-code-through-refactoring?utm_content=26784583&utm_medium=social&utm_source=linkedin

<!-- background: #fefe79 -->
<!-- color: #b13ad0 -->
<!-- font: univers -->

--



### Bootstrapping

A business term referring to a self-starter; or a self-starting process that proceeds without any external input, or minimal input. 

In software this usually means, building onto an existing system for the purpose of improving the software with the least amount of sweat equity and development cost in the process.

-- example

### The Project: Scholarships

-- example

### The Project: Scholarships

- Engineering **Foundation** receives money from donors to give to **students**

- Students apply each year giving information about themselves

- **Donors** specify criteria/rules for students to receive money

    - The information in a student's application helps them match to scholarships

- **Selection Committee** selects Candidates to receive money

- **Scholarship Coordinator** reports these Recipients to Financial Aid

- **Financial Aid** awards the money

--



### How to Bootstrap

1. Survey Your Application

    Legacy projects have business value baked in, that you must preserve.

2. Organize the Work to be done

    Based on the bugs, new features, etc.  You have to balance needs vs. wants to deliver this product.

--



### Survey Your Application

1. Talk to customers and users of the application 

2. Study the codebase

3. Examine the new feature requests; investigate how they might be implemented

--



### Talk to Users 

- **don’t rely exclusively on developer (different concerns)**


- Is their process consistent with the current application?  

- Identify the pain points

- Do they have concerns with the current application?

-- example

### User Feedback: Scholarship Process


- **Process was inconsistent with the application**



    Selection Committee used a spreadsheet of scholarships and money available; Selected candidates were added to a spreadsheet Student ID and Amount and Term of award (high margin of error)  **PAIN POINT**

-- example

### User Feedback: Scholarship Concerns

**They didn’t trust that Selection Committee was choosing the best candidates**

- Problems using spreadsheets to assign awards

- The Scoring algorithm was not clear/effective

- NOT ALL MONEY WAS BEING AWARDED

- MONEY LEFT UN-GIVEN ⇒ ANGRY DONORS

- Students weren't always considered when they had multiple majors

--



### Study the codebase

- Talk to past/current developers

- Verify that key functionality does what everyone thinks it does

- Look for entanglements 

--



### Codebase of Scholarship

- Large App model
    - most of the functionality was here

    - SQL queries, only slightly dynamic

    - Functions weren’t single-purpose

    - No Bounded Contexts between Students, Selection, and Foundation

- Student data was a single row in table
   - Academic information wasn’t updated when it changed

<!-- background: #e4dadf -->
<!-- color: #774c43 -->
<!-- font: univers -->

--



### New Features

- Examine the new feature requests 

- Investigate how they might be implemented

--

### New Features: Scholarships

- Explicit criteria matching, excluded non-matching applicants

- Current student data, query their GPA, Major, etc at time of selection

- Students have multiple majors

<!-- background: #e4dadf -->
<!-- color: #774c43 -->
<!-- font: univers -->

--



### Get Organized...

--



### Organize the Work because...
- Bootstrapping grows FAST!

- Large projects wear people down

    - requires more people

    - developers and users must remain engaged in the process

--



### Organize the work because...


- Build Trust

    - Explain why this work is necessary

    - Be open about errors in the application.

--



### Organize the work because...

- It helps decide whether bootstrapping is a worthwhile investment.

- It helps decide whether this Legacy is worth saving.

--



### How to Organize the work

- Research shows all that can/should to be done

- Scope the work you are agreeing to do

- Set expectations

    - Customer has an open door to you 
        - add work from the side 
        - processes change

    - Keep the door open anyway!

-- example

### Plan Features for Scholarships

Divided the application based on first need in the process

1. Student Application

2. Funding

3. Selection

4. Reports for Funding and Scholarship Coordinator

-- example

--



### Mitigate Risk 

--



### Control Risk in Bootstrapping

- Version control

    Stabilize the code base and preserves history

- Development and Staging environments (w/ Fake data)

    **No more developing in production!!!!**

--



### Control Risk in Bootstrapping

- Write Tests to verify that you aren't breaking key functionality

- Involve Users to work through the process

    - constant feedback loop

--



### Bootstrap

- Initial Bootstrapping

- Ongoing Bootstrapping

Customize to the needs of your project.

-- example

### Bootstrap the application

- new code in `/src` alongside the `/app` directory

- Create a configuration file

    - manage DB connections, details in the app

    - specified paths to base_url, templates, etc
    
    - notices to show specific messages on the application

-- example

### Bootstrap the application

- Composer
    - autoloaded our namespaced code in `/src`
    - use of moneyphp for handling currency
    - Phinx for database migrations
    - Pimple containers
    - Illuminate database
    - Twig templates
    - Testing packages (Codeception, PHPUnit, Mockery)

-- example

### Bootstrap the application

- Acceptance tests stabilize functionality you need

    - added hooks for testing interfaces 

    - Codeception needed to view contents of the pages

- Unit and Functional tests for everything you build

-- example

### Bootstrap the application

Within CodeIgniter

- New Controllers for new functionality

- Bindings for CodeIgniter to find the new code

- New Twig templates beside the existing Views in `/app`

-- example

### Lessons Learned: Scholarship Summary

- SUCCESS!

    - Restored confidence in selection process!

    - Fewer awards were rejected!

    - More Scholarship Money was awarded than ever before!

**By May 2015:  Approximately $1,074,394 Awarded for 2015-16**

-- example
### Lessons Learned: Scholarship Summary

- Huge time investment (approx. 9 months to complete selection) With more work over the summer to complete.  

- Over time we lost participation because we have too many other projects needing attention.

- Tight deadlines with un-scoped work, we created technical debt that we would have to address in the next academic year

-- example

### Lessons Learned: Scholarship Summary

- **University is replacing it this year**

- We learned a lot of new techniques
    - bootstrap  
    - event sourcing
    - Domain-Driven Design
    - Command Query Response Segregation
    - managing projects
    - A LOT!

--





### QUESTIONS?

Emily Stamey
Application Developer @ North Carolina State University

Twitter: [@elstamey](https://twitter.com/elstamey)

Blog with Bootstrapping details: [elstamey.com](http://www.elstamey.com/)