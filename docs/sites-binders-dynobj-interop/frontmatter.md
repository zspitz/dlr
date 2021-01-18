<span id="_Toc230529372" class="anchor"></span>**Alex Turner and Bill Chiles**

[**Alex Turner and Bill Chiles** 1](#_Toc230529372)

[1 Introduction 5](#introduction)

[1.1 Performance 5](#performance)

[1.2 Language Interop 6](#language-interop)

[2 Dynamic Call Sites 6](#dynamic-call-sites)

[2.1 Rules 7](#rules)

[2.2 CallSiteBinder 8](#callsitebinder)

[2.3 CallSite&lt;T&gt; 9](#callsitet)

[2.3.1 L0 Cache: CallSite’s Target Delegate 9](#l0-cache-callsites-target-delegate)

[2.3.2 L1 Cache: CallSite’s Rule Set 9](#l1-cache-callsites-rule-set)

[2.3.3 L2 Cache: Combined Rule Sets of All Equivalent CallSites 10](#l2-cache-combined-rule-sets-of-all-equivalent-callsites)

[2.3.4 Other Optimizations 10](#other-optimizations)

[3 IDynamicMetaObjectProvider and DynamicMetaObject 10](#idynamicmetaobjectprovider-and-dynamicmetaobject)

[3.1 IDynamicMetaObjectProvider 11](#idynamicmetaobjectprovider)

[3.2 DynamicMetaObject 11](#dynamicmetaobject)

[3.3 DynamicMetaObjectBinder 12](#dynamicmetaobjectbinder)

[3.3.1 Fallback Methods – Implementing the Language’s Semantics 13](#fallback-methods-implementing-the-languages-semantics)

[3.3.2 Error Suggestions 14](#error-suggestions)

[3.4 Dynamic Binding Walkthroughs 14](#dynamic-binding-walkthroughs)

[3.4.1 a + b 14](#a-b)

[SiteContainer.Site1 = 14](#_Toc230529392)

[3.4.2 a.Foo(b) 17](#a.foob)

[4 DynamicObject and ExpandoObject 18](#dynamicobject-and-expandoobject)

[4.1 DynamicObject 18](#dynamicobject)

[4.2 ExpandoObject 20](#expandoobject)

[4.3 Further Reading 20](#further-reading)

[5 Dynamic Object Conventions 20](#dynamic-object-conventions)

[5.1 Enumerability 20](#enumerability)

[5.2 Disposability 21](#disposability)

[6 API Reference 21](#api-reference)

[6.1 DynamicMetaObject Class 21](#dynamicmetaobject-class)

[6.1.1 Class Summary 21](#class-summary)

[6.1.2 Bind*\*Operation\** Methods 22](#bindoperation-methods)

[6.1.3 Expression Property 22](#expression-property)

[6.1.4 Restrictions Property 23](#restrictions-property)

[6.1.5 Value and HasValue Properties 23](#value-and-hasvalue-properties)

[6.1.6 LimitType Property 23](#limittype-property)

[6.1.7 Create Static Method 23](#create-static-method)

[6.1.8 GetDynamicMemberNames Method 24](#getdynamicmembernames-method)

[6.2 IDynamicMetaObjectProvider Interface 24](#idynamicmetaobjectprovider-interface)

[6.2.1 Class Summary 24](#class-summary-1)

[6.2.2 GetMetaObject Method 24](#getmetaobject-method)

[6.3 CallSiteBinder Abstract Class 24](#callsitebinder-abstract-class)

[6.3.1 Class Summary 25](#class-summary-2)

[6.3.2 Bind Method 25](#bind-method)

[6.3.3 BindDelegate Method 25](#binddelegate-method)

[6.3.4 CacheTarget Method 26](#cachetarget-method)

[6.3.5 UpdateLabel Static Property 26](#updatelabel-static-property)

[6.4 DynamicMetaObjectBinder Abstract Class 26](#dynamicmetaobjectbinder-abstract-class)

[6.4.1 Fallback Methods 26](#fallback-methods)

[6.4.2 Placing Canonical Binders on CallSites 27](#placing-canonical-binders-on-callsites)

[6.4.3 COM Support 27](#com-support)

[6.4.4 Class Summary 27](#class-summary-3)

[6.4.5 Bind Method 28](#bind-method-1)

[6.4.6 Defer Method 28](#defer-method)

[6.4.7 ReturnType Property 28](#returntype-property)

[6.4.8 GetUpdateExpression Method 28](#getupdateexpression-method)

[6.5 GetMemberBinder Abstract Class 29](#getmemberbinder-abstract-class)

[6.5.1 Class Summary 29](#class-summary-4)

[6.5.2 Name Property 29](#name-property)

[6.5.3 IgnoreCase Property 29](#ignorecase-property)

[6.6 SetMemberBinder Abstract Class 29](#setmemberbinder-abstract-class)

[6.6.1 Class Summary 30](#class-summary-5)

[6.6.2 Name Property 30](#name-property-1)

[6.6.3 IgnoreCase Property 30](#ignorecase-property-1)

[6.7 DeleteMemberBinder Abstract Class 30](#deletememberbinder-abstract-class)

[6.7.1 Class Summary 30](#class-summary-6)

[6.7.2 Name Property 30](#name-property-2)

[6.7.3 IgnoreCase Property 30](#ignorecase-property-2)

[6.8 GetIndexBinder Abstract Class 31](#getindexbinder-abstract-class)

[6.8.1 Class Summary 31](#class-summary-7)

[6.8.2 Calllnfo Property 31](#calllnfo-property)

[6.9 SetIndexBinder Abstract Class 31](#setindexbinder-abstract-class)

[6.9.1 Class Summary 31](#class-summary-8)

[6.9.2 Calllnfo Property 32](#calllnfo-property-1)

[6.10 DeleteIndexBinder Abstract Class 32](#deleteindexbinder-abstract-class)

[6.10.1 Class Summary 32](#class-summary-9)

[6.10.2 Calllnfo Property 32](#calllnfo-property-2)

[6.11 InvokeBinder Abstract Class 32](#invokebinder-abstract-class)

[6.11.1 Class Summary 32](#class-summary-10)

[6.11.2 Calllnfo Property 33](#calllnfo-property-3)

[6.12 InvokeMemberBinder Abstract Class 33](#invokememberbinder-abstract-class)

[6.12.1 Class Summary 33](#class-summary-11)

[6.12.2 Name Property 33](#name-property-3)

[6.12.3 IgnoreCase Property 33](#ignorecase-property-3)

[6.12.4 Calllnfo Property 33](#calllnfo-property-4)

[6.12.5 FallbackInvoke Method 34](#fallbackinvoke-method)

[6.13 CreateInstanceBinder Abstract Class 34](#createinstancebinder-abstract-class)

[6.13.1 Class Summary 34](#class-summary-12)

[6.13.2 Calllnfo Property 34](#calllnfo-property-5)

[6.14 ConvertBinder Abstract Class 34](#convertbinder-abstract-class)

[6.14.1 Class Summary 34](#class-summary-13)

[6.14.2 Type Property 35](#type-property)

[6.14.3 Explicit Property 35](#explicit-property)

[6.15 UnaryOperationBinder Abstract Class 35](#unaryoperationbinder-abstract-class)

[6.15.1 Class Summary 35](#class-summary-14)

[6.15.2 Operation Property 35](#operation-property)

[6.16 BinaryOperationBinder Abstract Class 35](#binaryoperationbinder-abstract-class)

[6.16.1 Class Summary 36](#class-summary-15)

[6.16.2 Operation Property 36](#operation-property-1)

[6.17 CallInfo Class 36](#callinfo-class)

[6.17.1 Class Summary 36](#class-summary-16)

[6.17.2 ArgumentCount Property 36](#argumentcount-property)

[6.17.3 ArgumentNames Property 36](#argumentnames-property)

[6.18 BindingRestrictions Class 36](#bindingrestrictions-class)

[6.18.1 Class Summary 37](#class-summary-17)

[6.18.2 GetTypeRestriction Method 37](#gettyperestriction-method)

[6.18.3 GetInstanceRestriction Method 37](#getinstancerestriction-method)

[6.18.4 GetExpressionRestriction Method 37](#getexpressionrestriction-method)

[6.18.5 Merge Method 37](#merge-method)

[6.18.6 Combine Static Method 37](#combine-static-method)

[6.19 CallSite and CallSite&lt;T&gt; Classes 38](#callsite-and-callsitet-classes)

[6.19.1 Class Summary 38](#class-summary-18)

[6.19.2 Create Static Method 38](#create-static-method-1)

[6.19.3 Target Field 38](#target-field)

[6.19.4 Update Property 38](#update-property)

[6.20 StrongBox Class 39](#strongbox-class)

[6.20.1 Class Summary 39](#class-summary-19)

[6.21 DynamicObject Class 39](#dynamicobject-class)

[6.21.1 Class Summary 39](#class-summary-20)

[6.22 ExpandoObject Class 40](#expandoobject-class)

[6.22.1 Class Summary 40](#class-summary-21)
