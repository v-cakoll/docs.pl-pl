---
title: Pobieranie akapitów i ich stylów (Visual Basic)
ms.date: 07/20/2015
ms.assetid: d9ed2238-d38e-4ad4-b88b-db7859df9bde
ms.openlocfilehash: 3c6554c44c95db13aada0d9edf96cc2df595c6d1
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/02/2019
ms.locfileid: "58816944"
---
# <a name="retrieving-the-paragraphs-and-their-styles-visual-basic"></a>Pobieranie akapitów i ich stylów (Visual Basic)
W tym przykładzie napiszemy zapytanie, które pobiera węzły akapit w dokumencie WordprocessingML. Określa on styl każdego akapitu.  
  
 To zapytanie jest oparta na zapytania w poprzednim przykładzie [znajdowanie domyślnego stylu akapitu (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/finding-the-default-paragraph-style.md), która pobiera domyślnego stylu z listy stylów. Te informacje są wymagane, aby zapytanie można zidentyfikować styl akapitów, które nie mają jawnie ustawić stylu. Style są ustawiane za pomocą `w:pPr` element; Jeśli akapitu nie zawiera tego elementu, jest formatowana przy użyciu domyślnego stylu.  
  
 W tym temacie wyjaśniono znaczenie niektóre elementy zapytania, a następnie wyświetla kwerendy jako część zakończeniu praktyczny przykład.  
  
## <a name="example"></a>Przykład  
 Źródło zapytanie, aby pobrać wszystkie akapitów w dokumencie i ich stylów jest następująca:  
  
```vb  
xDoc.Root.<w:body>...<w:p>  
```  
  
 To wyrażenie jest podobny do źródła zapytania w poprzednim przykładzie [znajdowanie stylu akapitu domyślne (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/finding-the-default-paragraph-style.md). Główną różnicą jest to, że używa on <xref:System.Xml.Linq.XContainer.Descendants%2A> osi zamiast <xref:System.Xml.Linq.XContainer.Elements%2A> osi. Zapytanie używa <xref:System.Xml.Linq.XContainer.Descendants%2A> osi, ponieważ w dokumentach, które mają sekcje, akapitów, nie będzie bezpośrednie elementy podrzędne elementu body; zamiast akapitów zostaną dwa poziomy w dół w hierarchii. Za pomocą <xref:System.Xml.Linq.XContainer.Descendants%2A> osi, ten kod będzie działać z czy dokument używa sekcje.  
  
## <a name="example"></a>Przykład  
 Zapytanie używa `Let` klauzuli, aby określić element, który zawiera węzeł style. Jeśli nie ma żadnego elementu, następnie `styleNode` ustawiono `Nothing`:  
  
```vb  
Let styleNode As XElement = para.<w:pPr>.<w:pStyle>.FirstOrDefault()  
```  
  
 `Let` Najpierw używa klauzuli <xref:System.Xml.Linq.XContainer.Elements%2A> osi, aby znaleźć wszystkie elementy o nazwie `pPr`, następnie używa <xref:System.Xml.Linq.Extensions.Elements%2A> metodę rozszerzenia, aby znaleźć wszystkie elementy podrzędne, o nazwie `pStyle`, a na koniec używa <xref:System.Linq.Enumerable.FirstOrDefault%2A> standardowej kwerendy Operator do przekonwertowania kolekcji na wzorzec singleton. Jeśli kolekcja jest pusta, `styleNode` ustawiono `Nothing`. Jest to przydatne idiom do wyszukania `pStyle` podrzędnego. Należy pamiętać, że jeśli `pPr` węzeł podrzędny nie istnieje, kod nie ani nie zakończyć się niepowodzeniem, zostanie zgłoszony wyjątek; zamiast tego `styleNode` ustawiono `Nothing`, czyli żądane zachowanie tego `Let` klauzuli.  
  
 Zapytanie projektów kolekcji typu anonimowego z dwoma elementami członkowskimi, `StyleName` i `ParagraphNode`.  
  
## <a name="example"></a>Przykład  
 W tym przykładzie przetwarza dokumentu WordprocessingML pobieranie węzłów akapit w dokumencie WordprocessingML. Określa on styl każdego akapitu. W tym przykładzie opiera się na poprzednich przykładach w tym samouczku. Nowe zapytanie jest wywoływane w komentarzach, w poniższym kodzie.  
  
 Można znaleźć instrukcje dotyczące tworzenia dokumentu źródłowego, w tym przykładzie w [tworzenie źródłowego dokumentu pakietu Office Open XML (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/creating-the-source-office-open-xml-document.md).  
  
 W tym przykładzie użyto klasy znalezione w zestawie WindowsBase. Używa typów w <xref:System.IO.Packaging?displayProperty=nameWithType> przestrzeni nazw.  
  
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
  
 Ten przykład generuje następujące dane wyjściowe po zastosowaniu do dokumentu opisano w [tworzenie źródłowego dokumentu pakietu Office Open XML (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/creating-the-source-office-open-xml-document.md).  
  
```  
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
 W następnym temacie [pobieranie tekstu akapitów (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/retrieving-the-text-of-the-paragraphs.md), utworzysz zapytanie, aby pobrać tekstu akapitów.  
  
## <a name="see-also"></a>Zobacz także

- [Samouczek: Manipulowanie zawartością w dokumencie WordprocessingML (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/tutorial-manipulating-content-in-a-wordprocessingml-document.md)
