```
@T:SDSearchLib.Helpers.HighlightHelper
```
```csharp
public class HighlightHelper
```
```
@M:SDSearchLib.Helpers.HighlightHelper.GetHighlightedStringInNodes(System.String,System.Collections.Generic.List{Lucene.Net.Index.TermVectorOffsetInfo},System.Xml.XmlDocument,System.Int32,System.Int32)
```
```csharp
public static LinkedList<XmlNode> GetHighlightedStringInNodes(string content, List<TermVectorOffsetInfo> termVectorOffsetInfos, XmlDocument xmlDocument, int charsCount, int charsTraceBackCount)
```
```
@M:SDSearchLib.Helpers.HighlightHelper.GetTermVectorOffsetInfosMap(Lucene.Net.Index.IndexReader,System.Collections.Generic.List{System.Collections.Generic.List{Lucene.Net.Index.Term}},System.Int32,System.String[])
```
```csharp
public static Dictionary<string, List<TermVectorOffsetInfo>> GetTermVectorOffsetInfosMap(IndexReader indexReader, List<List<Term>> multiTerms, int docID, String[] fields)
```
```
@M:SDSearchLib.Helpers.HighlightHelper.GetHighlightedLinesInNode(System.String,System.Collections.Generic.List{Lucene.Net.Index.TermVectorOffsetInfo},System.Xml.XmlDocument,System.String,System.Boolean)
```
```csharp
public static XmlNode GetHighlightedLinesInNode(string content, List<TermVectorOffsetInfo> termVectorOffsetInfos, XmlDocument xmlDocument, string lineOffsets, bool isReturnAllLines)
```
