---
title: Znajdowanie tekstu w dokumentach programu Word (C#)
ms.date: 07/20/2015
ms.assetid: 82f86677-560b-49dc-a089-610409939b2a
ms.openlocfilehash: 173472b9dbd669476c3e5529655d111b88b0dba2
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "70205398"
---
# <a name="finding-text-in-word-documents-c"></a><span data-ttu-id="0375b-102">Znajdowanie tekstu w dokumentach programu Word (C#)</span><span class="sxs-lookup"><span data-stu-id="0375b-102">Finding Text in Word Documents (C#)</span></span>
<span data-ttu-id="0375b-103">W tym temacie rozszerzono poprzednie kwerendy, aby zrobić coś pożytecznego: znaleźć wszystkie wystąpienia ciągu w dokumencie.</span><span class="sxs-lookup"><span data-stu-id="0375b-103">This topic extends the previous queries to do something useful: find all occurrences of a string in the document.</span></span>  
  
## <a name="example"></a><span data-ttu-id="0375b-104">Przykład</span><span class="sxs-lookup"><span data-stu-id="0375b-104">Example</span></span>  
 <span data-ttu-id="0375b-105">W tym przykładzie przetwarza dokument WordprocessingML, aby znaleźć wszystkie wystąpienia określonego fragmentu tekstu w dokumencie.</span><span class="sxs-lookup"><span data-stu-id="0375b-105">This example processes a WordprocessingML document, to find all the occurrences of a specific piece of text in the document.</span></span> <span data-ttu-id="0375b-106">Aby to zrobić, używamy kwerendy, która znajduje ciąg "Hello".</span><span class="sxs-lookup"><span data-stu-id="0375b-106">To do this, we use a query that finds the string "Hello".</span></span> <span data-ttu-id="0375b-107">W tym przykładzie opiera się na poprzednich przykładach w tym samouczku.</span><span class="sxs-lookup"><span data-stu-id="0375b-107">This example builds on the previous examples in this tutorial.</span></span> <span data-ttu-id="0375b-108">Nowe zapytanie jest wywoływane w komentarzach w poniższym kodzie.</span><span class="sxs-lookup"><span data-stu-id="0375b-108">The new query is called out in comments in the code below.</span></span>  
  
 <span data-ttu-id="0375b-109">Aby uzyskać instrukcje dotyczące tworzenia dokumentu źródłowego dla tego [przykładu, zobacz Tworzenie dokumentu XML open pakietu Source Office (C#).](./creating-the-source-office-open-xml-document.md)</span><span class="sxs-lookup"><span data-stu-id="0375b-109">For instructions for creating the source document for this example, see [Creating the Source Office Open XML Document (C#)](./creating-the-source-office-open-xml-document.md).</span></span>  
  
 <span data-ttu-id="0375b-110">W tym przykładzie użyto klas znalezionych w zestawie WindowsBase.</span><span class="sxs-lookup"><span data-stu-id="0375b-110">This example uses classes found in the WindowsBase assembly.</span></span> <span data-ttu-id="0375b-111">Używa typów w <xref:System.IO.Packaging?displayProperty=nameWithType> obszarze nazw.</span><span class="sxs-lookup"><span data-stu-id="0375b-111">It uses types in the <xref:System.IO.Packaging?displayProperty=nameWithType> namespace.</span></span>  
  
```csharp  
public static class LocalExtensions  
{  
    public static string StringConcatenate(this IEnumerable<string> source)  
    {  
        StringBuilder sb = new StringBuilder();  
        foreach (string s in source)  
            sb.Append(s);  
        return sb.ToString();  
    }  
  
    public static string StringConcatenate<T>(this IEnumerable<T> source,  
        Func<T, string> func)  
    {  
        StringBuilder sb = new StringBuilder();  
        foreach (T item in source)  
            sb.Append(func(item));  
        return sb.ToString();  
    }  
  
    public static string StringConcatenate(this IEnumerable<string> source, string separator)  
    {  
        StringBuilder sb = new StringBuilder();  
        foreach (string s in source)  
            sb.Append(s).Append(separator);  
        return sb.ToString();  
    }  
  
    public static string StringConcatenate<T>(this IEnumerable<T> source,  
        Func<T, string> func, string separator)  
    {  
        StringBuilder sb = new StringBuilder();  
        foreach (T item in source)  
            sb.Append(func(item)).Append(separator);  
        return sb.ToString();  
    }  
}  
  
class Program  
{  
    public static string ParagraphText(XElement e)  
    {  
        XNamespace w = e.Name.Namespace;  
        return e  
               .Elements(w + "r")  
               .Elements(w + "t")  
               .StringConcatenate(element => (string)element);  
    }  
  
    static void Main(string[] args)  
    {  
        const string fileName = "SampleDoc.docx";  
  
        const string documentRelationshipType =  
          "http://schemas.openxmlformats.org/officeDocument/2006/relationships/officeDocument";  
        const string stylesRelationshipType =  
          "http://schemas.openxmlformats.org/officeDocument/2006/relationships/styles";  
        const string wordmlNamespace =  
          "http://schemas.openxmlformats.org/wordprocessingml/2006/main";  
        XNamespace w = wordmlNamespace;  
  
        XDocument xDoc = null;  
        XDocument styleDoc = null;  
  
        using (Package wdPackage = Package.Open(fileName, FileMode.Open, FileAccess.Read))  
        {  
            PackageRelationship docPackageRelationship =  
              wdPackage.GetRelationshipsByType(documentRelationshipType).FirstOrDefault();  
            if (docPackageRelationship != null)  
            {  
                Uri documentUri = PackUriHelper.ResolvePartUri(new Uri("/", UriKind.Relative),  
                  docPackageRelationship.TargetUri);  
                PackagePart documentPart = wdPackage.GetPart(documentUri);  
  
                //  Load the document XML in the part into an XDocument instance.  
                xDoc = XDocument.Load(XmlReader.Create(documentPart.GetStream()));  
  
                //  Find the styles part. There will only be one.  
                PackageRelationship styleRelation =  
                  documentPart.GetRelationshipsByType(stylesRelationshipType).FirstOrDefault();  
                if (styleRelation != null)  
                {  
                    Uri styleUri =  
                      PackUriHelper.ResolvePartUri(documentUri, styleRelation.TargetUri);  
                    PackagePart stylePart = wdPackage.GetPart(styleUri);  
  
                    //  Load the style XML in the part into an XDocument instance.  
                    styleDoc = XDocument.Load(XmlReader.Create(stylePart.GetStream()));  
                }  
            }  
        }  
  
        string defaultStyle =  
            (string)(  
                from style in styleDoc.Root.Elements(w + "style")  
                where (string)style.Attribute(w + "type") == "paragraph" &&  
                      (string)style.Attribute(w + "default") == "1"  
                select style  
            ).First().Attribute(w + "styleId");  
  
        // Find all paragraphs in the document.  
        var paragraphs =  
            from para in xDoc  
                         .Root  
                         .Element(w + "body")  
                         .Descendants(w + "p")  
            let styleNode = para  
                            .Elements(w + "pPr")  
                            .Elements(w + "pStyle")  
                            .FirstOrDefault()  
            select new  
            {  
                ParagraphNode = para,  
                StyleName = styleNode != null ?  
                    (string)styleNode.Attribute(w + "val") :  
                    defaultStyle  
            };  
  
        // Retrieve the text of each paragraph.  
        var paraWithText =  
            from para in paragraphs  
            select new  
            {  
                ParagraphNode = para.ParagraphNode,  
                StyleName = para.StyleName,  
                Text = ParagraphText(para.ParagraphNode)  
            };  
  
        // Following is the new query that retrieves all paragraphs  
        // that have specific text in them.  
        var helloParagraphs =  
            from para in paraWithText  
            where para.Text.Contains("Hello")  
            select new  
            {  
                ParagraphNode = para.ParagraphNode,  
                StyleName = para.StyleName,  
                Text = para.Text  
            };  
  
        foreach (var p in helloParagraphs)  
            Console.WriteLine("StyleName:{0} >{1}<", p.StyleName, p.Text);  
    }  
}  
```  
  
 <span data-ttu-id="0375b-112">Ten przykład generuje następujące wyniki:</span><span class="sxs-lookup"><span data-stu-id="0375b-112">This example produces the following output:</span></span>  
  
```output  
StyleName:Code >        Console.WriteLine("Hello World");<  
StyleName:Code >Hello World<  
```  
  
 <span data-ttu-id="0375b-113">Oczywiście można zmodyfikować wyszukiwanie tak, aby wyszukiwać wiersze o określonym stylu.</span><span class="sxs-lookup"><span data-stu-id="0375b-113">You can, of course, modify the search so that it searches for lines with a specific style.</span></span> <span data-ttu-id="0375b-114">Następująca kwerenda wyszukuje wszystkie puste wiersze, które mają styl Kod:</span><span class="sxs-lookup"><span data-stu-id="0375b-114">The following query finds all blank lines that have the Code style:</span></span>  
  
```csharp  
public static class LocalExtensions  
{  
    public static string StringConcatenate(this IEnumerable<string> source)  
    {  
        StringBuilder sb = new StringBuilder();  
        foreach (string s in source)  
            sb.Append(s);  
        return sb.ToString();  
    }  
  
    public static string StringConcatenate<T>(this IEnumerable<T> source,  
        Func<T, string> func)  
    {  
        StringBuilder sb = new StringBuilder();  
        foreach (T item in source)  
            sb.Append(func(item));  
        return sb.ToString();  
    }  
  
    public static string StringConcatenate(this IEnumerable<string> source, string separator)  
    {  
        StringBuilder sb = new StringBuilder();  
        foreach (string s in source)  
            sb.Append(s).Append(separator);  
        return sb.ToString();  
    }  
  
    public static string StringConcatenate<T>(this IEnumerable<T> source,  
        Func<T, string> func, string separator)  
    {  
        StringBuilder sb = new StringBuilder();  
        foreach (T item in source)  
            sb.Append(func(item)).Append(separator);  
        return sb.ToString();  
    }  
}  
  
class Program  
{  
    public static string ParagraphText(XElement e)  
    {  
        XNamespace w = e.Name.Namespace;  
        return e  
               .Elements(w + "r")  
               .Elements(w + "t")  
               .StringConcatenate(element => (string)element);  
    }  
  
    static void Main(string[] args)  
    {  
        const string fileName = "SampleDoc.docx";  
  
        const string documentRelationshipType = "http://schemas.openxmlformats.org/officeDocument/2006/relationships/officeDocument";  
        const string stylesRelationshipType = "http://schemas.openxmlformats.org/officeDocument/2006/relationships/styles";  
        const string wordmlNamespace = "http://schemas.openxmlformats.org/wordprocessingml/2006/main";  
        XNamespace w = wordmlNamespace;  
  
        XDocument xDoc = null;  
        XDocument styleDoc = null;  
  
        using (Package wdPackage = Package.Open(fileName, FileMode.Open, FileAccess.Read))  
        {  
            PackageRelationship docPackageRelationship = wdPackage.GetRelationshipsByType(documentRelationshipType).FirstOrDefault();  
            if (docPackageRelationship != null)  
            {  
                Uri documentUri = PackUriHelper.ResolvePartUri(new Uri("/", UriKind.Relative), docPackageRelationship.TargetUri);  
                PackagePart documentPart = wdPackage.GetPart(documentUri);  
  
                //  Load the document XML in the part into an XDocument instance.  
                xDoc = XDocument.Load(XmlReader.Create(documentPart.GetStream()));  
  
                //  Find the styles part. There will only be one.  
                PackageRelationship styleRelation = documentPart.GetRelationshipsByType(stylesRelationshipType).FirstOrDefault();  
                if (styleRelation != null)  
                {  
                    Uri styleUri = PackUriHelper.ResolvePartUri(documentUri, styleRelation.TargetUri);  
                    PackagePart stylePart = wdPackage.GetPart(styleUri);  
  
                    //  Load the style XML in the part into an XDocument instance.  
                    styleDoc = XDocument.Load(XmlReader.Create(stylePart.GetStream()));  
                }  
            }  
        }  
  
        string defaultStyle =  
            (string)(  
                from style in styleDoc.Root.Elements(w + "style")  
                where (string)style.Attribute(w + "type") == "paragraph" &&  
                      (string)style.Attribute(w + "default") == "1"  
                select style  
            ).First().Attribute(w + "styleId");  
  
        // Find all paragraphs in the document.  
        var paragraphs =  
            from para in xDoc  
                         .Root  
                         .Element(w + "body")  
                         .Descendants(w + "p")  
            let styleNode = para  
                            .Elements(w + "pPr")  
                            .Elements(w + "pStyle")  
                            .FirstOrDefault()  
            select new  
            {  
                ParagraphNode = para,  
                StyleName = styleNode != null ?  
                    (string)styleNode.Attribute(w + "val") :  
                    defaultStyle  
            };  
  
        // Retrieve the text of each paragraph.  
        var paraWithText =  
            from para in paragraphs  
            select new  
            {  
                ParagraphNode = para.ParagraphNode,  
                StyleName = para.StyleName,  
                Text = ParagraphText(para.ParagraphNode)  
            };  
  
        // Retrieve all paragraphs that have no text and are styled Code.  
        var blankCodeParagraphs =  
            from para in paraWithText  
            where para.Text == "" && para.StyleName == "Code"  
            select new  
            {  
                ParagraphNode = para.ParagraphNode,  
                StyleName = para.StyleName,  
                Text = para.Text  
            };  
  
        foreach (var p in blankCodeParagraphs)  
            Console.WriteLine("StyleName:{0} >{1}<", p.StyleName, p.Text);  
    }  
}  
```  
  
 <span data-ttu-id="0375b-115">Ten przykład generuje następujące wyniki:</span><span class="sxs-lookup"><span data-stu-id="0375b-115">This example produces the following output:</span></span>  
  
```output  
StyleName:Code ><  
```  
  
 <span data-ttu-id="0375b-116">Oczywiście, ten przykład może być wzmocniony na wiele sposobów.</span><span class="sxs-lookup"><span data-stu-id="0375b-116">Of course, this example could be enhanced in a number of ways.</span></span> <span data-ttu-id="0375b-117">Na przykład możemy użyć wyrażeń regularnych do wyszukiwania tekstu, możemy iterować wszystkie pliki programu Word w określonym katalogu i tak dalej.</span><span class="sxs-lookup"><span data-stu-id="0375b-117">For example, we could use regular expressions to search for text, we could iterate through all the Word files in a particular directory, and so on.</span></span>  
  
 <span data-ttu-id="0375b-118">Należy zauważyć, że w tym przykładzie wykonuje w przybliżeniu, jak również jeśli zostały zapisane jako pojedyncze zapytanie.</span><span class="sxs-lookup"><span data-stu-id="0375b-118">Note that this example performs approximately as well as if it were written as a single query.</span></span> <span data-ttu-id="0375b-119">Ponieważ każda kwerenda jest implementowana w sposób leniwy, odroczone, każda kwerenda nie daje jego wyniki, dopóki kwerenda jest iterowana.</span><span class="sxs-lookup"><span data-stu-id="0375b-119">Because each query is implemented in a lazy, deferred fashion, each query does not yield its results until the query is iterated.</span></span> <span data-ttu-id="0375b-120">Aby uzyskać więcej informacji na temat wykonywania i oceny z opóźnieniem, zobacz [Odroczone wykonanie i ocena z opóźnieniem w LINQ do XML (C#)](./deferred-execution-and-lazy-evaluation-in-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="0375b-120">For more information about execution and lazy evaluation, see [Deferred Execution and Lazy Evaluation in LINQ to XML (C#)](./deferred-execution-and-lazy-evaluation-in-linq-to-xml.md).</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="0375b-121">Następne kroki</span><span class="sxs-lookup"><span data-stu-id="0375b-121">Next Steps</span></span>  
 <span data-ttu-id="0375b-122">Następna sekcja zawiera więcej informacji na temat dokumentów WordprocessingML:</span><span class="sxs-lookup"><span data-stu-id="0375b-122">The next section provides more information about WordprocessingML documents:</span></span>  
  
- [<span data-ttu-id="0375b-123">Szczegóły dokumentów wordprocessingml pakietu Office Open XML (C#)</span><span class="sxs-lookup"><span data-stu-id="0375b-123">Details of Office Open XML WordprocessingML Documents (C#)</span></span>](./wordprocessingml-document-with-styles.md)  
  
## <a name="see-also"></a><span data-ttu-id="0375b-124">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="0375b-124">See also</span></span>

- [<span data-ttu-id="0375b-125">Samouczek: manipulowanie zawartością w dokumencie WordprocessingML (C#)</span><span class="sxs-lookup"><span data-stu-id="0375b-125">Tutorial: Manipulating Content in a WordprocessingML Document (C#)</span></span>](./shape-of-wordprocessingml-documents.md)
- [<span data-ttu-id="0375b-126">Refaktoryzacja przy użyciu czystej funkcji (C#)</span><span class="sxs-lookup"><span data-stu-id="0375b-126">Refactoring Using a Pure Function (C#)</span></span>](./refactoring-using-a-pure-function.md)
- [<span data-ttu-id="0375b-127">Odroczone wykonanie i ocena z opóźnieniem w LINQ do XML (C#)</span><span class="sxs-lookup"><span data-stu-id="0375b-127">Deferred Execution and Lazy Evaluation in LINQ to XML (C#)</span></span>](./deferred-execution-and-lazy-evaluation-in-linq-to-xml.md)
