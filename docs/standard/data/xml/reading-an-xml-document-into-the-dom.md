---
title: Wczytywanie dokumentu XML do modelu DOM
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
ms.assetid: a4fb291f-5630-49ba-a49a-5b66c3b71e49
ms.openlocfilehash: 2e61a9ed1a1ccaa2f9f1543efa1d33c3fcf00061
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73130829"
---
# <a name="reading-an-xml-document-into-the-dom"></a>Wczytywanie dokumentu XML do modelu DOM
Informacje XML są odczytywane w pamięci z różnych formatów. Można go odczytać z ciągu, strumienia, adresu URL, czytnika tekstu lub klasy pochodnej <xref:System.Xml.XmlReader>.  
  
 Metoda <xref:System.Xml.XmlDocument.Load%2A> przenosi dokument do pamięci i ma dostępne przeciążone metody, aby pobrać dane z każdego z różnych formatów. Istnieje również Metoda <xref:System.Xml.XmlDocument.LoadXml%2A>, która odczytuje dane XML z ciągu.  
  
 Różne metody <xref:System.Xml.XmlDocument.Load%2A> mają wpływ na to, które węzły są tworzone podczas ładowania Document Object Model XML (DOM). W poniższej tabeli wymieniono różnice między niektórymi metodami <xref:System.Xml.XmlDocument.Load%2A> i tematami.  
  
|Temat|Temat|  
|-------------|-----------|  
|Tworzenie białych węzłów spacji|Obiekt użyty do załadowania modelu DOM ma wpływ na białe miejsce i znaczące węzły odstępu wygenerowane w modelu DOM. Aby uzyskać więcej informacji, zobacz [biały znak i znaczący biały znak podczas ładowania modelu dom](../../../../docs/standard/data/xml/white-space-and-significant-white-space-handling-when-loading-the-dom.md).|  
|Ładowanie kodu XML począwszy od określonego węzła lub ładowanie całego dokumentu XML|Przy użyciu danych metody <xref:System.Xml.XmlDocument.Load%2A?displayProperty=nameWithType> można ładować z określonego węzła do modelu DOM. Aby uzyskać więcej informacji, zobacz [ładowanie danych z czytnika](../../../../docs/standard/data/xml/load-data-from-a-reader.md).|  
|Sprawdzanie poprawności kodu XML w trakcie jego ładowania|Dane XML ładowane do modelu DOM mogą być zweryfikowane w miarę ich ładowania. Jest to realizowane przy użyciu walidacji <xref:System.Xml.XmlReader>. Aby uzyskać więcej informacji na temat walidacji kodu XML w trakcie jego ładowania, zobacz [Walidacja dokumentu XML w modelu dom](../../../../docs/standard/data/xml/validating-an-xml-document-in-the-dom.md).|  
  
 Poniższy przykład pokazuje, że kod XML jest ładowany przy użyciu metody <xref:System.Xml.XmlDocument.LoadXml%2A>, a dane są następnie zapisywane w pliku tekstowym o nazwie `data.xml`.  
  
```vb  
Imports System  
Imports System.IO  
Imports System.Xml  
  
Public Class Sample  
  
    Public Shared Sub Main()  
        ' Create the XmlDocument.  
        Dim doc As New XmlDocument()  
        doc.LoadXml(("<book genre='novel' ISBN='1-861001-57-5'>" & _  
                    "<title>Pride And Prejudice</title>" & _  
                    "</book>"))  
        ' Save the document to a file.  
        doc.Save("data.xml")  
    End Sub 'Main  
End Class 'Sample  
```  
  
```csharp  
using System;  
using System.IO;  
using System.Xml;  
  
public class Sample  
{  
    public static void Main()  
    {  
        // Create the XmlDocument.  
        XmlDocument doc = new XmlDocument();  
        doc.LoadXml("<book genre='novel' ISBN='1-861001-57-5'>" +  
                    "<title>Pride And Prejudice</title>" +  
                    "</book>");  
  
        // Save the document to a file.  
        doc.Save("data.xml");  
    }  
}  
```  
  
## <a name="see-also"></a>Zobacz także

- [Model DOM (XML Document Object Model)](../../../../docs/standard/data/xml/xml-document-object-model-dom.md)
