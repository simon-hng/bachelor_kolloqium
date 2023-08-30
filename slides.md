---
theme: ./theme
highlighter: shiki
lineNumbers: true
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
The last comment block of each slide will be treated as slide notes. It will be visible and editable in Presenter Mode along with the slide. [Read more in the docs](https://sli.dev/guide/syntax.html#notes)
-->

---

# Problem

<div class="grid grid-cols-3 color-[#0065bd] items-center justify-center mt-32">
    <v-click>
        <div class="flex flex-col items-center">
            <mdi-head-snowflake class="w-22 h-22"/>
            <p class="text-black">Student Understanding</p>
        </div>
    </v-click>
    <v-click>
        <div class="flex flex-col items-center">
            <mdi-cog class="w-20 h-20"/>
            <p class="text-black">Difficult Configuration</p>
        </div>
    </v-click>
    <v-click>
        <div class="flex flex-col items-center">
            <mdi-clock class="w-20 h-20"/>
            <p class="text-black">Time Consuming</p>
        </div>
    </v-click>
</div>

<!--
- Understanding the grading from instructors and tutors is difficult for student
    - What does this feedback mean? What is the impact on my grade?
- Configuring grading did not reflect the way instructors want to grade exercises
- Overall too time consuming; Instructors where not able to easily create the amount of exercises with
the required amount of information and detail
-->

---

# Motivation

---

# Objectives

- Feedback View
- Programming Exercise Configuration Wizard
- SCA Configuration Import
- Task Grading Configuration
- Automatic Grading Instructions

---
layout: section
---

# Feedback View

---
level: 2
---

# Old view

<div class="relative">
    <img src="/feedbackView.png"/>
    <svg class="absolute top-0 text-red" width="1132" height="503">
        <v-click>
            <rect x="5" y="60" width="860" height="105" fill="none" stroke="currentColor" stroke-width="5"/>
        </v-click>
        <v-click>
            <rect x="5" y="180" width="860" height="110" fill="none" stroke="currentColor" stroke-width="5"/>
        </v-click>
        <v-click>
            <rect x="5" y="290" width="280" height="30" fill="none" stroke="currentColor" stroke-width="5"/>
        </v-click>
    </svg>
</div>

---
level: 2
---

# Object design - Groups

<div class="px-16 relative">
    <img class="w-full" src="/feedback-node.svg" />
</div>

---
level: 2
---

# Object design - Grouping and Sorting

<div class="px-16 relative">
    <img src="/feedback-item-service.png" />
</div>

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
```ts{all|1|3|4|all}
initFeedbackInformation() {
    ...
    const feedbackItems = this.feedbackItemService.create(filteredFeedback, this.showTestDetails);
    this.feedbackItemNodes = this.feedbackItemService.group(feedbackItems, this.exercise!);
```

---
 layout: section
---

# Live Demo

---

# Status

---

# Discussion

---

# Bibliography
