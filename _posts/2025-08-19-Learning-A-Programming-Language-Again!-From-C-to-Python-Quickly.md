---
 layout: post
 title: "Week 6: Learning a Programming Language, Again! From C to Python, Quickly."
 date: 2025-08-19T19:45:00+02:00
 categories: CS50 Data Science PGDip Journey GIS
 tags: 
 - CS50
 - C Programming
 - Spatial Science
 - PGDip
 - Learning to Code
 description: "Deciding to deep-dive into Data Science, leveraging spatial data expertise and writing about the break." 
 draft: false
--- 
As a spatial scientist, starting on Python was particularly interesting. The language is largely preferred for spatial data manipulation operations. At this point, I hadn't delved Python to any great depth except encountering it in scripts at my 9 - 5 job, in esri software.  
  
In this week's Lecture, Shot and Section, Python is really dealt like rock skipping, touching the surface but, never sinking to depth.  It was really about "*How to Teach Yourself a New Programming Language*". Even with the Problem Set, the same was reiterated.

If I should gripe a little, every time the codespace had to be updated, I lost my theme - Cobalt 2. It however was not a pain getting things back to the way they were.
| <img src="/images/rebuilding_codespace.png" alt="Codespace Rebuild"/> |
|:--:|
| *Codespace My Way - A Dark Mode* |


## Learning a New Programming Language

It was not a struggle following highlights of differences between C and Python. What I had to contend with was 'throwing away' all the attention to detail and '*pseudo-control*' over what the code was doing. Python is high level and I had to actively ignore the under the hood stuff I knew coming from C and '*trust*' the computer to do the right thing. The compactness of  Python code was a breath of fresh air!

Because with Python indentation matters, it sort of forced one to create clean code from the start. The CS50 coding environment screamed ***Problem***, when a *(tab)* was missing.

After this brief run with Python, I found myself also asking the popular question [Python or R](https://www.datacamp.com/blog/python-vs-r-for-data-science-whats-the-difference). Because of the time I have invested in [R for Data Science](https://r4ds.had.co.nz/), I have developed some fondness for R. Curious about what the future holds.


## Revisiting Code

I grappled briefly converting my ***for loops*** from C to Python (*sentimental-mario-less*). But because I understood my code, with a little experimentation, I eventually got the code to work.

In one of the problems, I found myself using ***Debug50*** to trace variable changes. The problem brief from C had been twisted from dealing with integers to now dealing with floating point numbers in Python. It was exciting experiencing first hand float point precision!  The computer was working with 0.009999999999999967 whereas my expectation was 0.01. As a consequence, my function returned 0.0. With some research I employed ***round(change,2)*** which solved the problem. A successful debug, always scratches the inquirer's itch.

I also found a bug in my older code which I had inadvertently gotten away with. It was with a word counting function. Occurrence of '.' or space indicated end of a word but hadn't factored where they occurred together viz. *(dot)(space)*. I therefore ended up with an inflated word count.

Coding fatigue is a real thing.  Even after six weeks of coding, tiny errors are still possible and fundamentals of debugging still have to be observed. This was after my program just hung on execution because I had missed code to increment a counter.

## Reflections
Again I learn that every problem at first glance looks insurmountable. The problem set on DNA, felt overwhelmed on first encounter.  But by applying modular programming, sub-tasking and pseudo-coding, I was soon on my way disintegrating it piece by piece. 

I am looking forward to SQL and having to take a break from general purpose programming languages. The week-to-week tempo I adopted in the face of limited time makes everything feel like a rat race, albeit exciting, in the face of a weekend deadline.

Let me put an end of post bar hereunder in the form of a progress bar, which surprisingly is blue  from red at the moment. 
| <img src="/images/progress_week_6_of_11.png" alt="Past the Halfway Mark"/> |
|:--:|
| *The Gradebook - Blue Zone Progress* |
