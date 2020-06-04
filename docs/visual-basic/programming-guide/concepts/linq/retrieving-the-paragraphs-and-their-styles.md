---
title: Pobieranie akapitów i ich stylów
ms.date: 07/20/2015
ms.assetid: d9ed2238-d38e-4ad4-b88b-db7859df9bde
ms.openlocfilehash: ad904abf9bd94e83b981859662c22787652e294f
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84413414"
---
# <a name="retrieving-the-paragraphs-and-their-styles-visual-basic"></a>Pobieranie akapitów i ich stylów (Visual Basic)
W tym przykładzie napiszemy zapytanie, które pobiera węzły akapitu z dokumentu WordprocessingML. Identyfikuje także styl każdego akapitu.  
  
 To zapytanie kompiluje zapytanie w poprzednim przykładzie, [wyszukując domyślny styl akapitu (Visual Basic)](finding-the-default-paragraph-style.md), który Pobiera domyślny styl z listy stylów. Te informacje są wymagane, aby zapytanie mogło identyfikować styl akapitów, w których styl nie został jawnie ustawiony. Style akapitu są ustawiane za pomocą `w:pPr` elementu. Jeśli akapit nie zawiera tego elementu, zostanie sformatowany przy użyciu stylu domyślnego.  
  
 W tym temacie wyjaśniono znaczenie niektórych fragmentów zapytania, a następnie przedstawiono zapytanie w ramach kompletnego, działającego przykładu.  
  
## <a name="example"></a>Przykład  
 Źródło zapytania do pobrania wszystkich akapitów w dokumencie i ich stylów jest następująca:  
  
```vb  
xDoc.Root.<w:body>...<w:p>  
```  
  
 To wyrażenie jest podobne do źródła zapytania w poprzednim przykładzie, co umożliwia [znalezienie domyślnego stylu akapitu (Visual Basic)](finding-the-default-paragraph-style.md). Główną różnicą jest to, że używa <xref:System.Xml.Linq.XContainer.Descendants%2A> osi zamiast <xref:System.Xml.Linq.XContainer.Elements%2A> osi. Zapytanie używa <xref:System.Xml.Linq.XContainer.Descendants%2A> osi, ponieważ w dokumentach, w których znajdują się sekcje, akapity nie będą bezpośrednimi elementami podrzędnymi elementu body, a akapity będą dwa poziomy w hierarchii. Korzystając z <xref:System.Xml.Linq.XContainer.Descendants%2A> osi, kod będzie działał niezależnie od tego, czy dokument korzysta z sekcji.  
  
## <a name="example"></a>Przykład  
 Zapytanie używa `Let` klauzuli do określenia elementu, który zawiera węzeł stylu. Jeśli nie ma elementu, `styleNode` zostanie ustawiona wartość `Nothing` :  
  
```vb  
Let styleNode As XElement = para.<w:pPr>.<w:pStyle>.FirstOrDefault()  
```  
  
 `Let`Klauzula najpierw używa <xref:System.Xml.Linq.XContainer.Elements%2A> osi do znajdowania wszystkich elementów o nazwie `pPr` , a następnie używa <xref:System.Xml.Linq.Extensions.Elements%2A> metody rozszerzenia do znajdowania wszystkich elementów podrzędnych o nazwie `pStyle` , a wreszcie używa <xref:System.Linq.Enumerable.FirstOrDefault%2A> standardowego operatora zapytań do konwertowania kolekcji na pojedynczą. Jeśli kolekcja jest pusta, `styleNode` jest ustawiona na `Nothing` . Jest to przydatny idiom do wyszukiwania `pStyle` węzła podrzędnego. Należy pamiętać, że jeśli `pPr` węzeł podrzędny nie istnieje, kod jest lub nie powiedzie się, zwracając wyjątek; zamiast tego `styleNode` jest ustawiony na `Nothing` , który jest pożądanym zachowaniem tej `Let` klauzuli.  
  
 Zapytanie projektuje kolekcję typu anonimowego z dwoma członkami `StyleName` i `ParagraphNode` .  
  
## <a name="example"></a>Przykład  
 Ten przykład przetwarza dokument WordprocessingML, pobierając węzły akapitu z dokumentu WordprocessingML. Identyfikuje także styl każdego akapitu. Ten przykład kompiluje się zgodnie z poprzednimi przykładami w tym samouczku. Nowe zapytanie jest wywoływane w komentarzach w poniższym kodzie.  
  
 Instrukcje dotyczące tworzenia dokumentu źródłowego dla tego przykładu można znaleźć w temacie [Tworzenie źródłowego dokumentu Office Open XML (Visual Basic)](creating-the-source-office-open-xml-document.md).  
  
 Ten przykład używa klas znalezionych w zestawie 'Windowsbase. Używa typów w <xref:System.IO.Packaging?displayProperty=nameWithType> przestrzeni nazw.  
  
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
  
 Ten przykład generuje następujące dane wyjściowe w przypadku zastosowania do dokumentu opisanego w temacie [Tworzenie źródłowego dokumentu Office Open XML (Visual Basic)](creating-the-source-office-open-xml-document.md).  
  
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
 W następnym temacie, [pobierając tekst akapitów (Visual Basic)](retrieving-the-text-of-the-paragraphs.md), utworzysz zapytanie w celu pobrania tekstu akapitów.  
  
## <a name="see-also"></a>Zobacz też

- [Samouczek: manipulowanie zawartością w dokumencie WordprocessingML (Visual Basic)](tutorial-manipulating-content-in-a-wordprocessingml-document.md)
