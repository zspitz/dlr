---
sort: 0
---

**Bill Chiles**

**WARNING: This is a big document, in case you are thinking of printing it. This document is reasonably stable, but there is ongoing work in some sections. Some sections are not fully fleshed out for types more rarely used or "more obvious" in their usage.**

1 Introduction 8

2 High-level Hosting Model Concepts 9

2.1 Level One -- Script Runtimes, Scopes, and Executing Files and Snippets 11

2.1.1 Code Sample -- Application Programmability 12

2.2 Level Two -- Engines, Compiled Code, Sources, and Object Operations 13

2.2.1 Code Sample -- REPL and Merlin Web 15

2.3 Level Three -- Full Control, Remoting, Tool Support, and More 16

2.3.1 Code Sample -- Tools Support and Remoting 18

~~2.4~~ ~~Implementer’s Convenience~~ 22

3 Hosts Requirements 22

3.1 SilverLight (RIA) 22

3.2 MerlinWeb (Server Side) 23

3.2.1 Compilation 23

3.2.2 Globals and Member Injection 24

3.2.3 Error handling 25

3.3 Base Tools Support 26

3.3.1 General Hosting (ScriptEngineServer) 26

3.3.2 Language Tool Support (IScriptEngine or ILanguageToolService) 27

3.3.3 Static Analysis (Post MIX 07) 28

3.4 What Languages and DLR Need to Support 29

3.5 Configuration Notes 30

3.5.1 Requirements 31

3.5.2 Goals 31

3.5.3 Scenarios 31

3.6 Remote Construction Design Notes 32

4 API References 33

4.1 ScriptRuntime Class 33

4.1.1 Class Summary 33

4.1.2 Constructor 34

4.1.3 Create\* Methods 34

4.1.4 ExecuteFile Method 35

4.1.5 UseFile Method 35

4.1.6 Globals Property 36

4.1.7 CreateScope Method 36

4.1.8 GetEngine Method 36

4.1.9 GetEngineByFileExtension Method 36

~~4.1.10~~ ~~GetEngineByMimeType Method~~ 37

4.1.11 GetRegisteredFileExtensions Method 37

4.1.12 GetRegisteredLanguageIdentifiers Method 37

4.1.13 LoadAssembly Method 37

4.1.14 Operations Property 38

4.1.15 CreateOperations Methods 39

4.1.16 Setup Property 39

4.1.17 Host Property 39

4.1.18 IO Property 39

4.1.19 Shutdown Method 40

4.2 ScriptScope Class 40

4.2.1 Class Summary 40

4.2.2 GetVariable\* Methods 41

4.2.3 SetVariable Methods 41

4.2.4 TryGetVariable\* Methods 42

4.2.5 ContainsVariable Method 42

4.2.6 GetVariableNames Method 42

4.2.7 GetItems Method 42

4.2.8 RemoveVariable Method 43

4.2.9 Engine Property 43

4.3 ScriptEngine Class 43

4.3.1 Class Summary 43

4.3.2 Runtime Property 45

4.3.3 LanguageDisplayName Property 45

4.3.4 GetRegistered\* Methods 45

4.3.5 Execute\* Methods 45

4.3.6 ExecuteFile Methods 46

4.3.7 GetScope Method 46

4.3.8 Operations Property 46

4.3.9 CreateOperations Methods 47

4.3.10 CreateScriptSourceFromString Methods 47

4.3.11 CreateScriptSourceFromFile Methods 47

4.3.12 CreateScriptSource Methods 48

4.3.13 CreateScope Method 49

4.3.14 GetService Method 49

4.3.15 Setup Property 50

4.3.16 GetCompilerOptions Method 50

4.3.17 GetSearchPaths Method 51

4.3.18 SetSearchPaths Method 51

4.3.19 LanguageVersion Property 51

4.4 ScriptSource Class 51

4.4.1 Class Summary 52

4.4.2 Path Property 53

4.4.3 Kind Property 53

4.4.4 GetCodeProperties Methods 53

4.4.5 Engine Property 53

4.4.6 Compile Methods 54

4.4.7 Execute\* Methods 54

4.4.8 GetReader Method 55

4.4.9 DetectEncoding Method 55

4.4.10 GetCode Method 55

4.4.11 GetCodeLine\* Methods 55

4.4.12 MapLine Methods 56

4.4.13 MapLineToFile Method 56

4.5 CompiledCode Class 56

4.5.1 Class Summary 56

4.5.2 DefaultScope Property 57

4.5.3 Engine Property 57

4.5.4 Execute\* Methods 57

4.6 ObjectOperations Class 57

4.6.1 Class Summary 58

4.6.2 Engine Property 60

4.6.3 IsCallable Methods 61

4.6.4 Invoke Methods 61

4.6.5 InvokeMember Method 61

4.6.6 CreateInstance Methods 61

4.6.7 GetMember\* Methods 62

4.6.8 TryGetMember Methods 62

4.6.9 ContainsMember Methods 62

4.6.10 RemoveMember Methods 63

4.6.11 SetMember Methods 63

4.6.12 ConvertTo\* Methods 63

4.6.13 TryConvertTo\* Methods 64

4.6.14 ExplicitConvertTo\* Methods 64

4.6.15 TryExplicitConvertTo\* Methods 64

4.6.16 ImplicitConvertTo\* Methods 64

4.6.17 TryimplicitConvertTo\* Methods 65

4.6.18 Unwrap\<T\> Method 65

4.6.19 Format Methods 65

