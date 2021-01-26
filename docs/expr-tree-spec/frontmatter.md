---
sort: 0
---

**Bill Chiles**

**This document specifies ETs v2 for CLR 4.0.**

****PRINT WARNING**: Doc is almost 200 pages, but conceptual introduction is about 15 pages.**

1 Introduction 15

1.1 Relation to Other Models 15

1.2 Review from LINQ Expression Trees v1 16

1.3 Design Goals 16

1.3.1 Compatibility with V1 16

1.3.2 Model Abstraction Level 17

1.3.3 .NET 4.0 vs. V-next+1 17

1.3.4 Non-goal: Design Time Language Models 18

2 Highlighted Concepts 18

2.1 Expression-based Model 18

2.2 Reducible Nodes 19

2.3 Bound, Unbound, and Dynamic Nodes 20

2.3.1 DynamicExpression Node 21

2.3.2 Binding Information in Expression Nodes 22

2.4 Iteration, Goto's, and Exits 23

2.4.1 LoopExpression and Higher-level Iteration Node Types 24

2.4.2 Modeling Exits, LabelExpression, and GotoExpression with a Value 24

2.4.3 GotoExpression Capabilities 25

2.5 Assignments and L-values 25

2.5.1 Indexed Locations 26

2.5.2 Compound Assignment or In-place Binary and Unary Operations 26

2.5.3 User-defined Setting Syntax 27

2.5.4 Destructuring Assignment 27

2.6 Array Access 27

2.7 Blocks, Scopes, Variables, ParameterExpression, and Explicit Lifting 27

2.8 Lambdas 28

2.8.1 Ensuring Returns are Lexical Exits with Matching Types 28

2.8.2 Throw 29

2.8.3 Recursion 30

2.8.4 Tail Call 30

2.9 Generators (Codeplex only) 30

2.10 Rich Static Call Site Modeling (v-next+1) 30

2.11 Expression "Tree" Where Possible 31

2.12 Serializability 32

2.13 Shared Visitor Support 32

2.14 Design Impact from Performance Improvements 33

2.15 Annotations (Debug/Source Information Only) 33

2.15.1 Source Location Information 33

2.15.2 CUT General Annotations Support 34

2.16 Node Kind and Operator Enum Values 34

2.17 ToString Method 34

3 ET Runtime 34

4 API Reference 35

4.1 Terminology for Lifted V1 Spec Text (marked by boxed red text) 35

4.2 Quirks Mode for Silverlight 36

4.3 Expression Abstract Class 36

4.3.1 Class Summary 36

4.3.2 NodeType Property 49

4.3.3 Type Property 49

4.3.4 CanReduce Property 50

4.3.5 Reduce Method 50

4.3.6 ReduceAndCheck Method 50

4.3.7 ReduceExtensions Method 50

4.3.8 DebugView Property 51

4.3.9 DumpExpression Method (Codeplex only) 51

4.3.10 GetFuncType Method 51

4.3.11 TryGetFuncType Method 51

4.3.12 GetActionType Method 52

4.3.13 TryGetActionType Method 52

4.3.14 GetDelegateType Method 52

4.3.15 VisitChildren Method 52

4.3.16 Accept Method 53

4.4 ExpressionType Enum 53

4.4.1 Type Summary 53

4.4.2 Add 55

4.4.3 AddChecked 55

4.4.4 And 55

4.4.5 AndAlso 55

4.4.6 ArrayLength 56

4.4.7 ArrayIndex 56

4.4.8 Call 56

4.4.9 Coalesce 57

4.4.10 Conditional 57

4.4.11 Constant 58

4.4.12 Convert 58

4.4.13 ConvertChecked 58

4.4.14 Divide 58

4.4.15 Equal 58

4.4.16 ExclusiveOr 59

4.4.17 GreaterThan 59

4.4.18 GreaterThanOrEqual 59

4.4.19 Invoke 59

4.4.20 Lambda 59

4.4.21 LeftShift 60

4.4.22 LessThan 60

4.4.23 LessThanOrEqual 60

4.4.24 ListInit 60

4.4.25 MemberAccess 60

4.4.26 MemberInit 61

4.4.27 Modulo 61

4.4.28 Multiply 61

4.4.29 MulitplyChecked 61

4.4.30 Negate 61

4.4.31 UnaryPlus 62

4.4.32 NegateChecked 62

4.4.33 New 62

4.4.34 NewArrayInit 62

4.4.35 NewArrayBounds 62

4.4.36 Not 62

4.4.37 NotEqual 63

4.4.38 Or 63

4.4.39 OrElse 63

4.4.40 Parameter 64

4.4.41 Power 64

4.4.42 Quote 64

