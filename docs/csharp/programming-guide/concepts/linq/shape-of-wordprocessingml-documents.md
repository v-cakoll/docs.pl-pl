---
title: Kształt dokumentów WordprocessingML (C#)
ms.date: 07/20/2015
ms.assetid: 3791b5e0-c502-469b-bb75-a7bf6fdd0a94
ms.openlocfilehash: 84d893267c37ecf99a457ebb683d0451e2b4b68f
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/19/2019
ms.locfileid: "69591057"
---
# <a name="shape-of-wordprocessingml-documents-c"></a>Kształt dokumentów WordprocessingML (C#)
Ten temat zawiera wprowadzenie do kształtu XML dokumentu WordprocessingML.  
  
## <a name="microsoft-office-formats"></a>Formaty Microsoft Office  
 Format pliku natywnego dla systemu 2007 Microsoft Office to Office Open XML (często nazywanego Open XML). Open XML jest formatem opartym na formacie XML, który Standard ECMA i jest obecnie przechodzący przez proces standardów ISO-IEC. Język znaczników dla plików edytora tekstu w formacie Open XML ma nazwę WordprocessingML. Ten samouczek używa plików źródłowych WordprocessingML jako danych wejściowych dla przykładów.  
  
 Jeśli używasz Microsoft Office 2003, możesz zapisać dokumenty w formacie Office Open XML, jeśli zainstalowano pakiet zgodności Microsoft Office dla formatów plików programów Word, Excel i PowerPoint 2007.  
  
## <a name="the-shape-of-wordprocessingml-documents"></a>Kształt dokumentów WordprocessingML  
 Pierwszą rzeczą, którą należy zrozumieć, jest kształt dokumentów WordprocessingML. Dokument WordprocessingML zawiera element Body (o nazwie `w:body`) zawierający akapity dokumentu. Każdy akapit zawiera jeden lub więcej uruchomień tekstu ( `w:r`o nazwie). Każdy przebieg tekstowy zawiera jedną lub więcej fragmentów tekstu ( `w:t`o nazwie).  
  
 Oto bardzo prosty dokument WordprocessingML:  
  
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
  
 Ten dokument zawiera dwa akapity. Oba te elementy zawierają pojedynczy przebieg tekstowy, a każdy z nich jest pojedynczym fragmentem tekstu.  
  
 Najprostszym sposobem wyświetlenia zawartości dokumentu WordprocessingML w formularzu XML jest utworzenie go przy użyciu programu Microsoft Word, zapisanie go, a następnie uruchomienie następującego programu, który drukuje plik XML do konsoli programu.  
  
 Ten przykład używa klas znalezionych w zestawie 'Windowsbase. Używa typów w <xref:System.IO.Packaging?displayProperty=nameWithType> przestrzeni nazw.  
  
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
 [Wprowadzenie do pakietu Office (2007) otwartych formatów plików XML](https://docs.microsoft.com/previous-versions/office/developer/office-2007/aa338205%28v=office.12%29)  
 [Przegląd WordprocessingML](https://docs.microsoft.com/previous-versions/office/developer/office-2003/aa212812%28v=office.11%29)  
 [Anatomia pliku WordProcessingML](http://officeopenxml.com/anatomyofOOXML.php)  
 [Wprowadzenie do WordprocessingML](https://ericwhite.com/blog/introduction-to-wordprocessingml-series/)  
 [Office 2003: Strona pobierania schematów odwołań XML](https://www.microsoft.com/download/details.aspx?id=101)  
  
## <a name="see-also"></a>Zobacz także

- [Samouczek: Manipulowanie zawartością w dokumencie WordprocessingML (C#)](./shape-of-wordprocessingml-documents.md)
