---
title: Jak pobierać akapity z dokumentu XML otwierania pakietu Office (C#)
ms.date: 07/20/2015
ms.assetid: cc2687cf-d648-451e-88ac-3847c6c967c8
ms.openlocfilehash: 241bacc730f205bf501c1ab1ab47f6fda4c15d64
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "75347458"
---
# <a name="how-to-retrieve-paragraphs-from-an-office-open-xml-document-c"></a><span data-ttu-id="f47a7-102">Jak pobierać akapity z dokumentu XML otwierania pakietu Office (C#)</span><span class="sxs-lookup"><span data-stu-id="f47a7-102">How to retrieve paragraphs from an Office Open XML document (C#)</span></span>
<span data-ttu-id="f47a7-103">W tym temacie przedstawiono przykład, który otwiera dokument XML otwierania pakietu Office i pobiera kolekcję wszystkich akapitów w dokumencie.</span><span class="sxs-lookup"><span data-stu-id="f47a7-103">This topic presents an example that opens an Office Open XML document, and retrieves a collection of all of the paragraphs in the document.</span></span>  
  
 <span data-ttu-id="f47a7-104">Aby uzyskać więcej informacji na temat języka XML otwierania pakietu Office, zobacz [Otwieranie sdk XML](https://github.com/OfficeDev/Open-XML-SDK) i [www.ericwhite.com](http://ericwhite.com/).</span><span class="sxs-lookup"><span data-stu-id="f47a7-104">For more information on Office Open XML, see [Open XML SDK](https://github.com/OfficeDev/Open-XML-SDK) and [www.ericwhite.com](http://ericwhite.com/).</span></span>  
  
## <a name="example"></a><span data-ttu-id="f47a7-105">Przykład</span><span class="sxs-lookup"><span data-stu-id="f47a7-105">Example</span></span>  
 <span data-ttu-id="f47a7-106">W tym przykładzie otwiera pakiet Office Open XML, używa relacji w pakiecie Open XML, aby znaleźć dokument i części stylu.</span><span class="sxs-lookup"><span data-stu-id="f47a7-106">This example opens an Office Open XML package, uses the relationships within the Open XML package to find the document and the style parts.</span></span> <span data-ttu-id="f47a7-107">Następnie wysyła zapytanie do dokumentu, wyświetlając kolekcję <xref:System.Xml.Linq.XElement> typu anonimowego, która zawiera węzeł akapitu, nazwę stylu każdego akapitu i tekst każdego akapitu.</span><span class="sxs-lookup"><span data-stu-id="f47a7-107">It then queries the document, projecting a collection of an anonymous type that contains the paragraph <xref:System.Xml.Linq.XElement> node, the style name of each paragraph, and the text of each paragraph.</span></span>  
  
 <span data-ttu-id="f47a7-108">W przykładzie użyto `StringConcatenate`metody rozszerzenia o nazwie , która jest również podana w przykładzie.</span><span class="sxs-lookup"><span data-stu-id="f47a7-108">The example uses an extension method named `StringConcatenate`, which is also supplied in the example.</span></span>  
  
 <span data-ttu-id="f47a7-109">Aby uzyskać szczegółowy samouczek, który wyjaśnia, jak działa ten przykład, zobacz [Czyste transformacje funkcjonalne XML (C#).](./introduction-to-pure-functional-transformations.md)</span><span class="sxs-lookup"><span data-stu-id="f47a7-109">For a detailed tutorial that explains how this example works, see [Pure Functional Transformations of XML (C#)](./introduction-to-pure-functional-transformations.md).</span></span>  
  
 <span data-ttu-id="f47a7-110">W tym przykładzie użyto klas znalezionych w zestawie WindowsBase.</span><span class="sxs-lookup"><span data-stu-id="f47a7-110">This example uses classes found in the WindowsBase assembly.</span></span> <span data-ttu-id="f47a7-111">Używa typów w <xref:System.IO.Packaging?displayProperty=nameWithType> obszarze nazw.</span><span class="sxs-lookup"><span data-stu-id="f47a7-111">It uses types in the <xref:System.IO.Packaging?displayProperty=nameWithType> namespace.</span></span>  
  
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
              wdPackage  
              .GetRelationshipsByType(documentRelationshipType)  
              .FirstOrDefault();  
            if (docPackageRelationship != null)  
            {  
                Uri documentUri =  
                    PackUriHelper  
                    .ResolvePartUri(  
                       new Uri("/", UriKind.Relative),  
                             docPackageRelationship.TargetUri);  
                PackagePart documentPart =  
                    wdPackage.GetPart(documentUri);  
  
                //  Load the document XML in the part into an XDocument instance.  
                xDoc = XDocument.Load(XmlReader.Create(documentPart.GetStream()));  
  
                //  Find the styles part. There will only be one.  
                PackageRelationship styleRelation =  
                  documentPart.GetRelationshipsByType(stylesRelationshipType)  
                  .FirstOrDefault();  
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
  
        foreach (var p in paraWithText)  
            Console.WriteLine("StyleName:{0} >{1}<", p.StyleName, p.Text);  
    }  
}  
```  
  
 <span data-ttu-id="f47a7-112">Po uruchomieniu z próbkowania dokumentu Open XML opisane w [Tworzenie dokumentu XML open pakietu Source Office (C#),](./creating-the-source-office-open-xml-document.md)w tym przykładzie daje następujące dane wyjściowe:</span><span class="sxs-lookup"><span data-stu-id="f47a7-112">When run with the sample Open XML document described in [Creating the Source Office Open XML Document (C#)](./creating-the-source-office-open-xml-document.md), this example produces the following output:</span></span>  
  
```output  
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