4.4.43 RightShift 66

4.4.44 Subtract 66

4.4.45 SubtrtactChecked 66

4.4.46 TypeAs 66

4.4.47 TypeIs 66

4.4.48 TypeEqual 67

4.4.49 Assign 67

4.4.50 Block 67

4.4.51 DebugInfo 68

4.4.52 Decrement 68

4.4.53 Dynamic 68

4.4.54 Default 68

4.4.55 Extension 68

4.4.56 Goto 69

4.4.57 Increment 70

4.4.58 Index 70

4.4.59 Label 70

4.4.60 RuntimeVariables 70

4.4.61 Loop 71

4.4.62 Switch 71

4.4.63 Throw 72

4.4.64 Try 72

4.4.65 Unbox 72

4.4.66 AddAssign 73

4.4.67 AddAssignChecked 73

4.4.68 DivideAssign 74

4.4.69 ExclusiveOrAssign 74

4.4.70 LeftShiftAssign 74

4.4.71 ModuloAssign 75

4.4.72 MultiplyAssign 75

4.4.73 MulitplyAssignChecked 76

4.4.74 OrAssign 76

4.4.75 PowerAssign 76

4.4.76 RightShiftAssign 77

4.4.77 SubtractAssign 77

4.4.78 SubtractAssignChecked 77

4.4.79 PreIncrementAssign 78

4.4.80 PreDecrementAssign 78

4.4.81 PostIncrementAssign 78

4.4.82 PostDecrementAssign 79

4.4.83 OnesComplement 79

4.4.84 IsTrue 79

4.4.85 IsFalse 79

4.4.86 AssignRef (POST CLR 4.0) 80

4.5 DefaultExpression Class 81

4.5.1 Class Summary 81

4.5.2 Factory Methods 81

4.6 BinaryExpression Class 81

4.6.1 Class Summary 81

4.6.2 Conversion Property 82

4.6.3 IsLifted Property 82

4.6.4 IsLiftedToNull Property 82

4.6.5 Method Property 82

4.6.6 Left Property 82

4.6.7 Right Property 82

4.6.8 Update Method 82

4.6.9 Arithmetic, Shift, and Bit Operations Factory Methods 83

4.6.10 Obsolete Array Index (Single-dimension) Factory 87

4.6.11 Assignment Factory Method 87

4.6.12 Coalesce Operator Factory Methods 87

4.6.13 Conditional And and Or Operator Factory Methods 88

4.6.14 Comparison Operators Factory Methods 89

4.6.15 General Factory Methods 91

4.7 TypeBinaryExpression Class 91

4.7.1 Class Summary 92

4.7.2 Expression Property 92

4.7.3 TypeOperand Property 92

4.7.1 Update Method 92

4.7.2 Factory Methods 92

4.8 UnaryExpression Class 93

4.8.1 Class Summary 93

4.8.2 IsLifted Property 93

4.8.3 IsLiftedToNull Property 93

4.8.4 Method Property 93

4.8.5 Operand Property 94

4.8.6 Update Method 94

4.8.7 ArrayLength Factory Method 94

4.8.8 Conversion Factory Methods 94

4.8.9 Functional Increment and Decrement Factory Methods 95

4.8.10 Side-effecting Pre- and Post- Increment and Decrement Factory Methods 96

4.8.11 Numeric Negation and Plus Factory Methods 96

4.8.12 Logical and Bit Negation Factory Methods 97

4.8.13 IsTrue and IsFalse Factories 98

4.8.14 Quote Factory Method 99

4.8.15 Throw Flow Control Factory Mehtods 100

4.8.16 Reference Conversion Factory Methods 100

