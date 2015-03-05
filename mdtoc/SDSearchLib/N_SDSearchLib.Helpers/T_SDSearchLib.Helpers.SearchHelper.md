```
@T:SDSearchLib.Helpers.SearchHelper
```
```csharp
public class SearchHelper
```
```
@M:SDSearchLib.Helpers.SearchHelper.SearchSingleFile(SDSearchLib.Models.SearchRequest,SDSearchLib.Models.SearchResponse)
```
```csharp
public static void SearchSingleFile(SearchRequest request, SearchResponse response)
```
```
@M:SDSearchLib.Helpers.SearchHelper.GetResultFromResponse(SDSearchLib.Models.SearchResponse,System.String)
```
```csharp
public static Result GetResultFromResponse(SearchResponse response, string filePath)
```
```
@M:SDSearchLib.Helpers.SearchHelper.SearchNormal(SDSearchLib.Models.SearchRequest,SDSearchLib.Models.SearchResponse)
```
```csharp
public static void SearchNormal(SearchRequest request, SearchResponse response)
```
```
@M:SDSearchLib.Helpers.SearchHelper.GetSingleFileDocumentFromLuceneDocument(Lucene.Net.Documents.Document,System.Collections.Generic.Dictionary{System.String,System.Collections.Generic.List{Lucene.Net.Index.TermVectorOffsetInfo}},System.Xml.XmlDocument)
```
```csharp
public static Hashtable GetSingleFileDocumentFromLuceneDocument(Document doc, Dictionary<string, List<TermVectorOffsetInfo>> termVectorOffsetInfosMap, XmlDocument xmlDocument)
```
```
@M:SDSearchLib.Helpers.SearchHelper.GetNormalDocumentFromLuceneDocument(Lucene.Net.Documents.Document,System.Collections.Generic.Dictionary{System.String,System.Collections.Generic.List{Lucene.Net.Index.TermVectorOffsetInfo}},System.Xml.XmlDocument,System.Int32,System.Int32)
```
```csharp
public static Hashtable GetNormalDocumentFromLuceneDocument(Document doc, Dictionary<string, List<TermVectorOffsetInfo>> termVectorOffsetInfosMap, XmlDocument xmlDocument, int defaultCharsCount, int defaultCharsTraceBackCount)
```
