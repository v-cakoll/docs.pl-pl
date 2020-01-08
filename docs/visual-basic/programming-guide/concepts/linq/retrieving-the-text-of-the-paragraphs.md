---
title: Pobieranie tekstu akapitów
ms.date: 07/20/2015
ms.assetid: 095fa0d9-7b1b-4cbb-9c13-e2c9d8923d31
ms.openlocfilehash: 0f53eec44e0b11a6c23c7afb4892e4d5d876d6d6
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/25/2019
ms.locfileid: "75341599"
---
# <a name="retrieving-the-text-of-the-paragraphs-visual-basic"></a>Pobieranie tekstu akapitów (Visual Basic)
Ten przykład kompiluje się w poprzednim przykładzie, [pobierając akapity i ich style (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/retrieving-the-paragraphs-and-their-styles.md). Ten nowy przykład pobiera tekst każdego akapitu w postaci ciągu.  
  
 Aby pobrać tekst, ten przykład dodaje dodatkowe zapytanie, które iteruje przez kolekcję typów anonimowych i projektów nowej kolekcji typu anonimowego z dodaniem nowego elementu członkowskiego `Text`. Używa standardowego operatora zapytań <xref:System.Linq.Enumerable.Aggregate%2A> do łączenia wielu ciągów w jeden ciąg.  
  
 Ta technika (czyli najpierw projekcja do kolekcji typu anonimowego, a następnie użycie tej kolekcji w celu utworzenia nowej kolekcji typu anonimowego) jest powszechną i użyteczną idiom. To zapytanie mogło zostać zapisaną bez projekcji pierwszego typu anonimowego. Jednak ze względu na ocenę z opóźnieniem nie jest używana znacznie dodatkowa moc obliczeniowa. Idiom tworzy więcej krótkich obiektów na stercie, ale nie zmniejsza to wydajności.  
  
 Oczywiście można napisać pojedyncze zapytanie, które zawiera funkcje umożliwiające pobranie akapitów, stylu każdego akapitu i tekstu każdego akapitu. Często jednak warto rozdzielić bardziej skomplikowane zapytanie na wiele zapytań, ponieważ otrzymany kod jest bardziej modularny i łatwiejszy w obsłudze. Ponadto, jeśli konieczne jest ponowne użycie części zapytania, łatwiej jest refaktoryzację, jeśli zapytania są zapisywane w ten sposób.  
  
 Te zapytania, które są powiązane ze sobą, wykorzystują model przetwarzania, który jest szczegółowo rozpatrywany w [samouczku tematu: wykonywanie odroczone (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/tutorial-deferred-execution.md).  
  
## <a name="example"></a>Przykład  
 Ten przykład przetwarza dokument WordprocessingML, określając węzeł elementu, nazwę stylu i tekst każdego akapitu. Ten przykład kompiluje się zgodnie z poprzednimi przykładami w tym samouczku. Nowe zapytanie jest wywoływane w komentarzach w poniższym kodzie.  
  
 Aby uzyskać instrukcje dotyczące tworzenia dokumentu źródłowego dla tego przykładu, zobacz [Tworzenie źródłowego dokumentu Office Open XML (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/creating-the-source-office-open-xml-document.md).  
  
 W tym przykładzie zastosowano klasy z zestawu 'Windowsbase. Używa typów w przestrzeni nazw <xref:System.IO.Packaging?displayProperty=nameWithType>.  
  
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
  
 Ten przykład generuje następujące dane wyjściowe w przypadku zastosowania do dokumentu opisanego w temacie [Tworzenie źródłowego dokumentu Office Open XML (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/creating-the-source-office-open-xml-document.md).  
  
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
  
## <a name="next-steps"></a>Następne kroki  
 W następnym przykładzie pokazano, jak używać metody rozszerzenia zamiast <xref:System.Linq.Enumerable.Aggregate%2A>, aby połączyć wiele ciągów w jeden ciąg.  
  
- [Refaktoryzacja przy użyciu metody rozszerzającej (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/refactoring-using-an-extension-method.md)  
  
## <a name="see-also"></a>Zobacz także

- [Samouczek: manipulowanie zawartością w dokumencie WordprocessingML (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/tutorial-manipulating-content-in-a-wordprocessingml-document.md)
- [Wykonywanie odroczone i Ocena z opóźnieniem w LINQ to XML (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/deferred-execution-and-lazy-evaluation-in-linq-to-xml.md)
