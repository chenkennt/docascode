Doc-as-Code: Metadata Format for .NET Languages
===============================================

0. Introduction
---------------

### 0.1 Goal and Non-goals

### 0.2 Terminology

1. Items
--------------

The following .NET elements are defined as *items* in metadata:

1. Namespaces
2. Types, including class, struct, interface, enum, delegate
3. Type members, including field, property, method, event

Other elements like parameters, generic parameters are not standalone *items*, they're part of other *items*.

2. Identifiers
--------------

### 2.1 Namespaces

For a namespace, its *ID* is its name and its *UID* is its full name.

> Example 2.1
> C#:
> ```csharp
> namespace System
> {
>     namespace Linq
>     {
>     }
> }
> ```
> YAML:
> ```yaml
> uid: System.Linq
> id: Linq
> ```
