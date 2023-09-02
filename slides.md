---
theme: ./theme
highlighter: shiki
lineNumbers: true
download: true
presenter: dev
drawings:
  persist: false
transition: slide-left
title: Learning Analytics of Grading Programming Exercises
author: Simon Huang, Lucas Welscher
---

<div class="grid grid-cols-2">
    <div>
        <h1>{{ $slidev.configs.title }}</h1>
        <p class="text-tum-blue text-xl">Bachelor’s Thesis Final Presentation</p>
        <div class="my-12">
            <p class="font-bold">{{ $slidev.configs.author }}</p>
        </div>
        <p>
            Technical University of Munich<br/>
            School of Computation, Information and Technology<br/>
            Chair for Applied Software Engineering<br/>
            September 1<sup>st</sup>, 2023
        </p>
    </div>
    <img src="/uhrenturm.png"/>
</div>

<!--
- Bachelor's Thesis Final Presentation
- Learning Analytics of Grading Programming Exercises
- Extended Artemis's capabilities and current implementations of the concepts of learning analytics with focus on programming exercises
-->

---
layout: quote
---

## "Learning analytics is the practice of measuring, collecting, analyzing, and reporting data about learners and their learning environments to understand and optimize learning outcomes"

First International Conference on Learning Analytics
<sup>
    <a class="text-xs" href="https://www.solaresearch.org/about/what-is-learning-analytics/">1</a>
</sup>

<!--
- Conference held in 2011
- Analyzing exercise and course outcomes
- Show difficulties e.g. regarding competency areas
    - Show areas where they can improve
- Students need to learn from their mistakes and improve upon them
-->

---

# Problem

<div class="grid grid-cols-3 color-tum-blue items-center justify-center mt-32">
    <v-clicks>
        <div class="flex flex-col items-center">
            <mdi-emoticon-confused class="w-20 h-20"/>
            <p class="text-black">Student Confusion</p>
        </div>
        <div class="flex flex-col items-center">
            <mdi-cog class="w-20 h-20"/>
            <p class="text-black">Difficult Configuration</p>
        </div>
        <div class="flex flex-col items-center">
            <mdi-clock class="w-20 h-20"/>
            <p class="text-black">Time Consuming</p>
        </div>
    </v-clicks>
</div>

<!--
- Understanding the grading and feedback was difficult for students
    - not intuitively clear what e.g. the feedback means
    - they do not understand their mistakes
    - they do not understand how their mistakes relate to their grade
- Configuring grading was difficult due to multiple points  
    - steep learning curve as Artemis does have a lot of functions and is multi purpose
    - did not reflect the way instructors want to grade exercises  
    - task based grading - Lucas will tell you more about that later
- Overall too time consuming; 
    - Instructors where not able to easily create the amount of exercises
    - easily achieve quality in regards to information and detail
-->

---

# Motivation

<div class="grid grid-cols-3 color-tum-blue items-center justify-center mt-32">
    <v-clicks>
        <div class="flex flex-col items-center">
            <mdi-eye class="w-20 h-20"/>
            <p class="text-black">Transparency</p>
        </div>
        <div class="flex flex-col items-center">
            <mdi-check-bold class="w-18 h-18"/>
            <p class="text-black">Exercise Quality</p>
        </div>
        <div class="flex flex-col items-center">
            <mdi-account-switch class="w-18 h-18"/>
            <p class="text-black">Broader Uptake</p>
        </div>
    </v-clicks>
</div>

<!--
- Resolving the aforementioned problems would bring multiple benefits
- Students would better understand exercise, their grading and where to improve
   - Understand instructors wants and improve
   - Given students easier understanding leads to a more open learning environment
- Exercise Quality
  - Instructors can easier focus on their exercise at hand
  - Not only openness & transparency
  - Better and Fairer Grading
-  We hope that these improvements will enhance broad uptake of the Artemis
system and encourage more educators to make use of interactive learning.
-->

---

# Objectives

- <span class="text-tum-blue"> Feedback View </span>
- Programming Exercise Configuration Wizard
- <span class="text-tum-blue"> SCA Configuration Import </span>
- <span class="text-tum-blue"> Task Grading Configuration </span>
- Automatic Grading Instructions

<!--
- Feedback View: Improve understanding of students by adding additional context to feedback
- Create a Configuration Wizard where settings are displayed step by step, deceasing complexity in configuring exercises by conceptionally grouping similar settings and help instructors find relevant options
- Feature to import Static Code Analysis: SCA Efficiency, Consistency, Usability
- Task Grading Configuration, more intuitive, spend less time for too granular settings, achieve the quality of exercise they want
- Investigate the idea of automatic grouping feedback into grading instructions: Step after exercise created and first submission in. Consistency, Saving time, instructors understand mistakes as group and grading accordingly and fairly
-->

