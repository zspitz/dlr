---
sort: 0
title: Sites, Binders, and Dynamic Object Interop Spec
---

**Alex Turner and Bill Chiles**

**Alex Turner and Bill Chiles** 1

1 Introduction 5

1.1 Performance 5

1.2 Language Interop 6

2 Dynamic Call Sites 6

2.1 Rules 7

2.2 CallSiteBinder 8

2.3 CallSite\<T\> 9

2.3.1 L0 Cache: CallSite’s Target Delegate 9

2.3.2 L1 Cache: CallSite’s Rule Set 9

2.3.3 L2 Cache: Combined Rule Sets of All Equivalent CallSites 10

2.3.4 Other Optimizations 10

3 IDynamicMetaObjectProvider and DynamicMetaObject 10

3.1 IDynamicMetaObjectProvider 11

3.2 DynamicMetaObject 11

3.3 DynamicMetaObjectBinder 12

3.3.1 Fallback Methods – Implementing the Language’s Semantics 13

3.3.2 Error Suggestions 14

3.4 Dynamic Binding Walkthroughs 14

3.4.1 a + b 14

SiteContainer.Site1 = 14

3.4.2 a.Foo(b) 17

4 DynamicObject and ExpandoObject 18

4.1 DynamicObject 18

4.2 ExpandoObject 20

4.3 Further Reading 20

5 Dynamic Object Conventions 20

5.1 Enumerability 20

5.2 Disposability 21

6 API Reference 21

6.1 DynamicMetaObject Class 21

6.1.1 Class Summary 21

6.1.2 Bind*\*Operation\** Methods 22

6.1.3 Expression Property 22

6.1.4 Restrictions Property 23

6.1.5 Value and HasValue Properties 23

6.1.6 LimitType Property 23

6.1.7 Create Static Method 23

6.1.8 GetDynamicMemberNames Method 24

6.2 IDynamicMetaObjectProvider Interface 24

6.2.1 Class Summary 24

6.2.2 GetMetaObject Method 24

6.3 CallSiteBinder Abstract Class 24

6.3.1 Class Summary 25

6.3.2 Bind Method 25

6.3.3 BindDelegate Method 25

6.3.4 CacheTarget Method 26

6.3.5 UpdateLabel Static Property 26

6.4 DynamicMetaObjectBinder Abstract Class 26

6.4.1 Fallback Methods 26

6.4.2 Placing Canonical Binders on CallSites 27

6.4.3 COM Support 27

6.4.4 Class Summary 27

6.4.5 Bind Method 28

6.4.6 Defer Method 28

6.4.7 ReturnType Property 28

6.4.8 GetUpdateExpression Method 28

6.5 GetMemberBinder Abstract Class 29

6.5.1 Class Summary 29

6.5.2 Name Property 29

6.5.3 IgnoreCase Property 29

6.6 SetMemberBinder Abstract Class 29

6.6.1 Class Summary 30

6.6.2 Name Property 30

6.6.3 IgnoreCase Property 30

6.7 DeleteMemberBinder Abstract Class 30

6.7.1 Class Summary 30

6.7.2 Name Property 30

6.7.3 IgnoreCase Property 30

6.8 GetIndexBinder Abstract Class 31

6.8.1 Class Summary 31

6.8.2 Calllnfo Property 31

6.9 SetIndexBinder Abstract Class 31

6.9.1 Class Summary 31

6.9.2 Calllnfo Property 32

6.10 DeleteIndexBinder Abstract Class 32

6.10.1 Class Summary 32

6.10.2 Calllnfo Property 32

6.11 InvokeBinder Abstract Class 32

6.11.1 Class Summary 32

6.11.2 Calllnfo Property 33

6.12 InvokeMemberBinder Abstract Class 33

6.12.1 Class Summary 33

6.12.2 Name Property 33

6.12.3 IgnoreCase Property 33

6.12.4 Calllnfo Property 33

6.12.5 FallbackInvoke Method 34

6.13 CreateInstanceBinder Abstract Class 34

6.13.1 Class Summary 34

6.13.2 Calllnfo Property 34

6.14 ConvertBinder Abstract Class 34

6.14.1 Class Summary 34

6.14.2 Type Property 35

6.14.3 Explicit Property 35

6.15 UnaryOperationBinder Abstract Class 35

6.15.1 Class Summary 35

6.15.2 Operation Property 35

6.16 BinaryOperationBinder Abstract Class 35

6.16.1 Class Summary 36

6.16.2 Operation Property 36

6.17 CallInfo Class 36

6.17.1 Class Summary 36

6.17.2 ArgumentCount Property 36

6.17.3 ArgumentNames Property 36

6.18 BindingRestrictions Class 36

6.18.1 Class Summary 37

6.18.2 GetTypeRestriction Method 37

6.18.3 GetInstanceRestriction Method 37

6.18.4 GetExpressionRestriction Method 37

6.18.5 Merge Method 37

6.18.6 Combine Static Method 37

6.19 CallSite and CallSite\<T\> Classes 38

6.19.1 Class Summary 38

6.19.2 Create Static Method 38

6.19.3 Target Field 38

6.19.4 Update Property 38

6.20 StrongBox Class 39

6.20.1 Class Summary 39

6.21 DynamicObject Class 39

6.21.1 Class Summary 39

6.22 ExpandoObject Class 40

6.22.1 Class Summary 40
