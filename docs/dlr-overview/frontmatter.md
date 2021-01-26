---
sort: 0
---

**Bill Chiles and Alex Turner**

***Reading this Document:***

> ***The first section conveys mission, goals, and value propositions for the DLR.***
>
> ***The second section is a bird's eye view of the architecture with a few sentences about each DLR component.***
>
> ***The following sections drill into the major areas and components with conceptual introductions in moderate detail. These sections lift some text from more detailed documents that provide further reading such as samples, API references, etc. There are some sub sections here that are not found in the other documents.***

1 Introduction 3

1.1 Key DLR Advantages 3

1.2 Open Source Projects 4

1.3 Why Dynamic Languages 4

2 Architecture Introduction 6

2.1 Common Hosting 8

2.2 Runtime 8

2.3 Language Implementation 9

3 Common Hosting Model 10

3.1.1 Architecture Introduction 11

3.1.2 Level One -- Script Runtimes, Scopes, and Executing Files and Snippets 12

3.1.3 Level Two -- Engines, Compiled Code, Sources, and Object Operations 13

3.1.4 Level Three -- Full Control, Remoting, Tool Support, and More 15

4 Runtime 17

4.1 Dynamic Call Sites 18

4.1.1 Before Dynamic Call Sites 18

4.1.2 Language Interoperability 19

4.1.3 Creating Dynamic Call Sites 19

4.2 Rules 20

4.3 Binders and CallSiteBinder 21

4.4 CallSite\<T\> and Caching 21

4.4.1 L0 Cache: CallSite’s Target Delegate 22

4.4.2 L1 Cache: CallSite’s Rule Set 22

4.4.3 Other Optimizations 23

4.5 DynamicObject and ExpandoObject 23

4.5.1 DynamicObject 23

4.5.2 ExpandoObject 25

4.6 Default Binder -- Runtime Utility for Language Implementers 25

5 Language Implementation 26

5.1 Expression Trees 26

5.1.1 Expression-based Model 27

5.1.2 Reducible Nodes 28

5.1.3 Bound, Unbound, and Dynamic Nodes 29

5.1.4 Iteration, Goto's, and Exits 31

5.1.5 Assignments and L-values 33

5.1.6 Blocks, Scopes, Variables, ParameterExpression, and Explicit Lifting 35

5.1.7 Lambdas, Exits, and Result Types 36

5.1.8 Generators (Codeplex only) 37

5.1.9 Serializability 38

5.1.10 Shared Visitor Support 38

5.1.11 Annotations (Debug/Source Location Only) 39

5.2 LanguageContexts 39

5.3 Type System 40

5.3.1 Problems with Wrappers 40

5.3.2 Object and IDynamicMetaObjectProvider 41

5.4 IDynamicMetaObjectProvider and DynamicMetaObject 41

5.4.1 IDynamicMetaObjectProvider 42

5.4.2 DynamicMetaObject 42

5.4.3 DynamicMetaObjectBinder 43
