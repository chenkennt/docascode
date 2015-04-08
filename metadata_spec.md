Doc-as-Code: Metadata Format Specification
==========================================

0. Design Notes
---------------

### 0.1 Terms

The terms **MUST**, **MUST NOT**, **SHOULD**, **SHOULD NOT**, **MAY** (upper case and bold in this document) have exactly the same meaning as they are defined in [RFC 2119][1].

Words in *italic* imply they are terms defined in an earlier section of this document.

### 0.2 Language Agnostic

// TODO

1. Items and Identifiers
------------------------

### 1.1 Items

Item is the basic unit of metadata format. From documentation perspective, each item represents a "section" in the documentation. This "section" is the minimum unit that you can cross reference to, or customize its layout and content.

> When implementing the metadata format for your own language, you can decide which elements are items. For example, usually namespaces, classes, methods are items. But you can also make smaller elements like parameters to be item if you want them to be referencable and customizable.

Items can be hierarchical. One item can have other items as children. For example, in C#, namespaces and classes can have classes and/or methods as children.

### 1.2 Identifiers

Each *item* has an identifier (ID) which is unique under it's parent.

As we're targeting to support multiple languages, there is no special restrictions about which characters are allowed in identifiers. But to make identifier easier to be recognized and resolved in markdown, it's not **RECOMMENDED** to have whitespaces in identifier. Markdown processor **MAY** implement some algorithm to tolerate whitespaces in handwritten markdown. (Leading and trailing spaces **MUST** be removed from identifier.)

Identifier **MUST** be treated as case-sensitive when comparing equality.

Each *item* has a unique identifier (UID) which is globally unique. UID is defined as follows:
1. If an *item* does not have parent, its UID is its ID.
2. Otherwise its UID is the combination of the UID of its parent, a separator and the ID of the *item* itself.

