**Alex Turner and Bill Chiles**

[1 Introduction 2](#introduction)

[2 ExpandoObject 2](#expandoobject)

[3 DynamicObject 4](#dynamicobject)

[3.1 DynamicBag: Implementing Our Own ExpandoObject 5](#dynamicbag-implementing-our-own-expandoobject)

[3.2 NamedBag: Optimizing DynamicObject with Statically Defined Members 6](#namedbag-optimizing-dynamicobject-with-statically-defined-members)

[4 IDynamicMetaObjectProvider and DynamicMetaObject 8](#idynamicmetaobjectprovider-and-dynamicmetaobject)

[4.1 FastNBag: Faster Bags for N Slots 8](#fastnbag-faster-bags-for-n-slots)

[4.1.1 BindSetMember Method 9](#bindsetmember-method)

[4.1.2 BindGetMember Method 10](#bindgetmember-method)

[4.1.3 GetDynamicMemberNames Method 13](#getdynamicmembernames-method)

[4.2 Further Reading 14](#further-reading)

[5 Appendix 14](#appendix)

[5.1 DynamicObject Virtual Methods 14](#dynamicobject-virtual-methods)

[5.2 FastNBag Full Source 15](#fastnbag-full-source)
