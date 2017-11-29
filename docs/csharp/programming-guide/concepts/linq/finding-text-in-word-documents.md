---
title: Wyszukiwanie tekstu w dokumentach programu Word (C#)
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-csharp
ms.topic: article
ms.assetid: 82f86677-560b-49dc-a089-610409939b2a
caps.latest.revision: "3"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: ab93d21a05c5990092fca14b1368931f773b14fa
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="finding-text-in-word-documents-c"></a><span data-ttu-id="32495-102">Wyszukiwanie tekstu w dokumentach programu Word (C#)</span><span class="sxs-lookup"><span data-stu-id="32495-102">Finding Text in Word Documents (C#)</span></span>
<span data-ttu-id="32495-103">W tym temacie rozszerza poprzednich zapytań do zrobienia czegoś przydatne: Znajdź wszystkie wystąpienia ciągu w dokumencie.</span><span class="sxs-lookup"><span data-stu-id="32495-103">This topic extends the previous queries to do something useful: find all occurrences of a string in the document.</span></span>  
  
## <a name="example"></a><span data-ttu-id="32495-104">Przykład</span><span class="sxs-lookup"><span data-stu-id="32495-104">Example</span></span>  
 <span data-ttu-id="32495-105">W tym przykładzie przetwarza schemat WordprocessingML dokumentu, aby znaleźć wszystkie wystąpienia określonych fragment tekstu w dokumencie.</span><span class="sxs-lookup"><span data-stu-id="32495-105">This example processes a WordprocessingML document, to find all the occurences of a specific piece of text in the document.</span></span> <span data-ttu-id="32495-106">Aby to zrobić, używamy kwerendę, która wyszukuje ciąg "Hello".</span><span class="sxs-lookup"><span data-stu-id="32495-106">To do this, we use a query that finds the string "Hello".</span></span> <span data-ttu-id="32495-107">W tym przykładzie kompilacje w poprzednich przykładach, w tym samouczku.</span><span class="sxs-lookup"><span data-stu-id="32495-107">This example builds on the previous examples in this tutorial.</span></span> <span data-ttu-id="32495-108">Nowe zapytanie jest podana w komentarzach w poniższym kodzie.</span><span class="sxs-lookup"><span data-stu-id="32495-108">The new query is called out in comments in the code below.</span></span>  
  
 <span data-ttu-id="32495-109">Aby uzyskać instrukcje dotyczące tworzenia dokumentu źródłowego dla tego przykładu, zobacz [tworzenie źródło dokumentu pakietu Office Open XML (C#)](../../../../csharp/programming-guide/concepts/linq/creating-the-source-office-open-xml-document.md).</span><span class="sxs-lookup"><span data-stu-id="32495-109">For instructions for creating the source document for this example, see [Creating the Source Office Open XML Document (C#)](../../../../csharp/programming-guide/concepts/linq/creating-the-source-office-open-xml-document.md).</span></span>  
  
 <span data-ttu-id="32495-110">W tym przykładzie użyto znaleziony w zestawie WindowsBase klasy.</span><span class="sxs-lookup"><span data-stu-id="32495-110">This example uses classes found in the WindowsBase assembly.</span></span> <span data-ttu-id="32495-111">Używa typów w <xref:System.IO.Packaging?displayProperty=nameWithType> przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="32495-111">It uses types in the <xref:System.IO.Packaging?displayProperty=nameWithType> namespace.</span></span>  
  
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
  
 <span data-ttu-id="32495-112">Ten przykład generuje następujące wyniki:</span><span class="sxs-lookup"><span data-stu-id="32495-112">This example produces the following output:</span></span>  
  
```  
StyleName:Code >        Console.WriteLine("Hello World");<  
StyleName:Code >Hello World<  
```  
  
 <span data-ttu-id="32495-113">Oczywiście można zmodyfikuj wyszukiwanie, tak, aby wyszukiwania wierszy z określonego stylu.</span><span class="sxs-lookup"><span data-stu-id="32495-113">You can, of course, modify the search so that it searches for lines with a specific style.</span></span> <span data-ttu-id="32495-114">Następujące zapytanie wyszukuje wszystkie puste wiersze, które mają stylu kodu:</span><span class="sxs-lookup"><span data-stu-id="32495-114">The following query finds all blank lines that have the Code style:</span></span>  
  
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
  
 <span data-ttu-id="32495-115">Ten przykład generuje następujące wyniki:</span><span class="sxs-lookup"><span data-stu-id="32495-115">This example produces the following output:</span></span>  
  
```  
StyleName:Code ><  
```  
  
 <span data-ttu-id="32495-116">Oczywiście w tym przykładzie można wzbogacić na kilka sposobów.</span><span class="sxs-lookup"><span data-stu-id="32495-116">Of course, this example could be enhanced in a number of ways.</span></span> <span data-ttu-id="32495-117">Na przykład firma Microsoft może użyć wyrażeń regularnych do wyszukiwania tekstu, firma Microsoft może wykonać iterację wszystkie pliki programu Word w określonym katalogu i tak dalej.</span><span class="sxs-lookup"><span data-stu-id="32495-117">For example, we could use regular expressions to search for text, we could iterate through all the Word files in a particular directory, and so on.</span></span>  
  
 <span data-ttu-id="32495-118">Należy pamiętać, że w tym przykładzie około wykonuje również tak, jakby zostały zapisane jako pojedynczego zapytania.</span><span class="sxs-lookup"><span data-stu-id="32495-118">Note that this example performs approximately as well as if it were written as a single query.</span></span> <span data-ttu-id="32495-119">Ponieważ każde zapytanie jest zaimplementowana w sposób opóźnieniem, odroczone, każdego zapytania nie przekazuje wyniki, dopóki zapytanie jest iterowane.</span><span class="sxs-lookup"><span data-stu-id="32495-119">Because each query is implemented in a lazy, deferred fashion, each query does not yield its results until the query is iterated.</span></span> <span data-ttu-id="32495-120">Aby uzyskać więcej informacji na temat wykonywania i obliczanie leniwe, zobacz [wykonanie odroczone i obliczanie leniwe w składniku LINQ to XML (C#)](../../../../csharp/programming-guide/concepts/linq/deferred-execution-and-lazy-evaluation-in-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="32495-120">For more information about execution and lazy evaluation, see [Deferred Execution and Lazy Evaluation in LINQ to XML (C#)](../../../../csharp/programming-guide/concepts/linq/deferred-execution-and-lazy-evaluation-in-linq-to-xml.md).</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="32495-121">Następne kroki</span><span class="sxs-lookup"><span data-stu-id="32495-121">Next Steps</span></span>  
 <span data-ttu-id="32495-122">Następna sekcja zawiera więcej informacji na temat schemat WordprocessingML dokumentów:</span><span class="sxs-lookup"><span data-stu-id="32495-122">The next section provides more information about WordprocessingML documents:</span></span>  
  
-   [<span data-ttu-id="32495-123">Szczegóły pakietu Office otwieranie dokumentów schemat WordprocessingML XML (C#)</span><span class="sxs-lookup"><span data-stu-id="32495-123">Details of Office Open XML WordprocessingML Documents (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/details-of-office-open-xml-wordprocessingml-documents.md)  
  
## <a name="see-also"></a><span data-ttu-id="32495-124">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="32495-124">See Also</span></span>  
 [<span data-ttu-id="32495-125">Samouczek: Manipulowanie zawartości w dokumencie schemat WordprocessingML (C#)</span><span class="sxs-lookup"><span data-stu-id="32495-125">Tutorial: Manipulating Content in a WordprocessingML Document (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/tutorial-manipulating-content-in-a-wordprocessingml-document.md)  
 [<span data-ttu-id="32495-126">Refaktoryzacja przy użyciu czystej funkcji (C#)</span><span class="sxs-lookup"><span data-stu-id="32495-126">Refactoring Using a Pure Function (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/refactoring-using-a-pure-function.md)  
 [<span data-ttu-id="32495-127">Wykonanie odroczone i obliczanie leniwe w składniku LINQ to XML (C#)</span><span class="sxs-lookup"><span data-stu-id="32495-127">Deferred Execution and Lazy Evaluation in LINQ to XML (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/deferred-execution-and-lazy-evaluation-in-linq-to-xml.md)
