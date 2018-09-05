---
title: Refaktoryzacja przy użyciu czystej funkcji (C#)
ms.date: 07/20/2015
ms.assetid: a3416a45-9e12-4e4a-9747-897f06eef510
ms.openlocfilehash: 28f31b144cbdbd85febfc57acccb9bd7a158d702
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/04/2018
ms.locfileid: "43555212"
---
# <a name="refactoring-using-a-pure-function-c"></a><span data-ttu-id="4a515-102">Refaktoryzacja przy użyciu czystej funkcji (C#)</span><span class="sxs-lookup"><span data-stu-id="4a515-102">Refactoring Using a Pure Function (C#)</span></span>
<span data-ttu-id="4a515-103">Poniższy przykład refactors poprzedni przykład [Refaktoryzacja przy użyciu metody rozszerzenia (C#)](../../../../csharp/programming-guide/concepts/linq/refactoring-using-an-extension-method.md), aby używać czystej funkcji w tym przykładzie kod, aby znaleźć tekst akapitu jest przenoszony do czystych statycznej metody `ParagraphText`.</span><span class="sxs-lookup"><span data-stu-id="4a515-103">The following example refactors the previous example, [Refactoring Using an Extension Method (C#)](../../../../csharp/programming-guide/concepts/linq/refactoring-using-an-extension-method.md), to use a pure function In this example, the code to find the text of a paragraph is moved to the pure static method `ParagraphText`.</span></span>  
  
## <a name="example"></a><span data-ttu-id="4a515-104">Przykład</span><span class="sxs-lookup"><span data-stu-id="4a515-104">Example</span></span>  
 <span data-ttu-id="4a515-105">W tym przykładzie przetwarza dokumentu WordprocessingML pobieranie węzłów akapit w dokumencie WordprocessingML.</span><span class="sxs-lookup"><span data-stu-id="4a515-105">This example processes a WordprocessingML document, retrieving the paragraph nodes from a WordprocessingML document.</span></span> <span data-ttu-id="4a515-106">Określa on styl każdego akapitu.</span><span class="sxs-lookup"><span data-stu-id="4a515-106">It also identifies the style of each paragraph.</span></span> <span data-ttu-id="4a515-107">W tym przykładzie opiera się na poprzednich przykładach w tym samouczku.</span><span class="sxs-lookup"><span data-stu-id="4a515-107">This example builds on the previous examples in this tutorial.</span></span> <span data-ttu-id="4a515-108">Refaktoryzować kod jest wywoływane w komentarzach, w poniższym kodzie.</span><span class="sxs-lookup"><span data-stu-id="4a515-108">The refactored code is called out in comments in the code below.</span></span>  
  
 <span data-ttu-id="4a515-109">Aby uzyskać instrukcje dotyczące tworzenia dokumentu źródłowego, w tym przykładzie, zobacz [tworzenie źródłowego dokumentu pakietu Office Open XML (C#)](../../../../csharp/programming-guide/concepts/linq/creating-the-source-office-open-xml-document.md).</span><span class="sxs-lookup"><span data-stu-id="4a515-109">For instructions for creating the source document for this example, see [Creating the Source Office Open XML Document (C#)](../../../../csharp/programming-guide/concepts/linq/creating-the-source-office-open-xml-document.md).</span></span>  
  
 <span data-ttu-id="4a515-110">W tym przykładzie użyto klasy z zestawu WindowsBase.</span><span class="sxs-lookup"><span data-stu-id="4a515-110">This example uses classes from the WindowsBase assembly.</span></span> <span data-ttu-id="4a515-111">Używa typów w <xref:System.IO.Packaging?displayProperty=nameWithType> przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="4a515-111">It uses types in the <xref:System.IO.Packaging?displayProperty=nameWithType> namespace.</span></span>  
  
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
  
 <span data-ttu-id="4a515-112">Ten przykład generuje takie same dane wyjściowe sprzed refaktoryzacji:</span><span class="sxs-lookup"><span data-stu-id="4a515-112">This example produces the same output as before the refactoring:</span></span>  
  
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
  
### <a name="next-steps"></a><span data-ttu-id="4a515-113">Następne kroki</span><span class="sxs-lookup"><span data-stu-id="4a515-113">Next Steps</span></span>  
 <span data-ttu-id="4a515-114">Następny przykład pokazuje, jak projekt XML do innego kształtu:</span><span class="sxs-lookup"><span data-stu-id="4a515-114">The next example shows how to project XML into a different shape:</span></span>  
  
-   [<span data-ttu-id="4a515-115">Projektowanie kodu XML w innym kształcie (C#)</span><span class="sxs-lookup"><span data-stu-id="4a515-115">Projecting XML in a Different Shape (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/projecting-xml-in-a-different-shape.md)  
  
## <a name="see-also"></a><span data-ttu-id="4a515-116">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="4a515-116">See Also</span></span>

- [<span data-ttu-id="4a515-117">Samouczek: Manipulowanie zawartością w dokumencie WordprocessingML (C#)</span><span class="sxs-lookup"><span data-stu-id="4a515-117">Tutorial: Manipulating Content in a WordprocessingML Document (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/tutorial-manipulating-content-in-a-wordprocessingml-document.md)  
- [<span data-ttu-id="4a515-118">Refaktoryzacja przy użyciu metody rozszerzenia (C#)</span><span class="sxs-lookup"><span data-stu-id="4a515-118">Refactoring Using an Extension Method (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/refactoring-using-an-extension-method.md)  
- [<span data-ttu-id="4a515-119">Refaktoryzacja do czystych funkcji (C#)</span><span class="sxs-lookup"><span data-stu-id="4a515-119">Refactoring Into Pure Functions (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/refactoring-into-pure-functions.md)
