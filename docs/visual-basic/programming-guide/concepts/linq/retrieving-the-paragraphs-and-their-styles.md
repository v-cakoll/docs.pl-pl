---
title: Pobieranie akapitów i ich stylów (Visual Basic)
ms.date: 07/20/2015
ms.assetid: d9ed2238-d38e-4ad4-b88b-db7859df9bde
ms.openlocfilehash: 4bc20556fb668db2db3e6bcfa42e96cc0d963b93
ms.sourcegitcommit: 1f12db2d852d05bed8c53845f0b5a57a762979c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2019
ms.locfileid: "72582149"
---
# <a name="retrieving-the-paragraphs-and-their-styles-visual-basic"></a>Pobieranie akapitów i ich stylów (Visual Basic)
W tym przykładzie napiszemy zapytanie, które pobiera węzły akapitu z dokumentu WordprocessingML. Identyfikuje także styl każdego akapitu.  
  
 To zapytanie kompiluje zapytanie w poprzednim przykładzie, [wyszukując domyślny styl akapitu (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/finding-the-default-paragraph-style.md), który Pobiera domyślny styl z listy stylów. Te informacje są wymagane, aby zapytanie mogło identyfikować styl akapitów, w których styl nie został jawnie ustawiony. Style akapitu są ustawiane za pomocą elementu `w:pPr`; Jeśli akapit nie zawiera tego elementu, zostanie sformatowany przy użyciu stylu domyślnego.  
  
 W tym temacie wyjaśniono znaczenie niektórych fragmentów zapytania, a następnie przedstawiono zapytanie w ramach kompletnego, działającego przykładu.  
  
## <a name="example"></a>Przykład  
 Źródło zapytania do pobrania wszystkich akapitów w dokumencie i ich stylów jest następująca:  
  
```vb  
xDoc.Root.<w:body>...<w:p>  
```  
  
 To wyrażenie jest podobne do źródła zapytania w poprzednim przykładzie, co umożliwia [znalezienie domyślnego stylu akapitu (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/finding-the-default-paragraph-style.md). Główną różnicą jest to, że używa osi <xref:System.Xml.Linq.XContainer.Descendants%2A> zamiast osi <xref:System.Xml.Linq.XContainer.Elements%2A>. Zapytanie używa osi <xref:System.Xml.Linq.XContainer.Descendants%2A>, ponieważ w dokumentach zawierających sekcje akapity nie będą bezpośrednimi elementami podrzędnymi elementu body. Zamiast tego akapity będą znajdować się na poziomie dwóch poziomów w hierarchii. Korzystając z osi <xref:System.Xml.Linq.XContainer.Descendants%2A>, kod będzie działał niezależnie od tego, czy dokument korzysta z sekcji.  
  
## <a name="example"></a>Przykład  
 Zapytanie używa klauzuli `Let`, aby określić element, który zawiera węzeł stylu. Jeśli nie ma elementu, `styleNode` jest ustawiona na `Nothing`:  
  
```vb  
Let styleNode As XElement = para.<w:pPr>.<w:pStyle>.FirstOrDefault()  
```  
  
 Klauzula `Let` najpierw używa osi <xref:System.Xml.Linq.XContainer.Elements%2A> do znajdowania wszystkich elementów o nazwie `pPr`, a następnie używa metody rozszerzenia <xref:System.Xml.Linq.Extensions.Elements%2A> do znajdowania wszystkich elementów podrzędnych o nazwie `pStyle`, a na koniec używa standardowego operatora zapytań <xref:System.Linq.Enumerable.FirstOrDefault%2A> do konwertowania kolekcji na pojedynczą. Jeśli kolekcja jest pusta, `styleNode` jest ustawiona na `Nothing`. Jest to przydatny idiom do wyszukiwania `pStyle` węzła podrzędnego. Należy pamiętać, że jeśli węzeł podrzędny `pPr` nie istnieje, kod nie powiedzie się, ponieważ zgłasza wyjątek; Zamiast tego `styleNode` jest ustawiona na `Nothing`, co jest pożądanym zachowaniem tej klauzuli `Let`.  
  
 Zapytanie projektuje kolekcję typu anonimowego z dwoma elementami członkowskimi, `StyleName` i `ParagraphNode`.  
  
## <a name="example"></a>Przykład  
 Ten przykład przetwarza dokument WordprocessingML, pobierając węzły akapitu z dokumentu WordprocessingML. Identyfikuje także styl każdego akapitu. Ten przykład kompiluje się zgodnie z poprzednimi przykładami w tym samouczku. Nowe zapytanie jest wywoływane w komentarzach w poniższym kodzie.  
  
 Instrukcje dotyczące tworzenia dokumentu źródłowego dla tego przykładu można znaleźć w temacie [Tworzenie źródłowego dokumentu Office Open XML (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/creating-the-source-office-open-xml-document.md).  
  
 Ten przykład używa klas znalezionych w zestawie 'Windowsbase. Używa typów w przestrzeni nazw <xref:System.IO.Packaging?displayProperty=nameWithType>.  
  
```vb  
Imports <xmlns:w="http://schemas.openxmlformats.org/wordprocessingml/2006/main">  
  
Module Module1  
    Private Function GetStyleOfParagraph(ByVal styleNode As XElement, ByVal defaultStyle As String) As String  
        If (styleNode Is Nothing) Then  
            Return defaultStyle  
        Else  
            Return styleNode.@w:val  
        End If  
    End Function  
  
    Sub Main()  
        Dim fileName = "SampleDoc.docx"  
  
        Dim documentRelationshipType = "http://schemas.openxmlformats.org/officeDocument/2006/relationships/officeDocument"  
        Dim stylesRelationshipType = "http://schemas.openxmlformats.org/officeDocument/2006/relationships/styles"  
        Dim wordmlNamespace = "http://schemas.openxmlformats.org/wordprocessingml/2006/main"  
  
        Dim xDoc As XDocument = Nothing  
        Dim styleDoc As XDocument = Nothing  
        Using wdPackage As Package = Package.Open(fileName, FileMode.Open, FileAccess.Read)  
            Dim docPackageRelationship As PackageRelationship = wdPackage.GetRelationshipsByType(documentRelationshipType).FirstOrDefault()  
            If (docPackageRelationship IsNot Nothing) Then  
                Dim documentUri As Uri = PackUriHelper.ResolvePartUri(New Uri("/", UriKind.Relative), docPackageRelationship.TargetUri)  
                Dim documentPart As PackagePart = wdPackage.GetPart(documentUri)  
  
                '  Load the document XML in the part into an XDocument instance.  
                xDoc = XDocument.Load(XmlReader.Create(documentPart.GetStream()))  
  
                '  Find the styles part. There will only be one.  
                Dim styleRelation As PackageRelationship = documentPart.GetRelationshipsByType(stylesRelationshipType).FirstOrDefault()  
                If (styleRelation IsNot Nothing) Then  
                    Dim styleUri As Uri = PackUriHelper.ResolvePartUri(documentUri, styleRelation.TargetUri)  
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
  
        ' Following is the new query that finds all paragraphs in the  
        ' document and their styles.  
        Dim paragraphs = _  
            From para In xDoc.Root.<w:body>...<w:p> _  
        Let styleNode As XElement = para.<w:pPr>.<w:pStyle>.FirstOrDefault() _  
        Select New With { _  
            .ParagraphNode = para, _  
            .StyleName = GetStyleOfParagraph(styleNode, defaultStyle) _  
        }  
  
        For Each p In paragraphs  
            Console.WriteLine("StyleName:{0}", p.StyleName)  
        Next  
  
    End Sub  
End Module  
```  
  
 Ten przykład generuje następujące dane wyjściowe w przypadku zastosowania do dokumentu opisanego w temacie [Tworzenie źródłowego dokumentu Office Open XML (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/creating-the-source-office-open-xml-document.md).  
  
```console  
StyleName:Heading1  
StyleName:Normal  
StyleName:Normal  
StyleName:Normal  
StyleName:Code  
StyleName:Code  
StyleName:Code  
StyleName:Code  
StyleName:Code  
StyleName:Code  
StyleName:Code  
StyleName:Normal  
StyleName:Normal  
StyleName:Normal  
StyleName:Code  
```  
  
## <a name="next-steps"></a>Następne kroki  
 W następnym temacie, [pobierając tekst akapitów (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/retrieving-the-text-of-the-paragraphs.md), utworzysz zapytanie w celu pobrania tekstu akapitów.  
  
## <a name="see-also"></a>Zobacz także

- [Samouczek: manipulowanie zawartością w dokumencie WordprocessingML (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/tutorial-manipulating-content-in-a-wordprocessingml-document.md)
