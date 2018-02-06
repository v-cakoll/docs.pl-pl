---
title: "Kształt schemat WordprocessingML dokumentów (C#)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-csharp
ms.topic: article
ms.assetid: 3791b5e0-c502-469b-bb75-a7bf6fdd0a94
caps.latest.revision: 
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: ee03c9cd64c3c3b251049be0826c7b29abe80bfa
ms.sourcegitcommit: 099aa20d9b6450d1b7452d782a55771a6ad8ff35
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/05/2018
---
# <a name="shape-of-wordprocessingml-documents-c"></a>Kształt schemat WordprocessingML dokumentów (C#)
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
  
```csharp  
const string documentRelationshipType =  
  "http://schemas.openxmlformats.org/officeDocument/2006/relationships/officeDocument";  
const string wordmlNamespace =  
  "http://schemas.openxmlformats.org/wordprocessingml/2006/main";  
XNamespace w = wordmlNamespace;  
  
using (Package wdPackage = Package.Open("SampleDoc.docx", FileMode.Open, FileAccess.Read))  
{  
    PackageRelationship relationship =  
        wdPackage  
        .GetRelationshipsByType(documentRelationshipType)  
        .FirstOrDefault();  
    if (relationship != null)  
    {  
        Uri documentUri =  
            PackUriHelper.ResolvePartUri(  
                new Uri("/", UriKind.Relative),  
                relationship.TargetUri);  
        PackagePart documentPart = wdPackage.GetPart(documentUri);  
  
        //  Get the officeDocument part from the package.  
        //  Load the XML in the part into an XDocument instance.  
        XDocument xdoc =  
            XDocument.Load(XmlReader.Create(documentPart.GetStream()));  
        Console.WriteLine(xdoc.Root);  
    }  
}  
```  
  
## <a name="external-resources"></a>Zasoby zewnętrzne  
 [Wprowadzenie do formatów pakietu Office (2007) Open XML](https://msdn.microsoft.com/library/ms406049.aspx)  
 [Omówienie schemat WordprocessingML](https://msdn.microsoft.com/library/aa212812(office.11).aspx)  
 [Anatomia pliku schemat WordProcessingML](http://officeopenxml.com/anatomyofOOXML.php)  
 [Wprowadzenie do schemat WordprocessingML](http://ericwhite.com/blog/introduction-to-wordprocessingml-series/)  
 [Pakietu Office 2003: Strona pobierania schematy odwołanie XML](https://www.microsoft.com/en-us/download/details.aspx?id=101)  
  
## <a name="see-also"></a>Zobacz też  
 [Samouczek: Manipulowanie zawartości w dokumencie schemat WordprocessingML (C#)](../../../../csharp/programming-guide/concepts/linq/tutorial-manipulating-content-in-a-wordprocessingml-document.md)
