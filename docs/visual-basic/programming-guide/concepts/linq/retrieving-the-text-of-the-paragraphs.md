---
title: "Pobieranie tekstu akapitów (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 095fa0d9-7b1b-4cbb-9c13-e2c9d8923d31
caps.latest.revision: "4"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 492fc0dffd007f0ccdb7454c62e86cac753ca06b
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="retrieving-the-text-of-the-paragraphs-visual-basic"></a><span data-ttu-id="b07cc-102">Pobieranie tekstu akapitów (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="b07cc-102">Retrieving the Text of the Paragraphs (Visual Basic)</span></span>
<span data-ttu-id="b07cc-103">W tym przykładzie opiera się na poprzednim przykładzie [pobierania akapitów i ich style (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/retrieving-the-paragraphs-and-their-styles.md).</span><span class="sxs-lookup"><span data-stu-id="b07cc-103">This example builds on the previous example, [Retrieving the Paragraphs and Their Styles (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/retrieving-the-paragraphs-and-their-styles.md).</span></span> <span data-ttu-id="b07cc-104">W tym przykładzie nowe pobiera tekst każdego akapitu jako ciąg.</span><span class="sxs-lookup"><span data-stu-id="b07cc-104">This new example retrieves the text of each paragraph as a string.</span></span>  
  
 <span data-ttu-id="b07cc-105">Aby pobrać tekst, w tym przykładzie dodaje dodatkowe zapytania, który iteruje po kolekcji typy anonimowe i projektów nową kolekcję z uwzględnieniem nowego elementu członkowskiego typu anonimowego `Text`.</span><span class="sxs-lookup"><span data-stu-id="b07cc-105">To retrieve the text, this example adds an additional query that iterates through the collection of anonymous types and projects a new collection of an anonymous type with the addition of a new member, `Text`.</span></span> <span data-ttu-id="b07cc-106">Używa <xref:System.Linq.Enumerable.Aggregate%2A> — operator zapytań standardowa do łączenie wielu ciągów w jeden ciąg.</span><span class="sxs-lookup"><span data-stu-id="b07cc-106">It uses the <xref:System.Linq.Enumerable.Aggregate%2A> standard query operator to concatenate multiple strings into one string.</span></span>  
  
 <span data-ttu-id="b07cc-107">Ta technika (to znaczy pierwszy projekcji do kolekcji typu anonimowego, a następnie przy użyciu tej kolekcji do projektu do nowej kolekcji typu anonimowego) jest idiom typowe i przydatne.</span><span class="sxs-lookup"><span data-stu-id="b07cc-107">This technique (that is, first projecting to a collection of an anonymous type, then using this collection to project to a new collection of an anonymous type) is a common and useful idiom.</span></span> <span data-ttu-id="b07cc-108">To zapytanie można zapisać bez projekcji do pierwszego typu anonimowego.</span><span class="sxs-lookup"><span data-stu-id="b07cc-108">This query could have been written without projecting to the first anonymous type.</span></span> <span data-ttu-id="b07cc-109">Jednak ze względu na obliczanie leniwe to tak nie jest użycie zaoszczędzonej energii dodatkowego przetwarzania.</span><span class="sxs-lookup"><span data-stu-id="b07cc-109">However, because of lazy evaluation, doing so does not use much additional processing power.</span></span> <span data-ttu-id="b07cc-110">Idiom tworzy więcej krótkich okresów ważności obiektów na stercie, ale to nie znacznie zmniejsza wydajność.</span><span class="sxs-lookup"><span data-stu-id="b07cc-110">The idiom creates more short lived objects on the heap, but this does not substantially degrade performance.</span></span>  
  
 <span data-ttu-id="b07cc-111">Oczywiście byłoby można zapisywać pojedynczego zapytania, który zawiera funkcje, które można pobrać akapitów, styl każdego akapitu i tekst każdego akapitu.</span><span class="sxs-lookup"><span data-stu-id="b07cc-111">Of course, it would be possible to write a single query that contains the functionality to retrieve the paragraphs, the style of each paragraph, and the text of each paragraph.</span></span> <span data-ttu-id="b07cc-112">Jednak często warto podzielić bardziej skomplikowane zapytanie do wielu zapytań, ponieważ wynikowy kod jest bardziej moduły i łatwiejsze w obsłudze.</span><span class="sxs-lookup"><span data-stu-id="b07cc-112">However, it often is useful to break up a more complicated query into multiple queries because the resulting code is more modular and easier to maintain.</span></span> <span data-ttu-id="b07cc-113">Ponadto jeśli istnieje potrzeba ponownego użycia część zapytania, łatwiej jest zrefaktoryzuj Jeśli zapytania są zapisywane w ten sposób.</span><span class="sxs-lookup"><span data-stu-id="b07cc-113">Furthermore, if you need to reuse a portion of the query, it is easier to refactor if the queries are written in this manner.</span></span>  
  
 <span data-ttu-id="b07cc-114">Te zapytania, które są połączone, użyj przetwarzania modelu, która się zbadana szczegółowo w temacie [samouczek: wykonanie odroczone (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/tutorial-deferred-execution.md).</span><span class="sxs-lookup"><span data-stu-id="b07cc-114">These queries, which are chained together, use the processing model that is examined in detail in the topic [Tutorial: Deferred Execution (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/tutorial-deferred-execution.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="b07cc-115">Przykład</span><span class="sxs-lookup"><span data-stu-id="b07cc-115">Example</span></span>  
 <span data-ttu-id="b07cc-116">W tym przykładzie przetwarza dokument schemat WordprocessingML określania węzeł elementu, nazwę stylu i tekst każdego akapitu.</span><span class="sxs-lookup"><span data-stu-id="b07cc-116">This example processes a WordprocessingML document, determining the element node, the style name, and the text of each paragraph.</span></span> <span data-ttu-id="b07cc-117">W tym przykładzie kompilacje w poprzednich przykładach, w tym samouczku.</span><span class="sxs-lookup"><span data-stu-id="b07cc-117">This example builds on the previous examples in this tutorial.</span></span> <span data-ttu-id="b07cc-118">Nowe zapytanie jest podana w komentarzach w poniższym kodzie.</span><span class="sxs-lookup"><span data-stu-id="b07cc-118">The new query is called out in comments in the code below.</span></span>  
  
 <span data-ttu-id="b07cc-119">Aby uzyskać instrukcje dotyczące tworzenia dokumentu źródłowego dla tego przykładu, zobacz [tworzenie źródło dokumentu pakietu Office Open XML (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/creating-the-source-office-open-xml-document.md).</span><span class="sxs-lookup"><span data-stu-id="b07cc-119">For instructions for creating the source document for this example, see [Creating the Source Office Open XML Document (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/creating-the-source-office-open-xml-document.md).</span></span>  
  
 <span data-ttu-id="b07cc-120">W tym przykładzie użyto klasy z zestawu WindowsBase.</span><span class="sxs-lookup"><span data-stu-id="b07cc-120">This example uses classes from the WindowsBase assembly.</span></span> <span data-ttu-id="b07cc-121">Używa typów w <xref:System.IO.Packaging?displayProperty=nameWithType> przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="b07cc-121">It uses types in the <xref:System.IO.Packaging?displayProperty=nameWithType> namespace.</span></span>  
  
```vb  
Imports <xmlns:w="http://schemas.openxmlformats.org/wordprocessingml/2006/main">  
  
Module Module1  
    ' Following function is required because VB does not support short circuit evaluation  
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
  
 <span data-ttu-id="b07cc-122">Ten przykład generuje dane wyjściowe w przypadku zastosowanego do dokumentu opisano w następujących [tworzenie źródło dokumentu pakietu Office Open XML (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/creating-the-source-office-open-xml-document.md).</span><span class="sxs-lookup"><span data-stu-id="b07cc-122">This example produces the following output when applied to the document described in [Creating the Source Office Open XML Document (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/creating-the-source-office-open-xml-document.md).</span></span>  
  
```  
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
  
## <a name="next-steps"></a><span data-ttu-id="b07cc-123">Następne kroki</span><span class="sxs-lookup"><span data-stu-id="b07cc-123">Next Steps</span></span>  
 <span data-ttu-id="b07cc-124">W kolejnym przykładzie pokazano sposób użycia metody rozszerzenia, zamiast <xref:System.Linq.Enumerable.Aggregate%2A>, aby łączenie wielu ciągów w jednym ciągu.</span><span class="sxs-lookup"><span data-stu-id="b07cc-124">The next example shows how to use an extension method, instead of <xref:System.Linq.Enumerable.Aggregate%2A>, to concatenate multiple strings into a single string.</span></span>  
  
-   [<span data-ttu-id="b07cc-125">Refaktoryzacja za pomocą metody rozszerzenia (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="b07cc-125">Refactoring Using an Extension Method (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/refactoring-using-an-extension-method.md)  
  
## <a name="see-also"></a><span data-ttu-id="b07cc-126">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="b07cc-126">See Also</span></span>  
 [<span data-ttu-id="b07cc-127">Samouczek: Manipulowanie zawartości w dokumencie schemat WordprocessingML (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="b07cc-127">Tutorial: Manipulating Content in a WordprocessingML Document (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/tutorial-manipulating-content-in-a-wordprocessingml-document.md)  
 [<span data-ttu-id="b07cc-128">Wykonanie odroczone i obliczanie leniwe w składniku LINQ to XML (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="b07cc-128">Deferred Execution and Lazy Evaluation in LINQ to XML (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/deferred-execution-and-lazy-evaluation-in-linq-to-xml.md)
