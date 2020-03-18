---
title: Kształt dokumentów WordprocessingML (C#)
ms.date: 07/20/2015
ms.assetid: 3791b5e0-c502-469b-bb75-a7bf6fdd0a94
ms.openlocfilehash: 58c028fed465f45fdcf8f63f2119eb8e8b201e32
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "76732671"
---
# <a name="shape-of-wordprocessingml-documents-c"></a>Kształt dokumentów WordprocessingML (C#)
W tym temacie przedstawiono kształt XML dokumentu WordprocessingML.  
  
## <a name="microsoft-office-formats"></a>Formaty pakietu Microsoft Office  
 Natywnym formatem pliku dla pakietu Microsoft Office system 2007 jest office Open XML (powszechnie nazywany Open XML). Open XML to format oparty na XML, który jest standardem Ecma i obecnie przechodzi proces standardów ISO-IEC. Język znaczników dla plików edytora tekstu w otwartym pliku XML nosi nazwę WordprocessingML. W tym samouczku użyto plików źródłowych WordprocessingML jako danych wejściowych dla przykładów.  
  
 Jeśli używasz pakietu Microsoft Office 2003, możesz zapisywać dokumenty w formacie Otwartych xml pakietu Office, jeśli zainstalowano pakiet zgodności pakietu Microsoft Office dla formatów plików programów Word, Excel i PowerPoint 2007.  
  
## <a name="the-shape-of-wordprocessingml-documents"></a>Kształt dokumentów wordprocessingML  
 Pierwszą rzeczą do zrozumienia jest kształt dokumentów WordprocessingML. Dokument WordprocessingML zawiera element treści `w:body`(o nazwie), który zawiera akapity dokumentu. Każdy akapit zawiera jeden lub `w:r`więcej przebiegów tekstu (o nazwie). Każdy uruchomiony tekst zawiera jeden lub `w:t`więcej fragmentów tekstu (o nazwie).  
  
 Poniżej znajduje się bardzo prosty dokument WordprocessingML:  
  
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
  
 Ten dokument zawiera dwa akapity. Oba zawierają jeden przebieg tekstu, a każdy przebieg tekstu zawiera pojedynczy fragment tekstu.  
  
 Najprostszym sposobem wyświetlenia zawartości dokumentu WordprocessingML w formularzu XML jest utworzenie go przy użyciu programu Microsoft Word, zapisanie go, a następnie uruchomienie następującego programu, który drukuje kod XML na konsoli.  
  
 W tym przykładzie użyto klas znalezionych w zestawie WindowsBase. Używa typów w <xref:System.IO.Packaging?displayProperty=nameWithType> obszarze nazw.  
  
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

- [Przedstawiamy otwierane formaty plików XML pakietu Office (2007)](https://docs.microsoft.com/previous-versions/office/developer/office-2007/aa338205%28v=office.12%29)
- [Omówienie języka WordprocessingML](https://docs.microsoft.com/previous-versions/office/developer/office-2003/aa212812%28v=office.11%29)
- [Anatomia pliku WordProcessingML](http://officeopenxml.com/anatomyofOOXML.php)
- [Wprowadzenie do wordprocessingML](https://ericwhite.com/blog/introduction-to-wordprocessingml-series/)

## <a name="see-also"></a>Zobacz też

- [Samouczek: manipulowanie zawartością w dokumencie WordprocessingML (C#)](./shape-of-wordprocessingml-documents.md)
