---
title: Pobieranie tekstu akapitów (C#)
ms.date: 07/20/2015
ms.assetid: 127d635e-e559-408f-90c8-2bb621ca50ac
ms.openlocfilehash: 7c47420045def3fe973169e01143646c0f60a8eb
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "79168248"
---
# <a name="retrieving-the-text-of-the-paragraphs-c"></a><span data-ttu-id="4b37a-102">Pobieranie tekstu akapitów (C#)</span><span class="sxs-lookup"><span data-stu-id="4b37a-102">Retrieving the Text of the Paragraphs (C#)</span></span>
<span data-ttu-id="4b37a-103">W tym przykładzie opiera się na poprzednim [przykładzie, Pobieranie akapity i ich style (C#)](./retrieving-the-paragraphs-and-their-styles.md).</span><span class="sxs-lookup"><span data-stu-id="4b37a-103">This example builds on the previous example, [Retrieving the Paragraphs and Their Styles (C#)](./retrieving-the-paragraphs-and-their-styles.md).</span></span> <span data-ttu-id="4b37a-104">W tym nowym przykładzie pobiera tekst każdego akapitu jako ciąg.</span><span class="sxs-lookup"><span data-stu-id="4b37a-104">This new example retrieves the text of each paragraph as a string.</span></span>  
  
 <span data-ttu-id="4b37a-105">Aby pobrać tekst, w tym przykładzie dodaje dodatkowe zapytanie, które iteruje poprzez kolekcję typów anonimowych `Text`i projektów nowej kolekcji typu anonimowego z dodatkiem nowego elementu członkowskiego.</span><span class="sxs-lookup"><span data-stu-id="4b37a-105">To retrieve the text, this example adds an additional query that iterates through the collection of anonymous types and projects a new collection of an anonymous type with the addition of a new member, `Text`.</span></span> <span data-ttu-id="4b37a-106">Używa standardowego <xref:System.Linq.Enumerable.Aggregate%2A> operatora kwerendy do łączenia wielu ciągów w jeden ciąg.</span><span class="sxs-lookup"><span data-stu-id="4b37a-106">It uses the <xref:System.Linq.Enumerable.Aggregate%2A> standard query operator to concatenate multiple strings into one string.</span></span>  
  
 <span data-ttu-id="4b37a-107">Ta technika (czyli najpierw rzutowanie do kolekcji typu anonimowego, a następnie za pomocą tej kolekcji do projektu do nowej kolekcji typu anonimowego) jest typowyi i przydatne idiom.</span><span class="sxs-lookup"><span data-stu-id="4b37a-107">This technique (that is, first projecting to a collection of an anonymous type, then using this collection to project to a new collection of an anonymous type) is a common and useful idiom.</span></span> <span data-ttu-id="4b37a-108">Ta kwerenda mogła zostać napisana bez rzutowania na pierwszy typ anonimowy.</span><span class="sxs-lookup"><span data-stu-id="4b37a-108">This query could have been written without projecting to the first anonymous type.</span></span> <span data-ttu-id="4b37a-109">Jednak z powodu oceny z opóźnieniem, w ten sposób nie zużywa wiele dodatkowej mocy obliczeniowej.</span><span class="sxs-lookup"><span data-stu-id="4b37a-109">However, because of lazy evaluation, doing so does not use much additional processing power.</span></span> <span data-ttu-id="4b37a-110">Idiom tworzy bardziej krótkotrwałe obiekty na stercie, ale nie obniża to znacznie wydajności.</span><span class="sxs-lookup"><span data-stu-id="4b37a-110">The idiom creates more short lived objects on the heap, but this does not substantially degrade performance.</span></span>  
  
 <span data-ttu-id="4b37a-111">Oczywiście możliwe byłoby napisanie pojedynczej kwerendy zawierającej funkcje pobierania akapitów, styl każdego akapitu i tekst każdego akapitu.</span><span class="sxs-lookup"><span data-stu-id="4b37a-111">Of course, it would be possible to write a single query that contains the functionality to retrieve the paragraphs, the style of each paragraph, and the text of each paragraph.</span></span> <span data-ttu-id="4b37a-112">Jednak często jest przydatne do podziału bardziej skomplikowane zapytanie na wiele zapytań, ponieważ wynikowy kod jest bardziej modułowe i łatwiejsze w utrzymaniu.</span><span class="sxs-lookup"><span data-stu-id="4b37a-112">However, it often is useful to break up a more complicated query into multiple queries because the resulting code is more modular and easier to maintain.</span></span> <span data-ttu-id="4b37a-113">Ponadto jeśli trzeba ponownie użyć części kwerendy, łatwiej jest refaktoryzacji, jeśli zapytania są zapisywane w ten sposób.</span><span class="sxs-lookup"><span data-stu-id="4b37a-113">Furthermore, if you need to reuse a portion of the query, it is easier to refactor if the queries are written in this manner.</span></span>  
  
 <span data-ttu-id="4b37a-114">Te zapytania, które są ze sobą połączone łańcuchem, używają modelu przetwarzania, który jest szczegółowo sprawdzany w temacie [Samouczek: Łączenie zapytań razem (C#)](deferred-execution-and-lazy-evaluation-in-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="4b37a-114">These queries, which are chained together, use the processing model that is examined in detail in the topic [Tutorial: Chaining Queries Together (C#)](deferred-execution-and-lazy-evaluation-in-linq-to-xml.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="4b37a-115">Przykład</span><span class="sxs-lookup"><span data-stu-id="4b37a-115">Example</span></span>  
 <span data-ttu-id="4b37a-116">W tym przykładzie przetwarza dokument WordprocessingML, określając węzeł elementu, nazwę stylu i tekst każdego akapitu.</span><span class="sxs-lookup"><span data-stu-id="4b37a-116">This example processes a WordprocessingML document, determining the element node, the style name, and the text of each paragraph.</span></span> <span data-ttu-id="4b37a-117">W tym przykładzie opiera się na poprzednich przykładach w tym samouczku.</span><span class="sxs-lookup"><span data-stu-id="4b37a-117">This example builds on the previous examples in this tutorial.</span></span> <span data-ttu-id="4b37a-118">Nowe zapytanie jest wywoływane w komentarzach w poniższym kodzie.</span><span class="sxs-lookup"><span data-stu-id="4b37a-118">The new query is called out in comments in the code below.</span></span>  
  
 <span data-ttu-id="4b37a-119">Aby uzyskać instrukcje dotyczące tworzenia dokumentu źródłowego dla tego [przykładu, zobacz Tworzenie dokumentu XML open pakietu Source Office (C#).](./creating-the-source-office-open-xml-document.md)</span><span class="sxs-lookup"><span data-stu-id="4b37a-119">For instructions for creating the source document for this example, see [Creating the Source Office Open XML Document (C#)](./creating-the-source-office-open-xml-document.md).</span></span>  
  
 <span data-ttu-id="4b37a-120">W tym przykładzie użyto klas z zestawu WindowsBase.</span><span class="sxs-lookup"><span data-stu-id="4b37a-120">This example uses classes from the WindowsBase assembly.</span></span> <span data-ttu-id="4b37a-121">Używa typów w <xref:System.IO.Packaging?displayProperty=nameWithType> obszarze nazw.</span><span class="sxs-lookup"><span data-stu-id="4b37a-121">It uses types in the <xref:System.IO.Packaging?displayProperty=nameWithType> namespace.</span></span>  
  
```csharp  
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
        where (string)style.Attribute(w + "type") == "paragraph"&&  
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
  
// Following is the new query that retrieves the text of  
// each paragraph.  
var paraWithText =  
    from para in paragraphs  
    select new  
    {  
        ParagraphNode = para.ParagraphNode,  
        StyleName = para.StyleName,  
        Text = para  
               .ParagraphNode  
               .Elements(w + "r")  
               .Elements(w + "t")  
               .Aggregate(  
                   new StringBuilder(),  
                   (s, i) => s.Append((string)i),  
                   s => s.ToString()  
               )  
    };  
  
foreach (var p in paraWithText)  
    Console.WriteLine("StyleName:{0} >{1}<", p.StyleName, p.Text);  
```  
  
 <span data-ttu-id="4b37a-122">W tym przykładzie po zastosowaniu do dokumentu opisanego w [dokumencie Tworzenie dokumentu XML pakietu Source Office Open (C#).](./creating-the-source-office-open-xml-document.md)</span><span class="sxs-lookup"><span data-stu-id="4b37a-122">This example produces the following output when applied to the document described in [Creating the Source Office Open XML Document (C#)](./creating-the-source-office-open-xml-document.md).</span></span>  
  
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
  
## <a name="next-steps"></a><span data-ttu-id="4b37a-123">Następne kroki</span><span class="sxs-lookup"><span data-stu-id="4b37a-123">Next Steps</span></span>  
 <span data-ttu-id="4b37a-124">W następnym przykładzie pokazano, jak używać <xref:System.Linq.Enumerable.Aggregate%2A>metody rozszerzenia, zamiast , połączyć wiele ciągów w jeden ciąg.</span><span class="sxs-lookup"><span data-stu-id="4b37a-124">The next example shows how to use an extension method, instead of <xref:System.Linq.Enumerable.Aggregate%2A>, to concatenate multiple strings into a single string.</span></span>  
  
- [<span data-ttu-id="4b37a-125">Refaktoryzacja przy użyciu metody rozszerzenia (C#)</span><span class="sxs-lookup"><span data-stu-id="4b37a-125">Refactoring Using an Extension Method (C#)</span></span>](./refactoring-using-an-extension-method.md)  
  
## <a name="see-also"></a><span data-ttu-id="4b37a-126">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="4b37a-126">See also</span></span>

- [<span data-ttu-id="4b37a-127">Samouczek: manipulowanie zawartością w dokumencie WordprocessingML (C#)</span><span class="sxs-lookup"><span data-stu-id="4b37a-127">Tutorial: Manipulating Content in a WordprocessingML Document (C#)</span></span>](shape-of-wordprocessingml-documents.md)
- [<span data-ttu-id="4b37a-128">Odroczone wykonanie i ocena z opóźnieniem w LINQ do XML (C#)</span><span class="sxs-lookup"><span data-stu-id="4b37a-128">Deferred Execution and Lazy Evaluation in LINQ to XML (C#)</span></span>](./deferred-execution-and-lazy-evaluation-in-linq-to-xml.md)