4.6.20 GetMemberNames Methods 65

4.6.21 GetDocumentation Methods 65

4.6.22 GetCallSignatures Methods 66

4.6.23 DoOperation\* Methods 66

4.6.24 Add Methods 67

4.6.25 Subtract Methods 67

4.6.26 Power Methods 67

4.6.27 Multiply Methods 67

4.6.28 Divide Methods 67

4.6.29 Modulo Methods 67

4.6.30 LeftShift Methods 68

4.6.31 RightShift Methods 68

4.6.32 BitwiseAnd Methods 68

4.6.33 BitwiseOr Methods 68

4.6.34 ExclusiveOr Methods 68

4.6.35 Equal Methods 69

4.6.36 NotEqual Methods 69

4.6.37 LessThan Methods 69

4.6.38 LessThanOrEqual Methods 69

4.6.39 GreaterThan Methods 69

4.6.40 GreaterThanOrEqual Methods 70

4.7 SourceCodeKind Enum 70

4.7.1 Type Summary 70

4.7.2 Members 70

4.8 ScriptCodeParseResult Enum 71

4.8.1 Type Summary 71

4.8.2 Members 71

4.9 TextContentProvider Abstract Class 71

4.9.1 Class Summary 72

4.9.2 GetReader Method 72

4.10 StreamContentProvider Abstract Class 72

4.10.1 Class Summary 72

4.10.2 GetStream Method 72

4.11 ScriptCodeReader Sealed Class 72

4.11.1 Class Summary 72

4.12 ScriptIO Class 73

4.12.1 Class Summary 73

4.12.2 OutputStream Property 73

4.12.3 InputStream Property 74

4.12.4 ErrorStream Property 74

4.12.5 InputReader Property 74

4.12.6 OutputWriter Property 74

4.12.7 ErrorWriter Property 74

4.12.8 InputEncoding Property 75

4.12.9 OutputEncoding Property 75

4.12.10 ErrorEncoding Property 75

4.12.11 SetOutput Method 75

4.12.12 SetErrorOutput Method 75

4.12.13 SetInput Method 76

4.12.14 RedirectToConsole Method 76

4.13 ScriptRuntimeSetup Class 76

4.13.1 Class Summary 76

4.13.2 Constructor 77

4.13.3 ReadConfiguration Methods 77

4.13.4 LanguageSetups Property 79

4.13.5 HostType Property 79

4.13.6 HostArguments Property 79

4.13.7 Options Property 79

4.13.8 DebugMode Property 80

4.13.9 PrivateBinding Property 80

4.14 LanguageSetup Class 80

4.14.1 Class Summary 80

4.14.2 Constructors 80

4.14.3 TypeName Property 81

4.14.4 DisplayName Property 81

4.14.5 Names Property 81

4.14.6 FileExtensions Property 81

4.14.7 InterpretedMode Property 81

4.14.8 ExceptionDetail Property 82

4.14.9 PerfStats Property 82

4.14.10 Options Property 82

4.14.11 GetOption Method 82

4.15 ScriptHost Class 82

4.15.1 Class Summary 83

4.15.2 Runtime Property 83

4.15.3 PlatformAdaptationLayer Property 83

4.15.4 RuntimeAttached Method 83

4.15.5 EngineCreated Method 83

~~4.16~~ ~~ScriptRuntimeConfig Class~~ 84

~~4.16.1~~ ~~Class Summary~~ 84

~~4.17~~ ~~LanguageConfig Class~~ 84

~~4.17.1~~ ~~Class Summary~~ 84

4.18 PlatformAdaptationLayer Class 84

4.18.1 Class Summary 85

4.19 SyntaxErrorException Class 85

4.20 ScriptExecutionException Class 85

4.21 ErrorListener Class 85

4.21.1 Class Summary 85

4.22 Severity Enum 86

4.22.1 Type Summary 86

4.23 SourceLocation Struct 86

4.24 SourceSpan Struct 86

4.25 ExceptionOperations Class 86

4.25.1 Class Summary 86

4.26 DocumentOperations Class 86

4.26.1 Class Summary 86

4.26.2 GetMembers Method 87

4.26.3 GetOverloads 87

4.27 MemberDoc Class 87

4.27.1 Class Summary 87

4.27.2 Name Property 87

4.27.3 Kind Property 87

4.28 MemberKind Enum 87

4.28.1 Type Summary 87

4.28.2 Members 88

4.29 OverloadDoc Class 88

4.29.1 Class Summary 88

4.29.2 Name Property 89

4.29.3 Documenation Property 89

4.29.4 Parameters Property 89

4.29.5 ReturnParameter 89

4.30 ParameterDoc Class 89

4.30.1 Class Summary 89

4.30.2 Name Property 89

4.30.3 TypeName Property 89

4.30.4 Documentation Property 90

4.31 ParameterFlags Enum 90

4.31.1 Type Summary 90

4.31.2 Members 90

4.32 POST CLR 4.0 -- TokenCategorizer Abstract Class 90

4.32.1 Class Summary 90

4.33 POST CLR 4.0 -- TokenCategory Enum 91

4.34 POST CLR 4.0 -- TokenInfo Struct 91

4.35 POST CLR 4.0 -- TokenTriggers Enum 91

4.36 CUT -- ConsoleHost Abstract Class ??? 91

4.37 CUT -- ConsoleHostOptions Class 91

4.38 CUT -- ConsoleHostOptionsParser Class 91

5 Current Issues 92
