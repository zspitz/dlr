---
sort: 12
title: ErrorSuggestion Arguments to Binder FallbackX Methods
---

# 12 ErrorSuggestion Arguments to Binder FallbackX Methods

Recall that the convention in the DLR is for dynamic objects to call FallbackX methods so that the language owning the line of code that produced the CallSite can perform .NET static binding. Furthermore, from the description of the flow of execution when searching for a binding (see section 3.2.1), the DLR calls on DynamicMetaObjects first. You might ask yourself, should the object look for dynamic members first or static members, and how should this negotiation happen with the language binder.

The errorSuggestion parameter provides a mechanism for allowing dynamic objects to choose static first or not. To post-process dynamic members, the DynamicMetaObject can compute a binding rule and pass it to the binder via errorSuggestion. The binder will search for a static member on the .NET type and return a rule if it is successful. The binder will return the errorSuggestion if it is not null to allow the dynamic object to return a rule for a dynamic member. The pre-process dynamic members, the DynamicMetaObject can just return a rule on success and fallback to the binder on failure with a null errorSuggestion.

That's the basic concept, but the dance the DyanamicMetaObject needs to perform with the binder is a bit more intricate for total correctness in the post-process dynamic member case. This is described more fully in the sites-binders-dynobj-interop.doc document on www.codeplex.com/dlr, but here's a quick description. Recall the convention is to fall back to the binder for a language specific error if the dynamic member lookup fails. The meta-object calls on the binder twice to build a complete rule. The first call on the binder gets a successful static member lookup expression or a language-specific error. The DynamicMetaObject uses this expression in its "else" clause for its expression that looks up a dynamic member. Now the DynamicMetaObject calls the binder's FallbackX method again with the combined expression as the errorSuggestion. The binder now binds again (of course, producing exactly what it did before), but it now has an errorSuggestion when the static binding fails that looks up dynamically (after the static lookup) and has a language-specific error branch.
