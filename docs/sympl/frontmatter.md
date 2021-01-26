---
sort: 0
---

**Bill Chiles**

**This draft still needs a final proofreading pass!**

1 Introduction 4

1.1 Sources 4

1.2 Walkthrough Organization 5

2 Quick Language Overview 5

3 Walkthrough of Hello World 6

3.1 Quick Code Overview 7

3.2 Hosting, Globals, and .NET Namespaces Access 7

3.2.1 DLR Dynamic Binding and Interoperability -- a Very Quick Description 8

3.2.2 DynamicObjectHelpers 12

3.2.3 TypeModels and TypeModelMetaObjects 14

3.2.4 TypeModelMetaObject's BindInvokeMember -- Finding a Binding 14

3.2.5 TypeModelMetaObject.BindInvokeMember -- Restrictions and Conversions 17

3.3 Import Code Generation and File Module Scopes 19

3.4 Function Call and Dotted Expression Code Generation 20

3.4.1 Analyzing Function and Member Invocations 21

3.4.2 Analyzing Dotted Expressions 22

3.4.3 What Hello World Needs 23

3.5 Identifier and File Globals Code Generation 23

3.6 Sympl.ExecuteFile and Finally Running Code 24

4 Assignment to Globals and Locals 26

5 Function Definition and Dynamic Invocations 28

5.1 Defining Functions 28

5.2 SymplInvokeBinder and Binding Function Calls 30

6 CreateThrow Runtime Binding Helper 31

7 A Few Easy, Direct Translations to Expression Trees 33

7.1 Let\* Binding 33

7.2 Lambda Expressions and Closures 34

7.3 Conditional (IF) Expressions 34

7.4 Eq Expressions 35

7.5 Loop Expressions 36

8 Literal Expressions 37

8.1 Integers and Strings 37

8.2 Keyword Constants 37

8.3 Quoted Lists and Symbols 38

8.3.1 AnalyzeQuoteExpr -- Code Generation 38

8.3.2 Cons and List Keyword Forms and Runtime Support 39

9 Importing Sympl Libraries and Accessing and Invoking Their Globals 40

10 Type instantiation 41

10.1 New Keyword Form Code Generation 41

10.2 Binding CreateInstance Operations in TypeModelMetaObject 42

10.3 Binding CreateInstance Operations in FallbackCreateInstance 43

10.4 Instantiating Arrays and GetRuntimeTypeMoFromModel 44

11 SymplGetMemberBinder and Binding .NET Instance Members 45

12 ErrorSuggestion Arguments to Binder FallbackX Methods 46

13 SymplSetMemberBinder and Binding .NET Instance Members 47

14 SymplInvokeMemberBinder and Binding .NET Member Invocations 49

14.1 FallbackInvokeMember 49

14.2 FallbackInvoke 51

15 Indexing Expressions: GetIndex and SetIndex 52

15.1 SymplGetIndexBinder's FallbackGetIndex 53

15.2 GetIndexingExpression 53

15.3 SymplSetIndexBinder's FallbackSetIndex 55

16 Generic Type Instantiation 57

17 Arithmetic, Comparison, and Boolean Operators 57

17.1 Analysis and Code Generation for Binary Operations 58

17.2 Analysis and Code Generation for Unary Operations 59

17.3 SymplBinaryOperationBinder 59

17.4 SymplUnaryOperationBinder 60

18 Canonical Binders or L2 Cache Sharing 60

19 Binding COM Objects 61

20 Using Defer When MetaObjects Have No Value 62

21 SymPL Language Description 63

21.1 High-level 64

21.2 Lexical Aspects 64

21.3 Built-in Types 64

21.4 Control Flow 65

21.4.1 Function Call 65

21.4.2 Conditionals 66

21.4.3 Loops 66

21.4.4 Try/Catch/Finally and Throw 66

21.5 Built-in Operations 66

21.6 Globals, Scopes, and Import 67

21.6.1 File Scopes and Import 67

21.6.2 Lexical Scoping 68

21.6.3 Closures 68

21.7 Why No Classes 69

21.8 Keywords 69

21.9 Example Code (mostly from test.sympl) 69

22 Runtime and Hosting 71

22.1 Class Summary 71

23 Appendixes 72

23.1 Supporting the DLR Hosting APIs 72

23.1.1 Main and Example Host Consumer 73

23.1.2 Runtime.cs Changes 74

23.1.3 Sympl.cs Changes 75

23.1.4 Why Not Show Using ScriptRuntime.Globals Namespace Reflection 75

23.1.5 The New DlrHosting.cs File 75

23.2 Using the Codeplex.com DefaultBinder for rich .NET interop 78

23.3 Using Codeplex.com Namespace/Type Trackers instead of ExpandoObjects 79

23.4 Using Codeplex.com GeneratorFunctionExpression 79
