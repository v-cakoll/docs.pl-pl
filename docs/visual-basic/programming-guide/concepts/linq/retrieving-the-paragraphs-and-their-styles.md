---
title: Trwa pobieranie akapitów i ich style (Visual Basic)
ms.date: 07/20/2015
ms.assetid: d9ed2238-d38e-4ad4-b88b-db7859df9bde
ms.openlocfilehash: 5b8075b5aa05c32d2dc894149a8fa53f103138c6
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33648310"
---
# <a name="retrieving-the-paragraphs-and-their-styles-visual-basic"></a>Trwa pobieranie akapitów i ich style (Visual Basic)
W tym przykładzie mamy Napisz zapytanie, które pobiera węzły akapitu z dokumentu schemat WordprocessingML. Identyfikuje styl każdego akapitu.  
  
 To zapytanie opiera się na zapytanie w poprzednim przykładzie [znajdowanie domyślny styl akapitu (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/finding-the-default-paragraph-style.md), który pobiera styl domyślny z listy stylów. Te informacje są niezbędne, aby zapytanie można zidentyfikować styl akapitów, które nie mają jawnie ustawiona stylu. Style są ustawiane za pomocą `w:pPr` element; Jeśli akapitu nie zawiera tego elementu, jest sformatowany przy użyciu domyślnego stylu.  
  
 W tym temacie wyjaśniono znaczenie niektóre elementy zapytania, a następnie wyświetla zapytanie w ramach zakończeniu przykładu pracy.  
  
## <a name="example"></a>Przykład  
 Źródłem zapytania można pobrać wszystkich akapitów dokumentu oraz ich stylów jest następujący:  
  
```vb  
xDoc.Root.<w:body>...<w:p>  
```  
  
 To wyrażenie jest podobny do źródła zapytania w poprzednim przykładzie [znajdowanie domyślny styl akapitu (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/finding-the-default-paragraph-style.md). Główną różnicą jest to, że używa <xref:System.Xml.Linq.XContainer.Descendants%2A> osi zamiast <xref:System.Xml.Linq.XContainer.Elements%2A> osi. Zapytanie używa <xref:System.Xml.Linq.XContainer.Descendants%2A> osi ponieważ w dokumentach zawierających sekcje, akapitów nie będzie bezpośrednimi elementami podrzędnymi elementu body; zamiast akapitów będzie dwa poziomy w dół w hierarchii. Za pomocą <xref:System.Xml.Linq.XContainer.Descendants%2A> osi, kod będzie działać z czy dokument używa sekcje.  
  
## <a name="example"></a>Przykład  
 Zapytanie używa `Let` klauzuli, aby określić element, który zawiera węzeł stylu. Jeśli nie ma żadnych elementów `styleNode` ma ustawioną wartość `Nothing`:  
  
```vb  
Let styleNode As XElement = para.<w:pPr>.<w:pStyle>.FirstOrDefault()  
```  
  
 `Let` Najpierw używa klauzuli <xref:System.Xml.Linq.XContainer.Elements%2A> osi, aby znaleźć wszystkie elementy o nazwie `pPr`, następnie używa <xref:System.Xml.Linq.Extensions.Elements%2A> — metoda rozszerzenia, aby znaleźć wszystkie elementy podrzędne o nazwie `pStyle`, a na koniec używa <xref:System.Linq.Enumerable.FirstOrDefault%2A> standardowej kwerendy Operator do przekonwertowania kolekcji na pojedynczą. Jeśli kolekcja jest pusta, `styleNode` ma ustawioną wartość `Nothing`. Jest to przydatne idiom do wyszukania `pStyle` podrzędnego. Należy pamiętać, że jeśli `pPr` węzeł podrzędny nie istnieje, kod nie ani nie zakończyć się niepowodzeniem przez Zgłaszanie wyjątku; zamiast tego `styleNode` ustawiono `Nothing`, która jest zachowanie tej `Let` klauzuli.  
  
 Zapytanie projektów kolekcję typu anonimowego z dwóch członków `StyleName` i `ParagraphNode`.  
  
## <a name="example"></a>Przykład  
 W tym przykładzie przetwarza dokument schemat WordprocessingML pobieranie węzłów akapitu z dokumentem schemat WordprocessingML. Identyfikuje styl każdego akapitu. W tym przykładzie kompilacje w poprzednich przykładach, w tym samouczku. Nowe zapytanie jest podana w komentarzach w poniższym kodzie.  
  
 Można znaleźć instrukcje dotyczące tworzenia w tym przykładzie w dokumencie źródłowym [tworzenie źródło dokumentu pakietu Office Open XML (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/creating-the-source-office-open-xml-document.md).  
  
 W tym przykładzie użyto znaleziony w zestawie WindowsBase klasy. Używa typów w <xref:System.IO.Packaging?displayProperty=nameWithType> przestrzeni nazw.  
  
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
  
 Ten przykład generuje dane wyjściowe w przypadku zastosowanego do dokumentu opisano w następujących [tworzenie źródło dokumentu pakietu Office Open XML (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/creating-the-source-office-open-xml-document.md).  
  
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
 W następnym temacie [pobieranie tekstu akapitów (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/retrieving-the-text-of-the-paragraphs.md), utworzysz kwerendę, aby pobrać tekst akapitów.  
  
## <a name="see-also"></a>Zobacz też  
 [Samouczek: Manipulowanie zawartości w dokumencie schemat WordprocessingML (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/tutorial-manipulating-content-in-a-wordprocessingml-document.md)
