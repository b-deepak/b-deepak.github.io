---
layout: post
title: "O'Reilly Training: Software Architecture Tips"
date: 2020-06-07 10:24:24 -0700
categories: jekyll update
---

> _"Architecture is about the important stuff. Whatever that is” - Ralph Johnson_

- [Circle of Knowledge](#circle-of-knowledge)
- [Build Your Own Radar](#build-your-own-radar)
- [Leverage Checklists](#leverage-checklists)
- [6 steps in refactoring an architecture](#6-steps-in-refactoring-an-architecture)
- [Cost Benefit Analysis](#cost-benefit-analysis)
- [Architectural Decision Records (ADRs)](#architectural-decision-records-adrs)

# Circle of Knowledge

- **SYK**: Stuff You Know
- **SYKYDK**: Stuff You Know You Don't Know
- **SYDKYDK**: Stuff You Don't Know You Don't Know

{% mermaid %}
pie title Knowledge & Learning
"SYK" : 25
"SYKYDK" : 25
"SYDKYDK" : 50
{% endmermaid %}

# Build Your Own Radar

[How to BYOR](https://www.thoughtworks.com/radar/how-to-byor)

[Github: BYOR](https://github.com/thoughtworks/build-your-own-radar)

# Leverage Checklists

> List not the obvious but rather what's not obvious!

# 6 steps in refactoring an architecture

1. Root cause analysis
2. Determine changes needed
3. Create business case
4. Build refactoring plan
5. Create timeline and estimates
6. Present to business

# Cost Benefit Analysis

The [CBAM](https://resources.sei.cmu.edu/library/asset-view.cfm?assetid=513476) process consists of the following steps:

1. Choose scenarios and architectural strategies.
2. Assess quality attribute benefits.
3. Quantify the benefits of architectural strategies.
4. Quantify the costs and schedule implications of the
   architectural strategies.
5. Calculate the desirability of each option.
6. Make architectural design decisions

{% mermaid %}
flowchart LR
A(Business Goals) -->|Define| B(Software Architecture \n-ilities & NFRs)
B --> D(Benefits)
B --> E(Cost)
D --> F{Assess}
E --> F
F --> G(Selection)
{% endmermaid %}

# Architectural Decision Records (ADRs)

> [Lightweight Architecture Decision Records](https://www.thoughtworks.com/radar/techniques/lightweight-architecture-decision-records) is a technique for capturing important architectural decisions along with their context and consequences.

- **ADR (Simple)**

  - Sections:
    - Title
    - Context
    - Decision
    - Status
    - Consequences
  - [Template](https://github.com/joelparkerhenderson/architecture_decision_record/blob/master/adr_template_by_michael_nygard.md)
  - Examples
    - [here...](https://github.com/alphagov/govuk-aws/tree/master/doc/architecture/decisions)
    - [and here...](https://github.com/arachne-framework/architecture)

- **MADR (Options & Pros/Cons)**
  - Sections:
    - Title
    - Context
    - Decision
    - Considered Options
    - Outcome/Consequences
    - Pros/Cons
  - [Template](https://github.com/joelparkerhenderson/architecture_decision_record/blob/master/adr_template_madr.md)
  - [Example](https://adr.github.io/madr/template/0000-use-markdown-architectural-decision-records.html)
