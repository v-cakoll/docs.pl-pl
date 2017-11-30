---
title: "Kształt schemat WordprocessingML dokumentów (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 2dfb446b-5a07-4c00-9ab3-a74ba734ff3a
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: f29ed78062337c7036ada2405fa610ff1f883feb
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="shape-of-wordprocessingml-documents-visual-basic"></a>Kształt schemat WordprocessingML dokumentów (Visual Basic)
W tym temacie przedstawiono kształtu XML dokumentu schemat WordprocessingML.  
  
## <a name="microsoft-office-formats"></a>Formaty pakietu Microsoft Office  
 Format natywny plik pakietu Microsoft Office system 2007 jest Office Open XML (często nazywany Open XML). Otwieranie pliku XML jest oparte na języku XML format standardu Ecma i jest obecnie przechodzi przez proces normy ISO IEC. Język znaczników dla edytora plików w Open XML nosi nazwę schemat WordprocessingML. Ten samouczek używa plików źródłowych schemat WordprocessingML jako dane wejściowe dla przykładów.  
  
 Jeśli używasz programu Microsoft Office 2003 można zapisywać dokumenty w formacie Office Open XML po zainstalowaniu pakietu zgodności Microsoft Office dla programów Word, Excel i PowerPoint 2007.  
  
## <a name="the-shape-of-wordprocessingml-documents"></a>Kształt schemat WordprocessingML dokumentów  
 Najpierw zrozumieć jest kształtu schemat WordprocessingML dokumentów. Schemat WordprocessingML dokument zawiera body element (o nazwie `w:body`) zawierający akapitów dokumentu. Każdego akapitu zawiera co najmniej jeden przebieg tekstu (o nazwie `w:r`). Każdego tekstu Uruchom zawiera jeden lub kilka fragmentów tekstu (o nazwie `w:t`).  
  
 Poniżej znajduje się bardzo proste dokumentu schemat WordprocessingML:  
  
```xml  
<?xml version="1.0" encoding="utf-8" standalone="yes"?>  
<w:document  
xmlns:ve="http://schemas.openxmlformats.org/markup-compatibility/2006"  
xmlns:o="urn:schemas-microsoft-com:office:office"  
xmlns:r="http://schemas.openxmlformats.org/officeDocument/2006/relationships"  
xmlns:m="http://schemas.openxmlformats.org/officeDocument/2006/math"  
xmlns:v="urn:schemas-microsoft-com:vml"  
xmlns:wp="http://schemas.openxmlformats.org/drawingml/2006/wordprocessingDrawing"  
xmlns:w10="urn:schemas-microsoft-com:office:word"  
xmlns:w="http://schemas.openxmlformats.org/wordprocessingml/2006/main"  
xmlns:wne="http://schemas.microsoft.com/office/word/2006/wordml">  
  <w:body>  
    <w:p w:rsidR="00E22EB6"  
         w:rsidRDefault="00E22EB6">  
      <w:r>  
        <w:t>This is a paragraph.</w:t>  
      </w:r>  
    </w:p>  
    <w:p w:rsidR="00E22EB6"  
         w:rsidRDefault="00E22EB6">  
      <w:r>  
        <w:t>This is another paragraph.</w:t>  
      </w:r>  
    </w:p>  
  </w:body>  
</w:document>  
```  
  
 Ten dokument zawiera dwa akapitów. Zawierają jeden tekst Uruchom, a każdy tekst Uruchom zawiera element jeden tekst.  
  
 Najprostszym sposobem wyświetlenia zawartości dokumentu schemat WordprocessingML w postaci XML jest aby go utworzyć za pomocą programu Microsoft Word, zapisz go, a następnie uruchom następujący program, który wyświetla kod XML do konsoli.  
  
 W tym przykładzie użyto znaleziony w zestawie WindowsBase klasy. Używa typów w <xref:System.IO.Packaging?displayProperty=nameWithType> przestrzeni nazw.  
  
```vb  
Imports <xmlns:w="http://schemas.openxmlformats.org/wordprocessingml/2006/main">  
  
Module Module1  
    Sub Main()  
        Dim documentRelationshipType = _  
          "http://schemas.openxmlformats.org/officeDocument/2006/relationships/officeDocument"  
  
        Using wdPackage As Package = _  
          Package.Open("SampleDoc.docx", _  
                       FileMode.Open, FileAccess.Read)  
            Dim docPackageRelationship As PackageRelationship = wdPackage _  
                .GetRelationshipsByType(documentRelationshipType).FirstOrDefault()  
            If (docPackageRelationship IsNot Nothing) Then  
                Dim documentUri As Uri = PackUriHelper.ResolvePartUri( _  
                            New Uri("/", UriKind.Relative), _  
                            docPackageRelationship.TargetUri)  
                Dim documentPart As PackagePart = wdPackage.GetPart(documentUri)  
  
                ' Get the officeDocument part from the package.  
                ' Load the XML in the part into an XDocument instance.  
                Dim xDoc As XDocument = _  
                    XDocument.Load(XmlReader.Create(documentPart.GetStream()))  
                Console.WriteLine(xDoc.Root)  
            End If  
        End Using  
    End Sub  
End Module  
```  
  
## <a name="external-resources"></a>Zasoby zewnętrzne  
 [Wprowadzenie do formatów pakietu Office (2007) Open XML](http://go.microsoft.com/fwlink/?LinkId=98093)  
  
 [Omówienie schemat WordprocessingML](http://go.microsoft.com/fwlink/?LinkId=98094)  
  
 [Pakietu Office 2003: Strona pobierania schematy odwołanie XML](http://go.microsoft.com/fwlink/?LinkId=98095)  
  
## <a name="see-also"></a>Zobacz też  
 [Samouczek: Manipulowanie zawartości w dokumencie schemat WordprocessingML (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/tutorial-manipulating-content-in-a-wordprocessingml-document.md)
