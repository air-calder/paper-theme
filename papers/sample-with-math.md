---
layout: paper
title: "Teacher Value-Added and Student Outcomes: A Methodological Note"
paper_type: Short Paper
paper_number: "CALDER Short Paper No. 000-0000"
year: 2026
authors: >
  <a href="#">Jane Smith</a>,
  <a href="#">Robert Johnson</a>
doi: "10.00000/EXAMPLE"
pdf_url: "/files/sample.pdf"
math: true
research_areas:
  - Teacher Workforce
  - Methods & Measurement
abstract: >
  This note illustrates the use of value-added models in estimating teacher effectiveness.
  We describe the standard two-way fixed effects specification and discuss identification
  assumptions, demonstrating LaTeX math rendering and figure embedding for CALDER
  GitHub Pages.
citation: >
  Jane Smith, Robert Johnson (2026). Teacher Value-Added and Student Outcomes: A
  Methodological Note. CALDER Short Paper No. 000-0000. https://doi.org/10.00000/EXAMPLE
related:
  - title: Raising the Floor: Teacher Retention Effects of a Statewide Minimum Salary Increase
    url: /papers/raising-floor
    authors: "Gema Zamarro, Andrew M. Camp, Josh McGee, Taylor Wilson, Miranda Vernon"
    date: February 25, 2026
    type: Short Paper
    research_areas:
      - Education Systems & Policies
      - Teacher Workforce
---

## 1. Introduction

Value-added models (VAMs) are widely used to measure teacher effectiveness. The core
idea is to isolate the teacher's contribution to student achievement growth from the
contributions of other factors—prior achievement, family background, and peer composition.

## 2. Empirical Strategy

### 2.1 Baseline specification

Let $A_{ijt}$ denote the test score of student $i$ assigned to teacher $j$ in year $t$.
The standard value-added specification is:

$$
A_{ijt} = \alpha A_{i,t-1} + \mathbf{X}_{it}'\beta + \mu_j + \varepsilon_{ijt}
$$

where $A_{i,t-1}$ is the prior-year score, $\mathbf{X}_{it}$ is a vector of student
and classroom controls, $\mu_j$ is the teacher fixed effect (value-added), and
$\varepsilon_{ijt}$ is a student-level idiosyncratic error.

We estimate $\mu_j$ by within-teacher demeaning. The identifying assumption is
**conditional random assignment** of students to teachers:

$$
\mathbb{E}[\varepsilon_{ijt} \mid j, \mathbf{X}_{it}, A_{i,t-1}] = 0
$$

### 2.2 Shrinkage estimator

Because teacher fixed effects are estimated with error, raw OLS estimates are
noisy. The empirical Bayes shrinkage estimator is:

$$
\hat{\mu}_j^{\text{EB}} = \frac{\sigma^2_\mu}{\sigma^2_\mu + \sigma^2_\varepsilon / n_j}\,\hat{\mu}_j^{\text{OLS}}
$$

where $\sigma^2_\mu$ is the variance of true teacher effects, $\sigma^2_\varepsilon$ is
the within-teacher error variance, and $n_j$ is the number of students observed for
teacher $j$.

## 3. Results

Table 1 reports summary statistics for our estimation sample.

| Variable | Mean | SD | Min | Max |
|---|---|---|---|---|
| Math score (std.) | 0.00 | 1.00 | −4.2 | 4.1 |
| Reading score (std.) | 0.00 | 1.00 | −3.9 | 3.8 |
| Students per teacher | 22.4 | 6.1 | 5 | 45 |
| Years of experience | 8.3 | 7.7 | 0 | 42 |

Figure 1 plots the distribution of estimated teacher value-added in math and reading.

<figure>
  <img src="/assets/img/vam-distribution.png" alt="Distribution of estimated teacher value-added scores in math (blue) and reading (orange). Both distributions are approximately normal with mean zero; the math distribution is slightly wider." />
  <figcaption>Figure 1. Distribution of teacher value-added estimates. Math scores shown in blue; reading in orange. Dashed lines mark ±1 SD from the mean.</figcaption>
</figure>

The standard deviation of value-added is $\hat{\sigma}_\mu = 0.14$ in math and
$0.11$ in reading, consistent with prior literature (Hanushek & Rivkin, 2010;
Chetty, Friedman & Rockoff, 2014).

## 4. Discussion

These estimates imply that replacing a teacher at the 25th percentile of
effectiveness with one at the 75th percentile would raise average student
achievement by roughly $2 \times 0.14 \times 0.67 \approx 0.19$ standard
deviations—equivalent to about seven months of learning.

The inline math $R^2 \approx 0.65$ for the full model and the shrinkage factor
ranges from 0.42 to 0.91 across teachers, indicating that precision varies
considerably with class size.