---
layout: section
---

# Grading Configuration


---
layout: two-cols
level: 2
---

## Old System

<div class="overflow-hidden mt-5 shadow-lg h-72">
    <img src="/gradingPage.png" />
</div>

::right::

<div class="overflow-hidden h-72 mt-14 shadow-lg">
    <img src="/iptPoints.png" />
</div>

<!--
- Explain image on left
    - What are weights: Fractions of the grade
    - Complicated Configuration
- Based on test cases instead of tasks: Too granular
- Explain image on right
- No method of ensuring consistency across a course
-->

---

## Old System

<div class="h-90 overflow-hidden shadow-lg">
    <img src="/sca-grading.jpg" />
</div>

<!--
- Grading is good here; not too granular
- Missing feature for enforcing consistency
-->

---

# Analysis Object Model

<div class="relative">
    <img src="/aom2.png" class="h-90 px-16"/>
</div>


<!-- 
- First click: Tasks

-->

---

# Improved User Interface

<div class="overflow-hidden h-90 shadow-lg mx-18">
    <img src="/taskui.jpg" class=""/>
</div>

<!--
- Collapsible tasks
- Sorting by task and tests
- Inputs are aggregated intelligently
-->

---
layout: two-cols
---

# Improved User Interface

<div class="overflow-hidden h-90 mt-5 shadow-lg">
    <img src="/import-configuration-button.png" />
</div>

::right::

<div class="overflow-hidden h-90 mt-14 shadow-lg">
    <img src="/sca-import-modal.jpg" />
</div>

---
layout: section
---

# Feedback View

---
level: 2
---

# Old View

<div class="relative shadow-lg mx-8">
    <img src="/feedbackView.png"/>
    <svg class="w-full absolute top-0 text-red" viewBox="0 0 1000 500">
        <v-clicks>
            <rect x="5" y="65" width="990" height="125" fill="none" stroke="currentColor" stroke-width="3"/>
            <rect x="5" y="200" width="990" height="135" fill="none" stroke="currentColor" stroke-width="3"/>
            <rect x="5" y="340" width="321" height="25" fill="none" stroke="currentColor" stroke-width="3"/>
        </v-clicks>
    </svg>
</div>

<!--
- Chart showing composition of final grade
    - Limited to only Points and Deductions
- Correct feedback is aggregated into single feedback
    - Essentially two use cases:
        - Interactive Learning by pushing / updating our submission and having a look at the feedback; Works well with this view
        - Seing all the feedback at once after the deadline and reviewing our submission with no future changes to it.
    - "What did I do wrong? What did I do well?"
- Important information is shown in the bottom
-->

---
layout: section
---

# Live Demo

<!--
- Show programming
- Show modelling
-->

---
level: 2
---

# Subsystem Decomposition

<div class="p-4 mx-16 relative">
    <img class="h-85" src="/feedback-subsystem.svg" />
</div>

<!--
- Refactor existing implementation into multiple components/services, God-class antipattern
- UI Layer only responsible for viewing, templating, styling, calling functions
- Format data of Feedback Items; Chart library understands
- Feedback Item Service responsible for Formatting Feedback (Server) into something more suitable for UI needs
- Feedback/Result service communicating with server
-->
---
level: 2
---

# Object design - Groups

<div class="p-4 mx-16 relative">
    <img class="w-full" src="/feedback-node.svg" />
</div>

<!--
- Similiar to composite pattern
- Except relation between group and node
- Reason: extend functionality
    - Group not only by `correct`,`info`,`wrong`, etc
    - But also by groups appropriate for exercise type e.g. for programming: `tasks
-->

---
level: 2
---

# Object design - Grouping and Sorting

<div class="p-4 mx-16 relative">
    <img src="/feedback-item-service.png" />
</div>

<!--
- Similar to strategy pattern
-->

---
layout: section
---

# Status

---

# Status

- Feedback View ✅
- Programming Exercise Configuration Wizard ✅
- Task Grading Configuration ✅
- SCA Grading Import ✅
- Automatic Grading Instructions 🚧
---

# Future Work

### Feedback View
- Show missed points for failing test case feedback
- Automatically sort feedback within groups

--

### Static Code Analysis
- Automatically highlight SCA grading inconsistencies across a course

<!--
- Students to not see how many points they would have received
- Import grading is a good starting point
- Artemis should help instructors by highlighting inconsistencies
- Intelligent sorting of feedback
    - e.g. most recent feedback fist
    - order test case feedback in the order they need to be implemented
-->

---
layout: section
---

# Discussion

<!--
- test cases
- exercise creation improvements
-->

