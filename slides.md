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
---

<div class="grid grid-cols-2">
    <div>
        <h1>Learning Analytics of Grading Programming Exercises</h1>
        <p class="text-[#0065bd] text-xl">Bachelor’s Thesis Intermediate Presentation</p>
        <div class="my-12">
            <p class="font-bold">Simon Huang and Lucas Welscher</p>
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
- Extended Artemis's capabilities and implementations of the concepts of learning analytics
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
- Analyzing exercise and course outcomes
- Show difficulties e.g. regarding competency areas
    - Show areas where they can improve
- Students need to learn from their mistakes and improve upon them
-->

---

# Problem

<div class="grid grid-cols-3 color-[#0065bd] items-center justify-center mt-32">
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
- Understanding the grading from instructors and tutors was difficult for students
    - not intuitively clear what e.g. the feedback means
    - they do not understand their mistakes
    - they do not understand how their mistakes relate to their grade
- Configuring grading was difficult due to multiple points
    - did not reflect the way instructors want to grade exercises    
    - steep learning curve as Artemis does have a lot of functions and is multi purpose
    - grading based on test cases was to granular and fine tuned
- Overall too time consuming; 
    - Instructors where not able to easily create the amount of exercises
    - easily achieve quality in regards to information and detail
-->

---

# Motivation

<div class="grid grid-cols-3 color-[#0065bd] items-center justify-center mt-32">
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

- <span class="text-[#0065bd]"> Feedback View </span>
- Programming Exercise Configuration Wizard
- <span class="text-[#0065bd]"> SCA Configuration Import </span>
- <span class="text-[#0065bd]"> Task Grading Configuration </span>
- Automatic Grading Instructions

<!--
- Feedback View: Improve understanding of students by adding additional context to feedback
- Create a Wizard where settings are displayed step by step, deceasing complexity in configuring exercises and help instructors help relevant options
- SCA Efficiency, Consistency, Usability
- Task Grading Configuration, more intuitive, spend less time for too granular settings, achieve the quality of exercise they want
- Investigate the idea of automatic grouping of feedback into grading instructions: Saving time, understanding mistakes as group and grading them

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

<div class="mt-4">
    <img src="/gradingPage.png" />
</div>

::right::

<div class="overflow-hidden h-72 mt-14">
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

<div class="h-96 overflow-hidden">
    <img src="/sca-grading.jpg" />
</div>

<!--
- Grading is good here; not too granular
- Missing feature for enforcing consistency
-->

---

# Analysis Object Model

<img src="/aom.png" class="h-95 px-16"/>

<!-- 
- combined AOM with PE, feedback, tasks, etc 
-->

---

# Improved User Interface

<img src="/taskui.jpg" class="h-95"/>

<!--
- Collapsible tasks
- Sorting by task and tests
- Inputs are aggregated intelligently
-->

---
layout: two-cols
---

# Improved User Interface

<div class="overflow-hidden h-96 mt-4">
    <img src="/import-configuration-button.png" />
</div>

::right::

<div class="overflow-hidden h-96 mt-4">
    <img src="/sca-import-modal.jpg" class="mt-14"/>
</div>

---
layout: section
---

# Feedback View

---
level: 2
---

# Old View

<div class="relative">
    <img src="/feedbackView.png"/>
    <svg class="absolute top-0 text-red" width="1000" height="500">
        <v-clicks>
            <rect x="5" y="60" width="860" height="105" fill="none" stroke="currentColor" stroke-width="5"/>
            <rect x="5" y="180" width="860" height="110" fill="none" stroke="currentColor" stroke-width="5"/>
            <rect x="5" y="290" width="280" height="30" fill="none" stroke="currentColor" stroke-width="5"/>
        </v-clicks>
    </svg>
</div>

<!--
- Chart showing composition of final grade
    - Limited to only Points and Deductions
- Correct feedback is aggregated into single feedback
    - Works well when working on exercise but does not work well when reviewing exercise
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

---
level: 2
---

# Subsystem Decomposition

<div class="px-16 relative">
    <img class="h-96" src="/feedback-subsystem.svg" />
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

<div class="px-16 relative">
    <img class="w-full" src="/feedback-node.svg" />
</div>

<!--
- Similiar to composite pattern
- Except relation between group and node
- Reason: extend functionality
    - Group not only by `correct`,`info`,`wrong`, etc
    - But also by groups appropriate for exercise type e.g. for programming: `tasks`
-->

---
level: 2
---

# Object design - Grouping and Sorting

<div class="px-16 relative">
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
- Automatically highlight SCA grading inconsistencies accros a course

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

---

# Bibliography
