---
title: Refaktoryzacja przy użyciu czystej funkcji (C#)
ms.date: 07/20/2015
ms.assetid: a3416a45-9e12-4e4a-9747-897f06eef510
ms.openlocfilehash: d1c4b1fc59e52fbd72dec1ee0e73e7198a083868
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/19/2019
ms.locfileid: "69591310"
---
# <a name="refactoring-using-a-pure-function-c"></a><span data-ttu-id="829ab-102">Refaktoryzacja przy użyciu czystej funkcji (C#)</span><span class="sxs-lookup"><span data-stu-id="829ab-102">Refactoring Using a Pure Function (C#)</span></span>
<span data-ttu-id="829ab-103">Poniższy przykład refaktoryzacji w poprzednim przykładzie, refaktoryzacji [przy użyciu metody rozszerzeniaC#()](./refactoring-using-an-extension-method.md), aby użyć czystej funkcji w tym przykładzie, kod, aby znaleźć tekst akapitu, jest przenoszony do czystej metody `ParagraphText`statycznej.</span><span class="sxs-lookup"><span data-stu-id="829ab-103">The following example refactors the previous example, [Refactoring Using an Extension Method (C#)](./refactoring-using-an-extension-method.md), to use a pure function In this example, the code to find the text of a paragraph is moved to the pure static method `ParagraphText`.</span></span>  
  
## <a name="example"></a><span data-ttu-id="829ab-104">Przykład</span><span class="sxs-lookup"><span data-stu-id="829ab-104">Example</span></span>  
 <span data-ttu-id="829ab-105">Ten przykład przetwarza dokument WordprocessingML, pobierając węzły akapitu z dokumentu WordprocessingML.</span><span class="sxs-lookup"><span data-stu-id="829ab-105">This example processes a WordprocessingML document, retrieving the paragraph nodes from a WordprocessingML document.</span></span> <span data-ttu-id="829ab-106">Identyfikuje także styl każdego akapitu.</span><span class="sxs-lookup"><span data-stu-id="829ab-106">It also identifies the style of each paragraph.</span></span> <span data-ttu-id="829ab-107">Ten przykład kompiluje się zgodnie z poprzednimi przykładami w tym samouczku.</span><span class="sxs-lookup"><span data-stu-id="829ab-107">This example builds on the previous examples in this tutorial.</span></span> <span data-ttu-id="829ab-108">Kod refaktoryzacji jest wywoływany w komentarzach w kodzie poniżej.</span><span class="sxs-lookup"><span data-stu-id="829ab-108">The refactored code is called out in comments in the code below.</span></span>  
  
 <span data-ttu-id="829ab-109">Aby uzyskać instrukcje dotyczące tworzenia dokumentu źródłowego dla tego przykładu, zobacz [Tworzenie źródłowego dokumentu Office Open XML (C#)](./creating-the-source-office-open-xml-document.md).</span><span class="sxs-lookup"><span data-stu-id="829ab-109">For instructions for creating the source document for this example, see [Creating the Source Office Open XML Document (C#)](./creating-the-source-office-open-xml-document.md).</span></span>  
  
 <span data-ttu-id="829ab-110">W tym przykładzie zastosowano klasy z zestawu 'Windowsbase.</span><span class="sxs-lookup"><span data-stu-id="829ab-110">This example uses classes from the WindowsBase assembly.</span></span> <span data-ttu-id="829ab-111">Używa typów w <xref:System.IO.Packaging?displayProperty=nameWithType> przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="829ab-111">It uses types in the <xref:System.IO.Packaging?displayProperty=nameWithType> namespace.</span></span>  
  
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
    // This is a new method that assembles the paragraph text.  
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
                    Uri styleUri = PackUriHelper.ResolvePartUri(documentUri,  
                      styleRelation.TargetUri);  
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
  
        foreach (var p in paraWithText)  
            Console.WriteLine("StyleName:{0} >{1}<", p.StyleName, p.Text);  
    }  
}  
```  
  
 <span data-ttu-id="829ab-112">Ten przykład generuje te same dane wyjściowe, co przed refaktoryzacją:</span><span class="sxs-lookup"><span data-stu-id="829ab-112">This example produces the same output as before the refactoring:</span></span>  
  
```  
StyleName:Heading1 >Parsing WordprocessingML with LINQ to XML<  
StyleName:Normal ><  
StyleName:Normal >The following example prints to the console.<  
StyleName:Normal ><  
StyleName:Code >using System;<  
StyleName:Code ><  
StyleName:Code >class Program {<  
StyleName:Code >    public static void (string[] args) {<  
StyleName:Code >        Console.WriteLine("Hello World");<  
StyleName:Code >    }<  
StyleName:Code >}<  
StyleName:Normal ><  
StyleName:Normal >This example produces the following output:<  
StyleName:Normal ><  
StyleName:Code >Hello World<  
```  
  
### <a name="next-steps"></a><span data-ttu-id="829ab-113">Następne kroki</span><span class="sxs-lookup"><span data-stu-id="829ab-113">Next Steps</span></span>  
 <span data-ttu-id="829ab-114">W następnym przykładzie pokazano, jak projektować XML w innym kształcie:</span><span class="sxs-lookup"><span data-stu-id="829ab-114">The next example shows how to project XML into a different shape:</span></span>  
  
- [<span data-ttu-id="829ab-115">Projekcja XML w innym kształcie (C#)</span><span class="sxs-lookup"><span data-stu-id="829ab-115">Projecting XML in a Different Shape (C#)</span></span>](./projecting-xml-in-a-different-shape.md)  
  
## <a name="see-also"></a><span data-ttu-id="829ab-116">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="829ab-116">See also</span></span>

- [<span data-ttu-id="829ab-117">Samouczek: Manipulowanie zawartością w dokumencie WordprocessingML (C#)</span><span class="sxs-lookup"><span data-stu-id="829ab-117">Tutorial: Manipulating Content in a WordprocessingML Document (C#)</span></span>](./shape-of-wordprocessingml-documents.md)
- [<span data-ttu-id="829ab-118">Refaktoryzacja przy użyciu metody rozszerzającej (C#)</span><span class="sxs-lookup"><span data-stu-id="829ab-118">Refactoring Using an Extension Method (C#)</span></span>](./refactoring-using-an-extension-method.md)
- [<span data-ttu-id="829ab-119">Refaktoryzacja do czystych funkcji (C#)</span><span class="sxs-lookup"><span data-stu-id="829ab-119">Refactoring Into Pure Functions (C#)</span></span>](./refactoring-into-pure-functions.md)
