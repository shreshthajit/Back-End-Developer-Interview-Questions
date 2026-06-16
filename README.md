Back-End Developer Interview Questions
======================================

This page has been translated to [Chinese](https://github.com/monklof/Back-End-Developer-Interview-Questions) by [monklof](https://github.com/monklof).

I started writing down this list as my personal notes of topics I discussed with colleagues and friends, and that I wanted to deepen...

I'm not a big fan of asking technical questions in job interviews: I rather prefer to sit together with candidates in front of some real code, hands on the keyboard, facing a real problem, and to have a full day of pair programming, hopefully rotating with all the other team members. It is one of the best opportunities to know each others' style and to let candidates know some details about their future job.

Yet, I feel some categories of technical questions could be a good starting point to begin an engaging conversation. 

This repo collects a number of back-end related questions that can be used when vetting potential candidates. It is by no means recommended to use every single question on the same candidate: that would take hours, and would have no sense at all, as they cover a too broad set of topics for a single developer's to possibly know. Browse the section you find more relevant for your context, and pick the questions that give you more ideas on the conversation to have.

This project is admittedly inspired by [Front-end Job Interview Questions](https://github.com/darcyclarke/Front-end-Developer-Interview-Questions) by [@darcyclarke](https://github.com/darcyclarke)

## Where are the answers?
I didn't include any.<br/>
Most of the questions are open-ended, and some of them just don't have a *right* or a *wrong* answer. On the contrary, they are intended to be used as the starting point for a conversation that hopefully tells you more about the person's capabilities than a straight answer would. Personally, I would even choose the questions whose answers are not yet clear to me.

Feel free to open a [Discussion](https://github.com/arialdomartini/Back-End-Developer-Interview-Questions/discussions).





## <a name='toc'>Table of Contents</a>

* [Questions about Design Patterns](#patterns)
  * [Globals Are Evil](#globals-are-evil)
  * [Inversion of Control](#inversion-of-control)
  * [Law of Demeter](#law-of-demeter)
  * [Active-Record](#active-record)
  * [Data-Mapper](#data-mapper)
  * [Billion-Dollar Mistake](#billion-dollar-mistake)
  * [Inheritance vs Composition](#inheritance-vs-composition)
  * [Anti-Corruption Layer](#anti-corruption-layer)
  * [Singleton](#singleton)
  * [Data Abstraction](#data-abstraction)
  * [Don't Repeat Yourself](#dont-repeat-yourself)
  * [Dependency Hell](#dependency-hell)
  * [Goto Is Evil](#goto-is-evil)
  * [Robustness Principle](#robustness-principle)
  * [Separation of Concerns](#separation-of-concerns)

* [Questions about Code Design](#design)
  * [High Cohesion, Loose Coupling](#high-cohesion-loose-coupling)
  * [Index 0](#index-0)
  * [TDD](#tdd)
  * [DRY Violation](#dry-violation)
  * [Cohesion vs Coupling](#cohesion-vs-coupling)
  * [Refactoring](#refactoring)
  * [Code Comments](#code-comments)
  * [Design vs Architecture](#design-vs-architecture)
  * [Early Testing](#early-testing)
  * [Multiple Inheritance](#multiple-inheritance)
  * [Domain Logic in Stored Procedures](#domain-logic-in-stored-procedures)
  * [OOP Took Over the World](#oop-took-over-the-world)
  * [Bad Design](#bad-design)

* [Questions about languages](#languages)
  * [3 Worst Defects](#3-worst-defects)
  * [Functional Programming](#functional-programming)
  * [Closures](#closures)
  * [Generics](#generics)
  * [High-Order Functions](#high-order-functions)
  * [Loops and Recursion](#loops-and-recursion)
  * [Functions as First-Class Citizens](#functions-as-first-class-citizens)
  * [Anonymous Functions](#anonymous-functions)
  * [Static and Dynamic Typing](#static-and-dynamic-typing)
  * [Namespaces](#namespaces)
  * [Language Interoperability](#language-interoperability)
  * [Hate of Java](#hate-of-java)
  * [Good and Bad Languages](#good-and-bad-languages)
  * [Referential Transparency](#referencial-transparency)
  * [Stack and Heap](#stack-and-heap)
  * [Pattern Matching](#pattern-matching)
  * [Exceptions](#exceptions)
  * [Variant and Contravariant Inheritance](#variant-and-contravariant-inheritance)
  * [Constructors and Interfaces](#constructors-and-interfaces)
  * [Node.js](#node-js)
  * [Java and Time Traveling](#java-and-time-traveling)
  * [Eliminate Null](#eliminate-null)

* [Web Questions](#web)
  * [3rd Party Cookies](#3rd-party-cookies)
  * [API Versioning](#api-versioning)
  * [SPAs](#spas)
  * [Statelessness](#statelessness)
  * [REST vs SOAP](#rest-vs-soap)
  * [MVC and MVVM](#mvc-and-mvvm)

* [Databases Questions](#databases)
  * [DB Migrations](#db-migrations)
  * [NULL is special](#null-is-special)
  * [ACID](#acid)
  * [Schema Migrations](#schema-migrations)
  * [Lazy Loading](#lazy-loading)
  * [N+1 Problem](#n1-problem)
  * [Slowest Queries](#slowest-queries)
  * [Normalization](#normalization)
  * [Blue/Green Deployment](#bluegreen-deployment)

* [NoSQL Questions](#nosql)
  * [Eventual Consistency](#eventual-consistency)
  * [CAP Theorem](#cap-theorem)
  * [NoSql](#nosql)
  * [NoSQL and Scalability](#nosql-and-scalability)
  * [Document and Relational DBs](#document-and-relational-dbs)

* [Code Versioning Questions](#codeversioning)
  * [Branching in HG and in Git](#branching-in-hg-and-in-git)
  * [DVCS](dvcs)
  * [GitFlow and GitHubFlow](#gitflow-and-githubflow)
  * [Rebase](#rebase)
  * [Merging in HG and in Git](#merging-in-hg-and-in-git)

* [Questions about Concurrency](#concurrency)
  * [Why?](#why)
  * [Testing Concurrency](#testing-concurrency)
  * [Race Conditions](#race-conditions)
  * [Deadlocks](#deadlocks)
  * [Process Starvation](#process-starvation)
  * [Free Algorithm](#free-algorithm)

* [Questions about Distributed Systems](#distributed)
  * [Testing Distributed Systems](#testing-distributed-systems)
  * [Async Communication](#async-communication)
  * [Pitfalls of RPC](#pitfalls-of-rpc)
  * [Design of Distributed Systems](#design-of-distributed-systems)
  * [Fault Tolerance](#fault-tolerance)
  * [Failures](#failures)
  * [Network Partitions](#network-partitions)
  * [Fallacies of Distributed Computing](#fallacies-of-distibuted-computing)
  * [Request/Reply vs Publish/Subscribe](#requestreply-vs-publishsubscribe)
  * [Implement Transactions](#implement-transactions)

* [Questions about Software Lifecycle and Team Management](#management)
  * [Agility](#agility)
  * [Legacy Code](#legacy-code)
  * [Legacy Code ELI5](#legacy-code-eli5)
  * [Sell me Kanban](#sell-me-kanban)
  * [Agile vs Waterfall](#agile-vs-waterfall)
  * [Death by Meetings](#death-by-meetings)
  * [Late Projects](#late-projects)
  * [Agile Manifesto](#agile-manifesto)
  * [If I were the CTO](#if-i-were-the-cto)
  * [PMs](#pms)
  * [Team Organization](#team-organization)
  * [Turn Over](#turn-over)
  * [Qualities](#qualities)
  * [3 Things About Code](#3-things-about-code)
  * [1 Month's Revolution](#1-months-revolution)

* [Questions about logic and algorithms](#algorithms)
  * [FIFO with LIFO](#fifo-with-lifo)
  * [Stack Overflow](#stack-overflow)
  * [Tail Recursive n!](#tail-recursive-n)
  * [REPL](#repl)
  * [Defragger](#defragger)
  * [Mazes](#mazes)
  * [Memory Leaks](#memory-leaks)
  * [PRNG](#prng)
  * [Garbage Collecting](#garbage-collecting)
  * [Queues](#queues)
  * [Simple Web Server](#simple-web-server)
  * [Sorting Huge Files](#sorting-huge-files)
  * [Duplicates](#duplicates)

* [Questions about Software Architecture](#architecture)
  * [No Cache](#no-cache)
  * [Event-Driven Architecture](#event-driven-architecture)
  * [Readability](#readability)
  * [Emergent and Evolutionary](#emergent-and-evolutionary)
  * [Scale-Out, Scale-Up](#scale-out-scale-up)
  * [Failures User Sessions](#failures-user-sessions)
  * [CQRS](#cqrs)
  * [n-tier](#n-tier)
  * [Scalability](#scalability)
  * [C10K](#c10k)
  * [P2P](#p2p)
  * [CGI](#cgi)
  * [Vendor Lock-in](#vendor-lock-in)
  * [Pub/Sub](#pubsub)
  * [CPUs](#cpus)
  * [Performance](#performance)
  * [DDOS](#ddos)
  * [Performance and Scalability](#performance-and-scalability)
  * [Tight Coupling](#tight-coupling)
  * [Cloud Readiness](#cloud-readiness)
  * [Emergent Architecture](#emergent-architecture)
  * [Design, Architecture, Functionality, Aesthetic](#design-architecture-functionality-aesthetic)

* [Questions about Service Oriented Architecture and Microservices](#soa)
  * [Long-lived Transactions](#long-lived-transactions)
  * [SOA and Micro Services](#soa-and-micro-services)
  * [Versioning and Breaking Changes](#versioning-and-breaking-changes)
  * [Sagas and compensations](#sagas-and-compensations)
  * [Too Micro](#too-micro "Too Micro")
  * [Micro Services Architecture](#micro-services-architecture)

* [Questions about Security](#security)
  * [Security by Default](#security-by-default)
  * [Don't Invent Cryptography](#dont-invent-cryptography)
  * [2-FA](#2-fa)
  * [Confidential Data in Logs](#confidential-data-in-logs)
  * [SQL Injection](#sql-injection)
  * [Detect SQL Injection](#detect-sql-injection)
  * [XSS](#xss)
  * [Cross-Site Forgery Attack](#cross-site-forgery-attack)
  * [HTTPS](#https)
  * [MITM Attack](#mitm-attack)
  * [Stealing Sessions](#stealing-sessions)

* [General Questions](#general)
  * [Why FP?](#why-fp)
  * [Browsers](#browsers)
  * [TCP Sockets](#tcp-sockets)
  * [Encapsulation](#encapsulation)
  * [Real-time systems](#real-time-systems)
  * [Real-time and memory allocation](#real-time-and-memory-allocation)
  * [Immutability](#immutability)
  * [Mutable vs Immutable](#mutable-vs-immutable)
  * [Object-Relational Impedance Mismatch](#object-relational-impedance-mismatch)
  * [Sizing a Cache](#sizing-a-cache)
  * [TCP and HTTP](#tcp-and-http)
  * [Client-Side vs Server-Side](#client-side-vs-server-side)
  * [Reliable and non-reliable channels](#reliable-and-non-reliable-channels)

* [Open Questions](#open)
  * [Resistance to Change](#resistance-to-change)
  * [Threading ELI5](#threading-eli5)
  * [Innovation and Predictability](#innovation-and-predictability)
  * [Good Code](#good-code)
  * [Streaming](#streaming)
  * [1 Week Improvement](#1-week-improvement)
  * [Learnt this week](#learnt-this-week)
  * [Aesthetic](#aesthetic)
  * [Last 5 books](#last-5-books)
  * [Introducing CI/CD](#introducing-cicd)
  * [Reinvent the Wheel](#reinvent-the-wheel)
  * [Not Invented Here](#not-invented-here)
  * [Next Thing to Automate](#next-thing-to-automate)
  * [Coding is Hard](#coding-is-hard)
  * [Green Fields and Brown Fields](#green-fields-and-brown-fields)
  * [Type "Google.com"](#type-googlecom)
  * [While idle](#while-idle)
  * [Unicode](#unicode)
  * [Defending Monoliths](#defending-monoliths)
  * [Professional Developers](#professional-developers)
  * [It's an art](#its-an-art)
  * [People who like this also like...](#people-who-like-this-also-like)
  * [Corporations vs Startups](#corporations-vs-startups)
  * [I'm proud of](#im-proud-of)

* [Questions based on snippets of code](#snippets)
  * [Beware the Closure](#beware-the-closure)
  * [Type Erasure](#type-erasure)
  * [Memory Leak](#memory-leak)
  * [Kill the switch](#kill-the-switch)
  * [Kill the if](#kill-the-if)
  * [Kill the if-chain](#kill-the-if-chain)

* [Bill Gates Style Questions](#billgates)
  * [Mirrors](#mirrors)
  * [Clones](#clones)
  * [Revert](#revert)
  * [Quora](#quora)
  * [Cobol](#cobol)
  * [10 years](#10-years)
  * [Fire me](#fire-me)
  * [From scratch](#from-scratch)
  * [Telling lies](#telling-lies)
  * [Your past self](#your-past-self)




### [[↑]](#toc) <a name='patterns'>Questions about Design Patterns:</a>
#### Globals Are Evil

**Answer:**
This topic tests understanding of **Globals Are Evil**. A strong interview answer should define the concept, explain why it matters in real systems, discuss advantages and trade-offs, provide a practical example, and describe when you would or would not use the approach. When answering, connect the concept to maintainability, scalability, performance, reliability, security, and developer productivity where relevant.

Why are global and static objects evil? Can you show it with a code example?

#### Inversion of Control

**Answer:**
This topic tests understanding of **Inversion of Control**. A strong interview answer should define the concept, explain why it matters in real systems, discuss advantages and trade-offs, provide a practical example, and describe when you would or would not use the approach. When answering, connect the concept to maintainability, scalability, performance, reliability, security, and developer productivity where relevant.

Tell me about Inversion of Control and how it improves the design of code.<br/>
[Resources](design-patterns/inversion-of-control.md)


#### Law of Demeter

**Answer:**
This topic tests understanding of **Law of Demeter**. A strong interview answer should define the concept, explain why it matters in real systems, discuss advantages and trade-offs, provide a practical example, and describe when you would or would not use the approach. When answering, connect the concept to maintainability, scalability, performance, reliability, security, and developer productivity where relevant.

The Law of Demeter (the Principle of Least Knowledge) states that each unit should have only limited knowledge about other units and it should only talk to its immediate friends (sometimes stated as "don't talk to strangers").<br/>
Would you write code violating this principle, show why it is a bad design and then fix it?<br/>
[Resources](design-patterns/law-of-demeter.md)

#### Active-Record

**Answer:**
This topic tests understanding of **Active-Record**. A strong interview answer should define the concept, explain why it matters in real systems, discuss advantages and trade-offs, provide a practical example, and describe when you would or would not use the approach. When answering, connect the concept to maintainability, scalability, performance, reliability, security, and developer productivity where relevant.

Active-Record is the design pattern that promotes objects to include functions such as Insert, Update, and Delete, and properties that correspond to the columns in some underlying database table. In your opinion and experience, which are the limits and pitfalls of the this pattern?<br/>
[Resources](design-patterns/active-record.md)

#### Data-Mapper

**Answer:**
This topic tests understanding of **Data-Mapper**. A strong interview answer should define the concept, explain why it matters in real systems, discuss advantages and trade-offs, provide a practical example, and describe when you would or would not use the approach. When answering, connect the concept to maintainability, scalability, performance, reliability, security, and developer productivity where relevant.

Data-Mapper is a design pattern that promotes the use of a layer of Mappers that moves data between objects and a database while keeping them independent of each other and the mapper itself. On the contrary, in Active-Record objects directly incorporate operations for persisting themselves to a database, and properties corresponding to the underlying database tables. Do you have an opinion on those patterns? When would you use one instead of the other?

#### Billion Dollar Mistake

**Answer:**
This topic tests understanding of **Billion Dollar Mistake**. A strong interview answer should define the concept, explain why it matters in real systems, discuss advantages and trade-offs, provide a practical example, and describe when you would or would not use the approach. When answering, connect the concept to maintainability, scalability, performance, reliability, security, and developer productivity where relevant.

[Tony Hoare](https://en.m.wikipedia.org/wiki/Tony_Hoare) who invented the null reference once said "*I call it my billion-dollar mistake*" since it led to "*innumerable errors, vulnerabilities, and system crashes, which have probably caused a billion dollars of pain and damage in the last forty years*".

Would you discuss the techniques to avoid it, such as the Null Object Pattern introduced by the GOF book, or Option types?

#### Inheritance vs Composition

**Answer:**
This topic tests understanding of **Inheritance vs Composition**. A strong interview answer should define the concept, explain why it matters in real systems, discuss advantages and trade-offs, provide a practical example, and describe when you would or would not use the approach. When answering, connect the concept to maintainability, scalability, performance, reliability, security, and developer productivity where relevant.

Many state that, in Object-Oriented Programming, composition is often a better option than inheritance. What's you opinion?

#### Anti-Corruption Layer

**Answer:**
This topic tests understanding of **Anti-Corruption Layer**. A strong interview answer should define the concept, explain why it matters in real systems, discuss advantages and trade-offs, provide a practical example, and describe when you would or would not use the approach. When answering, connect the concept to maintainability, scalability, performance, reliability, security, and developer productivity where relevant.

What is an Anti-corruption Layer?

#### Singleton

**Answer:**
This topic tests understanding of **Singleton**. A strong interview answer should define the concept, explain why it matters in real systems, discuss advantages and trade-offs, provide a practical example, and describe when you would or would not use the approach. When answering, connect the concept to maintainability, scalability, performance, reliability, security, and developer productivity where relevant.

Singleton is a design pattern that restricts the instantiation of a class to one single object. Writing a Thread-Safe Singleton class is not so obvious. Would you try?

#### Data Abstraction

**Answer:**
This topic tests understanding of **Data Abstraction**. A strong interview answer should define the concept, explain why it matters in real systems, discuss advantages and trade-offs, provide a practical example, and describe when you would or would not use the approach. When answering, connect the concept to maintainability, scalability, performance, reliability, security, and developer productivity where relevant.

The ability to change implementation without affecting clients is called Data Abstraction. Produce an example violating this property, then fix it.

#### Don't Repeat Yourself

**Answer:**
This topic tests understanding of **Don't Repeat Yourself**. A strong interview answer should define the concept, explain why it matters in real systems, discuss advantages and trade-offs, provide a practical example, and describe when you would or would not use the approach. When answering, connect the concept to maintainability, scalability, performance, reliability, security, and developer productivity where relevant.

Write a snippet of code violating the Don't Repeat Yourself (DRY) principle. Then, fix it.

#### Dependency Hell

**Answer:**
This topic tests understanding of **Dependency Hell**. A strong interview answer should define the concept, explain why it matters in real systems, discuss advantages and trade-offs, provide a practical example, and describe when you would or would not use the approach. When answering, connect the concept to maintainability, scalability, performance, reliability, security, and developer productivity where relevant.

How would you deal with Dependency Hell?

#### Goto is Evil

**Answer:**
This topic tests understanding of **Goto is Evil**. A strong interview answer should define the concept, explain why it matters in real systems, discuss advantages and trade-offs, provide a practical example, and describe when you would or would not use the approach. When answering, connect the concept to maintainability, scalability, performance, reliability, security, and developer productivity where relevant.

Is goto evil? You may have heard of the famous paper "Go To Statement Considered Harmful" by Edsger Dijkstra, in which he criticized the use of the `goto` statement and advocated structured programming instead. The use of `goto` has always been controversial, so much that even Dijkstra's letter was criticized with articles such as "'GOTO Considered Harmful' Considered Harmful". What's your opinion on the use of `goto`?

#### Robustness Principle

**Answer:**
This topic tests understanding of **Robustness Principle**. A strong interview answer should define the concept, explain why it matters in real systems, discuss advantages and trade-offs, provide a practical example, and describe when you would or would not use the approach. When answering, connect the concept to maintainability, scalability, performance, reliability, security, and developer productivity where relevant.

The robustness principle is a general design guideline for software that recommends "*be conservative in what you send, be liberal in what you accept*". It is often reworded as "*be a tolerant reader and a careful writer*". Would you like to discuss the rationale of this principle?

#### Separation of Concerns

**Answer:**
This topic tests understanding of **Separation of Concerns**. A strong interview answer should define the concept, explain why it matters in real systems, discuss advantages and trade-offs, provide a practical example, and describe when you would or would not use the approach. When answering, connect the concept to maintainability, scalability, performance, reliability, security, and developer productivity where relevant.

Separation of Concerns is a design principle for separating a computer program into distinct areas, each one addressing a separate concern. There are a lot of different mechanisms for achieving Separation of Concerns (use of objects, functions, modules, or patterns such as MVC and the like). Would you discuss this topic?


### [[↑]](#toc) <a name='design'>Questions about Code Design:</a>

#### High Cohesion, Loose Coupling

**Answer:**
This topic tests understanding of **High Cohesion, Loose Coupling**. A strong interview answer should define the concept, explain why it matters in real systems, discuss advantages and trade-offs, provide a practical example, and describe when you would or would not use the approach. When answering, connect the concept to maintainability, scalability, performance, reliability, security, and developer productivity where relevant.

It is often said that one of the most important goals in Object-Oriented Design (and code design in general) is to have High Cohesion and Loose Coupling. What does it mean? Why is it that important and how is it achieved?

#### Index 0

**Answer:**
This topic tests understanding of **Index 0**. A strong interview answer should define the concept, explain why it matters in real systems, discuss advantages and trade-offs, provide a practical example, and describe when you would or would not use the approach. When answering, connect the concept to maintainability, scalability, performance, reliability, security, and developer productivity where relevant.

Why do array indexes start with '0' in most languages?

#### TDD

**Answer:**
This topic tests understanding of **TDD**. A strong interview answer should define the concept, explain why it matters in real systems, discuss advantages and trade-offs, provide a practical example, and describe when you would or would not use the approach. When answering, connect the concept to maintainability, scalability, performance, reliability, security, and developer productivity where relevant.

How do tests and TDD influence code design?

#### DRY Violation

**Answer:**
This topic tests understanding of **DRY Violation**. A strong interview answer should define the concept, explain why it matters in real systems, discuss advantages and trade-offs, provide a practical example, and describe when you would or would not use the approach. When answering, connect the concept to maintainability, scalability, performance, reliability, security, and developer productivity where relevant.

Write a snippet of code violating the Don't Repeat Yourself (DRY) principle. Then, explain why it is a bad design, and fix it.

#### Cohesion vs Coupling

**Answer:**
This topic tests understanding of **Cohesion vs Coupling**. A strong interview answer should define the concept, explain why it matters in real systems, discuss advantages and trade-offs, provide a practical example, and describe when you would or would not use the approach. When answering, connect the concept to maintainability, scalability, performance, reliability, security, and developer productivity where relevant.

What's the difference between cohesion and coupling?

#### Refactoring

**Answer:**
This topic tests understanding of **Refactoring**. A strong interview answer should define the concept, explain why it matters in real systems, discuss advantages and trade-offs, provide a practical example, and describe when you would or would not use the approach. When answering, connect the concept to maintainability, scalability, performance, reliability, security, and developer productivity where relevant.

What is refactoring useful for?

#### Code Comments

**Answer:**
This topic tests understanding of **Code Comments**. A strong interview answer should define the concept, explain why it matters in real systems, discuss advantages and trade-offs, provide a practical example, and describe when you would or would not use the approach. When answering, connect the concept to maintainability, scalability, performance, reliability, security, and developer productivity where relevant.

Are comments in code useful? Some say they should be avoided as much as possible, and hopefully made unnecessary. Do you agree?

#### Design vs Architecture

**Answer:**
This topic tests understanding of **Design vs Architecture**. A strong interview answer should define the concept, explain why it matters in real systems, discuss advantages and trade-offs, provide a practical example, and describe when you would or would not use the approach. When answering, connect the concept to maintainability, scalability, performance, reliability, security, and developer productivity where relevant.

What is the difference between design and architecture?

#### Early Testing

**Answer:**
This topic tests understanding of **Early Testing**. A strong interview answer should define the concept, explain why it matters in real systems, discuss advantages and trade-offs, provide a practical example, and describe when you would or would not use the approach. When answering, connect the concept to maintainability, scalability, performance, reliability, security, and developer productivity where relevant.

In TDD, why are tests written before code?

#### Multiple Inheritance

**Answer:**
This topic tests understanding of **Multiple Inheritance**. A strong interview answer should define the concept, explain why it matters in real systems, discuss advantages and trade-offs, provide a practical example, and describe when you would or would not use the approach. When answering, connect the concept to maintainability, scalability, performance, reliability, security, and developer productivity where relevant.

C++ supports multiple inheritance, and Java allows a class to implement multiple interfaces. What impact does using these facilities have on orthogonality? Is there a difference in impact between using multiple inheritance and multiple interfaces? Is there a difference between using delegation and using inheritance? [This question is from The Pragmatic Programmer, by Andrew Hunt and David Thomas]

#### Domain Logic in Stored Procedures

**Answer:**
This topic tests understanding of **Domain Logic in Stored Procedures**. A strong interview answer should define the concept, explain why it matters in real systems, discuss advantages and trade-offs, provide a practical example, and describe when you would or would not use the approach. When answering, connect the concept to maintainability, scalability, performance, reliability, security, and developer productivity where relevant.

What are the pros and cons of holding domain logic in Stored Procedures?

#### OOP Took Over the World

**Answer:**
This topic tests understanding of **OOP Took Over the World**. A strong interview answer should define the concept, explain why it matters in real systems, discuss advantages and trade-offs, provide a practical example, and describe when you would or would not use the approach. When answering, connect the concept to maintainability, scalability, performance, reliability, security, and developer productivity where relevant.

In your opinion, why has Object-Oriented Design dominated the market for so many years?

#### Bad Design

**Answer:**
This topic tests understanding of **Bad Design**. A strong interview answer should define the concept, explain why it matters in real systems, discuss advantages and trade-offs, provide a practical example, and describe when you would or would not use the approach. When answering, connect the concept to maintainability, scalability, performance, reliability, security, and developer productivity where relevant.

What would you do to understand if your code has a bad design?


### [[↑]](#toc) <a name='languages'>Questions about Languages:</a>

#### 3 worst defects

**Answer:**
This topic tests understanding of **3 worst defects**. A strong interview answer should define the concept, explain why it matters in real systems, discuss advantages and trade-offs, provide a practical example, and describe when you would or would not use the approach. When answering, connect the concept to maintainability, scalability, performance, reliability, security, and developer productivity where relevant.

Tell me the 3 worst defects of your preferred language

#### Functional Programming

**Answer:**
This topic tests understanding of **Functional Programming**. A strong interview answer should define the concept, explain why it matters in real systems, discuss advantages and trade-offs, provide a practical example, and describe when you would or would not use the approach. When answering, connect the concept to maintainability, scalability, performance, reliability, security, and developer productivity where relevant.

Why is there a rising interest on Functional Programming?

#### Closures

**Answer:**
This topic tests understanding of **Closures**. A strong interview answer should define the concept, explain why it matters in real systems, discuss advantages and trade-offs, provide a practical example, and describe when you would or would not use the approach. When answering, connect the concept to maintainability, scalability, performance, reliability, security, and developer productivity where relevant.

What is a closure, and what is useful for? What's in common between closures and classes?

#### Generics

**Answer:**
This topic tests understanding of **Generics**. A strong interview answer should define the concept, explain why it matters in real systems, discuss advantages and trade-offs, provide a practical example, and describe when you would or would not use the approach. When answering, connect the concept to maintainability, scalability, performance, reliability, security, and developer productivity where relevant.

What are generics useful for?

#### High-Order Functions

**Answer:**
This topic tests understanding of **High-Order Functions**. A strong interview answer should define the concept, explain why it matters in real systems, discuss advantages and trade-offs, provide a practical example, and describe when you would or would not use the approach. When answering, connect the concept to maintainability, scalability, performance, reliability, security, and developer productivity where relevant.

What are higher-order functions? What are they useful for? Write one, in your preferred language.

#### Loops and Recursion

**Answer:**
This topic tests understanding of **Loops and Recursion**. A strong interview answer should define the concept, explain why it matters in real systems, discuss advantages and trade-offs, provide a practical example, and describe when you would or would not use the approach. When answering, connect the concept to maintainability, scalability, performance, reliability, security, and developer productivity where relevant.

Write a loop, then transform it into a recursive function, using only immutable structures (i.e. avoid using variables). Discuss.

#### Functions as First-Class Citizens

**Answer:**
This topic tests understanding of **Functions as First-Class Citizens**. A strong interview answer should define the concept, explain why it matters in real systems, discuss advantages and trade-offs, provide a practical example, and describe when you would or would not use the approach. When answering, connect the concept to maintainability, scalability, performance, reliability, security, and developer productivity where relevant.

What does it mean when a language treats functions as first-class citizens?
Why is it important that in a language functions are first-class citizens?

#### Anonymous Functions

**Answer:**
This topic tests understanding of **Anonymous Functions**. A strong interview answer should define the concept, explain why it matters in real systems, discuss advantages and trade-offs, provide a practical example, and describe when you would or would not use the approach. When answering, connect the concept to maintainability, scalability, performance, reliability, security, and developer productivity where relevant.

Show me an example where an anonymous function can be useful.

#### Static and Dynamic typing

**Answer:**
This topic tests understanding of **Static and Dynamic typing**. A strong interview answer should define the concept, explain why it matters in real systems, discuss advantages and trade-offs, provide a practical example, and describe when you would or would not use the approach. When answering, connect the concept to maintainability, scalability, performance, reliability, security, and developer productivity where relevant.

There are a lot of different type systems. Let's talk about static and dynamic type systems, and about strong and weak ones. You surely have an opinion and a preference about this topic. Would you like to share them, and discuss why and when would you promote one particular type system for developing an enterprise software?

#### Namespaces

**Answer:**
This topic tests understanding of **Namespaces**. A strong interview answer should define the concept, explain why it matters in real systems, discuss advantages and trade-offs, provide a practical example, and describe when you would or would not use the approach. When answering, connect the concept to maintainability, scalability, performance, reliability, security, and developer productivity where relevant.

What are namespaces useful for? Invent an alternative.

#### Language Interoperability

**Answer:**
This topic tests understanding of **Language Interoperability**. A strong interview answer should define the concept, explain why it matters in real systems, discuss advantages and trade-offs, provide a practical example, and describe when you would or would not use the approach. When answering, connect the concept to maintainability, scalability, performance, reliability, security, and developer productivity where relevant.

Talk about interoperability between Java and C# (in alternative, choose 2 other arbitrary languages)

#### Hate of Java

**Answer:**
This topic tests understanding of **Hate of Java**. A strong interview answer should define the concept, explain why it matters in real systems, discuss advantages and trade-offs, provide a practical example, and describe when you would or would not use the approach. When answering, connect the concept to maintainability, scalability, performance, reliability, security, and developer productivity where relevant.

Why do many software engineers not like Java?

#### Good and Bad Languages

**Answer:**
This topic tests understanding of **Good and Bad Languages**. A strong interview answer should define the concept, explain why it matters in real systems, discuss advantages and trade-offs, provide a practical example, and describe when you would or would not use the approach. When answering, connect the concept to maintainability, scalability, performance, reliability, security, and developer productivity where relevant.

What makes a good language good and a bad language bad?

#### Referential Transparency

**Answer:**
This topic tests understanding of **Referential Transparency**. A strong interview answer should define the concept, explain why it matters in real systems, discuss advantages and trade-offs, provide a practical example, and describe when you would or would not use the approach. When answering, connect the concept to maintainability, scalability, performance, reliability, security, and developer productivity where relevant.

Write two functions, one referentially transparent and the other one referentially opaque. Discuss.

#### Stack and Heap

**Answer:**
This topic tests understanding of **Stack and Heap**. A strong interview answer should define the concept, explain why it matters in real systems, discuss advantages and trade-offs, provide a practical example, and describe when you would or would not use the approach. When answering, connect the concept to maintainability, scalability, performance, reliability, security, and developer productivity where relevant.

What is a stack and what is a heap? What's a stack overflow?

#### Pattern Matching

**Answer:**
This topic tests understanding of **Pattern Matching**. A strong interview answer should define the concept, explain why it matters in real systems, discuss advantages and trade-offs, provide a practical example, and describe when you would or would not use the approach. When answering, connect the concept to maintainability, scalability, performance, reliability, security, and developer productivity where relevant.

Some languages, especially the ones that promote a functional approach, allow a technique called pattern matching. Do you know it? How is pattern matching different from switch clauses?

#### Exceptions

**Answer:**
This topic tests understanding of **Exceptions**. A strong interview answer should define the concept, explain why it matters in real systems, discuss advantages and trade-offs, provide a practical example, and describe when you would or would not use the approach. When answering, connect the concept to maintainability, scalability, performance, reliability, security, and developer productivity where relevant.

Why do some languages have no exceptions by design? What are the pros and cons?

#### Variant and Contravariant Inheritance

**Answer:**
This topic tests understanding of **Variant and Contravariant Inheritance**. A strong interview answer should define the concept, explain why it matters in real systems, discuss advantages and trade-offs, provide a practical example, and describe when you would or would not use the approach. When answering, connect the concept to maintainability, scalability, performance, reliability, security, and developer productivity where relevant.

If `Cat` is an `Animal`, is `TakeCare<Cat>` a `TakeCare<Animal>`?

#### Constructors and Interfaces

**Answer:**
This topic tests understanding of **Constructors and Interfaces**. A strong interview answer should define the concept, explain why it matters in real systems, discuss advantages and trade-offs, provide a practical example, and describe when you would or would not use the approach. When answering, connect the concept to maintainability, scalability, performance, reliability, security, and developer productivity where relevant.

In Java, C# and many other languages, why are constructors not part of the interface?

#### Node.js

**Answer:**
This topic tests understanding of **Node.js**. A strong interview answer should define the concept, explain why it matters in real systems, discuss advantages and trade-offs, provide a practical example, and describe when you would or would not use the approach. When answering, connect the concept to maintainability, scalability, performance, reliability, security, and developer productivity where relevant.

In the last years there has been a lot of hype around Node.js. What's your opinion on using a language that was initially conceived to run in the browser in the backend?

#### Java and time-traveling

**Answer:**
This topic tests understanding of **Java and time-traveling**. A strong interview answer should define the concept, explain why it matters in real systems, discuss advantages and trade-offs, provide a practical example, and describe when you would or would not use the approach. When answering, connect the concept to maintainability, scalability, performance, reliability, security, and developer productivity where relevant.

* Pretend you have a time machine and pretend that you have the opportunity to go to a particular point in time during Java's (or C#, Python, Go or whatever) history, and talk with some of the JDK architects. What would you try to convince them of? Removing checked exceptions? Adding unsigned primitives? Adding multiple-inheritance?
#### Eliminate Null

**Answer:**
This topic tests understanding of **Eliminate Null**. A strong interview answer should define the concept, explain why it matters in real systems, discuss advantages and trade-offs, provide a practical example, and describe when you would or would not use the approach. When answering, connect the concept to maintainability, scalability, performance, reliability, security, and developer productivity where relevant.

Imagine you want to remove the possibility to have null references in your preferred language: how would you achieve this goal? What consequences would this have?


### [[↑]](#toc) <a name='web'>Questions about Web development:</a>

#### 3rd Party Cookies

**Answer:**
This topic tests understanding of **3rd Party Cookies**. A strong interview answer should define the concept, explain why it matters in real systems, discuss advantages and trade-offs, provide a practical example, and describe when you would or would not use the approach. When answering, connect the concept to maintainability, scalability, performance, reliability, security, and developer productivity where relevant.

Why are first-party cookies and third-party cookies treated so differently?

#### API Versioning

**Answer:**
This topic tests understanding of **API Versioning**. A strong interview answer should define the concept, explain why it matters in real systems, discuss advantages and trade-offs, provide a practical example, and describe when you would or would not use the approach. When answering, connect the concept to maintainability, scalability, performance, reliability, security, and developer productivity where relevant.

How would you manage Web Services API versioning?

#### SPAs

**Answer:**
This topic tests understanding of **SPAs**. A strong interview answer should define the concept, explain why it matters in real systems, discuss advantages and trade-offs, provide a practical example, and describe when you would or would not use the approach. When answering, connect the concept to maintainability, scalability, performance, reliability, security, and developer productivity where relevant.

From a backend perspective, are there any disadvantages or drawbacks on the adoption of Single Page Applications?

#### Statelessness

**Answer:**
This topic tests understanding of **Statelessness**. A strong interview answer should define the concept, explain why it matters in real systems, discuss advantages and trade-offs, provide a practical example, and describe when you would or would not use the approach. When answering, connect the concept to maintainability, scalability, performance, reliability, security, and developer productivity where relevant.

Why do we usually put so much effort for having stateless services? What's so good in stateless code and why and when is statefulness bad?

#### REST vs SOAP

**Answer:**
This topic tests understanding of **REST vs SOAP**. A strong interview answer should define the concept, explain why it matters in real systems, discuss advantages and trade-offs, provide a practical example, and describe when you would or would not use the approach. When answering, connect the concept to maintainability, scalability, performance, reliability, security, and developer productivity where relevant.

REST and SOAP: when would you choose one, and when the other?

#### MVC and MVVM

**Answer:**
This topic tests understanding of **MVC and MVVM**. A strong interview answer should define the concept, explain why it matters in real systems, discuss advantages and trade-offs, provide a practical example, and describe when you would or would not use the approach. When answering, connect the concept to maintainability, scalability, performance, reliability, security, and developer productivity where relevant.

In web development, Model-View Controller and Model-View-View-Model approaches are very common, both in the backend and in the frontend. What are they, and why are they advisable?


### [[↑]](#toc) <a name='databases'>Questions about Databases:</a>

#### DB Migrations

**Answer:**
This topic tests understanding of **DB Migrations**. A strong interview answer should define the concept, explain why it matters in real systems, discuss advantages and trade-offs, provide a practical example, and describe when you would or would not use the approach. When answering, connect the concept to maintainability, scalability, performance, reliability, security, and developer productivity where relevant.

How would you migrate an application from a database to another, for example from MySQL to PostgreSQL? If you had to manage that project, which issues would you expect to face?

#### NULL is special

**Answer:**
This topic tests understanding of **NULL is special**. A strong interview answer should define the concept, explain why it matters in real systems, discuss advantages and trade-offs, provide a practical example, and describe when you would or would not use the approach. When answering, connect the concept to maintainability, scalability, performance, reliability, security, and developer productivity where relevant.

Why do databases treat null as a so special case? For example, why does ```SELECT * FROM table WHERE field = null``` not match records with null ``field`` in SQL?

#### ACID

**Answer:**
This topic tests understanding of **ACID**. A strong interview answer should define the concept, explain why it matters in real systems, discuss advantages and trade-offs, provide a practical example, and describe when you would or would not use the approach. When answering, connect the concept to maintainability, scalability, performance, reliability, security, and developer productivity where relevant.

ACID is an acronym that refers to Atomicity, Consistency, Isolation and Durability, 4 properties guaranteed by a database transaction in most database engines. What do you know about this topic? Would you like to elaborate?

#### Schema Migrations

**Answer:**
This topic tests understanding of **Schema Migrations**. A strong interview answer should define the concept, explain why it matters in real systems, discuss advantages and trade-offs, provide a practical example, and describe when you would or would not use the approach. When answering, connect the concept to maintainability, scalability, performance, reliability, security, and developer productivity where relevant.

How would you manage database schema migrations? That is, how would you automate changes to database schema, as the application evolves, version after version?

#### Lazy Loading

**Answer:**
This topic tests understanding of **Lazy Loading**. A strong interview answer should define the concept, explain why it matters in real systems, discuss advantages and trade-offs, provide a practical example, and describe when you would or would not use the approach. When answering, connect the concept to maintainability, scalability, performance, reliability, security, and developer productivity where relevant.

How is lazy loading achieved? When is it useful? What are its pitfalls?

#### N+1 Problem

**Answer:**
This topic tests understanding of **N+1 Problem**. A strong interview answer should define the concept, explain why it matters in real systems, discuss advantages and trade-offs, provide a practical example, and describe when you would or would not use the approach. When answering, connect the concept to maintainability, scalability, performance, reliability, security, and developer productivity where relevant.

The so called "N + 1 problem" is an issue that occurs when code needs to load the children of a parent-child relationship with a ORMs that have lazy-loading enabled, and that therefore issue a query for the parent record, and then one query for each child record. How to fix it?

#### Slowest Queries

**Answer:**
This topic tests understanding of **Slowest Queries**. A strong interview answer should define the concept, explain why it matters in real systems, discuss advantages and trade-offs, provide a practical example, and describe when you would or would not use the approach. When answering, connect the concept to maintainability, scalability, performance, reliability, security, and developer productivity where relevant.

How would you find the most expensive queries in an application?

#### Normalization

**Answer:**
This topic tests understanding of **Normalization**. A strong interview answer should define the concept, explain why it matters in real systems, discuss advantages and trade-offs, provide a practical example, and describe when you would or would not use the approach. When answering, connect the concept to maintainability, scalability, performance, reliability, security, and developer productivity where relevant.

In your opinion, is it always needed to use database normalization? When is it advisable to use denormalized databases?

#### Blue/Green Deployment

**Answer:**
This topic tests understanding of **Blue/Green Deployment**. A strong interview answer should define the concept, explain why it matters in real systems, discuss advantages and trade-offs, provide a practical example, and describe when you would or would not use the approach. When answering, connect the concept to maintainability, scalability, performance, reliability, security, and developer productivity where relevant.

One of the Continuous Integration's techniques is called Blue-Green Deployment: it consists in having two production environments, as identical as possible, and in performing the deployment in one of them while the other one is still operating, and than in safely switching the traffic to the second one after some convenient testing. This technique becomes more complicated when the deployment includes changes to the database structure or content. I'd like to discuss this topic with you.


### [[↑]](#toc) <a name='nosql'>Questions about NoSQL:</a>

#### Eventual Consistency

**Answer:**
This topic tests understanding of **Eventual Consistency**. A strong interview answer should define the concept, explain why it matters in real systems, discuss advantages and trade-offs, provide a practical example, and describe when you would or would not use the approach. When answering, connect the concept to maintainability, scalability, performance, reliability, security, and developer productivity where relevant.

What is eventual consistency?

#### CAP Theorem

**Answer:**
This topic tests understanding of **CAP Theorem**. A strong interview answer should define the concept, explain why it matters in real systems, discuss advantages and trade-offs, provide a practical example, and describe when you would or would not use the approach. When answering, connect the concept to maintainability, scalability, performance, reliability, security, and developer productivity where relevant.

Brewer's Theorem, most commonly known as the CAP theorem, states that in the presence of a network partition (the P in CAP), a system's designer has to choose between consistency (the C in CAP) and availability (the A in CAP). Can you think about examples of CP, AP and CA systems?

#### NoSQL

**Answer:**
This topic tests understanding of **NoSQL**. A strong interview answer should define the concept, explain why it matters in real systems, discuss advantages and trade-offs, provide a practical example, and describe when you would or would not use the approach. When answering, connect the concept to maintainability, scalability, performance, reliability, security, and developer productivity where relevant.

How would you explain the recent rise in interest in NoSQL?

#### NoSQL and Scalability

**Answer:**
This topic tests understanding of **NoSQL and Scalability**. A strong interview answer should define the concept, explain why it matters in real systems, discuss advantages and trade-offs, provide a practical example, and describe when you would or would not use the approach. When answering, connect the concept to maintainability, scalability, performance, reliability, security, and developer productivity where relevant.

How does NoSQL tackle scalability challenges?

#### Document and Relational DBs

**Answer:**
This topic tests understanding of **Document and Relational DBs**. A strong interview answer should define the concept, explain why it matters in real systems, discuss advantages and trade-offs, provide a practical example, and describe when you would or would not use the approach. When answering, connect the concept to maintainability, scalability, performance, reliability, security, and developer productivity where relevant.

When would you use a document database like MongoDB instead of a relational database like MySQL or PostgreSQL?


### [[↑]](#toc) <a name='codeversioning'>Questions about code versioning:</a>

#### Branching in HG and in Git

**Answer:**
This topic tests understanding of **Branching in HG and in Git**. A strong interview answer should define the concept, explain why it matters in real systems, discuss advantages and trade-offs, provide a practical example, and describe when you would or would not use the approach. When answering, connect the concept to maintainability, scalability, performance, reliability, security, and developer productivity where relevant.

Why is branching with Mercurial or git easier than with SVN?
 
#### DVCS

**Answer:**
This topic tests understanding of **DVCS**. A strong interview answer should define the concept, explain why it matters in real systems, discuss advantages and trade-offs, provide a practical example, and describe when you would or would not use the approach. When answering, connect the concept to maintainability, scalability, performance, reliability, security, and developer productivity where relevant.

What are the pros and cons of distributed version control systems like Git over centralized ones like SVN?

#### GitFlow and GitHubFlow

**Answer:**
This topic tests understanding of **GitFlow and GitHubFlow**. A strong interview answer should define the concept, explain why it matters in real systems, discuss advantages and trade-offs, provide a practical example, and describe when you would or would not use the approach. When answering, connect the concept to maintainability, scalability, performance, reliability, security, and developer productivity where relevant.

Could you describe GitHub Flow and GitFlow workflows?

#### Rebase

**Answer:**
This topic tests understanding of **Rebase**. A strong interview answer should define the concept, explain why it matters in real systems, discuss advantages and trade-offs, provide a practical example, and describe when you would or would not use the approach. When answering, connect the concept to maintainability, scalability, performance, reliability, security, and developer productivity where relevant.

What's a rebase?

#### Merging in HG and in Git

**Answer:**
This topic tests understanding of **Merging in HG and in Git**. A strong interview answer should define the concept, explain why it matters in real systems, discuss advantages and trade-offs, provide a practical example, and describe when you would or would not use the approach. When answering, connect the concept to maintainability, scalability, performance, reliability, security, and developer productivity where relevant.

Why are merges easier with Mercurial and Git than with SVN and CVS?


### [[↑]](#toc) <a name='concurrency'>Questions about Concurrency:</a>

#### Why?

**Answer:**
This topic tests understanding of **Why?**. A strong interview answer should define the concept, explain why it matters in real systems, discuss advantages and trade-offs, provide a practical example, and describe when you would or would not use the approach. When answering, connect the concept to maintainability, scalability, performance, reliability, security, and developer productivity where relevant.

Why do we need concurrency, anyway? Explain.

#### Testing Concurrency

**Answer:**
This topic tests understanding of **Testing Concurrency**. A strong interview answer should define the concept, explain why it matters in real systems, discuss advantages and trade-offs, provide a practical example, and describe when you would or would not use the approach. When answering, connect the concept to maintainability, scalability, performance, reliability, security, and developer productivity where relevant.

Why is testing multithreaded/concurrent code so difficult?

#### Race Conditions

**Answer:**
This topic tests understanding of **Race Conditions**. A strong interview answer should define the concept, explain why it matters in real systems, discuss advantages and trade-offs, provide a practical example, and describe when you would or would not use the approach. When answering, connect the concept to maintainability, scalability, performance, reliability, security, and developer productivity where relevant.

What is a race condition? Code an example, using whatever language you like.

#### Deadlocks

**Answer:**
This topic tests understanding of **Deadlocks**. A strong interview answer should define the concept, explain why it matters in real systems, discuss advantages and trade-offs, provide a practical example, and describe when you would or would not use the approach. When answering, connect the concept to maintainability, scalability, performance, reliability, security, and developer productivity where relevant.

What is a deadlock? Would you be able to write some code that is affected by deadlocks?

#### Process Starvation

**Answer:**
This topic tests understanding of **Process Starvation**. A strong interview answer should define the concept, explain why it matters in real systems, discuss advantages and trade-offs, provide a practical example, and describe when you would or would not use the approach. When answering, connect the concept to maintainability, scalability, performance, reliability, security, and developer productivity where relevant.

What is process starvation? If you need, let's review its definition.

#### Free Algorithm

**Answer:**
This topic tests understanding of **Free Algorithm**. A strong interview answer should define the concept, explain why it matters in real systems, discuss advantages and trade-offs, provide a practical example, and describe when you would or would not use the approach. When answering, connect the concept to maintainability, scalability, performance, reliability, security, and developer productivity where relevant.

What is a wait free algorithm?


### [[↑]](#toc) <a name='distributed'>Questions about Distributed Systems:</a>

#### Testing Distributed Systems

**Answer:**
This topic tests understanding of **Testing Distributed Systems**. A strong interview answer should define the concept, explain why it matters in real systems, discuss advantages and trade-offs, provide a practical example, and describe when you would or would not use the approach. When answering, connect the concept to maintainability, scalability, performance, reliability, security, and developer productivity where relevant.

How would you test a distributed system?

#### Async Communication

**Answer:**
This topic tests understanding of **Async Communication**. A strong interview answer should define the concept, explain why it matters in real systems, discuss advantages and trade-offs, provide a practical example, and describe when you would or would not use the approach. When answering, connect the concept to maintainability, scalability, performance, reliability, security, and developer productivity where relevant.

When would you apply asynchronous communication between two systems?

#### Pitfalls of RPC

**Answer:**
This topic tests understanding of **Pitfalls of RPC**. A strong interview answer should define the concept, explain why it matters in real systems, discuss advantages and trade-offs, provide a practical example, and describe when you would or would not use the approach. When answering, connect the concept to maintainability, scalability, performance, reliability, security, and developer productivity where relevant.

What are the general pitfalls of remote procedure calls?

#### Design of Distributed Systems

**Answer:**
This topic tests understanding of **Design of Distributed Systems**. A strong interview answer should define the concept, explain why it matters in real systems, discuss advantages and trade-offs, provide a practical example, and describe when you would or would not use the approach. When answering, connect the concept to maintainability, scalability, performance, reliability, security, and developer productivity where relevant.

If you are building a distributed system for scalability and robustness, what are the different things you'd think of if you are working in a closed and secure network environment versus when you are working in a geographically distributed and public system?

#### Fault Tolerance

**Answer:**
This topic tests understanding of **Fault Tolerance**. A strong interview answer should define the concept, explain why it matters in real systems, discuss advantages and trade-offs, provide a practical example, and describe when you would or would not use the approach. When answering, connect the concept to maintainability, scalability, performance, reliability, security, and developer productivity where relevant.

How would you manage fault tolerance in a web application? What about in a desktop one?

#### Failures

**Answer:**
This topic tests understanding of **Failures**. A strong interview answer should define the concept, explain why it matters in real systems, discuss advantages and trade-offs, provide a practical example, and describe when you would or would not use the approach. When answering, connect the concept to maintainability, scalability, performance, reliability, security, and developer productivity where relevant.

How would you deal with failures in a distributed system?

#### Network Partitions

**Answer:**
This topic tests understanding of **Network Partitions**. A strong interview answer should define the concept, explain why it matters in real systems, discuss advantages and trade-offs, provide a practical example, and describe when you would or would not use the approach. When answering, connect the concept to maintainability, scalability, performance, reliability, security, and developer productivity where relevant.

Let's talk about the several approaches to reconciliation after network partitions.

#### Fallacies of Distributed Computing

**Answer:**
This topic tests understanding of **Fallacies of Distributed Computing**. A strong interview answer should define the concept, explain why it matters in real systems, discuss advantages and trade-offs, provide a practical example, and describe when you would or would not use the approach. When answering, connect the concept to maintainability, scalability, performance, reliability, security, and developer productivity where relevant.

What are the fallacies of distributed computing?

#### Request/Reply vs Publish/Subscribe

**Answer:**
This topic tests understanding of **Request/Reply vs Publish/Subscribe**. A strong interview answer should define the concept, explain why it matters in real systems, discuss advantages and trade-offs, provide a practical example, and describe when you would or would not use the approach. When answering, connect the concept to maintainability, scalability, performance, reliability, security, and developer productivity where relevant.

When would you use request/reply and when publish/subscribe?

#### Implement Transactions

**Answer:**
This topic tests understanding of **Implement Transactions**. A strong interview answer should define the concept, explain why it matters in real systems, discuss advantages and trade-offs, provide a practical example, and describe when you would or would not use the approach. When answering, connect the concept to maintainability, scalability, performance, reliability, security, and developer productivity where relevant.

Suppose the system you are working on does not support transactionality. How would you implement it from scratch?


### [[↑]](#toc) <a name='management'>Questions about Software Lifecycle and Team Management:</a>

#### Agility

**Answer:**
This topic tests understanding of **Agility**. A strong interview answer should define the concept, explain why it matters in real systems, discuss advantages and trade-offs, provide a practical example, and describe when you would or would not use the approach. When answering, connect the concept to maintainability, scalability, performance, reliability, security, and developer productivity where relevant.

What is agility?

#### Legacy Code

**Answer:**
This topic tests understanding of **Legacy Code**. A strong interview answer should define the concept, explain why it matters in real systems, discuss advantages and trade-offs, provide a practical example, and describe when you would or would not use the approach. When answering, connect the concept to maintainability, scalability, performance, reliability, security, and developer productivity where relevant.

How would you deal with legacy code?

#### Legacy Code ELI5

**Answer:**
This topic tests understanding of **Legacy Code ELI5**. A strong interview answer should define the concept, explain why it matters in real systems, discuss advantages and trade-offs, provide a practical example, and describe when you would or would not use the approach. When answering, connect the concept to maintainability, scalability, performance, reliability, security, and developer productivity where relevant.

Say I'm your project manager, and I'm no expert in programming. Would you try explaining to me what legacy code is and why should I care about code quality?

#### Sell me Kanban

**Answer:**
This topic tests understanding of **Sell me Kanban**. A strong interview answer should define the concept, explain why it matters in real systems, discuss advantages and trade-offs, provide a practical example, and describe when you would or would not use the approach. When answering, connect the concept to maintainability, scalability, performance, reliability, security, and developer productivity where relevant.

I'm the CEO of your company. Explain to me Kanban and convince me to invest in it.

#### Agile vs Waterfall

**Answer:**
This topic tests understanding of **Agile vs Waterfall**. A strong interview answer should define the concept, explain why it matters in real systems, discuss advantages and trade-offs, provide a practical example, and describe when you would or would not use the approach. When answering, connect the concept to maintainability, scalability, performance, reliability, security, and developer productivity where relevant.

What is the biggest difference between Agile and Waterfall?

#### Death by Meetings

**Answer:**
This topic tests understanding of **Death by Meetings**. A strong interview answer should define the concept, explain why it matters in real systems, discuss advantages and trade-offs, provide a practical example, and describe when you would or would not use the approach. When answering, connect the concept to maintainability, scalability, performance, reliability, security, and developer productivity where relevant.

Being a team manager, how would you deal with the problem of having too many meetings?

#### Late Projects

**Answer:**
This topic tests understanding of **Late Projects**. A strong interview answer should define the concept, explain why it matters in real systems, discuss advantages and trade-offs, provide a practical example, and describe when you would or would not use the approach. When answering, connect the concept to maintainability, scalability, performance, reliability, security, and developer productivity where relevant.

How would you manage a very late project?

#### Agile Manifesto

**Answer:**
This topic tests understanding of **Agile Manifesto**. A strong interview answer should define the concept, explain why it matters in real systems, discuss advantages and trade-offs, provide a practical example, and describe when you would or would not use the approach. When answering, connect the concept to maintainability, scalability, performance, reliability, security, and developer productivity where relevant.

"*Individuals and interactions over processes and tools*" and "*Customer collaboration over contract negotiation*" comprise half of the values of the Agile Manifesto. Discuss

#### If I were the CTO

**Answer:**
This topic tests understanding of **If I were the CTO**. A strong interview answer should define the concept, explain why it matters in real systems, discuss advantages and trade-offs, provide a practical example, and describe when you would or would not use the approach. When answering, connect the concept to maintainability, scalability, performance, reliability, security, and developer productivity where relevant.

Tell me what decisions would you take if you could be the CTO of your Company.

#### PMs

**Answer:**
This topic tests understanding of **PMs**. A strong interview answer should define the concept, explain why it matters in real systems, discuss advantages and trade-offs, provide a practical example, and describe when you would or would not use the approach. When answering, connect the concept to maintainability, scalability, performance, reliability, security, and developer productivity where relevant.

Are program managers useful?

#### Team Organization

**Answer:**
This topic tests understanding of **Team Organization**. A strong interview answer should define the concept, explain why it matters in real systems, discuss advantages and trade-offs, provide a practical example, and describe when you would or would not use the approach. When answering, connect the concept to maintainability, scalability, performance, reliability, security, and developer productivity where relevant.

Organize a development team using flexible schedules (that is, no imposed working hours) and "take as you need" vacation policy

#### Turn Over

**Answer:**
This topic tests understanding of **Turn Over**. A strong interview answer should define the concept, explain why it matters in real systems, discuss advantages and trade-offs, provide a practical example, and describe when you would or would not use the approach. When answering, connect the concept to maintainability, scalability, performance, reliability, security, and developer productivity where relevant.

How would you manage a very high turn over and convince developers not to leave the team, without increasing compensation? What could a company improve to make them stay?

#### Qualities

**Answer:**
This topic tests understanding of **Qualities**. A strong interview answer should define the concept, explain why it matters in real systems, discuss advantages and trade-offs, provide a practical example, and describe when you would or would not use the approach. When answering, connect the concept to maintainability, scalability, performance, reliability, security, and developer productivity where relevant.

What are the top 3 qualities you look for in colleagues, beyond their code?

#### 3 Things About Code

**Answer:**
This topic tests understanding of **3 Things About Code**. A strong interview answer should define the concept, explain why it matters in real systems, discuss advantages and trade-offs, provide a practical example, and describe when you would or would not use the approach. When answering, connect the concept to maintainability, scalability, performance, reliability, security, and developer productivity where relevant.

What are the top 3 things you wish non-technical people knew about code?

#### 1 month's revolution

**Answer:**
This topic tests understanding of **1 month's revolution**. A strong interview answer should define the concept, explain why it matters in real systems, discuss advantages and trade-offs, provide a practical example, and describe when you would or would not use the approach. When answering, connect the concept to maintainability, scalability, performance, reliability, security, and developer productivity where relevant.

Imagine your company gives you 1 month and some budget to improve your and your colleagues' daily life. What would you do?


### [[↑]](#toc) <a name='algorithms'>Questions about logic and algorithms:</a>

#### FIFO with LIFO

**Answer:**
This topic tests understanding of **FIFO with LIFO**. A strong interview answer should define the concept, explain why it matters in real systems, discuss advantages and trade-offs, provide a practical example, and describe when you would or would not use the approach. When answering, connect the concept to maintainability, scalability, performance, reliability, security, and developer productivity where relevant.

Make a FIFO queue using only LIFO stacks. Then build a LIFO stack using only FIFO queues.

#### Stack Overflow

**Answer:**
This topic tests understanding of **Stack Overflow**. A strong interview answer should define the concept, explain why it matters in real systems, discuss advantages and trade-offs, provide a practical example, and describe when you would or would not use the approach. When answering, connect the concept to maintainability, scalability, performance, reliability, security, and developer productivity where relevant.

Write a snippet of code affected by a stack overflow.

#### Tail Recursive n!

**Answer:**
This topic tests understanding of **Tail Recursive n!**. A strong interview answer should define the concept, explain why it matters in real systems, discuss advantages and trade-offs, provide a practical example, and describe when you would or would not use the approach. When answering, connect the concept to maintainability, scalability, performance, reliability, security, and developer productivity where relevant.

Write a tail-recursive version of the factorial function.
#### REPL

**Answer:**
This topic tests understanding of **REPL**. A strong interview answer should define the concept, explain why it matters in real systems, discuss advantages and trade-offs, provide a practical example, and describe when you would or would not use the approach. When answering, connect the concept to maintainability, scalability, performance, reliability, security, and developer productivity where relevant.

Using your preferred language, write a REPL that echoes your inputs. Evolve it to make it an RPN calculator.

#### Defragger

**Answer:**
This topic tests understanding of **Defragger**. A strong interview answer should define the concept, explain why it matters in real systems, discuss advantages and trade-offs, provide a practical example, and describe when you would or would not use the approach. When answering, connect the concept to maintainability, scalability, performance, reliability, security, and developer productivity where relevant.

How would you design a "defragger" utility?

#### Mazes

**Answer:**
This topic tests understanding of **Mazes**. A strong interview answer should define the concept, explain why it matters in real systems, discuss advantages and trade-offs, provide a practical example, and describe when you would or would not use the approach. When answering, connect the concept to maintainability, scalability, performance, reliability, security, and developer productivity where relevant.

Write a program that builds random mazes.

#### Memory Leaks

**Answer:**
This topic tests understanding of **Memory Leaks**. A strong interview answer should define the concept, explain why it matters in real systems, discuss advantages and trade-offs, provide a practical example, and describe when you would or would not use the approach. When answering, connect the concept to maintainability, scalability, performance, reliability, security, and developer productivity where relevant.

Write a sample program that produces a memory leak.

#### PRNG

**Answer:**
This topic tests understanding of **PRNG**. A strong interview answer should define the concept, explain why it matters in real systems, discuss advantages and trade-offs, provide a practical example, and describe when you would or would not use the approach. When answering, connect the concept to maintainability, scalability, performance, reliability, security, and developer productivity where relevant.

Generate a sequence of unique random numbers.

#### Garbage Collecting

**Answer:**
This topic tests understanding of **Garbage Collecting**. A strong interview answer should define the concept, explain why it matters in real systems, discuss advantages and trade-offs, provide a practical example, and describe when you would or would not use the approach. When answering, connect the concept to maintainability, scalability, performance, reliability, security, and developer productivity where relevant.

Write a simple garbage collection system.

#### Queues

**Answer:**
This topic tests understanding of **Queues**. A strong interview answer should define the concept, explain why it matters in real systems, discuss advantages and trade-offs, provide a practical example, and describe when you would or would not use the approach. When answering, connect the concept to maintainability, scalability, performance, reliability, security, and developer productivity where relevant.

Write a basic message broker, using whatever language you like.

#### Simple Web Server

**Answer:**
This topic tests understanding of **Simple Web Server**. A strong interview answer should define the concept, explain why it matters in real systems, discuss advantages and trade-offs, provide a practical example, and describe when you would or would not use the approach. When answering, connect the concept to maintainability, scalability, performance, reliability, security, and developer productivity where relevant.

Write a very basic web server. Draw a road map for features to be implemented in the future.

#### Sorting Huge Files

**Answer:**
This topic tests understanding of **Sorting Huge Files**. A strong interview answer should define the concept, explain why it matters in real systems, discuss advantages and trade-offs, provide a practical example, and describe when you would or would not use the approach. When answering, connect the concept to maintainability, scalability, performance, reliability, security, and developer productivity where relevant.

How would you sort a 10GB file? How would your approach change with a 10TB one?

#### Duplicates

**Answer:**
This topic tests understanding of **Duplicates**. A strong interview answer should define the concept, explain why it matters in real systems, discuss advantages and trade-offs, provide a practical example, and describe when you would or would not use the approach. When answering, connect the concept to maintainability, scalability, performance, reliability, security, and developer productivity where relevant.

How would you programmatically detect file duplicates?

### [[↑]](#toc) <a name='architecture'>Questions about Software Architecture:</a>

#### No Cache

**Answer:**
This topic tests understanding of **No Cache**. A strong interview answer should define the concept, explain why it matters in real systems, discuss advantages and trade-offs, provide a practical example, and describe when you would or would not use the approach. When answering, connect the concept to maintainability, scalability, performance, reliability, security, and developer productivity where relevant.

When is a cache not useful or even dangerous?

#### Event-Driven Architecture

**Answer:**
This topic tests understanding of **Event-Driven Architecture**. A strong interview answer should define the concept, explain why it matters in real systems, discuss advantages and trade-offs, provide a practical example, and describe when you would or would not use the approach. When answering, connect the concept to maintainability, scalability, performance, reliability, security, and developer productivity where relevant.

Why does Event-Driven Architecture improve scalability?

#### Readability

**Answer:**
This topic tests understanding of **Readability**. A strong interview answer should define the concept, explain why it matters in real systems, discuss advantages and trade-offs, provide a practical example, and describe when you would or would not use the approach. When answering, connect the concept to maintainability, scalability, performance, reliability, security, and developer productivity where relevant.

What makes code readable?

#### Emergent and Evolutionary

**Answer:**
This topic tests understanding of **Emergent and Evolutionary**. A strong interview answer should define the concept, explain why it matters in real systems, discuss advantages and trade-offs, provide a practical example, and describe when you would or would not use the approach. When answering, connect the concept to maintainability, scalability, performance, reliability, security, and developer productivity where relevant.

What is the difference between emergent design and evolutionary architecture?

#### Scale-Out, Scale-Up

**Answer:**
This topic tests understanding of **Scale-Out, Scale-Up**. A strong interview answer should define the concept, explain why it matters in real systems, discuss advantages and trade-offs, provide a practical example, and describe when you would or would not use the approach. When answering, connect the concept to maintainability, scalability, performance, reliability, security, and developer productivity where relevant.

Scale out vs scale up: how are they different? When to apply one, when the other?

#### Failures User Sessions

**Answer:**
This topic tests understanding of **Failures User Sessions**. A strong interview answer should define the concept, explain why it matters in real systems, discuss advantages and trade-offs, provide a practical example, and describe when you would or would not use the approach. When answering, connect the concept to maintainability, scalability, performance, reliability, security, and developer productivity where relevant.

How to deal with failover and user sessions?

#### CQRS

**Answer:**
This topic tests understanding of **CQRS**. A strong interview answer should define the concept, explain why it matters in real systems, discuss advantages and trade-offs, provide a practical example, and describe when you would or would not use the approach. When answering, connect the concept to maintainability, scalability, performance, reliability, security, and developer productivity where relevant.

What is CQRS (Command Query Responsibility Segregation)? How is it different from the oldest Command-Query Separation Principle?

#### n-tier

**Answer:**
This topic tests understanding of **n-tier**. A strong interview answer should define the concept, explain why it matters in real systems, discuss advantages and trade-offs, provide a practical example, and describe when you would or would not use the approach. When answering, connect the concept to maintainability, scalability, performance, reliability, security, and developer productivity where relevant.

The so called "multitier architecture" is an approach to design a client–server system aimed to keep physically and logically separated presentation, application processing, data management and other functions. The most widespread of the multitier architectures is the three-tier architecture. Would you discuss the pros and cons of such an approach?

#### Scalability

**Answer:**
This topic tests understanding of **Scalability**. A strong interview answer should define the concept, explain why it matters in real systems, discuss advantages and trade-offs, provide a practical example, and describe when you would or would not use the approach. When answering, connect the concept to maintainability, scalability, performance, reliability, security, and developer productivity where relevant.

How would you design a software system for scalability?

#### C10K

**Answer:**
This topic tests understanding of **C10K**. A strong interview answer should define the concept, explain why it matters in real systems, discuss advantages and trade-offs, provide a practical example, and describe when you would or would not use the approach. When answering, connect the concept to maintainability, scalability, performance, reliability, security, and developer productivity where relevant.

Someone gave the name "The "C10k problem" to the problem of optimising network sockets to handle over 10.000 open connections at once. While handling 10.000 concurrent clients is not the same as handling 10.000 open connection, the context is similar. It's a tough challenge anyway, and no one is expected to know every single detail to solve it. It may be interesting to discuss the strategies you know to deal with that problem. Would you like to try?

#### P2P

**Answer:**
This topic tests understanding of **P2P**. A strong interview answer should define the concept, explain why it matters in real systems, discuss advantages and trade-offs, provide a practical example, and describe when you would or would not use the approach. When answering, connect the concept to maintainability, scalability, performance, reliability, security, and developer productivity where relevant.

How would you design a decentralized (that is, with no central server) P2P system?

#### CGI

**Answer:**
This topic tests understanding of **CGI**. A strong interview answer should define the concept, explain why it matters in real systems, discuss advantages and trade-offs, provide a practical example, and describe when you would or would not use the approach. When answering, connect the concept to maintainability, scalability, performance, reliability, security, and developer productivity where relevant.

You may recall that Common Gateway Interface (CGI) is a standard protocol for web servers to execute programs (CGI scripts) that execute as Command-line programs on a server, and that dynamically generate HTML pages when invoked by a HTTP request. Perl and PHP used to be common languages for such scripts. In CGI, a HTTP request generally causes the invocation of a new process on the server, but FastCGI, SCGI and other approaches improved the mechanism, raising the performance, with techniques such as preforking processes. Can you discuss why CGI became obsolete, and was instead replaced with other architectural approaches?

#### Vendor Lock-in

**Answer:**
This topic tests understanding of **Vendor Lock-in**. A strong interview answer should define the concept, explain why it matters in real systems, discuss advantages and trade-offs, provide a practical example, and describe when you would or would not use the approach. When answering, connect the concept to maintainability, scalability, performance, reliability, security, and developer productivity where relevant.

How would you defend the design of your systems against vendor Lock-in?

#### Pub/Sub

**Answer:**
This topic tests understanding of **Pub/Sub**. A strong interview answer should define the concept, explain why it matters in real systems, discuss advantages and trade-offs, provide a practical example, and describe when you would or would not use the approach. When answering, connect the concept to maintainability, scalability, performance, reliability, security, and developer productivity where relevant.

What are the disadvantages of the publish-subscribe pattern at scale?

#### CPUs

**Answer:**
This topic tests understanding of **CPUs**. A strong interview answer should define the concept, explain why it matters in real systems, discuss advantages and trade-offs, provide a practical example, and describe when you would or would not use the approach. When answering, connect the concept to maintainability, scalability, performance, reliability, security, and developer productivity where relevant.

What's new in CPUs since the 80s, and how does it affect programming?

#### Performance

**Answer:**
This topic tests understanding of **Performance**. A strong interview answer should define the concept, explain why it matters in real systems, discuss advantages and trade-offs, provide a practical example, and describe when you would or would not use the approach. When answering, connect the concept to maintainability, scalability, performance, reliability, security, and developer productivity where relevant.

In which part of the lifecycle of a software performance should be taken in consideration, and how?

#### DDOS

**Answer:**
This topic tests understanding of **DDOS**. A strong interview answer should define the concept, explain why it matters in real systems, discuss advantages and trade-offs, provide a practical example, and describe when you would or would not use the approach. When answering, connect the concept to maintainability, scalability, performance, reliability, security, and developer productivity where relevant.

How could a denial of service arise not maliciously but due to a design or architectural problem?

#### Performance and Scalability

**Answer:**
This topic tests understanding of **Performance and Scalability**. A strong interview answer should define the concept, explain why it matters in real systems, discuss advantages and trade-offs, provide a practical example, and describe when you would or would not use the approach. When answering, connect the concept to maintainability, scalability, performance, reliability, security, and developer productivity where relevant.

What’s the relationship between performance and scalability?

#### Tight Coupling

**Answer:**
This topic tests understanding of **Tight Coupling**. A strong interview answer should define the concept, explain why it matters in real systems, discuss advantages and trade-offs, provide a practical example, and describe when you would or would not use the approach. When answering, connect the concept to maintainability, scalability, performance, reliability, security, and developer productivity where relevant.

When is it OK (if ever) to use tight coupling?

#### Cloud Readiness

**Answer:**
This topic tests understanding of **Cloud Readiness**. A strong interview answer should define the concept, explain why it matters in real systems, discuss advantages and trade-offs, provide a practical example, and describe when you would or would not use the approach. When answering, connect the concept to maintainability, scalability, performance, reliability, security, and developer productivity where relevant.

What characteristic should a system have to be cloud ready?

#### Emergent Architecture

**Answer:**
This topic tests understanding of **Emergent Architecture**. A strong interview answer should define the concept, explain why it matters in real systems, discuss advantages and trade-offs, provide a practical example, and describe when you would or would not use the approach. When answering, connect the concept to maintainability, scalability, performance, reliability, security, and developer productivity where relevant.

Does unity of design imply an aristocracy of architects? Putting it simple: can good design emerge from a collective effort of all developers?

#### Design, Architecture, Functionality, Aesthetic

**Answer:**
This topic tests understanding of **Design, Architecture, Functionality, Aesthetic**. A strong interview answer should define the concept, explain why it matters in real systems, discuss advantages and trade-offs, provide a practical example, and describe when you would or would not use the approach. When answering, connect the concept to maintainability, scalability, performance, reliability, security, and developer productivity where relevant.

What's the difference between design, architecture, functionality and aesthetic? Discuss.



### [[↑]](#toc) <a name='soa'>Questions about Service Oriented Architecture and Microservices:</a>

#### Long-lived Transactions

**Answer:**
This topic tests understanding of **Long-lived Transactions**. A strong interview answer should define the concept, explain why it matters in real systems, discuss advantages and trade-offs, provide a practical example, and describe when you would or would not use the approach. When answering, connect the concept to maintainability, scalability, performance, reliability, security, and developer productivity where relevant.

Why, in a SOA, long-lived transactions are discouraged and sagas are suggested instead?

#### SOA and Micro Services

**Answer:**
This topic tests understanding of **SOA and Micro Services**. A strong interview answer should define the concept, explain why it matters in real systems, discuss advantages and trade-offs, provide a practical example, and describe when you would or would not use the approach. When answering, connect the concept to maintainability, scalability, performance, reliability, security, and developer productivity where relevant.

What are the differences between SOA and microservice?

#### Versioning and Breaking Changes

**Answer:**
This topic tests understanding of **Versioning and Breaking Changes**. A strong interview answer should define the concept, explain why it matters in real systems, discuss advantages and trade-offs, provide a practical example, and describe when you would or would not use the approach. When answering, connect the concept to maintainability, scalability, performance, reliability, security, and developer productivity where relevant.

Let's talk about web services versioning, version compatibility and breaking changes.

#### Sagas and compensations

**Answer:**
This topic tests understanding of **Sagas and compensations**. A strong interview answer should define the concept, explain why it matters in real systems, discuss advantages and trade-offs, provide a practical example, and describe when you would or would not use the approach. When answering, connect the concept to maintainability, scalability, performance, reliability, security, and developer productivity where relevant.

What's the difference between a transaction and a compensation operation in a saga, in SOA?

#### Too Micro

**Answer:**
This topic tests understanding of **Too Micro**. A strong interview answer should define the concept, explain why it matters in real systems, discuss advantages and trade-offs, provide a practical example, and describe when you would or would not use the approach. When answering, connect the concept to maintainability, scalability, performance, reliability, security, and developer productivity where relevant.

When is a microservice too micro?

#### Micro Services Architecture

**Answer:**
This topic tests understanding of **Micro Services Architecture**. A strong interview answer should define the concept, explain why it matters in real systems, discuss advantages and trade-offs, provide a practical example, and describe when you would or would not use the approach. When answering, connect the concept to maintainability, scalability, performance, reliability, security, and developer productivity where relevant.

What are the pros and cons of microservice architecture?


### [[↑]](#toc) <a name='security'>Questions about Security:</a>
#### Security by Default

**Answer:**
This topic tests understanding of **Security by Default**. A strong interview answer should define the concept, explain why it matters in real systems, discuss advantages and trade-offs, provide a practical example, and describe when you would or would not use the approach. When answering, connect the concept to maintainability, scalability, performance, reliability, security, and developer productivity where relevant.

How do you write secure code? In your opinion, is it one of the developer's duties, or does it require a specialized role in the company? And why?

#### Don't Invent Cryptography

**Answer:**
This topic tests understanding of **Don't Invent Cryptography**. A strong interview answer should define the concept, explain why it matters in real systems, discuss advantages and trade-offs, provide a practical example, and describe when you would or would not use the approach. When answering, connect the concept to maintainability, scalability, performance, reliability, security, and developer productivity where relevant.

Why is it said that cryptography is not something you should try to invent or design yourself?

#### 2-FA

**Answer:**
This topic tests understanding of **2-FA**. A strong interview answer should define the concept, explain why it matters in real systems, discuss advantages and trade-offs, provide a practical example, and describe when you would or would not use the approach. When answering, connect the concept to maintainability, scalability, performance, reliability, security, and developer productivity where relevant.

What is two factor authentication? How would you implement it in an existing web application?

#### Confidential Data in Logs

**Answer:**
This topic tests understanding of **Confidential Data in Logs**. A strong interview answer should define the concept, explain why it matters in real systems, discuss advantages and trade-offs, provide a practical example, and describe when you would or would not use the approach. When answering, connect the concept to maintainability, scalability, performance, reliability, security, and developer productivity where relevant.

If not carefully handled, there is always a risk of logs containing sensitive information, such as passwords. How would you deal with this?

#### SQL Injection

**Answer:**
This topic tests understanding of **SQL Injection**. A strong interview answer should define the concept, explain why it matters in real systems, discuss advantages and trade-offs, provide a practical example, and describe when you would or would not use the approach. When answering, connect the concept to maintainability, scalability, performance, reliability, security, and developer productivity where relevant.

Write down a snippet of code affected by SQL injection and fix it.

#### Detect SQL Injection

**Answer:**
This topic tests understanding of **Detect SQL Injection**. A strong interview answer should define the concept, explain why it matters in real systems, discuss advantages and trade-offs, provide a practical example, and describe when you would or would not use the approach. When answering, connect the concept to maintainability, scalability, performance, reliability, security, and developer productivity where relevant.

How would it be possible to detect SQL injection via static code analysis? I don't expect you to write an algorithm capable of doing this, as it is probably a huge topic, but let's discuss a general approach.

#### XSS

**Answer:**
This topic tests understanding of **XSS**. A strong interview answer should define the concept, explain why it matters in real systems, discuss advantages and trade-offs, provide a practical example, and describe when you would or would not use the approach. When answering, connect the concept to maintainability, scalability, performance, reliability, security, and developer productivity where relevant.

What do you know about Cross-Site Scripting? If you don't remember it, let's review online its definition and let's discuss about it.

#### Cross-Site Forgery Attack

**Answer:**
This topic tests understanding of **Cross-Site Forgery Attack**. A strong interview answer should define the concept, explain why it matters in real systems, discuss advantages and trade-offs, provide a practical example, and describe when you would or would not use the approach. When answering, connect the concept to maintainability, scalability, performance, reliability, security, and developer productivity where relevant.

What do you know about Cross-Site Forgery Attack? If you don't remember it, let's review online its definition and let's discuss about it.

#### HTTPS

**Answer:**
This topic tests understanding of **HTTPS**. A strong interview answer should define the concept, explain why it matters in real systems, discuss advantages and trade-offs, provide a practical example, and describe when you would or would not use the approach. When answering, connect the concept to maintainability, scalability, performance, reliability, security, and developer productivity where relevant.

How does HTTPS work?

#### MITM Attack

**Answer:**
This topic tests understanding of **MITM Attack**. A strong interview answer should define the concept, explain why it matters in real systems, discuss advantages and trade-offs, provide a practical example, and describe when you would or would not use the approach. When answering, connect the concept to maintainability, scalability, performance, reliability, security, and developer productivity where relevant.

What's a man-in-the-middle Attack, and why does HTTPS help protect against it?

#### Stealing Sessions

**Answer:**
This topic tests understanding of **Stealing Sessions**. A strong interview answer should define the concept, explain why it matters in real systems, discuss advantages and trade-offs, provide a practical example, and describe when you would or would not use the approach. When answering, connect the concept to maintainability, scalability, performance, reliability, security, and developer productivity where relevant.

How can you prevent the user's session from being stolen? Chances are you remember what session or cookie hijacking is, otherwise let's read its Wikipedia page together.


### [[↑]](#toc) <a name='general'>General Questions:</a>

#### Why FP?

**Answer:**
This topic tests understanding of **Why FP?**. A strong interview answer should define the concept, explain why it matters in real systems, discuss advantages and trade-offs, provide a practical example, and describe when you would or would not use the approach. When answering, connect the concept to maintainability, scalability, performance, reliability, security, and developer productivity where relevant.

Why does functional programming matter? When should a functional programming language be used?

#### Browsers

**Answer:**
This topic tests understanding of **Browsers**. A strong interview answer should define the concept, explain why it matters in real systems, discuss advantages and trade-offs, provide a practical example, and describe when you would or would not use the approach. When answering, connect the concept to maintainability, scalability, performance, reliability, security, and developer productivity where relevant.

How do companies like Microsoft, Google, Opera and Mozilla profit from their browsers?

#### TCP Sockets

**Answer:**
This topic tests understanding of **TCP Sockets**. A strong interview answer should define the concept, explain why it matters in real systems, discuss advantages and trade-offs, provide a practical example, and describe when you would or would not use the approach. When answering, connect the concept to maintainability, scalability, performance, reliability, security, and developer productivity where relevant.

Why does opening a TCP socket have a large overhead?

#### Encapsulation

**Answer:**
This topic tests understanding of **Encapsulation**. A strong interview answer should define the concept, explain why it matters in real systems, discuss advantages and trade-offs, provide a practical example, and describe when you would or would not use the approach. When answering, connect the concept to maintainability, scalability, performance, reliability, security, and developer productivity where relevant.

What is encapsulation important for?

#### Real-time systems

**Answer:**
This topic tests understanding of **Real-time systems**. A strong interview answer should define the concept, explain why it matters in real systems, discuss advantages and trade-offs, provide a practical example, and describe when you would or would not use the approach. When answering, connect the concept to maintainability, scalability, performance, reliability, security, and developer productivity where relevant.

What is a real-time system and how is it different from an ordinary system?

#### Real-time and memory allocation

**Answer:**
This topic tests understanding of **Real-time and memory allocation**. A strong interview answer should define the concept, explain why it matters in real systems, discuss advantages and trade-offs, provide a practical example, and describe when you would or would not use the approach. When answering, connect the concept to maintainability, scalability, performance, reliability, security, and developer productivity where relevant.

What's the relationship between real-time languages and heap memory allocation?

#### Immutability

**Answer:**
This topic tests understanding of **Immutability**. A strong interview answer should define the concept, explain why it matters in real systems, discuss advantages and trade-offs, provide a practical example, and describe when you would or would not use the approach. When answering, connect the concept to maintainability, scalability, performance, reliability, security, and developer productivity where relevant.

Immutability is the practice of setting values once, at the moment of their creation, and never changing them. How can immutability help write safer code?

#### Mutable vs Immutable

**Answer:**
This topic tests understanding of **Mutable vs Immutable**. A strong interview answer should define the concept, explain why it matters in real systems, discuss advantages and trade-offs, provide a practical example, and describe when you would or would not use the approach. When answering, connect the concept to maintainability, scalability, performance, reliability, security, and developer productivity where relevant.

What are the pros and cons of mutable and immutable values.

#### Object-Relational Impedance Mismatch

**Answer:**
This topic tests understanding of **Object-Relational Impedance Mismatch**. A strong interview answer should define the concept, explain why it matters in real systems, discuss advantages and trade-offs, provide a practical example, and describe when you would or would not use the approach. When answering, connect the concept to maintainability, scalability, performance, reliability, security, and developer productivity where relevant.

What's the Object-Relational impedance mismatch?

#### Sizing a Cache

**Answer:**
This topic tests understanding of **Sizing a Cache**. A strong interview answer should define the concept, explain why it matters in real systems, discuss advantages and trade-offs, provide a practical example, and describe when you would or would not use the approach. When answering, connect the concept to maintainability, scalability, performance, reliability, security, and developer productivity where relevant.

Which principles would you apply to define the size of a cache?

#### TCP and HTTP

**Answer:**
This topic tests understanding of **TCP and HTTP**. A strong interview answer should define the concept, explain why it matters in real systems, discuss advantages and trade-offs, provide a practical example, and describe when you would or would not use the approach. When answering, connect the concept to maintainability, scalability, performance, reliability, security, and developer productivity where relevant.

What's the difference between TCP and HTTP?

#### Client-Side vs Server-Side

**Answer:**
This topic tests understanding of **Client-Side vs Server-Side**. A strong interview answer should define the concept, explain why it matters in real systems, discuss advantages and trade-offs, provide a practical example, and describe when you would or would not use the approach. When answering, connect the concept to maintainability, scalability, performance, reliability, security, and developer productivity where relevant.

What are the tradeoffs of client-side rendering vs. server-side rendering?

#### Reliable and non-reliable channels

**Answer:**
This topic tests understanding of **Reliable and non-reliable channels**. A strong interview answer should define the concept, explain why it matters in real systems, discuss advantages and trade-offs, provide a practical example, and describe when you would or would not use the approach. When answering, connect the concept to maintainability, scalability, performance, reliability, security, and developer productivity where relevant.

How could you develop a reliable communication protocol based on a non-reliable one?




### [[↑]](#toc) <a name='open'>Open Questions:</a>

#### Resistance to Change

**Answer:**
This topic tests understanding of **Resistance to Change**. A strong interview answer should define the concept, explain why it matters in real systems, discuss advantages and trade-offs, provide a practical example, and describe when you would or would not use the approach. When answering, connect the concept to maintainability, scalability, performance, reliability, security, and developer productivity where relevant.

Why do people resist change?

#### Threading ELI5

**Answer:**
This topic tests understanding of **Threading ELI5**. A strong interview answer should define the concept, explain why it matters in real systems, discuss advantages and trade-offs, provide a practical example, and describe when you would or would not use the approach. When answering, connect the concept to maintainability, scalability, performance, reliability, security, and developer productivity where relevant.

Explain threads to your grandparents

#### Innovation and Predictability

**Answer:**
This topic tests understanding of **Innovation and Predictability**. A strong interview answer should define the concept, explain why it matters in real systems, discuss advantages and trade-offs, provide a practical example, and describe when you would or would not use the approach. When answering, connect the concept to maintainability, scalability, performance, reliability, security, and developer productivity where relevant.

As a software engineer you want both to innovate and to be predictable. How those two goals can coexist in the same strategy?

#### Good Code

**Answer:**
This topic tests understanding of **Good Code**. A strong interview answer should define the concept, explain why it matters in real systems, discuss advantages and trade-offs, provide a practical example, and describe when you would or would not use the approach. When answering, connect the concept to maintainability, scalability, performance, reliability, security, and developer productivity where relevant.

What makes good code good?

#### Streaming

**Answer:**
This topic tests understanding of **Streaming**. A strong interview answer should define the concept, explain why it matters in real systems, discuss advantages and trade-offs, provide a practical example, and describe when you would or would not use the approach. When answering, connect the concept to maintainability, scalability, performance, reliability, security, and developer productivity where relevant.

Explain streaming and how you would implement it.

#### 1 Week Improvement

**Answer:**
This topic tests understanding of **1 Week Improvement**. A strong interview answer should define the concept, explain why it matters in real systems, discuss advantages and trade-offs, provide a practical example, and describe when you would or would not use the approach. When answering, connect the concept to maintainability, scalability, performance, reliability, security, and developer productivity where relevant.

Say your company gives you one week you can use to improve your and your colleagues' lifes: how would you use that week?

#### Learnt this week

**Answer:**
This topic tests understanding of **Learnt this week**. A strong interview answer should define the concept, explain why it matters in real systems, discuss advantages and trade-offs, provide a practical example, and describe when you would or would not use the approach. When answering, connect the concept to maintainability, scalability, performance, reliability, security, and developer productivity where relevant.

What did you learn this week?

#### Aesthetic

**Answer:**
This topic tests understanding of **Aesthetic**. A strong interview answer should define the concept, explain why it matters in real systems, discuss advantages and trade-offs, provide a practical example, and describe when you would or would not use the approach. When answering, connect the concept to maintainability, scalability, performance, reliability, security, and developer productivity where relevant.

There is an aesthetic element to all design. The question is, is this aesthetic element your friend or your enemy?

#### Last 5 books

**Answer:**
This topic tests understanding of **Last 5 books**. A strong interview answer should define the concept, explain why it matters in real systems, discuss advantages and trade-offs, provide a practical example, and describe when you would or would not use the approach. When answering, connect the concept to maintainability, scalability, performance, reliability, security, and developer productivity where relevant.

List the last 5 books you read.

#### Introducing CI/CD

**Answer:**
This topic tests understanding of **Introducing CI/CD**. A strong interview answer should define the concept, explain why it matters in real systems, discuss advantages and trade-offs, provide a practical example, and describe when you would or would not use the approach. When answering, connect the concept to maintainability, scalability, performance, reliability, security, and developer productivity where relevant.

How would you introduce Continuous Delivery in a successful, huge company for which the change from Waterfall to Continuous Delivery would be not trivial, because of the size and complexity of the business?

#### Reinvent the Wheel

**Answer:**
This topic tests understanding of **Reinvent the Wheel**. A strong interview answer should define the concept, explain why it matters in real systems, discuss advantages and trade-offs, provide a practical example, and describe when you would or would not use the approach. When answering, connect the concept to maintainability, scalability, performance, reliability, security, and developer productivity where relevant.

When does it make sense to reinvent the wheel?

#### Not Invented Here

**Answer:**
This topic tests understanding of **Not Invented Here**. A strong interview answer should define the concept, explain why it matters in real systems, discuss advantages and trade-offs, provide a practical example, and describe when you would or would not use the approach. When answering, connect the concept to maintainability, scalability, performance, reliability, security, and developer productivity where relevant.

Let's have a conversation about "*reinventing the wheel*", the "*not invented here syndrome*" and the "*eating your own food*" practice

#### Next Thing to Automate

**Answer:**
This topic tests understanding of **Next Thing to Automate**. A strong interview answer should define the concept, explain why it matters in real systems, discuss advantages and trade-offs, provide a practical example, and describe when you would or would not use the approach. When answering, connect the concept to maintainability, scalability, performance, reliability, security, and developer productivity where relevant.

What's the next thing you would automate in your current workflow?
#### Coding is Hard

**Answer:**
This topic tests understanding of **Coding is Hard**. A strong interview answer should define the concept, explain why it matters in real systems, discuss advantages and trade-offs, provide a practical example, and describe when you would or would not use the approach. When answering, connect the concept to maintainability, scalability, performance, reliability, security, and developer productivity where relevant.

Why is writing software difficult? What makes maintaining software hard?

#### Green Fields and Brown Fields

**Answer:**
This topic tests understanding of **Green Fields and Brown Fields**. A strong interview answer should define the concept, explain why it matters in real systems, discuss advantages and trade-offs, provide a practical example, and describe when you would or would not use the approach. When answering, connect the concept to maintainability, scalability, performance, reliability, security, and developer productivity where relevant.

Would you prefer working on green field or brown field projects? Why?

#### Type "Google.com"

**Answer:**
This topic tests understanding of **Type "Google.com"**. A strong interview answer should define the concept, explain why it matters in real systems, discuss advantages and trade-offs, provide a practical example, and describe when you would or would not use the approach. When answering, connect the concept to maintainability, scalability, performance, reliability, security, and developer productivity where relevant.

[What happens when you type google.com into your browser and press enter?](https://github.com/alex/what-happens-when)

#### While idle

**Answer:**
This topic tests understanding of **While idle**. A strong interview answer should define the concept, explain why it matters in real systems, discuss advantages and trade-offs, provide a practical example, and describe when you would or would not use the approach. When answering, connect the concept to maintainability, scalability, performance, reliability, security, and developer productivity where relevant.

What does an operating system do when it has got no custom code to run, and therefore it looks idle? I would like to start a discussions about interrupts, daemons, background services, polling, event handling and so on.

#### Unicode

**Answer:**
This topic tests understanding of **Unicode**. A strong interview answer should define the concept, explain why it matters in real systems, discuss advantages and trade-offs, provide a practical example, and describe when you would or would not use the approach. When answering, connect the concept to maintainability, scalability, performance, reliability, security, and developer productivity where relevant.

Explain Unicode and database transactions to a 5 year old child.

#### Defending Monoliths

**Answer:**
This topic tests understanding of **Defending Monoliths**. A strong interview answer should define the concept, explain why it matters in real systems, discuss advantages and trade-offs, provide a practical example, and describe when you would or would not use the approach. When answering, connect the concept to maintainability, scalability, performance, reliability, security, and developer productivity where relevant.

Defend the monolithic architecture.

#### Professional Developers

**Answer:**
This topic tests understanding of **Professional Developers**. A strong interview answer should define the concept, explain why it matters in real systems, discuss advantages and trade-offs, provide a practical example, and describe when you would or would not use the approach. When answering, connect the concept to maintainability, scalability, performance, reliability, security, and developer productivity where relevant.

What does it mean to be a "professional developer"?

#### It's an art

**Answer:**
This topic tests understanding of **It's an art**. A strong interview answer should define the concept, explain why it matters in real systems, discuss advantages and trade-offs, provide a practical example, and describe when you would or would not use the approach. When answering, connect the concept to maintainability, scalability, performance, reliability, security, and developer productivity where relevant.

Is developing software Art, Engineering, Crafts or Science? Your opinion.

#### People who like this also like...

**Answer:**
This topic tests understanding of **People who like this also like...**. A strong interview answer should define the concept, explain why it matters in real systems, discuss advantages and trade-offs, provide a practical example, and describe when you would or would not use the approach. When answering, connect the concept to maintainability, scalability, performance, reliability, security, and developer productivity where relevant.

"People who like this also like... ". How would you implement this feature in an e-commerce shop?

#### Corporations vs Startups

**Answer:**
This topic tests understanding of **Corporations vs Startups**. A strong interview answer should define the concept, explain why it matters in real systems, discuss advantages and trade-offs, provide a practical example, and describe when you would or would not use the approach. When answering, connect the concept to maintainability, scalability, performance, reliability, security, and developer productivity where relevant.

Why are corporations slower than startups in innovating?

#### I'm proud of

**Answer:**
This topic tests understanding of **I'm proud of**. A strong interview answer should define the concept, explain why it matters in real systems, discuss advantages and trade-offs, provide a practical example, and describe when you would or would not use the approach. When answering, connect the concept to maintainability, scalability, performance, reliability, security, and developer productivity where relevant.

What have you achieved recently that you are proud of?



### [[↑]](#toc) <a name='snippets'>Questions about snippets of code:</a>

#### Beware the Closure

**Answer:**
This topic tests understanding of **Beware the Closure**. A strong interview answer should define the concept, explain why it matters in real systems, discuss advantages and trade-offs, provide a practical example, and describe when you would or would not use the approach. When answering, connect the concept to maintainability, scalability, performance, reliability, security, and developer productivity where relevant.

What's the output of this Javascript function?
```javascript
function hookupevents() {
  for (var i = 0; i < 3; i++) {
    document.getElementById("button" + i)
      .addEventListener("click", function() {
        alert(i);
      });
  }
}
```

#### Type Erasure

**Answer:**
This topic tests understanding of **Type Erasure**. A strong interview answer should define the concept, explain why it matters in real systems, discuss advantages and trade-offs, provide a practical example, and describe when you would or would not use the approach. When answering, connect the concept to maintainability, scalability, performance, reliability, security, and developer productivity where relevant.

About Type Erasure, what's the output of this Java snippet, and why?
```java
ArrayList<Integer> li = new ArrayList<Integer>();
ArrayList<Float> lf = new ArrayList<Float>();
if (li.getClass() == lf.getClass()) // evaluates to true
  System.out.println("Equal");
```

#### Memory Leak

**Answer:**
This topic tests understanding of **Memory Leak**. A strong interview answer should define the concept, explain why it matters in real systems, discuss advantages and trade-offs, provide a practical example, and describe when you would or would not use the approach. When answering, connect the concept to maintainability, scalability, performance, reliability, security, and developer productivity where relevant.

Can you spot the memory leak?
```java
public class Stack {
    private Object[] elements;
    private int size = 0;
    private static final int DEFAULT_INITIAL_CAPACITY = 16;

    public Stack() {
        elements = new Object[DEFAULT_INITIAL_CAPACITY];
    }

    public void push(Object e) {
        ensureCapacity();
        elements[size++] = e;
    }

    public Object pop() {
        if (size == 0)
            throw new EmptyStackException();
        return elements[--size];
    }

    /**
     * Ensure space for at least one more element, roughly
     * doubling the capacity each time the array needs to grow.
     */
    private void ensureCapacity() {
        if (elements.length == size)
            elements = Arrays.copyOf(elements, 2 * size + 1);
    }
}
```

#### Kill the witch

**Answer:**
This topic tests understanding of **Kill the witch**. A strong interview answer should define the concept, explain why it matters in real systems, discuss advantages and trade-offs, provide a practical example, and describe when you would or would not use the approach. When answering, connect the concept to maintainability, scalability, performance, reliability, security, and developer productivity where relevant.

`if`s and in general conditional statements lead to procedural and imperative programming. Can you get rid of this `switch` and make this snippet more object oriented?

```java
public class Formatter {

    private Service service;

    public Formatter(Service service) {
        this.service = service;
    }

    public String doTheJob(String theInput) {
        String response = service.askForPermission();
        switch (response) {
        case "FAIL":
            return "error";
        case "OK":
            return String.format("%s%s", theInput, theInput);
        default:
            return null;
        }
    }
}
```

#### Kill the if

**Answer:**
This topic tests understanding of **Kill the if**. A strong interview answer should define the concept, explain why it matters in real systems, discuss advantages and trade-offs, provide a practical example, and describe when you would or would not use the approach. When answering, connect the concept to maintainability, scalability, performance, reliability, security, and developer productivity where relevant.

Can you get rid of these `if`s and make this snippet of code more object oriented?

```java
public class TheService {
    private final FileHandler fileHandler;
    private final FooRepository fooRepository;

    public TheService(FileHandler fileHandler, FooRepository fooRepository) {
        this.fileHandler = fileHandler;
        this.fooRepository = fooRepository;
    }

    public String Execute(final String file) {

        final String rewrittenUrl = fileHandler.getXmlFileFromFileName(file);
        final String executionId = fileHandler.getExecutionIdFromFileName(file);

        if (executionId.equals("") || rewrittenUrl.equals("")) {
            return "";
        }

        Foo knownFoo = fooRepository.getFooByXmlFileName(rewrittenUrl);

        if (knownFoo == null) {
            return "";
        }

        return knownFoo.DoThat(file);
    }
}
```

#### Kill the if-chain

**Answer:**
This topic tests understanding of **Kill the if-chain**. A strong interview answer should define the concept, explain why it matters in real systems, discuss advantages and trade-offs, provide a practical example, and describe when you would or would not use the approach. When answering, connect the concept to maintainability, scalability, performance, reliability, security, and developer productivity where relevant.

How would you refactor this code?

```js
function()
{
    HRESULT error = S_OK;

    if(SUCCEEDED(Operation1()))
    {
        if(SUCCEEDED(Operation2()))
        {
            if(SUCCEEDED(Operation3()))
            {
                if(SUCCEEDED(Operation4()))
                {
                }
                else
                {
                    error = OPERATION4FAILED;
                }
            }
            else
            {
                error = OPERATION3FAILED;
            }
        }
        else
        {
            error = OPERATION2FAILED;
        }
    }
    else
    {
        error = OPERATION1FAILED;
    }

    return error;
}
```
[Resources](snippets/kill-the-if-chain.md)

### [[↑]](#toc) <a name='billgates'>Bill Gates Style Questions:</a>
This section collects some weird questions along the lines of the [Manhole Cover Question](https://en.wikipedia.org/wiki/Microsoft_interview#Manhole_cover_question).

#### Mirrors

**Answer:**
This topic tests understanding of **Mirrors**. A strong interview answer should define the concept, explain why it matters in real systems, discuss advantages and trade-offs, provide a practical example, and describe when you would or would not use the approach. When answering, connect the concept to maintainability, scalability, performance, reliability, security, and developer productivity where relevant.

What would happen if you put a mirror in a scanner?

#### Clones

**Answer:**
This topic tests understanding of **Clones**. A strong interview answer should define the concept, explain why it matters in real systems, discuss advantages and trade-offs, provide a practical example, and describe when you would or would not use the approach. When answering, connect the concept to maintainability, scalability, performance, reliability, security, and developer productivity where relevant.

Imagine there's a perfect clone of yourself. Imagine that that clone is your boss. Would you like to work for him/her?

#### Revert

**Answer:**
This topic tests understanding of **Revert**. A strong interview answer should define the concept, explain why it matters in real systems, discuss advantages and trade-offs, provide a practical example, and describe when you would or would not use the approach. When answering, connect the concept to maintainability, scalability, performance, reliability, security, and developer productivity where relevant.

Interview me.

#### Quora

**Answer:**
This topic tests understanding of **Quora**. A strong interview answer should define the concept, explain why it matters in real systems, discuss advantages and trade-offs, provide a practical example, and describe when you would or would not use the approach. When answering, connect the concept to maintainability, scalability, performance, reliability, security, and developer productivity where relevant.

Why are Quora's answers better than Yahoo Answers' ones?

#### Cobol

**Answer:**
This topic tests understanding of **Cobol**. A strong interview answer should define the concept, explain why it matters in real systems, discuss advantages and trade-offs, provide a practical example, and describe when you would or would not use the approach. When answering, connect the concept to maintainability, scalability, performance, reliability, security, and developer productivity where relevant.

Let's play a game: defend Cobol against modern languages, and try to find as many reasonable arguments as you can.

#### 10 years

**Answer:**
This topic tests understanding of **10 years**. A strong interview answer should define the concept, explain why it matters in real systems, discuss advantages and trade-offs, provide a practical example, and describe when you would or would not use the approach. When answering, connect the concept to maintainability, scalability, performance, reliability, security, and developer productivity where relevant.

Where will you be in 10 years?

#### Fire me

**Answer:**
This topic tests understanding of **Fire me**. A strong interview answer should define the concept, explain why it matters in real systems, discuss advantages and trade-offs, provide a practical example, and describe when you would or would not use the approach. When answering, connect the concept to maintainability, scalability, performance, reliability, security, and developer productivity where relevant.

You are my boss and I'm fired. Inform me.

#### From scratch

**Answer:**
This topic tests understanding of **From scratch**. A strong interview answer should define the concept, explain why it matters in real systems, discuss advantages and trade-offs, provide a practical example, and describe when you would or would not use the approach. When answering, connect the concept to maintainability, scalability, performance, reliability, security, and developer productivity where relevant.

I want to refactor a legacy system. You want to rewrite it from scratch. Argument. Then, switch our roles.

#### Telling lies

**Answer:**
This topic tests understanding of **Telling lies**. A strong interview answer should define the concept, explain why it matters in real systems, discuss advantages and trade-offs, provide a practical example, and describe when you would or would not use the approach. When answering, connect the concept to maintainability, scalability, performance, reliability, security, and developer productivity where relevant.

Your boss asks you to lie to the company. What's your reaction?

#### Your past self

**Answer:**
This topic tests understanding of **Your past self**. A strong interview answer should define the concept, explain why it matters in real systems, discuss advantages and trade-offs, provide a practical example, and describe when you would or would not use the approach. When answering, connect the concept to maintainability, scalability, performance, reliability, security, and developer productivity where relevant.

If you could travel back in time, which advice would you give to your younger self?
