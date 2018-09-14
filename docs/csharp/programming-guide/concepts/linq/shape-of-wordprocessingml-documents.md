---
title: Kształt dokumentów WordprocessingML (C#)
ms.date: 07/20/2015
ms.assetid: 3791b5e0-c502-469b-bb75-a7bf6fdd0a94
ms.openlocfilehash: aeb047f23f60ba6951950a85a6e2ef57fcbd9dda
ms.sourcegitcommit: 6eac9a01ff5d70c6d18460324c016a3612c5e268
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/14/2018
ms.locfileid: "45597313"
---
# <a name="shape-of-wordprocessingml-documents-c"></a>Kształt dokumentów WordprocessingML (C#)
W tym temacie przedstawiono kształt XML w dokumencie WordprocessingML.  
  
## <a name="microsoft-office-formats"></a>Formaty pakietu Microsoft Office  
 Format pliku natywnych dla systemu 2007 Microsoft Office to Office Open XML (często nazywany Open XML). Otwieranie pliku XML jest oparty na składni XML format standard Ecma i jest obecnie wykonywana przez proces normy ISO IEC. Język znaczników dla plików przetwarzania tekstu w Open XML nosi nazwę WordprocessingML. Ten samouczek używa plików źródłowych WordprocessingML jako dane wejściowe dla przykładów.  
  
 Jeśli używasz programu Microsoft Office 2003 można zapisywać dokumenty w format Office Open XML, jeśli zainstalowano pakiet zgodności programu Microsoft Office Word, Excel i PowerPoint 2007 File Formats.  
  
## <a name="the-shape-of-wordprocessingml-documents"></a>Kształt dokumentów WordprocessingML  
 Pierwszą rzeczą, aby dowiedzieć się, jest kształt dokumentów WordprocessingML. Dokument WordprocessingML zawiera body element (o nazwie `w:body`) zawierający akapitów dokumentu. Każdego akapitu zawiera co najmniej jeden przebieg tekstu (o nazwie `w:r`). Każdego tekstu, uruchom zawiera jeden lub kilka fragmentów tekstu (o nazwie `w:t`).  
  
 Poniżej przedstawiono bardzo prosty dokumentu WordprocessingML:  
  
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
  
 Ten dokument zawiera dwa akapitach. Zawierają jeden tekst, uruchom, a każdy tekst Uruchom zawiera element jeden tekst.  
  
 Najprostszym sposobem wyświetlenia zawartości dokumentu WordprocessingML w postaci XML jest ją utworzyć za pomocą programu Microsoft Word, zapisz go, a następnie uruchom następujący program, który wyświetla kod XML do konsoli.  
  
 W tym przykładzie użyto klasy znalezione w zestawie WindowsBase. Używa typów w <xref:System.IO.Packaging?displayProperty=nameWithType> przestrzeni nazw.  
  
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
 [Omówienie WordprocessingML](https://msdn.microsoft.com/library/aa212812(office.11).aspx)  
 [Anatomia pliku WordProcessingML](http://officeopenxml.com/anatomyofOOXML.php)  
 [Wprowadzenie do WordprocessingML](http://ericwhite.com/blog/introduction-to-wordprocessingml-series/)  
 [Office 2003: XML odwołanie schematów strony plików do pobrania](https://www.microsoft.com/en-us/download/details.aspx?id=101)  
  
## <a name="see-also"></a>Zobacz też

- [Samouczek: Manipulowanie zawartością w dokumencie WordprocessingML (C#)](../../../../csharp/programming-guide/concepts/linq/tutorial-manipulating-content-in-a-wordprocessingml-document.md)
