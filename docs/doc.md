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
  



# Documentation 
## Tell me a story I can Understand
 (that makes me want to use your code)
  
 "I have made this letter longer since I did not have time to make it shorter" -- Blaise Pascal
  
- Documentation is **hard**
- [Doc generation tools](http://menzies.us/bnbad2/duo4.html) are the start, not end, of documentation
- Badges are “bling” (not documentation)

![image](https://user-images.githubusercontent.com/29195/130994411-6dffc04e-a8fd-442d-bff7-0e8ee702197b.png)

##   Example of good “why” documentation

Showcases succintly, 
- the key points
- what the thing is
- where to learn more?

e.g. [Starship](https://github.com/starship/starship)
  
![image](https://user-images.githubusercontent.com/29195/130994728-5d4c4c9d-1686-43c6-940a-6d1d475e9247.png)

## Some Documentation Generation tools'

  Lightweight (markdown):
  
  ![image](https://user-images.githubusercontent.com/29195/130996948-68d19e6e-c7ed-443f-a906-2e01e307f146.png)
  
  Heavyweight (latex):
  
  ![image](https://user-images.githubusercontent.com/29195/130997040-797ccb18-176e-41ec-9275-a53134343905.png)

(Aside: please take a moment to read the [sad, sad story about markdown's creator](https://en.wikipedia.org/wiki/Aaron_Swartz)).
  
 
 
Pdoc3: Python doc strings ⇒ markdown ⇒ web pages  
  
 <img width=600 src="https://user-images.githubusercontent.com/29195/130997647-d933884e-8e5c-4f0c-a367-6a5d69bb1df1.png">

 Trans-document documentation tools
- [Pandoc](https://pandoc.org/Pandoc)
  ![image](https://user-images.githubusercontent.com/29195/130997844-830d0381-48bb-484a-b0fb-9afb7dc358f0.png)

## So that's it? The Documenation Problem is Solved?
  
Not really
  
None of these tools solve the documentation problem
  
Kinds of doc (hint: "why not"; rarer than "why"; rarer than "how"; rarer than "what"):

- What : point description 
  - e.g. UML, 
  - e.g. what pdoc3 generates 
- How: common use cases
  - See [The scikit-learn doco](https://scikit-learn.org/stable/) (exploding with examples)
  - See [last third of “PCL”[(https://gigamonkeys.com/book/)
- Why: top-level motivation
  - See Meyer’s OO software construction [Chapter1](https://web.uettaxila.edu.pk/CMS/AUT2011/seSCbs/tutorial/Object%20Oriented%20Software%20Construction.pdf) says nothing about objects
  - See [“Data mining from scratch”](http://math.ecnu.edu.cn/~lfzhou/seminar/[Joel_Grus]_Data_Science_from_Scratch_First_Princ.pdf) (Joel Grus) 
- Why-not: choices within the design
  - Path not travelled

 For a sensational case study, read the original textbook on "C". 
  - [Chapter1](http://www.ccapitalia.net/descarga/docs/1978-ritchie-the-c-programming-language.pdf) is a work of art
 
  
## If you want to reap the benefits of good documentation 

Make the documents something reasonable 

(e.g. documentation ⇒ verification 
or documentation ⇒ code generation)

### “Why not” documentation
- e.g. Feature model: looks like “just” a pretty picture.
-  But look again: see the logic?  the constraints? the why nots
  
![image](https://user-images.githubusercontent.com/29195/130999315-28599041-7988-49a0-bd36-3af6fd8a245c.png)

- This model: 10 variables, 8 rules
- Linux kernel: 6,888 variables, 344000 rules

### “What” documentation: 
- e.g. State transition diagrams
- David Harel, Statecharts: A visual formalism for complex systems. Science of Computer Programming, 8(3):231-274, June 1987. 
10,100+ citations (!!!)
- Black dot = initial state
- Dashed lines: parallel work
- Words on arcs: transition guards
- Solid line: nested sub-state machines (and all transitions on super-states apply to sub-states)
  
  ![image](https://user-images.githubusercontent.com/29195/130999564-4965a203-83c0-46cb-b293-57a94a6d940d.png)

- Good for scriblling on white board: 
  - very good for small systems ( e.g. internal reasoning within one class )
- Good for reasoning about mission critical kernels on safety critical systems
  - Can reason over diagram to look for
    - Live locks: loops which never terminate
    - Dead locks: states we can never escape

![image](https://user-images.githubusercontent.com/29195/130999771-d6d4e927-fc0e-4cfe-8216-25c0bfaa1209.png)

### **“What”** documentation
- e.g. Entity-Relationship Diagrams
- Database design
  - Don’t document the code
  - Document the data it runs on
- Everything is tables, whose cells can be String, Number, Date, Blob (binary object), Null, etc...
  - But NOT a nested table
- If many of these things depends on many of those things
  - Add a relationship table in between
- A set of sanity checks for “bad” table design
  -  Store every datum once, and only once
  - Avoid, add/delete/update anomalies
- Many tools for auto-application generation (GUI screen 
Generation, ORMs like Entity Framework [C#], mapping to databases).


![image](https://user-images.githubusercontent.com/29195/131000060-bb703a24-2ad5-4375-a108-1bd52d166b62.png)

## Documentation ⇒  code generation
  
###  e.g. ER diagrams: screen painting tools

Interactive GUIs generated from database table design
  
  ![image](https://user-images.githubusercontent.com/29195/131000390-f043ca40-20f4-4592-946a-29b887c4a4d3.png)

  
### e.g. State transition diagrams
  
cross-compile to “C”
  
  ![image](https://user-images.githubusercontent.com/29195/131000444-08b270ac-977b-437b-8d7c-2bb6b5995fdd.png)

  ![image](https://user-images.githubusercontent.com/29195/131000462-fef5adcc-602c-4178-84ff-d8bc0c15e85c.png)

### e.g. Compartmental diagrams: Easy to code:

- _Flows_ change _stuff_ (and _stuff_ is called _Stocks_).
- _Stocks_ are real-valued variables , some entity that is 
accumulated over time by inflows and/or depleted by 
outflows.
 


 ![image](https://user-images.githubusercontent.com/29195/131000757-04597f42-c96f-40cc-804f-9876a16b00ca.png)

  ![image](https://user-images.githubusercontent.com/29195/131000808-af4e8634-baaf-47ba-a4b1-31c881d532f6.png)

- To code CM,
  - sum in + out_flows_ around each _stock_;
  - multiply that by the time tick dt
  - add the result back to the _stock_
  - e.g.  v.C += dt*(u.q - u.r) (u,v = before,now)

  ![image](https://user-images.githubusercontent.com/29195/131000841-b2ac37f9-3489-4342-be3e-a0c2c39fd850.png)

  ![image](https://user-images.githubusercontent.com/29195/131000861-5e207f38-0526-4e01-98da-372fabd3c1ea.png)

## Digression: A little trip into the land of UML

“What” documentation: 
UML = ER + procedures
- Unified modeling language
  
  ![image](https://user-images.githubusercontent.com/29195/131001293-3de8f7ed-1ce8-488b-b2fb-2e835a441715.png)

  ![image](https://user-images.githubusercontent.com/29195/131001314-f4ea547d-d6c5-4858-a7bc-9c6c76cb4e67.png)

Hints for writing class diagrams

- Don't add gets/setters to class methods
- If there is a relationship classX to classY, 
  - Don't add variables to X,Y. 
  - Instead connect them with a line and label the line.
  - E.g. Professor instructs student
- Also, consider [writing fewer classes](https://www.youtube.com/watch?v=o9pEzgHorH0)  (this one will just blow your mind).
  - e.g. Before: 10,000 LOC, 115 modules, 207 classes
    - After: Downsized to 135 LOC, 3 classes (to handle a particular application)
- Brainstorm with CRC cards
  - Class, responsibility, collaboration cards
    - Walk through specific scenarios
  - Hold the card to your chest and say “I update the X”
  - And when the responsibility feels wrong, pass it to another class

![image](https://user-images.githubusercontent.com/29195/131001997-5539a9f1-a395-4ab6-bf6e-6a432f397b76.png)

History has not been kind to UML
  
- UML = under-defined modeling language
  - Not enough semantics to support verification
- Marian Petre: "UML in practice" ICSE'13, 2013. http://oro.open.ac.uk/35805/
  - UML has been described by some as "the lingua franca of software engineering". Evidence from industry does not necessarily support such endorsements. How exactly is UML being used in industry — if it is? Interviews with 50 professional software engineers in 50 companies 


| | Number|
|--|------|
|  no UML	      |     35|
|selective	     |      11|
|auto-code gen	 |   3|
|retrofit	        |     1|
|wholehearted	   | 0|

  |Who uses what	  |     Number|
  |------|--------|
|Class diagrams	     |          7|
|Sequence diagrams 	 |      6|
|Activity diagrams	  |     6  |
|State machine diagram |   3|
|Use case diagrams	   |   1 |

  
- UML useful for 
  - A  'thought tool'
  - For communicating with stakeholders
  - For collaborative dialogs
  - As the starting point for adaptation (i.e., using a homegrown variant of the "real" notation)
- Two  ways to read Petre’14:
  - An indictment: after 20 years, UML is still mostly not used and not valued.
  - More hopefully,  parts of UML are used; the more we learn about which ones, where, why, and how, the better our chances of building something better.
