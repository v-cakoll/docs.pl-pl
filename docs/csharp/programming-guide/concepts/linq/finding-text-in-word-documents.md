---
title: Znajdowanie tekstu w dokumentach programu Word (C#)
description: Dowiedz się, jak przetwarzać dokument WordprocessingML za pomocą LINQ w języku C#. Ten przykład odnajduje wszystkie wystąpienia ciągu w dokumencie.
ms.date: 07/20/2015
ms.assetid: 82f86677-560b-49dc-a089-610409939b2a
ms.openlocfilehash: 1efcbef6185b718287f1222ecc086f4c675f02ab
ms.sourcegitcommit: 04022ca5d00b2074e1b1ffdbd76bec4950697c4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/23/2020
ms.locfileid: "87105392"
---
# <a name="finding-text-in-word-documents-c"></a><span data-ttu-id="c643c-104">Znajdowanie tekstu w dokumentach programu Word (C#)</span><span class="sxs-lookup"><span data-stu-id="c643c-104">Finding Text in Word Documents (C#)</span></span>
<span data-ttu-id="c643c-105">Ten temat rozszerza poprzednie zapytania, aby wykonać coś użytecznego: Znajdź wszystkie wystąpienia ciągu w dokumencie.</span><span class="sxs-lookup"><span data-stu-id="c643c-105">This topic extends the previous queries to do something useful: find all occurrences of a string in the document.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c643c-106">Przykład</span><span class="sxs-lookup"><span data-stu-id="c643c-106">Example</span></span>  
 <span data-ttu-id="c643c-107">Ten przykład przetwarza dokument WordprocessingML, aby znaleźć wszystkie wystąpienia określonego fragmentu tekstu w dokumencie.</span><span class="sxs-lookup"><span data-stu-id="c643c-107">This example processes a WordprocessingML document, to find all the occurrences of a specific piece of text in the document.</span></span> <span data-ttu-id="c643c-108">W tym celu użyjemy zapytania, które odnajdzie ciąg "Hello".</span><span class="sxs-lookup"><span data-stu-id="c643c-108">To do this, we use a query that finds the string "Hello".</span></span> <span data-ttu-id="c643c-109">Ten przykład kompiluje się zgodnie z poprzednimi przykładami w tym samouczku.</span><span class="sxs-lookup"><span data-stu-id="c643c-109">This example builds on the previous examples in this tutorial.</span></span> <span data-ttu-id="c643c-110">Nowe zapytanie jest wywoływane w komentarzach w poniższym kodzie.</span><span class="sxs-lookup"><span data-stu-id="c643c-110">The new query is called out in comments in the code below.</span></span>  
  
 <span data-ttu-id="c643c-111">Aby uzyskać instrukcje dotyczące tworzenia dokumentu źródłowego dla tego przykładu, zobacz [Tworzenie źródłowego dokumentu Office Open XML (C#)](./creating-the-source-office-open-xml-document.md).</span><span class="sxs-lookup"><span data-stu-id="c643c-111">For instructions for creating the source document for this example, see [Creating the Source Office Open XML Document (C#)](./creating-the-source-office-open-xml-document.md).</span></span>  
  
 <span data-ttu-id="c643c-112">Ten przykład używa klas znalezionych w zestawie 'Windowsbase.</span><span class="sxs-lookup"><span data-stu-id="c643c-112">This example uses classes found in the WindowsBase assembly.</span></span> <span data-ttu-id="c643c-113">Używa typów w <xref:System.IO.Packaging?displayProperty=nameWithType> przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="c643c-113">It uses types in the <xref:System.IO.Packaging?displayProperty=nameWithType> namespace.</span></span>  
  
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
  
 <span data-ttu-id="c643c-114">Ten przykład generuje następujące wyniki:</span><span class="sxs-lookup"><span data-stu-id="c643c-114">This example produces the following output:</span></span>  
  
```output  
StyleName:Code >        Console.WriteLine("Hello World");<  
StyleName:Code >Hello World<  
```  
  
 <span data-ttu-id="c643c-115">Można oczywiście zmodyfikować wyszukiwanie, tak aby wyszukiwać wiersze o określonym stylu.</span><span class="sxs-lookup"><span data-stu-id="c643c-115">You can, of course, modify the search so that it searches for lines with a specific style.</span></span> <span data-ttu-id="c643c-116">Poniższe zapytanie znajduje wszystkie puste wiersze, które mają styl kodu:</span><span class="sxs-lookup"><span data-stu-id="c643c-116">The following query finds all blank lines that have the Code style:</span></span>  
  
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
  
 <span data-ttu-id="c643c-117">Ten przykład generuje następujące wyniki:</span><span class="sxs-lookup"><span data-stu-id="c643c-117">This example produces the following output:</span></span>  
  
```output  
StyleName:Code ><  
```  
  
 <span data-ttu-id="c643c-118">Oczywiście ten przykład można rozszerzyć na wiele sposobów.</span><span class="sxs-lookup"><span data-stu-id="c643c-118">Of course, this example could be enhanced in a number of ways.</span></span> <span data-ttu-id="c643c-119">Na przykład możemy używać wyrażeń regularnych do wyszukiwania tekstu, możemy przejść przez wszystkie pliki programu Word w określonym katalogu i tak dalej.</span><span class="sxs-lookup"><span data-stu-id="c643c-119">For example, we could use regular expressions to search for text, we could iterate through all the Word files in a particular directory, and so on.</span></span>  
  
 <span data-ttu-id="c643c-120">Należy zauważyć, że ten przykład wykonuje około, a także, jeśli został zapisany jako pojedyncze zapytanie.</span><span class="sxs-lookup"><span data-stu-id="c643c-120">Note that this example performs approximately as well as if it were written as a single query.</span></span> <span data-ttu-id="c643c-121">Ponieważ każde zapytanie jest zaimplementowane w opóźniony, odroczony sposób, każde zapytanie nie zwraca wyników, dopóki zapytanie nie zostanie powtórzone.</span><span class="sxs-lookup"><span data-stu-id="c643c-121">Because each query is implemented in a lazy, deferred fashion, each query does not yield its results until the query is iterated.</span></span> <span data-ttu-id="c643c-122">Aby uzyskać więcej informacji na temat wykonywania i oceny z opóźnieniem, zobacz [wykonywanie odroczone i obliczanie z opóźnieniem w LINQ to XML (C#)](./deferred-execution-and-lazy-evaluation-in-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="c643c-122">For more information about execution and lazy evaluation, see [Deferred Execution and Lazy Evaluation in LINQ to XML (C#)](./deferred-execution-and-lazy-evaluation-in-linq-to-xml.md).</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="c643c-123">Następne kroki</span><span class="sxs-lookup"><span data-stu-id="c643c-123">Next Steps</span></span>  
 <span data-ttu-id="c643c-124">Następna sekcja zawiera więcej informacji na temat dokumentów WordprocessingML:</span><span class="sxs-lookup"><span data-stu-id="c643c-124">The next section provides more information about WordprocessingML documents:</span></span>  
  
- [<span data-ttu-id="c643c-125">Szczegóły dotyczące dokumentów Office Open XML WordprocessingML (C#)</span><span class="sxs-lookup"><span data-stu-id="c643c-125">Details of Office Open XML WordprocessingML Documents (C#)</span></span>](./wordprocessingml-document-with-styles.md)  
  
## <a name="see-also"></a><span data-ttu-id="c643c-126">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="c643c-126">See also</span></span>

- [<span data-ttu-id="c643c-127">Samouczek: manipulowanie zawartością w dokumencie WordprocessingML (C#)</span><span class="sxs-lookup"><span data-stu-id="c643c-127">Tutorial: Manipulating Content in a WordprocessingML Document (C#)</span></span>](./shape-of-wordprocessingml-documents.md)
- [<span data-ttu-id="c643c-128">Refaktoryzacja przy użyciu czystej funkcji (C#)</span><span class="sxs-lookup"><span data-stu-id="c643c-128">Refactoring Using a Pure Function (C#)</span></span>](./refactoring-using-a-pure-function.md)
- [<span data-ttu-id="c643c-129">Wykonywanie odroczone i Ocena z opóźnieniem w LINQ to XML (C#)</span><span class="sxs-lookup"><span data-stu-id="c643c-129">Deferred Execution and Lazy Evaluation in LINQ to XML (C#)</span></span>](./deferred-execution-and-lazy-evaluation-in-linq-to-xml.md)
