---
title: Refaktoryzacja przy użyciu metody rozszerzenia (Visual Basic)
ms.date: 07/20/2015
ms.assetid: d87ae99a-cfa9-4a31-a5e4-9d6437be6810
ms.openlocfilehash: 429f1fb106eca6b6a9ce0f64ea81c260c10a088a
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54671580"
---
# <a name="refactoring-using-an-extension-method-visual-basic"></a><span data-ttu-id="3fefc-102">Refaktoryzacja przy użyciu metody rozszerzenia (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="3fefc-102">Refactoring Using an Extension Method (Visual Basic)</span></span>
<span data-ttu-id="3fefc-103">W tym przykładzie opiera się na poprzednim przykładzie [pobieranie tekstu akapitów (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/retrieving-the-text-of-the-paragraphs.md), przez refaktoryzacji łączenia ciągów przy użyciu czystej funkcji, który jest implementowany jako metodę rozszerzenia.</span><span class="sxs-lookup"><span data-stu-id="3fefc-103">This example builds on the previous example, [Retrieving the Text of the Paragraphs (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/retrieving-the-text-of-the-paragraphs.md), by refactoring the concatenation of strings using a pure function that is implemented as an extension method.</span></span>  
  
 <span data-ttu-id="3fefc-104">W poprzednim przykładzie użyto <xref:System.Linq.Enumerable.Aggregate%2A> standardowego operatora zapytania na łączenie wielu ciągów w jeden ciąg.</span><span class="sxs-lookup"><span data-stu-id="3fefc-104">The previous example used the <xref:System.Linq.Enumerable.Aggregate%2A> standard query operator to concatenate multiple strings into one string.</span></span> <span data-ttu-id="3fefc-105">Jednak jest bardziej wygodne do zapisania metodę rozszerzenia, aby to zrobić, ponieważ wynikowy zapytania mniejsze i bardziej proste.</span><span class="sxs-lookup"><span data-stu-id="3fefc-105">However, it is more convenient to write an extension method to do this, because the resulting query smaller and more simple.</span></span>  
  
## <a name="example"></a><span data-ttu-id="3fefc-106">Przykład</span><span class="sxs-lookup"><span data-stu-id="3fefc-106">Example</span></span>  
 <span data-ttu-id="3fefc-107">W tym przykładzie przetwarza dokumentu WordprocessingML pobieranie akapitów, styl każdego akapitu, a tekst każdego akapitu.</span><span class="sxs-lookup"><span data-stu-id="3fefc-107">This example processes a WordprocessingML document, retrieving the paragraphs, the style of each paragraph, and the text of each paragraph.</span></span> <span data-ttu-id="3fefc-108">W tym przykładzie opiera się na poprzednich przykładach w tym samouczku.</span><span class="sxs-lookup"><span data-stu-id="3fefc-108">This example builds on the previous examples in this tutorial.</span></span>  
  
 <span data-ttu-id="3fefc-109">Przykład zawiera wiele przeciążeń `StringConcatenate` metody.</span><span class="sxs-lookup"><span data-stu-id="3fefc-109">The example contains multiple overloads of the `StringConcatenate` method.</span></span>  
  
 <span data-ttu-id="3fefc-110">Można znaleźć instrukcje dotyczące tworzenia dokumentu źródłowego, w tym przykładzie w [tworzenie źródłowego dokumentu pakietu Office Open XML (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/creating-the-source-office-open-xml-document.md).</span><span class="sxs-lookup"><span data-stu-id="3fefc-110">You can find instructions for creating the source document for this example in [Creating the Source Office Open XML Document (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/creating-the-source-office-open-xml-document.md).</span></span>  
  
 <span data-ttu-id="3fefc-111">W tym przykładzie użyto klasy z zestawu WindowsBase.</span><span class="sxs-lookup"><span data-stu-id="3fefc-111">This example uses classes from the WindowsBase assembly.</span></span> <span data-ttu-id="3fefc-112">Używa typów w <xref:System.IO.Packaging?displayProperty=nameWithType> przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="3fefc-112">It uses types in the <xref:System.IO.Packaging?displayProperty=nameWithType> namespace.</span></span>  
  
```vb  
<System.Runtime.CompilerServices.Extension()> _  
Public Function StringConcatenate(ByVal source As IEnumerable(Of String)) As String  
    Dim sb As StringBuilder = New StringBuilder()  
    For Each s As String In source  
        sb.Append(s)  
    Next  
    Return sb.ToString()  
End Function  
  
<System.Runtime.CompilerServices.Extension()> _  
Public Function StringConcatenate(Of T)(ByVal source As IEnumerable(Of T), _  
ByVal func As Func(Of T, String)) As String  
    Dim sb As StringBuilder = New StringBuilder()  
    For Each item As T In source  
        sb.Append(func(item))  
    Next  
    Return sb.ToString()  
End Function  
  
<System.Runtime.CompilerServices.Extension()> _  
Public Function StringConcatenate(Of T)(ByVal source As IEnumerable(Of T), _  
ByVal separator As String) As String  
    Dim sb As StringBuilder = New StringBuilder()  
    For Each s As T In source  
        sb.Append(s).Append(separator)  
    Next  
    Return sb.ToString()  
End Function  
  
<System.Runtime.CompilerServices.Extension()> _  
Public Function StringConcatenate(Of T)(ByVal source As IEnumerable(Of T), _  
ByVal func As Func(Of T, String), ByVal separator As String) As String  
    Dim sb As StringBuilder = New StringBuilder()  
    For Each item As T In source  
        sb.Append(func(item)).Append(separator)  
    Next  
    Return sb.ToString()  
End Function  
```  
  
## <a name="example"></a><span data-ttu-id="3fefc-113">Przykład</span><span class="sxs-lookup"><span data-stu-id="3fefc-113">Example</span></span>  
 <span data-ttu-id="3fefc-114">Istnieją cztery przeciążenia `StringConcatenate` metody.</span><span class="sxs-lookup"><span data-stu-id="3fefc-114">There are four overloads of the `StringConcatenate` method.</span></span> <span data-ttu-id="3fefc-115">Kilkoma przeciążeniami po prostu kolekcji ciągów i zwraca jeden ciąg.</span><span class="sxs-lookup"><span data-stu-id="3fefc-115">One overload simply takes a collection of strings and returns a single string.</span></span> <span data-ttu-id="3fefc-116">Innego przeciążenia metody może potrwać kolekcji dowolnego typu i delegata tego projektów z pojedynczego kolekcji na ciąg.</span><span class="sxs-lookup"><span data-stu-id="3fefc-116">Another overload can take a collection of any type, and a delegate that projects from a singleton of the collection to a string.</span></span> <span data-ttu-id="3fefc-117">Istnieją dwa więcej przeciążenia metody, które pozwalają na określenie ciągu separatora.</span><span class="sxs-lookup"><span data-stu-id="3fefc-117">There are two more overloads that allow you to specify a separator string.</span></span>  
  
 <span data-ttu-id="3fefc-118">W poniższym kodzie użyto wszystkie cztery przeciążenia.</span><span class="sxs-lookup"><span data-stu-id="3fefc-118">The following code uses all four overloads.</span></span>  
  
```vb  
Dim numbers As String() = {"one", "two", "three"}  
  
Console.WriteLine("{0}", numbers.StringConcatenate())  
Console.WriteLine("{0}", numbers.StringConcatenate(":"))  
  
Dim intNumbers As Integer() = {1, 2, 3}  
Console.WriteLine("{0}", intNumbers.StringConcatenate(Function(i) i.ToString()))  
Console.WriteLine("{0}", intNumbers.StringConcatenate(Function(i) i.ToString(), ":"))  
```  
  
 <span data-ttu-id="3fefc-119">Ten przykład generuje następujące wyniki:</span><span class="sxs-lookup"><span data-stu-id="3fefc-119">This example produces the following output:</span></span>  
  
```  
onetwothree  
one:two:three:  
123  
1:2:3:  
```  
  
## <a name="example"></a><span data-ttu-id="3fefc-120">Przykład</span><span class="sxs-lookup"><span data-stu-id="3fefc-120">Example</span></span>  
 <span data-ttu-id="3fefc-121">Teraz można zmodyfikować przykładu, aby korzystać z zalet nowej metody rozszerzenia:</span><span class="sxs-lookup"><span data-stu-id="3fefc-121">Now, the example can be modified to take advantage of the new extension method:</span></span>  
  
```vb  
Imports <xmlns:w="http://schemas.openxmlformats.org/wordprocessingml/2006/main">  
  
Module Module1  
    <System.Runtime.CompilerServices.Extension()> _  
    Public Function StringConcatenate(ByVal source As IEnumerable(Of String)) As String  
        Dim sb As StringBuilder = New StringBuilder()  
        For Each s As String In source  
            sb.Append(s)  
        Next  
        Return sb.ToString()  
    End Function  
  
    <System.Runtime.CompilerServices.Extension()> _  
    Public Function StringConcatenate(Of T)(ByVal source As IEnumerable(Of T), _  
    ByVal func As Func(Of T, String)) As String  
        Dim sb As StringBuilder = New StringBuilder()  
        For Each item As T In source  
            sb.Append(func(item))  
        Next  
        Return sb.ToString()  
    End Function  
  
    <System.Runtime.CompilerServices.Extension()> _  
    Public Function StringConcatenate(Of T)(ByVal source As IEnumerable(Of T), _  
    ByVal separator As String) As String  
        Dim sb As StringBuilder = New StringBuilder()  
        For Each s As T In source  
            sb.Append(s).Append(separator)  
        Next  
        Return sb.ToString()  
    End Function  
  
    <System.Runtime.CompilerServices.Extension()> _  
    Public Function StringConcatenate(Of T)(ByVal source As IEnumerable(Of T), _  
    ByVal func As Func(Of T, String), ByVal separator As String) As String  
        Dim sb As StringBuilder = New StringBuilder()  
        For Each item As T In source  
            sb.Append(func(item)).Append(separator)  
        Next  
        Return sb.ToString()  
    End Function  
  
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
  
        ' Retrieve the text of each paragraph.  
        Dim paraWithText = _  
            From para In paragraphs _  
            Select New With { _  
                .ParagraphNode = para.ParagraphNode, _  
                .StyleName = para.StyleName, _  
                .Text = para.ParagraphNode.<w:r>.<w:t>.StringConcatenate(Function(e) CStr(e)) _  
            }  
  
        For Each p In paraWithText  
            Console.WriteLine("StyleName:{0} >{1}<", p.StyleName, p.Text)  
        Next  
  
    End Sub  
End Module  
```  
  
 <span data-ttu-id="3fefc-122">Ten przykład generuje następujące dane wyjściowe po zastosowaniu do dokumentu opisano w [tworzenie źródłowego dokumentu pakietu Office Open XML (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/creating-the-source-office-open-xml-document.md).</span><span class="sxs-lookup"><span data-stu-id="3fefc-122">This example produces the following output when applied to the document described in [Creating the Source Office Open XML Document (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/creating-the-source-office-open-xml-document.md).</span></span>  
  
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
  
 <span data-ttu-id="3fefc-123">Należy pamiętać, że ta Refaktoryzacja jest wariant Refaktoryzacja do czystych funkcji.</span><span class="sxs-lookup"><span data-stu-id="3fefc-123">Note that this refactoring is a variant of refactoring into a pure function.</span></span> <span data-ttu-id="3fefc-124">Następny temat przedstawiono koncepcję wyprowadzenie do czystych funkcji bardziej szczegółowo.</span><span class="sxs-lookup"><span data-stu-id="3fefc-124">The next topic will introduce the idea of factoring into pure functions in more detail.</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="3fefc-125">Następne kroki</span><span class="sxs-lookup"><span data-stu-id="3fefc-125">Next Steps</span></span>  
 <span data-ttu-id="3fefc-126">W kolejnym przykładzie pokazano sposób Refaktoryzuj ten kod w inny sposób, przy użyciu czystej funkcji:</span><span class="sxs-lookup"><span data-stu-id="3fefc-126">The next example shows how to refactor this code in another way, by using pure functions:</span></span>  
  
-   [<span data-ttu-id="3fefc-127">Refaktoryzacja przy użyciu czystej funkcji (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="3fefc-127">Refactoring Using a Pure Function (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/refactoring-using-a-pure-function.md)  
  
## <a name="see-also"></a><span data-ttu-id="3fefc-128">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="3fefc-128">See also</span></span>
- [<span data-ttu-id="3fefc-129">Samouczek: Manipulowanie zawartością w dokumencie WordprocessingML (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="3fefc-129">Tutorial: Manipulating Content in a WordprocessingML Document (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/tutorial-manipulating-content-in-a-wordprocessingml-document.md)
- [<span data-ttu-id="3fefc-130">Refaktoryzacja do czystych funkcji (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="3fefc-130">Refactoring Into Pure Functions (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/refactoring-into-pure-functions.md)
