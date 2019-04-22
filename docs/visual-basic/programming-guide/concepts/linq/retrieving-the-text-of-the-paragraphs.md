---
title: Pobieranie tekstu akapitów (Visual Basic)
ms.date: 07/20/2015
ms.assetid: 095fa0d9-7b1b-4cbb-9c13-e2c9d8923d31
ms.openlocfilehash: bc6035c7d894d30b1441dd35925c233e02d35163
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "58830009"
---
# <a name="retrieving-the-text-of-the-paragraphs-visual-basic"></a>Pobieranie tekstu akapitów (Visual Basic)
W tym przykładzie opiera się na poprzednim przykładzie [pobieranie akapitów i ich stylów (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/retrieving-the-paragraphs-and-their-styles.md). W tym przykładzie nowe pobiera tekst każdego akapitu jako ciąg.  
  
 Aby pobrać tekstu, ten przykład dodaje dodatkowe zapytania, który iteruje po kolekcji typów anonimowych i projekty Nowa kolekcja typu anonimowego dodając nowy element członkowski `Text`. Używa ona <xref:System.Linq.Enumerable.Aggregate%2A> standardowego operatora zapytania na łączenie wielu ciągów w jeden ciąg.  
  
 Ta technika (czyli projekcji pierwszej kolekcji typu anonimowego, a następnie przy użyciu tej kolekcji do projektu do nowej kolekcji typu anonimowego) to idiom typowe i przydatne. To zapytanie może zapisywane bez wyświetlanie na pierwszym typu anonimowego. Jednak ze względu na obliczanie z opóźnieniem, spowoduje to więc nie korzysta z dużo mocy dodatkowego przetwarzania. Idiom tworzy więcej krótki czas życia obiektów na stosie, ale to nie znacznie zmniejszyć wydajność.  
  
 Oczywiście będzie możliwość napisania jednego zapytania, który zawiera funkcje umożliwiające pobieranie akapitów, styl każdego akapitu, a tekst każdego akapitu. Jednak często warto podzielić bardziej skomplikowane zapytanie do wielu zapytań, ponieważ wynikowy kod jest bardziej modułowego i łatwiejsze w konserwacji. Ponadto jeśli zajdzie potrzeba ponownego użycia część zapytania, łatwiej jest Refaktoryzacja Jeśli zapytania są zapisywane w ten sposób.  
  
 Te zapytania, które są połączone, użyj przetwarzania modelu, który jest sprawdzany pod szczegółowo w temacie [samouczka: Odroczone wykonania (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/tutorial-deferred-execution.md).  
  
## <a name="example"></a>Przykład  
 W tym przykładzie przetwarza dokumentu WordprocessingML określania węzła elementu, nazwę stylu i tekst każdego akapitu. W tym przykładzie opiera się na poprzednich przykładach w tym samouczku. Nowe zapytanie jest wywoływane w komentarzach, w poniższym kodzie.  
  
 Aby uzyskać instrukcje dotyczące tworzenia dokumentu źródłowego, w tym przykładzie, zobacz [tworzenie źródłowego dokumentu pakietu Office Open XML (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/creating-the-source-office-open-xml-document.md).  
  
 W tym przykładzie użyto klasy z zestawu WindowsBase. Używa typów w <xref:System.IO.Packaging?displayProperty=nameWithType> przestrzeni nazw.  
  
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
  
 Ten przykład generuje następujące dane wyjściowe po zastosowaniu do dokumentu opisano w [tworzenie źródłowego dokumentu pakietu Office Open XML (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/creating-the-source-office-open-xml-document.md).  
  
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
  
## <a name="next-steps"></a>Następne kroki  
 W kolejnym przykładzie pokazano sposób użycia metody rozszerzenia, zamiast <xref:System.Linq.Enumerable.Aggregate%2A>, aby łączenie wielu ciągów w jeden ciąg.  
  
-   [Refaktoryzacja przy użyciu metody rozszerzenia (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/refactoring-using-an-extension-method.md)  
  
## <a name="see-also"></a>Zobacz także

- [Samouczek: Manipulowanie zawartością w dokumencie WordprocessingML (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/tutorial-manipulating-content-in-a-wordprocessingml-document.md)
- [Wykonanie odroczone i obliczanie z opóźnieniem w LINQ to XML (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/deferred-execution-and-lazy-evaluation-in-linq-to-xml.md)
