---
sort: 1
title: Introduction
---

# 1 Introduction

The Dynamic Language Runtime's (DLR) mission is to enable an ecosystem of dynamic languages on .NET and to support developing libraries that work well with dynamic language features. Dynamic languages have become very popular in the last several years, and static languages are adopting affordances for dynamic operations on objects. The DLR helps language implementers move languages to .NET and enhance existing languages with dynamic features. Library authors can engage in this space easily too.

A key aspect of the DLR is a common dynamic object interoperability protocol. Language implementers targeting the DLR participate in the protocol and use the DLR's dynamic dispatch caching mechanism to make their dynamic objects fast and portable across languages. Library authors can participate in this protocol at a very high-level and still enjoy much of the efficiency that language implementers get. Library authors can also go further and engage at the same level languages do, but they usually do not need to do that.

For example, if you have a library for crawling through XML or working with JSON objects, you'd really like to enable your objects to appear as dynamic objects to C\# 4.0, VB 10.0 and dynamic languages. This lets consumers write syntactically simpler and more natural code for accessing members, drilling into, and operating on your objects. They can write code like XMLElement.Customer.Name instead of XElement.Element("Customer").Element(“Name”). Although the calls to Element in the second form are “statically typed”, the tokens meaningful to you, Customer and Name, are passed as strings anyway, so the code has been dynamic in practice all along.

The DLR provides two high-level helper objects so that library authors do not have to work at the level of language implementers to support dynamic operations. These types are ExpandoObject and DynamicObject, which are explained below with samples.