Valid separators are `.`, `:`, `/` and `\`.

For example, for a class `String` under namespace `System`, its ID is `String` and UID is `System.String`.

> Given the above definition, an *item*'s UID **MUST** starts with the UID of its parent (and any ancestor) and ends with the ID of itself. This is useful to quickly determine whether an *item* is under another item.

### 1.3 Alias

*Identifier* could be very long, which makes it difficult to write by hand in markdown. For example, it's easy to create a long *ID* in C# like this:

```markdown
Format(System.IFormatProvider,System.String,System.Object,System.Object)
```

We can create short alias for *items* so that they can be referenced easily.

Alias is same as *ID*, except:
1. It doesn't have to be unique.
2. One *item* can have multiple aliases.

> It's not **RECOMMENDED** to create alias that has nothing to do with item's *ID*. Usually an *item*'s alias is part of its *ID* so it's easy to recognize and memorize.  
> For example, for the case above, we usually create an alias `Format()`.

We can easily create a "global" alias for an *item* by replacing the *ID* part of its *UID* with its alias.

### 1.4 Reference Item by Identifier and Alias

We utilize markdown syntax to represent reference to one or more *items*. First we introduce a new markdown syntax to represent *item* reference:

If a string starts with `@`, and followed by a string enclosed by curly braces `{}`, it will be treated as an *item* reference. The string inside `{}` is the *UID* of the *item*. Here is one example:

```markdown
@{System.String}
```

*UID* can be enclosed by multiple curly braces, but the number of `{` and `}` should match, for example, `@{{System.String}}` is also a valid reference. By doing this, we can allow curly braces inside *UID*.

> Markdown processor **MAY** implement some algorithm to allow omit curly braces if *ID* is simple enough. For example, For reference like `@{int}`, we may also want to allow `@int`.

When rendering reference in markdown, they will be expanded into a link with the *item*'s name (will be defined in a later section) as link title. You can also customize the link title using the standard link syntax of markdown:

```markdown
[Dictionary](@{System.Collections.Generic.Dictionary`2})<[String](@{System.String}), [String](@{System.String})>
```

Will be rendered to:
[Dictionary](@{System.Collections.Generic.Dictionary`2})<[String](@{System.String}), [String](@{System.String})>

We use curly braces as the separator as it hardly appears in identifiers in most programming languages. As we said before, if you really want to use them, you have to escape them manually.

> In many programming languages, there is a concept of "template instantiation". For example, in C#, you can create a new type `List<int>` from `List<T>` with argument `int`. It's not **RECOMMENDED** to create *items* for "template instances". Instead, you can reference to them using markdown. For example, in this case, ``[List](@{List`1})<@{int}>``.

Besides *UID*, we also allow reference item using *ID* and *alias*, in markdown processor, the following algorithm **SHOULD** be implemented to resolve references:
1. Check whether the reference matches any *identifier* of current *item*'s children.
2. Check whether the reference matches any *alias* of current *item*'s children.
3. Check whether the reference matches any *identifier* of current *item*'s silbings
4. Check whether the reference matches any *alias* of current *item*'s silbings
5. Check whether the reference matches a *UID*.
6. Check whether the reference matches a *global alias*.

2. File Structure
-----------------

### 2.1 File Format

You can use any file format that can represent structural data to store metadata. But we recommend to use [YAML][2] or [JSON][3]. In this specification, we use YAML in examples, but all YAML can be converted to JSON easily.

### 2.2 File Layout

A metadata file consists of a list of *item* objects. Each object is a key-value pair (hereafter referred to as "property") list.

Though *items* can be hierarchical, they are in a flat layout in file. Instead, each *item* has an "children" property indicates its children and a "parent" property indicates its parent.

An *item* object has some basic properties:

Property   | Description                                      
-----------|-------------------------------------------------
uid        | **REQUIRED**. The unique identifier of the item. 
children   | **OPTIONAL**. A list of *UIDs* of the *item*'s children. Can be omitted if there is no children.
parent     | **OPTIONAL**. The *UID* of the parent of the **item**. If omitted, parser will try to figure out its parent from the children information of other *items* within the same file.
isExternal | **OPTIONAL**. If true, it means this *item* only serves as a reference by other *items* in the same file. Default value is false.

Here is an example of a YAML format metadata file for C# Object class:

```yaml
- uid: System.Object
  parent: System
  children:
  - System.Object.Object()
  - System.Object.Equals(System.Object)
  - System.Object.Equals(System.Object,System.Object)
  - System.Object.Finalize()
  - System.Object.GetHashCode()
  - System.Object.GetType()
  - System.Object.MemberwiseClone()
  - System.Object.ReferenceEquals()
  - System.Object.ToString()
- uid: System.Object.Object()
  parent: System.Object
- uid: System.Object.Equals(System.Object)
  parent: System.Object
- uid: System.Object.Equals(System.Object,System.Object)
  parent: System.Object
- uid: System.Object.Finalize()
  parent: System.Object
- uid: System.Object.GetHashCode()
  parent: System.Object
- uid: System.Object.GetType()
  parent: System.Object
- uid: System.Object.MemberwiseClone()
  parent: System.Object
- uid: System.Object.ReferenceEquals()
  parent: System.Object
- uid: System.Object.ToString()
  parent: System.Object
- uid: System
  isExternal: true
```

> It's **RECOMMENDED** to include referenced *items* in the same file as externals. This makes the file self contained and easy to render at runtime. External *items* doesn't need to have all properties, it just contains some necessary properties for rendering the documentation.

> *Items* **SHOULD** be organized based on how they will be displayed in documentation. For example, if you want all members of a class displayed in a single page, put all of them in a single metadata file.

### 2.3 Item Object
In additional to the *properties* listed in last section, *item object* also has some **OPTIONAL** *properties*:

Property | Description
---------|-----------------------------------
id       | The *identifier* of the *item*.
alias    | A list of *aliases* of the *item*.
name     | The display name of the *item*.
fullName | The full display name of the *item*. In programming languages, it's usually the full qualified name.
type     | The type of the *item*, like class, method, etc.
url      | If it's a relative url, it points to another metadata file that defines the *item*. If it's an absolute url, it means the *item* is coming from an external library, and the url is the documentation page of this *item*. If omitted, the url is the location of the current file.
source   | The source code information of the *item*. It's an object which contains following properties:<br>1. repo: the remote git repository of the source code.<br>2. branch: the branch of the source code.<br>3. revision: the git revision of the source code.<br>4. path: the path of the source code file where the *item* is defined.<br>5. startLine: the start line of the *item* definition.<br>6. endLine: the end line of the *item* definition.

Here is an example of a C# Dictionary class:

```yaml
- uid: System.Collections.Generic.Dictionary`2
  id: Dictionary`2
  alias:
  - Dictionary
  parent: System.Collections.Generic
  name: Dictionary<TKey, TValue>
  fullName: System.Collections.Generic.Dictionary<TKey, TValue>
  type: method
  url: System.Collections.Generic.Dictionary`2.yml
  source:
    repo: https://github.com/dotnet/netfx.git
    branch: master
    revision: 5ed47001acfb284a301260271f7d36d2bb014432
    path: src/system/collections/generic/dictionary.cs
    startLine: 1
    endLine: 100
```

### 2.4 Custom Properties

3. Multiple Language Support
----------------------------


```
  name.csharp: Dictionary<TKey, TValue>
  name.vb: Dictionary(Of TKey, TValue)
  fullName.csharp: System.Collections.Generic.Dictionary<{0}, {1}>
  fullName.vb: System.Collections.Generic.Dictionary(Of {0}, {1})
  documentation:
```
  



### 1.6 Reference Item by ID, UID and Alias

*ID*, *UID* and *alias* are designed to 

### Overload
Overload is a group of *items* which have the same *ID* under a *scope*. This is a common concept in many programming languages.
For example, in C#, function `Equals()` may have the following overloads:
```csharp
bool Equals(object);
bool Equals(string);
bool Equals(string, string);
bool Equals(string, StringComparison);
bool Equals(string, string, StringComparison);
```

All these methods will have the same *ID*, but with an overload section to distinguish between different overloads.
Overload section **MUST** be surrounded by overload separator.

Valid overload separator are `()`, `[]` and `{}`.

Overload section **MAY** contain a list of *QIDs*, which are separated by separators (valid separators are `,`, `

> An algorithm **SHOULD** be implemented to allow match *QID* without overload section.
> For example, user can write `Equals` to match one of the overload function of Equals.

> When designing *QID* for your own languages, it's **RECOMMENDED** to always include overload separators if the type of item supports overload,
> no matter the *item* itself is overloaded or not. For example, use `ToString()` instead of `ToString` even it's not overloaded.

### Whitespaces
*QID* can contain whitespace, but they will be ignored when comparing equality.

For example, 
`Equals (string, string)` and `Equals(string,string)` are same *QID*.

### ID in C# 

#### Types
1. Predefined types: `object`, `string`, `int`, etc.
2. Simple types: `System.Exception`
3. Generic types: ``System.Collections.Generic.IEnumerable`1``, ``System.Collections.Generic.Dictionary`2``

#### Methods


`System.String.Equals(System.String, System.String)`
`String.Equals(String, String)`




#### Combined IDs
Combined ID is used to represent types like generic type instantiation.
Theoretically these types doesn't really exist, so these IDs are used to reference multiple APIs at the same time.  
For example:  
``System.Collections.Generic.IEnumerable`1<string>``  
``System.Collections.Generic.Dictionary`2<int, System.Exception>``


[1]: https://www.ietf.org/rfc/rfc2119.txt
[2]: http://www.yaml.org/
[3]: http://www.json.org/
