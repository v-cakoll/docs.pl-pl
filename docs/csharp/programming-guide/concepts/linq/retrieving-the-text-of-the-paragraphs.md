---
title: Pobieranie tekstu akapitów (C#)
ms.date: 07/20/2015
ms.assetid: 127d635e-e559-408f-90c8-2bb621ca50ac
ms.openlocfilehash: 88a7e82a7d27048ce3f901e6e9d50b8737797adb
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/19/2019
ms.locfileid: "69591076"
---
# <a name="retrieving-the-text-of-the-paragraphs-c"></a><span data-ttu-id="1e829-102">Pobieranie tekstu akapitów (C#)</span><span class="sxs-lookup"><span data-stu-id="1e829-102">Retrieving the Text of the Paragraphs (C#)</span></span>
<span data-ttu-id="1e829-103">Ten przykład kompiluje się w poprzednim przykładzie, [pobierając akapity i ich styleC#()](./retrieving-the-paragraphs-and-their-styles.md).</span><span class="sxs-lookup"><span data-stu-id="1e829-103">This example builds on the previous example, [Retrieving the Paragraphs and Their Styles (C#)](./retrieving-the-paragraphs-and-their-styles.md).</span></span> <span data-ttu-id="1e829-104">Ten nowy przykład pobiera tekst każdego akapitu w postaci ciągu.</span><span class="sxs-lookup"><span data-stu-id="1e829-104">This new example retrieves the text of each paragraph as a string.</span></span>  
  
 <span data-ttu-id="1e829-105">Aby pobrać tekst, ten przykład dodaje dodatkowe zapytanie, które iteruje przez kolekcję typów anonimowych i projektów nowej kolekcji typu anonimowego z dodaniem nowego elementu członkowskiego `Text`.</span><span class="sxs-lookup"><span data-stu-id="1e829-105">To retrieve the text, this example adds an additional query that iterates through the collection of anonymous types and projects a new collection of an anonymous type with the addition of a new member, `Text`.</span></span> <span data-ttu-id="1e829-106">Używa <xref:System.Linq.Enumerable.Aggregate%2A> standardowego operatora zapytania do łączenia wielu ciągów w jeden ciąg.</span><span class="sxs-lookup"><span data-stu-id="1e829-106">It uses the <xref:System.Linq.Enumerable.Aggregate%2A> standard query operator to concatenate multiple strings into one string.</span></span>  
  
 <span data-ttu-id="1e829-107">Ta technika (czyli najpierw projekcja do kolekcji typu anonimowego, a następnie użycie tej kolekcji w celu utworzenia nowej kolekcji typu anonimowego) jest powszechną i użyteczną idiom.</span><span class="sxs-lookup"><span data-stu-id="1e829-107">This technique (that is, first projecting to a collection of an anonymous type, then using this collection to project to a new collection of an anonymous type) is a common and useful idiom.</span></span> <span data-ttu-id="1e829-108">To zapytanie mogło zostać zapisaną bez projekcji pierwszego typu anonimowego.</span><span class="sxs-lookup"><span data-stu-id="1e829-108">This query could have been written without projecting to the first anonymous type.</span></span> <span data-ttu-id="1e829-109">Jednak ze względu na ocenę z opóźnieniem nie jest używana znacznie dodatkowa moc obliczeniowa.</span><span class="sxs-lookup"><span data-stu-id="1e829-109">However, because of lazy evaluation, doing so does not use much additional processing power.</span></span> <span data-ttu-id="1e829-110">Idiom tworzy więcej krótkich obiektów na stercie, ale nie zmniejsza to wydajności.</span><span class="sxs-lookup"><span data-stu-id="1e829-110">The idiom creates more short lived objects on the heap, but this does not substantially degrade performance.</span></span>  
  
 <span data-ttu-id="1e829-111">Oczywiście można napisać pojedyncze zapytanie, które zawiera funkcje umożliwiające pobranie akapitów, stylu każdego akapitu i tekstu każdego akapitu.</span><span class="sxs-lookup"><span data-stu-id="1e829-111">Of course, it would be possible to write a single query that contains the functionality to retrieve the paragraphs, the style of each paragraph, and the text of each paragraph.</span></span> <span data-ttu-id="1e829-112">Często jednak warto rozdzielić bardziej skomplikowane zapytanie na wiele zapytań, ponieważ otrzymany kod jest bardziej modularny i łatwiejszy w obsłudze.</span><span class="sxs-lookup"><span data-stu-id="1e829-112">However, it often is useful to break up a more complicated query into multiple queries because the resulting code is more modular and easier to maintain.</span></span> <span data-ttu-id="1e829-113">Ponadto, jeśli konieczne jest ponowne użycie części zapytania, łatwiej jest refaktoryzację, jeśli zapytania są zapisywane w ten sposób.</span><span class="sxs-lookup"><span data-stu-id="1e829-113">Furthermore, if you need to reuse a portion of the query, it is easier to refactor if the queries are written in this manner.</span></span>  
  
 <span data-ttu-id="1e829-114">Te zapytania, które są powiązane ze sobą, wykorzystują model przetwarzania, który jest szczegółowo rozpatrywany w samouczku tematu [: Łączenie łańcuchowe zapytań (C#)](./tutorial-chaining-queries-together.md).</span><span class="sxs-lookup"><span data-stu-id="1e829-114">These queries, which are chained together, use the processing model that is examined in detail in the topic [Tutorial: Chaining Queries Together (C#)](./tutorial-chaining-queries-together.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="1e829-115">Przykład</span><span class="sxs-lookup"><span data-stu-id="1e829-115">Example</span></span>  
 <span data-ttu-id="1e829-116">Ten przykład przetwarza dokument WordprocessingML, określając węzeł elementu, nazwę stylu i tekst każdego akapitu.</span><span class="sxs-lookup"><span data-stu-id="1e829-116">This example processes a WordprocessingML document, determining the element node, the style name, and the text of each paragraph.</span></span> <span data-ttu-id="1e829-117">Ten przykład kompiluje się zgodnie z poprzednimi przykładami w tym samouczku.</span><span class="sxs-lookup"><span data-stu-id="1e829-117">This example builds on the previous examples in this tutorial.</span></span> <span data-ttu-id="1e829-118">Nowe zapytanie jest wywoływane w komentarzach w poniższym kodzie.</span><span class="sxs-lookup"><span data-stu-id="1e829-118">The new query is called out in comments in the code below.</span></span>  
  
 <span data-ttu-id="1e829-119">Aby uzyskać instrukcje dotyczące tworzenia dokumentu źródłowego dla tego przykładu, zobacz [Tworzenie źródłowego dokumentu Office Open XML (C#)](./creating-the-source-office-open-xml-document.md).</span><span class="sxs-lookup"><span data-stu-id="1e829-119">For instructions for creating the source document for this example, see [Creating the Source Office Open XML Document (C#)](./creating-the-source-office-open-xml-document.md).</span></span>  
  
 <span data-ttu-id="1e829-120">W tym przykładzie zastosowano klasy z zestawu 'Windowsbase.</span><span class="sxs-lookup"><span data-stu-id="1e829-120">This example uses classes from the WindowsBase assembly.</span></span> <span data-ttu-id="1e829-121">Używa typów w <xref:System.IO.Packaging?displayProperty=nameWithType> przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="1e829-121">It uses types in the <xref:System.IO.Packaging?displayProperty=nameWithType> namespace.</span></span>  
  
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
  
 <span data-ttu-id="1e829-122">Ten przykład generuje następujące dane wyjściowe w przypadku zastosowania do dokumentu opisanego w temacie [Tworzenie źródłowego dokumentu Office Open XML (C#)](./creating-the-source-office-open-xml-document.md).</span><span class="sxs-lookup"><span data-stu-id="1e829-122">This example produces the following output when applied to the document described in [Creating the Source Office Open XML Document (C#)](./creating-the-source-office-open-xml-document.md).</span></span>  
  
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
  
## <a name="next-steps"></a><span data-ttu-id="1e829-123">Następne kroki</span><span class="sxs-lookup"><span data-stu-id="1e829-123">Next Steps</span></span>  
 <span data-ttu-id="1e829-124">W następnym przykładzie pokazano, jak używać metody rozszerzenia zamiast <xref:System.Linq.Enumerable.Aggregate%2A>, aby połączyć wiele ciągów w jeden ciąg.</span><span class="sxs-lookup"><span data-stu-id="1e829-124">The next example shows how to use an extension method, instead of <xref:System.Linq.Enumerable.Aggregate%2A>, to concatenate multiple strings into a single string.</span></span>  
  
- [<span data-ttu-id="1e829-125">Refaktoryzacja przy użyciu metody rozszerzającej (C#)</span><span class="sxs-lookup"><span data-stu-id="1e829-125">Refactoring Using an Extension Method (C#)</span></span>](./refactoring-using-an-extension-method.md)  
  
## <a name="see-also"></a><span data-ttu-id="1e829-126">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="1e829-126">See also</span></span>

- [<span data-ttu-id="1e829-127">Samouczek: Manipulowanie zawartością w dokumencie WordprocessingML (C#)</span><span class="sxs-lookup"><span data-stu-id="1e829-127">Tutorial: Manipulating Content in a WordprocessingML Document (C#)</span></span>](./tutorial-manipulating-content-in-a-wordprocessingml-document.md)
- [<span data-ttu-id="1e829-128">Wykonywanie odroczone i Ocena z opóźnieniem w LINQ to XMLC#()</span><span class="sxs-lookup"><span data-stu-id="1e829-128">Deferred Execution and Lazy Evaluation in LINQ to XML (C#)</span></span>](./deferred-execution-and-lazy-evaluation-in-linq-to-xml.md)
