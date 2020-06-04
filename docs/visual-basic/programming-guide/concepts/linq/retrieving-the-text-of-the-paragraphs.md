---
title: Pobieranie tekstu akapitów
ms.date: 07/20/2015
ms.assetid: 095fa0d9-7b1b-4cbb-9c13-e2c9d8923d31
ms.openlocfilehash: 24167ade2d0326ef9382536f79f9e45eb22c89c5
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84413391"
---
# <a name="retrieving-the-text-of-the-paragraphs-visual-basic"></a><span data-ttu-id="78f1c-102">Pobieranie tekstu akapitów (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="78f1c-102">Retrieving the Text of the Paragraphs (Visual Basic)</span></span>
<span data-ttu-id="78f1c-103">Ten przykład kompiluje się w poprzednim przykładzie, [pobierając akapity i ich style (Visual Basic)](retrieving-the-paragraphs-and-their-styles.md).</span><span class="sxs-lookup"><span data-stu-id="78f1c-103">This example builds on the previous example, [Retrieving the Paragraphs and Their Styles (Visual Basic)](retrieving-the-paragraphs-and-their-styles.md).</span></span> <span data-ttu-id="78f1c-104">Ten nowy przykład pobiera tekst każdego akapitu w postaci ciągu.</span><span class="sxs-lookup"><span data-stu-id="78f1c-104">This new example retrieves the text of each paragraph as a string.</span></span>  
  
 <span data-ttu-id="78f1c-105">Aby pobrać tekst, ten przykład dodaje dodatkowe zapytanie, które iteruje przez kolekcję typów anonimowych i projektów nowej kolekcji typu anonimowego z dodaniem nowego elementu członkowskiego `Text` .</span><span class="sxs-lookup"><span data-stu-id="78f1c-105">To retrieve the text, this example adds an additional query that iterates through the collection of anonymous types and projects a new collection of an anonymous type with the addition of a new member, `Text`.</span></span> <span data-ttu-id="78f1c-106">Używa <xref:System.Linq.Enumerable.Aggregate%2A> standardowego operatora zapytania do łączenia wielu ciągów w jeden ciąg.</span><span class="sxs-lookup"><span data-stu-id="78f1c-106">It uses the <xref:System.Linq.Enumerable.Aggregate%2A> standard query operator to concatenate multiple strings into one string.</span></span>  
  
 <span data-ttu-id="78f1c-107">Ta technika (czyli najpierw projekcja do kolekcji typu anonimowego, a następnie użycie tej kolekcji w celu utworzenia nowej kolekcji typu anonimowego) jest powszechną i użyteczną idiom.</span><span class="sxs-lookup"><span data-stu-id="78f1c-107">This technique (that is, first projecting to a collection of an anonymous type, then using this collection to project to a new collection of an anonymous type) is a common and useful idiom.</span></span> <span data-ttu-id="78f1c-108">To zapytanie mogło zostać zapisaną bez projekcji pierwszego typu anonimowego.</span><span class="sxs-lookup"><span data-stu-id="78f1c-108">This query could have been written without projecting to the first anonymous type.</span></span> <span data-ttu-id="78f1c-109">Jednak ze względu na ocenę z opóźnieniem nie jest używana znacznie dodatkowa moc obliczeniowa.</span><span class="sxs-lookup"><span data-stu-id="78f1c-109">However, because of lazy evaluation, doing so does not use much additional processing power.</span></span> <span data-ttu-id="78f1c-110">Idiom tworzy więcej krótkich obiektów na stercie, ale nie zmniejsza to wydajności.</span><span class="sxs-lookup"><span data-stu-id="78f1c-110">The idiom creates more short lived objects on the heap, but this does not substantially degrade performance.</span></span>  
  
 <span data-ttu-id="78f1c-111">Oczywiście można napisać pojedyncze zapytanie, które zawiera funkcje umożliwiające pobranie akapitów, stylu każdego akapitu i tekstu każdego akapitu.</span><span class="sxs-lookup"><span data-stu-id="78f1c-111">Of course, it would be possible to write a single query that contains the functionality to retrieve the paragraphs, the style of each paragraph, and the text of each paragraph.</span></span> <span data-ttu-id="78f1c-112">Często jednak warto rozdzielić bardziej skomplikowane zapytanie na wiele zapytań, ponieważ otrzymany kod jest bardziej modularny i łatwiejszy w obsłudze.</span><span class="sxs-lookup"><span data-stu-id="78f1c-112">However, it often is useful to break up a more complicated query into multiple queries because the resulting code is more modular and easier to maintain.</span></span> <span data-ttu-id="78f1c-113">Ponadto, jeśli konieczne jest ponowne użycie części zapytania, łatwiej jest refaktoryzację, jeśli zapytania są zapisywane w ten sposób.</span><span class="sxs-lookup"><span data-stu-id="78f1c-113">Furthermore, if you need to reuse a portion of the query, it is easier to refactor if the queries are written in this manner.</span></span>  
  
 <span data-ttu-id="78f1c-114">Te zapytania, które są powiązane ze sobą, wykorzystują model przetwarzania, który jest szczegółowo rozpatrywany w [samouczku tematu: wykonywanie odroczone (Visual Basic)](tutorial-deferred-execution.md).</span><span class="sxs-lookup"><span data-stu-id="78f1c-114">These queries, which are chained together, use the processing model that is examined in detail in the topic [Tutorial: Deferred Execution (Visual Basic)](tutorial-deferred-execution.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="78f1c-115">Przykład</span><span class="sxs-lookup"><span data-stu-id="78f1c-115">Example</span></span>  
 <span data-ttu-id="78f1c-116">Ten przykład przetwarza dokument WordprocessingML, określając węzeł elementu, nazwę stylu i tekst każdego akapitu.</span><span class="sxs-lookup"><span data-stu-id="78f1c-116">This example processes a WordprocessingML document, determining the element node, the style name, and the text of each paragraph.</span></span> <span data-ttu-id="78f1c-117">Ten przykład kompiluje się zgodnie z poprzednimi przykładami w tym samouczku.</span><span class="sxs-lookup"><span data-stu-id="78f1c-117">This example builds on the previous examples in this tutorial.</span></span> <span data-ttu-id="78f1c-118">Nowe zapytanie jest wywoływane w komentarzach w poniższym kodzie.</span><span class="sxs-lookup"><span data-stu-id="78f1c-118">The new query is called out in comments in the code below.</span></span>  
  
 <span data-ttu-id="78f1c-119">Aby uzyskać instrukcje dotyczące tworzenia dokumentu źródłowego dla tego przykładu, zobacz [Tworzenie źródłowego dokumentu Office Open XML (Visual Basic)](creating-the-source-office-open-xml-document.md).</span><span class="sxs-lookup"><span data-stu-id="78f1c-119">For instructions for creating the source document for this example, see [Creating the Source Office Open XML Document (Visual Basic)](creating-the-source-office-open-xml-document.md).</span></span>  
  
 <span data-ttu-id="78f1c-120">W tym przykładzie zastosowano klasy z zestawu 'Windowsbase.</span><span class="sxs-lookup"><span data-stu-id="78f1c-120">This example uses classes from the WindowsBase assembly.</span></span> <span data-ttu-id="78f1c-121">Używa typów w <xref:System.IO.Packaging?displayProperty=nameWithType> przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="78f1c-121">It uses types in the <xref:System.IO.Packaging?displayProperty=nameWithType> namespace.</span></span>  
  
```vb  
Imports <xmlns:w="http://schemas.openxmlformats.org/wordprocessingml/2006/main">  
  
Module Module1  
    ' Following function is required because Visual Basic does not support short circuit evaluation  
    Private Function GetStyleOfParagraph(ByVal styleNode As XElement, _  
                                         ByVal defaultStyle As String) As String  
        If (styleNode Is Nothing) Then  
            Return defaultStyle  
        Else  
            Return styleNode.@w:val  
        End If  
    End Function  
  
    Sub Main()  
        Dim fileName = "SampleDoc.docx"  
  
        Dim documentRelationshipType = _  
          "http://schemas.openxmlformats.org/officeDocument/2006/relationships/officeDocument"  
        Dim stylesRelationshipType = _  
          "http://schemas.openxmlformats.org/officeDocument/2006/relationships/styles"  
        Dim wordmlNamespace = _  
          "http://schemas.openxmlformats.org/wordprocessingml/2006/main"  
  
        Dim xDoc As XDocument = Nothing  
        Dim styleDoc As XDocument = Nothing  
        Using wdPackage As Package = Package.Open(fileName, FileMode.Open, FileAccess.Read)  
            Dim docPackageRelationship As PackageRelationship = _  
              wdPackage.GetRelationshipsByType(documentRelationshipType).FirstOrDefault()  
            If (docPackageRelationship IsNot Nothing) Then  
                Dim documentUri As Uri = PackUriHelper.ResolvePartUri(New Uri("/", UriKind.Relative), _  
                  docPackageRelationship.TargetUri)  
                Dim documentPart As PackagePart = wdPackage.GetPart(documentUri)  
  
                '  Load the document XML in the part into an XDocument instance.  
                xDoc = XDocument.Load(XmlReader.Create(documentPart.GetStream()))  
  
                '  Find the styles part. There will only be one.  
                Dim styleRelation As PackageRelationship = _  
                  documentPart.GetRelationshipsByType(stylesRelationshipType).FirstOrDefault()  
                If (styleRelation IsNot Nothing) Then  
                    Dim styleUri As Uri = _  
                      PackUriHelper.ResolvePartUri(documentUri, styleRelation.TargetUri)  
                    Dim stylePart As PackagePart = wdPackage.GetPart(styleUri)  
  
                    '  Load the style XML in the part into an XDocument instance.  
                    styleDoc = XDocument.Load(XmlReader.Create(stylePart.GetStream()))  
                End If  
            End If  
        End Using  
  
        Dim defaultStyle As String = _  
            ( _  
                From style In styleDoc.Root.<w:style> _  
                Where style.@w:type = "paragraph" And _  
                      style.@w:default = "1" _  
                Select style _  
            ).First().@w:styleId  
  
        ' Find all paragraphs in the document.  
        Dim paragraphs = _  
            From para In xDoc.Root.<w:body>...<w:p> _  
        Let styleNode As XElement = para.<w:pPr>.<w:pStyle>.FirstOrDefault _  
        Select New With { _  
            .ParagraphNode = para, _  
            .StyleName = GetStyleOfParagraph(styleNode, defaultStyle) _  
        }  
  
        ' Following is the new query that retrieves the text of  
        ' each paragraph.  
        Dim paraWithText = _  
            From para In paragraphs _  
            Select New With { _  
                .ParagraphNode = para.ParagraphNode, _  
                .StyleName = para.StyleName, _  
                .Text = para.ParagraphNode.<w:r>.<w:t> _  
                    .Aggregate(New StringBuilder(), _  
                               Function(s As StringBuilder, i As String) s.Append(CStr(i)), _  
                               Function(s As StringBuilder) s.ToString) _  
            }  
  
        For Each p In paraWithText  
            Console.WriteLine("StyleName:{0} >{1}<", p.StyleName, p.Text)  
        Next  
  
    End Sub  
End Module  
```  
  
 <span data-ttu-id="78f1c-122">Ten przykład generuje następujące dane wyjściowe w przypadku zastosowania do dokumentu opisanego w temacie [Tworzenie źródłowego dokumentu Office Open XML (Visual Basic)](creating-the-source-office-open-xml-document.md).</span><span class="sxs-lookup"><span data-stu-id="78f1c-122">This example produces the following output when applied to the document described in [Creating the Source Office Open XML Document (Visual Basic)](creating-the-source-office-open-xml-document.md).</span></span>  
  
```console  
StyleName:Heading1 >Parsing WordprocessingML with LINQ to XML<  
StyleName:Normal ><  
StyleName:Normal >The following example prints to the console.<  
StyleName:Normal ><  
StyleName:Code >Imports System<  
StyleName:Code ><  
StyleName:Code >Class Program<  
StyleName:Code >    Public Shared  Sub Main(ByVal args() As String)<  
StyleName:Code >        Console.WriteLine("Hello World")<  
StyleName:Code >   End Sub<  
StyleName:Code >End Class<  
StyleName:Normal ><  
StyleName:Normal >This example produces the following output:<  
StyleName:Normal ><  
StyleName:Code >Hello World<  
```  
  
## <a name="next-steps"></a><span data-ttu-id="78f1c-123">Następne kroki</span><span class="sxs-lookup"><span data-stu-id="78f1c-123">Next Steps</span></span>  
 <span data-ttu-id="78f1c-124">W następnym przykładzie pokazano, jak używać metody rozszerzenia zamiast <xref:System.Linq.Enumerable.Aggregate%2A> , aby połączyć wiele ciągów w jeden ciąg.</span><span class="sxs-lookup"><span data-stu-id="78f1c-124">The next example shows how to use an extension method, instead of <xref:System.Linq.Enumerable.Aggregate%2A>, to concatenate multiple strings into a single string.</span></span>  
  
- [<span data-ttu-id="78f1c-125">Refaktoryzacja przy użyciu metody rozszerzającej (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="78f1c-125">Refactoring Using an Extension Method (Visual Basic)</span></span>](refactoring-using-an-extension-method.md)  
  
## <a name="see-also"></a><span data-ttu-id="78f1c-126">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="78f1c-126">See also</span></span>

- [<span data-ttu-id="78f1c-127">Samouczek: manipulowanie zawartością w dokumencie WordprocessingML (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="78f1c-127">Tutorial: Manipulating Content in a WordprocessingML Document (Visual Basic)</span></span>](tutorial-manipulating-content-in-a-wordprocessingml-document.md)
- [<span data-ttu-id="78f1c-128">Wykonywanie odroczone i Ocena z opóźnieniem w LINQ to XML (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="78f1c-128">Deferred Execution and Lazy Evaluation in LINQ to XML (Visual Basic)</span></span>](deferred-execution-and-lazy-evaluation-in-linq-to-xml.md)
