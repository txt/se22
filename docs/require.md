
  <a name=top><p>&nbsp;<hr>
  <p align=center>
  &nbsp;<a href="/README.md#top">home</a> &nbsp; | &nbsp;
  <a href="/docs/syllabus.md#top">syllabus</a> &nbsp; | &nbsp;
  <a href="https://docs.google.com/spreadsheets/d/1KuW-SH46KmFW0grEX2wT01jicUSew_5sr1QdGuSrweU/edit#gid=0">groups</a> &nbsp; | &nbsp;
  <a href="https://moodle-courses2223.wolfware.ncsu.edu/course/view.php?id=1771">moodle</a> &nbsp; | &nbsp;
  <a href="https://ncsu.hosted.panopto.com/Panopto/Pages/Sessions/List.aspx#folderID=%22389b8ebf-2f29-4c15-8231-aee9000e3f05%22">video</a> &nbsp; | &nbsp;
  <a href="/docs/review.md">review</a> &nbsp; | &nbsp;
  <a href="/LICENSE.md#top">&copy; 2022</a></p>
  <hr>
  <p align=center><a href="/README.md#top"><img  width=700 src="/etc/img/banner.png"></a></p>
  





Software Engineering is the:

+ process of the
+ design,
+ construction and
+ maintenance of
+ good enough
+ software,
+ given the available resources.

The last point means that we are always trading off
between what we want with what we need with what
we've got. Software engineers, therefore are the
people we look to:

+ Make and
+ justify
+ well-informed decisions
+ about trade-offs
+ in software engineering.

This, in turn means that at any time, software
engineering are aware of multiple possibilities and
the reasons why we should be doing one, and not the
others.

Parts of SE:

- requirements;
- architecture;
- process (life cycle);
- risk management;
- patterns, anti-patterns, bad smells;
- construction;
- verification;
- testing;
- maintenance, enhancement;
- programming languages and databases.

Requirements Engineering Defined
- The development and use of cost- effective technology for the elicitation, specification and analysis of the stakeholder requirements which are to
be met by software intensive systems.”


## REQUIREMENTS: BAD IDEA?
- Beware analysis paralysis
  - "The systems's through manufacture and in test. Has the customer sent the requirements spec yet"
- Fans of agile say
  - "Experience tells you more than excessive initial analysis" XXX PIC
- Assessing any of the following in a rigorous manner is an open research issue
  - Completeness
  - Comprehensibility 
  - Testability
  - Consistency
  - Unambiguity
  - Writeability
  -  Modifiability
  -  Implementability
- As to the real value of requirements....
  - Ideally, we look before we leap • Find best ways to do proceed
    - And we don’t get it wrong
  -  In reality, our initial peeks are wrong
    - Need extensive modification
    - If you want God to laugh, tell her your plans
  -  Recent research says requirements are an illusion
   - Cognitive phenomena including anchoring bias, fixation and confirmation bias
   - Misrepresenting decisions as requirements in situations where no real requirements are evident.
   - Misrepresenting an incidental feature as a requirement will reduce exploration of the design space, curtailing innovation
 - Nevertheless, sometime in your career,
   - you will be asked “how do we start?”
   - you will be asked (by an accountant) "has IT been delivered?" and they
     will want a precise definition of "IT"
   -  Welcome to the black art of requirements engineering

## GETTING IT WRONG
Examples to make you tremble 

Must have mobility access ramps

Must have external staircase

The Geneis crash landing
- NASA deep space sample return probe
  - collected a sample of solar wind
  -  returned it to Earth for analysis
  - Then crash landed in Utah in 2004
  -  Landing chute did not deploy
- Design error
  - Acceleration installed backwards
- Cost
  - $164 million for spacecraft development and science instruments
  - $45 million for operations and science data analysis.
- Mistake have been made worse by reuse
  - Same design in the (already launched) Stardust cometary sample return craft
  - Stardust landed successfully in 2006.


|What|What|Sadness|Observed| Cause|
|----|----|-------|--------|------|
|HMS Sheffield Exocet Missile Mis- classification| May 4, 1982| 30 deaths 257 lives at risk £23,200,000| Failure to intercept incoming missile. Ship loss| inadequate requirements; unnecessary simplicity|
| Y2K (\*) |  Jan 1, 2000 |  $100 Billion (usa)  | large-scale effort ;widespread problems | Short-sighted temporal requirements. Premature optimization. Arithmetic overflow |
|Virtual Case File|  2000- 2005 | $170,000,000 | entire program scrapped | •shifting requirements •scope creep •mismanagement |
|Vancouver Stock Exchange Rounding Error | 1984| unspecified , index off by 50%(!) | •inadequate research •inadequate testing •rounding error |
|NASA Mariner 1 | 1962|  A booster went off course during launch, resulting in the destruction | • Failure of a transcriber to notice an overbar in a written specification for the guidance program, resulting in the coding of an incorrect formula in
its FORTRAN software|

