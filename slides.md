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
- Add examples of learning analytics usages to notes
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
- Understanding the grading from instructors and tutors is difficult for students
    - What does this feedback mean? What is the impact on my grade?
- Configuring grading did not reflect the way instructors want to grade exercises
    - Steep learning curve as Artemis does have a lot of functions and is multi purpose
    - Grading based on test cases was to granular and fine tuned
- Overall too time consuming; Instructors where not able to easily create the amount of exercises with the required amount of information and detail
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
- Exercise Quality
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
level: 2
---

<p>
    Selecting the right <tt>feedbackItemService</tt><br />
    <tt class="text-sm text-gray">feedback.component.ts:129-130</tt>
</p>
```ts{all|1|2-3|all}
this.feedbackItemService = this.exerciseType === ExerciseType.PROGRAMMING 
    ? this.injector.get(ProgrammingFeedbackItemService) 
    : this.injector.get(FeedbackItemServiceImpl);

this.initFeedbackInformation();
```

<p>
    Using the service<br />
    <tt class="text-sm text-gray">feedback.component.ts:188-189</tt>
</p>

```ts{all|1|3-4|all}
initFeedbackInformation() {
    ...
    const feedbackItems = this.feedbackItemService.create(filteredFeedback, this.showTestDetails);
    this.feedbackItemNodes = this.feedbackItemService.group(feedbackItems, this.exercise!);
```

---
layout: section
---

# Grading Configuration

---
layout: two-cols
level: 2
---

## Old System

<div class="overflow-hidden h-72 mt-4">
    <img src="/iptPoints.png" />
</div>

::right::

<img src="/gradingPage.png" class="mt-14"/>

<!--
- Complicated Configuration
- Based on test cases instead of tasks
- No method of ensuring consistency across a course
-->

---

<img src="/sca-grading.jpg" />

---

# Analysis Object Model

<img src="/aom.png" class="h-95"/>

<!-- combined AOM with PE, feedback, tasks, etc -->

---

# Improved User Interface

<img src="/taskui.jpg" class="h-95"/>

---
layout: two-cols
---

# Improved User Interface

<div class="overflow-hidden h-72 mt-4">
    <img src="/import-configuration-button.png" />
</div>

::right::

<img src="/sca-import-modal.jpg" class="mt-14"/>

---

# Status

- Feedback View ✅
- Programming Exercise Configuration Wizard ✅
- Task Grading Configuration ✅
- SCA Grading Import ✅
- Task Grading Configuration TODO: Find emoji

--- 

# Future Work

- Show missed points for failing test cases
- Automatically highlight SCA grading inconsistencies accros a course
- TODO: Add feedback view sorting

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
