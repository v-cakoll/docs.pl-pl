---
title: Znajdowanie domyślnego stylu akapitu (Visual Basic)
ms.date: 07/20/2015
ms.assetid: 9d094a4a-ec8c-41b0-b7ab-a3deb2a01d45
ms.openlocfilehash: 0694c9144e44e4a5de262f97581eb18943937243
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/02/2019
ms.locfileid: "58841111"
---
# <a name="finding-the-default-paragraph-style-visual-basic"></a>Znajdowanie domyślnego stylu akapitu (Visual Basic)
Pierwsze zadanie w manipulowanie informacje przedstawione w samouczku dokumentu WordprocessingML jest znajdowanie domyślnego stylu akapitów w dokumencie.  
  
## <a name="example"></a>Przykład  
  
### <a name="description"></a>Opis  
 Poniższy przykład spowoduje otwarcie dokumentu Office Open XML WordprocessingML, znajduje dokument i styl części pakietu, a następnie wykonuje zapytanie, które znajdzie domyślną nazwę stylu. Dla informacji na temat pakietów dokumentu Office Open XML i części składają się one z [szczegóły dla dokumentów pakietu Office Open XML WordprocessingML (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/details-of-office-open-xml-wordprocessingml-documents.md).  
  
 Zapytanie znajdzie węzła o nazwie `w:style` zawierającego atrybut o nazwie `w:type` z wartością "akapitu", a także ma atrybut o nazwie `w:default` z wartością "1". Ponieważ będzie istniało tylko jeden węzeł XML za pomocą tych atrybutów, zapytanie używa <xref:System.Linq.Enumerable.First%2A?displayProperty=nameWithType> operatora do przekonwertowania kolekcji na wzorzec singleton. Następnie pobiera wartość atrybutu o nazwie `w:styleId`.  
  
 W tym przykładzie użyto klasy z zestawu WindowsBase. Używa typów w <xref:System.IO.Packaging?displayProperty=nameWithType> przestrzeni nazw.  
  
### <a name="code"></a>Kod  
  
```vb  
Imports <xmlns:w="http://schemas.openxmlformats.org/wordprocessingml/2006/main">  
  
Module Module1  
  
    Sub Main()  
  
        Const fileName As String = "SampleDoc.docx"  
  
        Const documentRelationshipType As String = _  
          "http://schemas.openxmlformats.org/officeDocument/2006/relationships/officeDocument"  
        Const stylesRelationshipType As String = _  
          "http://schemas.openxmlformats.org/officeDocument/2006/relationships/styles"  
  
        Dim xDoc As XDocument = Nothing  
        Dim styleDoc As XDocument = Nothing  
  
        Using wdPackage As Package = Package.Open(fileName, FileMode.Open, FileAccess.Read)  
            Dim docPackageRelationship As PackageRelationship = _  
              wdPackage.GetRelationshipsByType(documentRelationshipType).FirstOrDefault()  
            If docPackageRelationship IsNot Nothing Then  
                Dim documentUri As Uri = PackUriHelper.ResolvePartUri(New Uri("/", UriKind.Relative), _  
                  docPackageRelationship.TargetUri)  
                Dim documentPart As PackagePart = wdPackage.GetPart(documentUri)  
  
                ' Load the document XML in the part into an XDocument instance.  
                xDoc = XDocument.Load(XmlReader.Create(documentPart.GetStream()))  
  
                ' Find the styles part. There will only be one.  
                Dim styleRelation As PackageRelationship = _  
                  documentPart.GetRelationshipsByType(stylesRelationshipType).FirstOrDefault()  
                If styleRelation IsNot Nothing Then  
                    Dim styleUri As Uri = _  
                      PackUriHelper.ResolvePartUri(documentUri, styleRelation.TargetUri)  
                    Dim stylePart As PackagePart = wdPackage.GetPart(styleUri)  
  
                    ' Load the style XML in the part into an XDocument instance.  
                    styleDoc = XDocument.Load(XmlReader.Create(stylePart.GetStream()))  
                End If  
            End If  
        End Using  
  
        ' The following query finds all the paragraphs that have the default style.  
        Dim defParas As IEnumerable(Of XElement) = _  
            From style In styleDoc.Root.<w:style> _  
            Where style.@w:type.Equals("paragraph") And _  
                   style.@w:default.Equals("1") _  
            Select style  
        ' Then find the style of the first.  
        Dim defaultStyle As String = defParas.First().@w:styleId  
  
        Console.WriteLine("The default style is: " & defaultStyle)  
    End Sub  
End Module  
```  
  
### <a name="comments"></a>Komentarze  
 Ten przykład generuje następujące wyniki:  
  
```  
The default style is: Normal  
```  
  
## <a name="next-steps"></a>Następne kroki  
 W następnym przykładzie utworzysz podobne zapytanie, które umożliwia znalezienie wszystkich akapitów w dokumencie i ich stylów:  
  
-   [Pobieranie akapitów i ich stylów (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/retrieving-the-paragraphs-and-their-styles.md)  
  
## <a name="see-also"></a>Zobacz także

- [Samouczek: Manipulowanie zawartością w dokumencie WordprocessingML (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/tutorial-manipulating-content-in-a-wordprocessingml-document.md)
