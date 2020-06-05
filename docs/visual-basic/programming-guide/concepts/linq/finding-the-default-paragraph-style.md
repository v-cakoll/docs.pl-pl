---
title: Znajdowanie domyślnego stylu akapitu
ms.date: 07/20/2015
ms.assetid: 9d094a4a-ec8c-41b0-b7ab-a3deb2a01d45
ms.openlocfilehash: b70ae72c293d00c4f7b7a2601bfd20b85702b6d5
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84398080"
---
# <a name="finding-the-default-paragraph-style-visual-basic"></a>Znajdowanie domyślnego stylu akapitu (Visual Basic)
Pierwsze zadanie w informacjach manipulowania w programie WordprocessingML Documents to znalezienie domyślnego stylu akapitów w dokumencie.  
  
## <a name="example"></a>Przykład  
  
### <a name="description"></a>Opis  
 W poniższym przykładzie zostanie otwarty dokument pakietu Office Open XML WordprocessingML, znajduje się w nim części dokumentu i stylu pakietu, a następnie wykonywana jest kwerenda, która znajduje domyślną nazwę stylu. Aby uzyskać informacje na temat pakietów dokumentów Office Open XML i części, które składają się z, zobacz [szczegóły programu Office Open XML WordprocessingML Documents (Visual Basic)](details-of-office-open-xml-wordprocessingml-documents.md).  
  
 Zapytanie znajduje węzeł o nazwie `w:style` , który ma atrybut o nazwie o `w:type` wartości "Paragraph", a także ma atrybut o nazwie o `w:default` wartości "1". Ponieważ będzie istnieć tylko jeden węzeł XML z tymi atrybutami, zapytanie używa <xref:System.Linq.Enumerable.First%2A?displayProperty=nameWithType> operatora do konwersji kolekcji na pojedynczą. Następnie pobiera wartość atrybutu o nazwie `w:styleId` .  
  
 W tym przykładzie zastosowano klasy z zestawu 'Windowsbase. Używa typów w <xref:System.IO.Packaging?displayProperty=nameWithType> przestrzeni nazw.  
  
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
  
```console  
The default style is: Normal  
```  
  
## <a name="next-steps"></a>Następne kroki  
 W następnym przykładzie utworzysz podobne zapytanie, które znajdzie wszystkie akapity w dokumencie i ich style:  
  
- [Pobieranie akapitów i ich stylów (Visual Basic)](retrieving-the-paragraphs-and-their-styles.md)  
  
## <a name="see-also"></a>Zobacz też

- [Samouczek: manipulowanie zawartością w dokumencie WordprocessingML (Visual Basic)](tutorial-manipulating-content-in-a-wordprocessingml-document.md)
