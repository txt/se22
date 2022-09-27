
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
  

# Requirements Engineering
  
  ![image](https://user-images.githubusercontent.com/29195/192362532-73ba977b-1a21-4991-a974-230df1df38cb.png)


 

Requirements Engineering Defined
- The development and use of cost- effective technology for the elicitation, specification and analysis of the stakeholder requirements which are to
be met by software intensive systems.”


## REQUIREMENTS: BAD IDEA?
  
![image](https://user-images.githubusercontent.com/29195/192362600-70599602-df29-4e9e-9429-db1d39d74844.png)

  
- Beware analysis paralysis
  - "The systems's through manufacture and in test. Has the customer sent the requirements spec yet"
- Fans of agile say
  - "Experience tells you more than excessive initial analysis"  
  
![image](https://user-images.githubusercontent.com/29195/192362659-127da7d1-c4b2-4f20-9bd7-6ed6190d914d.png)

<img align=right width=400 src="https://user-images.githubusercontent.com/29195/192362693-6ea2ffd1-4981-4bbe-8412-aaf32e541000.png">

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
  
![image](https://user-images.githubusercontent.com/29195/192362807-1c73a161-894e-4df3-b299-9b4040cb57c7.png)

Must have external staircase

![image](https://user-images.githubusercontent.com/29195/192362855-12b4888c-31a8-41b9-beca-826ec1d4af55.png)

<img align=right width=300 src="https://user-images.githubusercontent.com/29195/192362905-71a0312a-be01-49fd-9c9e-7e2505ac86d2.png">

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
|NASA Mariner 1 | 1962|  A booster went off course during launch, resulting in the destruction | • Failure of a transcriber to notice an overbar in a written specification for the guidance program, resulting in the coding of an incorrect formula in its FORTRAN software|

(\*) (*) A similar problem will occur in 2038 (the year 2038 problem), as many Unix-like systems calculate the time in seconds since 1 January 1970, and store this number as a 32-bit signed integer, for which the maximum possible value is 231 − 1 (2,147,483,647) seconds.[19]


## WHY PROJECTS FAIL 
Jim Johnson, The Standish Group International Project Leadership Conference, Chicago:

| What | Pecent%|
|----|---------:|
|1. Incomplete Requirements| 13.1 |
|2. Lack of user involvement |12.4|
|3. Lack of resources |10.6 |
|4. Unrealistic Expectations| 9.9|
|5. Lack of executive support| 9.3|
|6. Changing requirements| 8.7|
|7. Lack of planning| 8.1|
|8. Didn’t need it any longer|7.5|
|9. Lack of IT management| 6.2|
|10. Technology illiteracy| 4.3|

## Stakeholders:
Do all these folks want the same thing? 

“one” thing is “many” things, depending on stakeholder perspective.

![image](https://user-images.githubusercontent.com/29195/192363050-f2a2b95b-008e-492d-8950-0ee6afb66398.png)

  
Do all these folks want the same thing?
  
![image](https://user-images.githubusercontent.com/29195/192363104-7234e507-b622-4953-ac05-74982fb948b7.png)
  
![image](https://user-images.githubusercontent.com/29195/192363137-ddda7f3b-d0a9-4c4b-9e0c-ee211d3804c1.png)

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

## Utilities 

Stakeholders have different “non-functional requirements”
![image](https://user-images.githubusercontent.com/29195/192363236-44801242-d8de-4e38-aabe-11363fd41593.png)


- properties, or qualities, that the product must have • may be critical to the product’s success



  |Quality attribute|	Key interest|
|-----------------|-------------|
|Availability|	Can I use the system when and where I need to?|
|Conformance to standards |	Does the system comply with all applicable standards for functionality, safety, communication, certification, and interfaces?|
|Efficiency	|Does the system use computer resources economically?|
|Installability|	Can I easily install, uninstall, and reinstall the system and upgrades?|
|Integrity	|Does the system protect against data inaccuracy, corruption, and loss?|
|Interoperability	|Does the system connect well with others to exchange data and services?|
|Maintainability	|Can developers easily modify, correct, and enhance the system?|
|Performance|Does the system respond sufficiently quickly to user actions and external events?|
|Portability|	Can the system be migrated to different platforms easily?|
|Reliability|	Does the system run when it’s supposed to without failing?|
|Reusability	|Can developers reuse portions of the system in other products?|
|Robustness|	Does the system respond sensibly to erroneous inputs and unexpected operating conditions?|
|Safety|Does the system protect users from harm and property from damage?|
|Scalability	|Can the system easily expand to accommodate more users, data, or transactions?|
|Security|	Does the system protect against malware attacks, intruders, unauthorized users, and data theft?|
|Usability	|Can users easily learn how to use the system to accomplish their tasks?|
|Verifiability	|Can testers determine whether the software was implemented correctly?|


<img src="https://user-images.githubusercontent.com/29195/192363287-827dd70c-cce0-4beb-a2a8-16c595ce3ddc.png" width=7-- align=right>

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
  
Column effects row
 - optimizing for effeciency (col2) hurts lots of things (row3 to row8)
 - reliabillity (col8) helps avialbility (row1) 
 - availability (col1) helps maintainability (row6) and reliability (row8)
   - but maintainability (col6) says nothing about a availabilty (row1)
 - maintainability hurts portability (in this project)
   - but portability does nothing to maintainability (no, I don't know why either)
  
![image](https://user-images.githubusercontent.com/29195/192589531-be8abcb9-2a2a-4980-8ccb-c0ace4ef471d.png)

 (Note that the  rules are only approximate and may not hold for specific projects.)
  
## Reviewing Requirements

How to "test" something that does not yet execute (pic)

- separate:
 - xfr (nonfunctionals)
 - stories (definition of user-level demos)
 - actual system requirements
 - things talked about but might do best in future systems.

![image](https://user-images.githubusercontent.com/29195/192363418-67264122-7cd3-478c-bbae-d752faf6c9bc.png)

  
One thing to look for: is there more than one design? Have those options been assessed? (pic)

Assessing options of criteria (pic)
- predictability (1), security (2), adaptability (3), coordinability (4), cooperativity (5), availability (6), integrity (7), modularity (8), or aggregability (9)

![image](https://user-images.githubusercontent.com/29195/192364055-dae1f823-db5d-4fa9-8e29-df308c166a9e.png)
  
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
  
  ![image](https://user-images.githubusercontent.com/29195/192364416-23531ee9-2141-4db7-aac0-cb17ed9ba3da.png)

## Development models

  Waterfall (how to do it. 1970s)
  
  ![image](https://user-images.githubusercontent.com/29195/192364610-488e0657-d619-4e51-912e-8719c9c03912.png)
  
Spiral (how to do it. 1980s.
  
  ![image](https://user-images.githubusercontent.com/29195/192364739-e53e2b5a-74d7-479e-8c2b-f0ef778d9cff.png)

Agile (2000's)

![image](https://user-images.githubusercontent.com/29195/192362659-127da7d1-c4b2-4f20-9bd7-6ed6190d914d.png)

Now? Hard to say. So much diversity. 
 -  Average tarining for an SE person (less than 2 years) so much adapation of SE to the masses that develop it
 - Lots more component based thing (so not much design as look-it-up in the catalog)
 - Tiny buisness functions (serverless) which keep changing,  built on lots of cloud resources?
  
![image](https://user-images.githubusercontent.com/29195/192365914-5ea0e361-3309-4545-be4b-07993fd3c4af.png)
   

  