4.8.17 Unboxing (as Pointer to Box's Value) Factory Method 100

4.8.18 General Factory Methods 101

4.8.19 NewDelegate Expression (V-next+1) 101

4.9 BlockExpression Class 102

4.9.1 Class Summary 102

4.9.2 Expressions Property 103

4.9.3 Result Property 103

4.9.4 Variables Property 103

4.9.5 Update Method 103

4.9.6 Factory Methods 103

4.10 ConstantExpression Class 104

4.10.1 Class Summary 104

4.10.2 Value Property 104

4.10.3 Factory Methods 105

4.11 ConditionalExpression Class 105

4.11.1 Class Summary 105

4.11.2 IfFalse Property 105

4.11.3 IfTrue Property 105

4.11.4 Test Property 105

4.11.5 Update Method 106

4.11.6 Factory Methods 106

4.12 DynamicExpression Class 106

4.12.1 Class Summary 107

4.12.2 Arguments Property 107

4.12.3 Binder Property 107

4.12.4 DelegateType 107

4.12.5 Update Method 107

4.12.6 Factories 108

4.13 CallInfo Class 108

4.13.1 Class Summary 108

4.13.2 ArgumentCount Property 109

4.13.3 ArgumentNames Property 109

4.13.4 Factory Methods 109

4.14 DebugInfoExpression Class 109

4.14.1 Class Summary 109

4.14.2 Document Property 109

4.14.3 StartLine Property 110

4.14.4 StartColumn Property 110

4.14.5 EndLine Property 110

4.14.6 EndColumn Property 110

4.14.7 IsClear Property 110

4.14.8 Factory Methods 110

4.15 SymbolDocumentInfo Class 110

4.15.1 Class Summary 110

4.15.2 DocumentType Property 111

4.15.3 FileName Property 111

4.15.4 Language Property 111

4.15.5 LanguageVendor Property 111

4.15.6 Factory Methods 111

4.16 TryExpression Class 112

4.16.1 Class Summary 112

4.16.2 Body Property 112

4.16.3 Fault Property 112

4.16.4 Finally Property 113

4.16.5 Handlers Property 113

4.16.6 Update Method 113

4.16.7 Factory Methods 113

4.17 CatchBlock Class 114

4.17.1 Class Summary 114

4.17.2 Body Property 114

4.17.3 Filter Property 114

4.17.4 Test Property 114

4.17.5 Variable Property 115

4.17.6 Update Method 115

4.17.7 Factories 115

4.18 MethodCallExpression Class 115

4.18.1 Class Summary 116

4.18.2 Arguments Property 116

4.18.3 Method Property 116

4.18.4 Object Property 116

4.18.5 Update Method 117

4.18.6 General Call Factories 117

4.18.7 Obsolete Multi-dimensional Array Index Factory 118

4.19 POST CLR 4.0 -- ComplexMethodCallExpression Class 119

4.19.1 Class Summary 119

4.20 InvocationExpression Class 119

4.20.1 Class Summary 119

4.20.2 Arguments Property 119

4.20.3 Expression Property 120

4.20.4 Update Method 120

4.20.5 Factory Methods 120

4.21 IndexExpression Class 121

4.21.1 Class Summary 121

4.21.2 Arguments Property 121

4.21.3 Indexer Property 121

4.21.4 Object Property 121

4.21.5 Update Method 121

4.21.6 Factory Methods 121

4.22 LoopExpression Class 122

4.22.1 Examples 123

4.22.2 Class Summary 127

4.22.3 Update Method 127

4.22.4 Factory Methods 127

4.23 POST CLR 4.0 -- ForExpression Class 128

4.23.1 Class Summary 128

4.24 POST CLR 4.0 -- ForEachExpression Class 128

4.24.1 Class Summary 129

4.25 POST CLR 4.0 -- WhileExpression Class 129

4.25.1 Class Summary 129

4.26 POST CLR 4.0 -- RepeatUntilExpression Class 129

4.26.1 Class Summary 129

4.27 GotoExpression Class 129

4.27.1 Class Summary 130

4.27.2 Kind Property 130

4.27.3 Target Property 130

4.27.4 Value Property 130

4.27.5 Update Method 130

4.27.6 Factory Methods 131

4.28 GotoExpressionKind Enum 132

4.28.1 Type Summary 132

4.28.2 Members 132

4.29 LabelExpression Class 132

4.29.1 Example 133

4.29.2 Class Summary 133

4.29.3 DefaultValue Property 134

4.29.4 Target Property 134

4.29.5 Update Method 134

4.29.6 Factory Methods 134

4.30 LabelTarget Class 135

4.30.1 Class Summary 135

4.30.2 Name Property 135

4.30.3 Type Property 135

4.30.4 Factory Methods 135

4.31 MemberExpression Class 136

4.31.1 Class Summary 136

4.31.2 Expression Property 136

4.31.3 Member Property 136

4.31.4 Update Method 136

4.31.5 Factory Methods 136

4.32 MemberInitExpression Class 137

4.32.1 Class Summary 138

4.32.2 Bindings Property 138

4.32.3 NewExpression Property 138

4.32.4 Update Method 138

4.32.5 Factory Methods 138

4.33 MemberBinding Class 139

4.33.1 Class Summary 139

4.33.2 MemberBinding Constructor 139

4.33.3 BindingType Property 139

4.33.4 Member Property 139

4.34 MemberBindingType Enum 140

4.34.1 Type Summary 140

4.34.2 Type Members 140

4.35 MemberListBinding Class 140

4.35.1 Class Summary 140

4.35.2 Initializers Property 141

4.35.3 Update Method 141

4.35.4 Factory Methods 141

4.36 MemberMemberBinding Class 141

4.36.1 Class Summary 142

4.36.2 Bindings Property 142

4.36.3 Update Method 142

4.36.4 Factory Methods 142

4.37 MemberAssignment Class 142

4.37.1 Class Summary 143

4.37.2 Expression Property 143

4.37.3 Update Method 143

4.37.4 Factory Methods 143

4.38 ListInitExpression Class 144

4.38.1 Class Summary 145

4.38.2 Initializers Property 145

4.38.3 NewExpression Property 145

4.38.4 Update Method 145

4.38.5 Factory Methods 145

4.39 ElementInit Class 146

4.39.1 Class Summary 146

4.39.2 AddMethod Property 147

4.39.3 Arguments Property 147

4.39.4 Update Method 147

4.39.5 Factory Methods 147

4.40 NewExpression Class 148

4.40.1 Class Summary 148

4.40.2 Arguments Property 148

4.40.3 Constructor Property 148

4.40.4 Members Property 148

4.40.5 Update Method 149

4.40.6 Factory Methods 149

4.41 NewArrayExpression Class 150

4.41.1 Class Summary 150

4.41.2 Expressions Property 150

4.41.3 Update Method 150

4.41.4 Factory Methods 151

4.42 LambdaExpression Class 151

4.42.1 Examples 152

4.42.2 Class Summary 153

4.42.3 Body Property 153

4.42.4 Name Property 154

4.42.5 Parameters Property 154

4.42.6 ReturnType Property 154

4.42.7 TallCall Property 154

4.42.8 Compile\* Methods 155

4.42.9 Update Method 155

4.42.10 Factory Methods 155

4.43 Expression\<TDelegate\> Class 157

4.43.1 Class Summary 157

4.44 DebugInfoGenerator Class 158

4.44.1 Class Summary 158

4.44.2 DebugInfoGenerator Method 158

4.44.3 MarkSequencePoint Method 158

4.45 ParameterExpression Class 158

4.45.1 Class Summary 159

4.45.2 IsByRef Property 159

4.45.3 Name Property 159

4.45.4 Factory Methods 159

4.46 RuntimeVariablesExpression Class 159

4.46.1 Class Summary 160

4.46.2 Variables Property 160

4.46.3 Update Method 160

4.46.4 Factory Methods 160

4.47 IRuntimeVariables Interface 160

4.47.1 Class Summary 160

4.47.2 Count Property 161

4.47.3 This Property 161

4.48 SwitchExpression Class 161

4.48.1 Class Summary 161

4.48.2 Cases Property 162

4.48.3 Comparison Property 162

4.48.4 DefaultBody Property 162

4.48.5 SwitchValue Property 162

4.48.6 Update Method 162

4.48.7 Factory Methods 162

4.49 SwitchCase Class 163

4.49.1 Class Summary 163

4.49.2 Body Property 164

4.49.3 TestValues Property 164

4.49.4 Update Method 164

4.49.5 Factory Methods 164

4.50 ExpressionVisitor Class 165

4.50.1 Rebinding When Children Nodes' Type Properties Change 165

4.50.2 Class Summary 166

4.50.3 Visit\<T\> Method 168

4.50.4 VisitLambda\<T\> Method 168

4.50.5 VisitAndConvert\<T\> Method 168

4.50.6 VisitConstant Method 168

4.50.7 VisitDebugInfo Method 169

4.50.8 VisitDynamic Method 169

4.50.9 VisitDefault Method 169

4.50.10 VisitExtension Method 169

4.50.11 VisitLabelTarget Method 169

4.50.12 VisitMember Method 169

4.50.13 VisitNew Method 170

4.50.14 VisitParameter Method 170

4.51 POST CLR 4.0 -- GlobalVariableExpression Class 170

4.51.1 Class Summary 170

4.52 POST CLR 4.0 -- GeneratorExpression 170

4.52.1 Class Summary 170

4.52.2 Body Property 171

4.52.3 Target Property 171

4.53 POST CLR 4.0 -- YieldExpression Class 171

4.53.1 Class Summary 171

4.53.2 Target Property 171

4.53.3 Value Property 171

4.53.4 YieldMarker Property 171

~~4.54~~ CUT ~~Annotations Class~~ 172

~~4.54.1~~ ~~Class Summary~~ 172

~~4.54.2~~ ~~Empty Field~~ 172

~~4.54.3~~ ~~Add\<T\> Method~~ 172

~~4.54.4~~ ~~Contains\<T\> Method~~ 172

~~4.54.5~~ ~~Get\<T\> Method~~ 173

~~4.54.6~~ ~~TryGet\<T\> Method~~ 173

~~4.54.7~~ ~~Remove\<T\> Method~~ 173
