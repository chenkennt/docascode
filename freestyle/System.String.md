#String Class

.NET Framework 4.5

-----
Represents text as a series of Unicode characters.
To browse the .NET Framework source code for this type, see the [Reference Source](http://referencesource.microsoft.com/#mscorlib/system/string.cs#8281103e6f23cb5c).


Inheritance   | Namespace     | Assemblies| Thread Safety
------------- | ------------- | -------------|-------
[System.Object](file:///system.object.md) </br> ↳ System.String  | [System](file:///system.md) |  System.Runtime (in System.Runtime.dll) </br> mscorlib (in mscorlib.dll) | `This type is thread safe`

```csharp
public sealed class String : IEnumerable<char>,
IEnumerable, IComparable, IComparable<string>, IEquatable<string>
```
##Summary
###Constructors

Type| Name| Discription
----|----|----
public| [String(Char*)](#user-content-stringchar)| Initializes a new instance of the String class to the value indicated by a specified pointer to an array of Unicode characters.
public| [String(Char[])](#user-content-stringchar-1)| Initializes a new instance of the String class to the value indicated by an array of Unicode characters.

###Properties
Type| Name| Discription
----|----|----
public| [Chars](#prop_Chars) |Gets the [Char](file:///system.Char.md) object at a specified position in the current String object.
public| [Length](#prop_Length) |Gets the number of characters in the current String object.

###Methods

Type| Name| Discription
----|----|----
public| [Clone](#method_Clone) |Returns a reference to this instance of String.
public| [Compare(String, String)](#method_Compare_String_String) |Compares two specified String objects and returns an integer that indicates their relative position in the sort order.

###Operators

Type| Name| Discription
----|----|----
public| [Equality](#Equality) |Determines whether two specified strings have the same value.
public| [Inequality](#Inequality) |Determines whether two specified strings have different values.

##Remarks

>*NOTE*

>To view the .NET Framework source code for this type, see the Reference Source. You can browse through the source code online, download the reference for offline viewing, and step through the sources (including patches and updates) during debugging; see instructions.

###Instantiating a String object
You can instantiate a String object in the following ways:

By assigning a string literal to a String variable. This is the most commonly used method for creating a string. The following example uses assignment to create several strings. Note that in C#, because the backslash (\) is an escape character, literal backslashes in a string must be escaped or the entire string must be @-quoted.

```csharp
string string1 = "This is a string created by assignment.";
Console.WriteLine(string1);
string string2a = "The path is C:\\PublicDocuments\\Report1.doc";
Console.WriteLine(string2a);
string string2b = @"The path is C:\PublicDocuments\Report1.doc";
Console.WriteLine(string2b);
// The example displays the following output:
//       This is a string created by assignment.
//       The path is C:\PublicDocuments\Report1.doc
//       The path is C:\PublicDocuments\Report1.doc
```

##Constructors

###String(Char*)
Initializes a new instance of the String class to the value indicated by a specified pointer to an array of Unicode characters.
###String(Char[])
Initializes a new instance of the String class to the value indicated by an array of Unicode characters.

##Properties
###Chars
Gets the [Char](file:///system.Char.md) object at a specified position in the current String object.
###Length
Gets the number of characters in the current String object.

##Methods

###Clone
Returns a reference to this instance of String.
###Compare(String, String)
Compares two specified String objects and returns an integer that indicates their relative position in the sort order.

##Operators

###Equality
Determines whether two specified strings have the same value.
```csharp
public static bool operator ==(
	string a,
	string b
)
```
**Parameters**

*a* [System.String](file:///System.String.md) The first string to compare, or **null**
*b* [System.String](file:///System.String.md) The second string to compare, or **null**

**Returns** [System.Boolean](file:///System.Boolean.md)
**true** if the value of a is the same as the value of b; otherwise, **false**.

###Inequality
##Version Information
* .NET Framework
	* Supported in: 4.6, 4, 3.5, 3.0, 2.0, 1.1, 1.0
* .NET Framework Client Profile
	* Supported in: 4, 3.5 SP1
* Portable Class Library
	* Supported in: Portable Class Library
* .NET for Windows Store apps
	* Supported in: Windows 8
	* Supported in: Windows Phone 8.1
	* Supported in: Windows Phone Silverlight 8.1
	* Supported in: Windows Phone Silverlight 8

##Platforms
Windows Phone 8.1, Windows Phone 8, Windows 8.1, Windows Server 2012 R2, Windows 8, Windows Server 2012, Windows 7, Windows Vista SP2, Windows Server 2008 (Server Core Role not supported), Windows Server 2008 R2 (Server Core Role supported with SP1 or later; Itanium not supported)

The .NET Framework does not support all versions of every platform. For a list of the supported versions, see [.NET Framework System Requirements](http://msdn.microsoft.com/en-us/library/8z6watww.aspx).

## See Also
* Reference
	* [System Namespace](http://msdn.microsoft.com/en-us/library/system.aspx)
	* [IComparable](http://msdn.microsoft.com/en-us/library/system.icomparable.aspx)
* Other Resources
	* [Formatting Types in the .NET Framework](http://msdn.microsoft.com/en-us/library/26etazsy.aspx)
