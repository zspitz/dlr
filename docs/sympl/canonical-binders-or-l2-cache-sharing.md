---
sort: 18
title: Canonical Binders or L2 Cache Sharing
---

# 18 Canonical Binders or L2 Cache Sharing

This section will briefly describe the DLR's caching for dynamic dispatch and explain the code that calls GetXBinder helpers rather than calling a SymplXBinder constructor. For a full discussion of caching, see sites-binders-dynobj-interop.doc on www.codeplex.com/dlr .

As described in section 3.2.1, when you use a DynamicExpression, the Expression Tree compiler creates a CallSite to cache rules for how to perform the CallSite's operation. The delegate that is stored in the CallSite's Target property is considered to be the L0 cache. When the rule in this delegate fails, the CallSite looks to the rules it has cached on the CallSite object (for now, up to ten such rules). These ten rules are considered to be the L1 cache.

When none of the rules seen previously by a CallSite match the current arguments, before the CallSite starts the binding search described in section 3.2.1, it looks at internal state of the binder attached to the CallSite. A binder instance caches up to 100 rules that it has produced. This is considered to be the L2 cache, and it can be shared across multiple CallSites. The idea is that, for example, any call site performing addition with the same metadata on the binder should share rules across an entire program. It is highly likely they are all just adding integers, strings, or a small number of combinations of argument types. Because producing a rule is expensive, you want to save that work once one call site has paid the price.

Sympl maps all binders with the same operation and metadata to a single such binder. It does this per Sympl runtime instance. Having canonical binders per Sympl runtime instance isn't really needed, but it is a good example of what real languages likely need to do. There might be global options per runtime instance, such as whether integers roll over to bignums, or whether division is truncating or float-producing, and so on.

The code for the GetXBinder methods is pretty straightforward. This section just makes a couple of points about how it creates canonical binders, but you can see the code in sympl.cs, which is well commented. You need to hash on the binder type's metadata, which is a little bit of work for InvokeMember binders. All the others just hash on the member name string or a CallInfo object (for which the DLR provides GetHashCode and Equals). For InvokeMember binders, you need to make a key class, InvokeMemberBinderKey, that holds a name and a CallInfo, and then implement GetHashCode and Equals.

Sympl hashes name strings with default .NET semantics and '==' equality, thus comparing case-senstively. The reason is that while Sympl is case-INsensitive, it is case-preserving in the binder metadata, as explained in section 4. This allows for more opportunity of language and library interoperability. Since a DynamicMetaObject might return a rule for looking up a member based on the case-sensitive spelling (that is, ignoring the ignoreCase metadata), Sympl needs to ensure no two CallSites with different spellings could share L2 rules.
