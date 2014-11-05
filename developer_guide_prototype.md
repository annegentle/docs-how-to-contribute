# Introduction

This guide helps Rackspace technical writers create and adapt content for developer guides.

This guide aims to uphold the DevEx docs mission:

    "Our docs are a trustworthy guide so developers can invent powerful applications."
    
## What this guide contains

These [best practices](#bestpractices) improve your developer guides.

This guide includes a [Markdown template for developer guides](#devguidetemplate)--useful if you intend to publish in GitHub or on any Markdown-supported platform.
## Why it matters

There are better ways to create documentation that how we've created it in the past; this guide aims to help us improve.

<a id="bestpractices"></a>
# Best practices

As technical writers, we provide fanatical support to our readers through top-quality documentation. Here are some tips to provide what Racker Aaron Sullivan calls *Humanity as a Service*.

## Explain things well

Put the most important information first.

Structure documents around user tasks. Document what users do, not what features do.

## Write with empathy for your readers 

Empathy is defined as the ability to identify and share the needs of another. Know your 
    
### Use the words that users use

Write in a conversational tone; remember that you are a person writing to another person.

## Know your audience

| Is | Is Not |
|:--:|:------:|
| Entreprenurial | Low spend, high support |
| Inventive | Homework kiddies |
| Comparison shopping | 100% Classical Developers |
| Efficiency-based | Want to ? (Illegible) |
| Educated on cloud options | |
| DIY | |
| Automation seeking | |
| Mid to high spend, targeted support needs | |

**Zach Corleissen**: We need to have a larger conversation around user personas and doc metrics: how does Rackspace determine its doc audience? What are the empirical tools we use? It's all well and good to encourage empathetic writing, but empathy thrives on specificity: *for whom* do our docs show empathy? How do we know?

## Write empathetically

Instead of creating content to document a feature, write to anticipate a reader's needs.

Empathy is **the ability to identify and share the needs of another**. Writing empathetically requires us as writers to know our users' needs and adopt them as our own, advocating for users' best interests with clear, concise documentation.

## Establish trust

Set expectations, then meet them consistently. Present content with reader-friendly formatting. Make navigation easy. 

Reduce the burden of discovery. Improve users' access to information by minimizing click distance (for example, with one-page docs) and improving searchability.

Provide accurate, complete information. Verify that code samples are functional and ready for use.

## Document user tasks

Write most about what matters most to users. Provide clear instructions on how to use a product. Focus on the most common tasks.

Make information easy to find. Put the most important information first. 

Organize content to build on previous skills. 

Lavishly document solutions for common problems. Point users to additional help and support if the problem they have isn't covered in the documentation.

## Weight topics appropriately

Describe how to form API calls.

Describe how to make calls to accomplish common user tasks.

Tell users how to fix common problems.

* Lavishly document error states and edge cases. Which errors are users most likely to encounter? What are the most common fixes? How can users get more help if they need it?

* Provide descriptive, useful HTTP status code messages.

Tell users how to find further help if they need it.

* Build a relationship with support teams for products you document. Contact them periodically to find out which issues customers encounter most frequently and how better documentation can help.

## Write for the web

Reduce click distance between users and content. Write single-page documents wherever possible. 

Extensive reference material, like auto-generated documentation, may belong on its own page or pages. For example, with a RESTful API, users may benefit from separate pages for each endpoint's auto-generated documentation.

Follow best practices on [Usability.gov](http://www.usability.gov/how-to-and-tools/methods/writing-for-the-web.html).

## Write for impermanence

Best practices and tooling in the tech writing landscape change quickly. If you see something out of date, please update it!

## Embrace paradox

Avoid jargon *and* be specific.

Provide generous depth *and* omit needless words.

Avoid colloquialisms or an overly familiar tone **and** write with human empathy for a human audience.

## Resources

[Rackspace web content style guide](http://rax.io/webstyleguide)

[Rackspace writing style guide](https://one.rackspace.com/display/C3/Writing+Style+Guide)

[Usability.gov: Writing for the Web](http://www.usability.gov/how-to-and-tools/methods/writing-for-the-web.html)

<a id="devguidetemplate"></a>
# Developer Guide Template

Feel free to copy and paste the contents below as a basis for new or updated developer guides.

```
# Developer Guide for $productName

## Table of Contents

Hyperlink to sections. When writing single-page docs in Markdown, use anchor tags with ID attributes to link within the same page. For example: 

<a id="foo">bar</a>

Tags can be empty to improve readability. For example:

<a id="foo"></a>bar

## Introduction

Briefly introduce the product and what it does.

### Why it matters

List specific tasks users can accomplish with the product.

### What this guide contains

Provide easy, weighted navigation to sections of greatest user interest: how to form API calls, error message/HTTP status codes, and API reference material.

### Intended audience

List specific skill competencies that may be required.

## How to

### Form a call

Introduce components of a RESTful API call.

Describe authentication and list requirements.

### Accomplish specific tasks

Include a new header for each task.

### Fix a problem

#### Diagnose a problem

#### Make sense of HTTP status codes

### Get help if you need it

Link to preferred points of contact for support.

## API reference

This section may best be broken into separate pages for each endpoint. 

### Endpoint

Add separate headings for each endpoint.

```
