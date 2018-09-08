---
title: Wczytywanie dokumentu XML do modelu DOM
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
ms.assetid: a4fb291f-5630-49ba-a49a-5b66c3b71e49
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 9031f5df0d0f48dc2844cdfd0654ee4ab876cc22
ms.sourcegitcommit: c7f3e2e9d6ead6cc3acd0d66b10a251d0c66e59d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/08/2018
ms.locfileid: "44209540"
---
# <a name="reading-an-xml-document-into-the-dom"></a>Wczytywanie dokumentu XML do modelu DOM
Informacje o XML jest do odczytu do pamięci z różnych formatów. Może być odczytany z ciągu, strumienia, adres URL, czytnika tekstu lub klasę pochodną <xref:System.Xml.XmlReader>.  
  
 <xref:System.Xml.XmlDocument.Load%2A> Metoda udostępnia dokument do pamięci i ma skonfigurowane przeciążone metody dostępne dla pobierają dane z każdego z różnych formatów. Istnieje również <xref:System.Xml.XmlDocument.LoadXml%2A> metodę, która odczytuje XML z ciągu.  
  
 Różne <xref:System.Xml.XmlDocument.Load%2A> metody wpływają na węzły, które są tworzone po załadowaniu XML Document Object Model (DOM). W poniższej tabeli przedstawiono różnice między część <xref:System.Xml.XmlDocument.Load%2A> metody i tematy, które ich dotyczą.  
  
|Temat|Temat|  
|-------------|-----------|  
|Tworzenie węzły odstępów|Obiekt używany do załadowania modelu DOM ma to wpływu na biały i istotnych białych węzłów generowane w modelu DOM. Aby uzyskać więcej informacji, zobacz [biały znak i znaczące biały znak obsługi podczas ładowania modelu DOM](../../../../docs/standard/data/xml/white-space-and-significant-white-space-handling-when-loading-the-dom.md).|  
|Podczas ładowania XML, zaczynając od określonego węzła lub ładowania całego dokumentu XML|Za pomocą <xref:System.Xml.XmlDocument.Load%2A?displayProperty=nameWithType> danych metody mogą być ładowane z określonego węzła do modelu DOM. Aby uzyskać więcej informacji, zobacz [ładowanie danych z czytnika](../../../../docs/standard/data/xml/load-data-from-a-reader.md).|  
|Walidacja kodu XML w postaci, w jakiej jest ładowany.|Mogą być sprawdzone dane XML załadowane do modelu DOM, ponieważ jest on ładowany. Jest to realizowane przy użyciu sprawdzania poprawności <xref:System.Xml.XmlReader>. Aby uzyskać więcej informacji na temat sprawdzania poprawności XML, ponieważ jest on ładowany zobacz [Weryfikowanie dokumentu XML w modelu DOM](../../../../docs/standard/data/xml/validating-an-xml-document-in-the-dom.md).|  
  
 W poniższym przykładzie pokazano XML ładowany z <xref:System.Xml.XmlDocument.LoadXml%2A> metody i danych, następnie zapisywane do pliku tekstowego o nazwie `data.xml`.  
  
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
