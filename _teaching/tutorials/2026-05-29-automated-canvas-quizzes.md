---
title: "Automated Canvas Quiz Generation with R exams"
excerpt: "Learn how to use the R `exams` package to generate hundreds of randomized quiz questions and export them directly to Canvas (QTI format)."
collection: teaching
type: "tutorial"
date: 2026-05-29
header:
  teaser: "r-exams-teaser.png"
toc: true
toc_label: "Post Contents"
toc_icon: "list"
tags:
  - R
  - Canvas
  - EdTech
---

{% include base_path %}

**Prerequisites:** You must have R and RStudio installed. Familiarity with LaTeX or Markdown is helpful for designing the question templates.
{: .notice--info}

## Introduction
Manual quiz entry in Canvas is tedious and prone to error. Using the `exams` package, we can write a single question template and generate infinite variations.

## Step 1: Install the Package
First, install the library from CRAN:

```r
install.packages("exams")
library(exams)
```

## Step 2: Create a Question Template
A typical question file (e.g., `derivative.Rmd`) looks like this:

```r
# Define randomized variables
a <- sample(2:9, 1)
b <- sample(2:9, 1)
sol <- a * b

# Question text
# What is the derivative of {{a}}x^{{b}} at x=1?
```

## Step 3: Export to Canvas (QTI 1.2)
Use the following function to create a `.zip` file that you can import directly into Canvas:

```r
exams2canvas("derivative.Rmd", n = 50, dir = "output", name = "calculus-quiz")
```

**Common Pitfall:** Canvas requires images to be embedded carefully. If your questions include plots, ensure you set `selfcontained = TRUE` in the export function.
{: .notice--warning}

## Conclusion
This workflow saves hours of grading and prevents cheating by ensuring every student gets a unique version of the same conceptual problem.