(\*) (*) A similar problem will occur in 2038 (the year 2038 problem), as many Unix-like systems calculate the time in seconds since 1 January 1970, and store this number as a 32-bit signed integer, for which the maximum possible value is 231 − 1 (2,147,483,647) seconds.[19]


## WHY PROJECTS FAIL 
Jim Johnson, The Standish Group International Project Leadership Conference, Chicago:

| What | Pecent%|
|----|---------:|
|1. Incomplete Requirements| 13.1 |
|2. Lack of user involvement 12.4|
|3. Lack of resources |10.6 |
|4. Unrealistic Expectations| 9.9|
|5. Lack of executive support| 9.3|
|6. Changing requirements| 8.7|
|7. Lack of planning| 8.1|
|8. Didn’t need it any longer|7.5|
|9. Lack of IT management| 6.2|
|10. Technology illiteracy| 4.3|

## Stakeholders:
Do all these folks want the same thing? (pic)w

“one” thing is “many” things, depending on stakeholder perspective.

Do all these folks want the same thing?

## WRITING REQUIREMENTS

- The official statement of what is required of the system developers
  - Should include both a definition and a specification of requirements
  - It is NOT a design document
  - As far as possible, it should set of WHAT the
    system should do rather than HOW it should do it
  - Also, it should have tests that can be applied incrementally
    -  See “commit partition”, below

### Requirements Document Structure

- Introduction
  - Describe need for the system and how it fits with business
objectives
- Glossary
  - Define technical terms used
- System models
  - Define models showing system components and
relationships
- Functional requirements definition
  - Describe the services to be provided
  - User stories go here
  - Add in notes for the commit partition here

- Non-functional requirements definition
  - Define constraints on the system and the development process • Add in notes for the commit partition here
- Constraints
  - What can't happen
  - What has to happen
-  System evolution
  -  Define fundamental assumptions on which the system is based
and anticipated changes
- Requirements specification
  - Detailed specification of functional requirements
- Appendices
  - System hardware platform description
  -  Database requirements (as an ER model perhaps)
- Index

## Utilities (pic)

Stakeholders have different “non-functional requirements”

- properties, or qualities, that the product must have • may be critical to the product’s success

- Time
  -  Transactions / sec
  -  Response time
  -  Time to complete an operation
- Space
  -  Main memory
  -  Auxiliary memory -  (Cache)
- Usability
  -  Training time
  -  Number of choices -  Mouse clicks
- Reliability
  -  Mean time to failure -  Downtime probability -  Failure rate
  -  Availability
- Robustness
  -  Time to recovery
  -  % of incidents leading to
  catastrophic failures
  -  Odds data corruption after failure
- Portability
  -  % of non-portable code
  -  RunsonNoperatingsystems -  Runs on desktop, tablet, mobile
- Etc

## Reviewing REquirements

How to "test" something that does not yet execute (pic)

- separate:
 - xfr (nonfunctionals)
 - stories (definition of user-level demos)
 - actual system requirements
 - things talked about but might do best in future systems.

One thing to look for: is there more than one design? Have those options been assessed? (pic)

Assessing options of criteria (pic)
- predictability (1), security (2), adaptability (3), coordinability (4), cooperativity (5), availability (6), integrity (7), modularity (8), or aggregability (9)

- Which is best? Dunno. Ask your stakeholders!
  - But add value to their discussions
  -  Give them considered conclusions to aid their decisions

## Checklist

- Validity
  - Does the system provide the functions which best support
   the customer’s needs? 
- Consistency
  - Are there any requirements conflicts? 
- Completeness
  - Are all functions required by the customer included? 
- Realism
  - Can the requirements be implemented given available budget and technology
- Verifiability
  - Is the requirement realistically testable?
- Comprehensibility
  - Is the requirement properly understood?
- Traceability
  - Is the origin of the requirement clearly stated?
- Adaptability
  - Can the requirement be changed without a large impact on other requirements?

V-diagram
