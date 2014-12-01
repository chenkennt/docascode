```
@T:Microsoft.Content.Build.LocalizationUtility
```
```csharp
public static class LocalizationUtility
```
```
@M:Microsoft.Content.Build.LocalizationUtility.SummarizeHandoffCategories(System.String[])
```
```csharp
public static IReadOnlyDictionary<EntityType, Tuple<bool, bool>> SummarizeHandoffCategories(string[] handoffCategories)
```
```
@M:Microsoft.Content.Build.LocalizationUtility.GetHandbackFileType(System.String)
```
```csharp
public static HandbackFileType GetHandbackFileType(string filePath)
```
```
@M:Microsoft.Content.Build.LocalizationUtility.ExtractUhg(System.String,Microsoft.Content.Build.DataContracts.EntityId)
```
```csharp
public static Tuple<EntityIdentifier, EntityIdentifier, int ? , int ? , string> ExtractUhg(string uniqueHandoffIdentifier, EntityId projectId)
```
```
@M:Microsoft.Content.Build.LocalizationUtility.GetBuildBlobPropertyKey(System.String,System.Globalization.CultureInfo)
```
```csharp
public static string GetBuildBlobPropertyKey(string revisionName, CultureInfo locale)
```
```
@M:Microsoft.Content.Build.LocalizationUtility.GenerateUhg(System.String,System.String,System.String,System.Nullable{System.Int32},System.Nullable{System.Int32},System.String)
```
```csharp
public static string GenerateUhg(string handoffItemId, string entityId, string targetLocale, int ? blobRevision, int ? metadataRevsion, string skeletonRelativeXPath)
```
```
@M:Microsoft.Content.Build.LocalizationUtility.Compress(System.String)
```
```csharp
public static string Compress(string text)
```
```
@M:Microsoft.Content.Build.LocalizationUtility.CategorizeTargetLocales(System.Collections.Generic.IEnumerable{System.String},System.Collections.Generic.IEnumerable{System.String})
```
```csharp
public static Tuple<IEnumerable<string>, IEnumerable<string>, IEnumerable<string>> CategorizeTargetLocales(IEnumerable<string> contentHandoffLcoales, IEnumerable<string> metadataHandoffLocalse)
```
```
@M:Microsoft.Content.Build.LocalizationUtility.GetReportName(Microsoft.Content.Build.DataContracts.EntityIdentifier,System.String,System.String)
```
```csharp
public static string GetReportName(EntityIdentifier buildJobId, string buildJobName = null, string reportExtension = null)
```
```
@M:Microsoft.Content.Build.LocalizationUtility.Decompress(System.String)
```
```csharp
public static string Decompress(string compressedText)
```
```
@M:Microsoft.Content.Build.LocalizationUtility.GetHandoffPackageBlobPath(Microsoft.Content.Build.DataContracts.EntityIdentifier,System.String)
```
```csharp
public static string GetHandoffPackageBlobPath(EntityIdentifier handoffId, string handoffName = null)
```
