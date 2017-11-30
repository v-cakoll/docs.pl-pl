---
title: Odczytywanie dokumentu XML do modelu DOM
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: a4fb291f-5630-49ba-a49a-5b66c3b71e49
caps.latest.revision: "3"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: b8844705b492574443ff4f37de33ccaf1f5fedd7
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="reading-an-xml-document-into-the-dom"></a>Odczytywanie dokumentu XML do modelu DOM
Informacje o XML jest do odczytu do pamięci z różnych formatach. Mogą być odczytywane z ciągiem, strumienia, adres URL, czytnika tekstu lub klasy pochodzącej od <xref:System.Xml.XmlReader>.  
  
 <xref:System.Xml.XmlDocument.Load%2A> Metoda powoduje przeniesienie dokumentu do pamięci i ma skonfigurowane przeciążone metody podjąć danych z każdej z różnych formatach. Istnieje również <xref:System.Xml.XmlDocument.LoadXml%2A> metoda odczytuje z ciągu XML.  
  
 Różne <xref:System.Xml.XmlDocument.Load%2A> metody wpływają na węzły, które są tworzone po załadowaniu XML modelu DOM (Document Object). W poniższej tabeli przedstawiono różnice między niektóre <xref:System.Xml.XmlDocument.Load%2A> metody i tematy, które rozwiązują je.  
  
|Temat|Temat|  
|-------------|-----------|  
|Tworzenie węzłów biały znak|Obiekt używany do załadowania modelu DOM ma wpływ na biały znak i węzły znaczący biały znak wygenerowanych w modelu DOM. Aby uzyskać więcej informacji, zobacz [biały znak i znaczący biały znak obsługi podczas ładowania modelu DOM](../../../../docs/standard/data/xml/white-space-and-significant-white-space-handling-when-loading-the-dom.md).|  
|Podczas ładowania XML, zaczynając od określonego węzła lub ładowanie całego dokumentu XML|Przy użyciu <xref:System.Xml.XmlDocument.Load%2A?displayProperty=nameWithType> danych metody mogą być ładowane z określonego węzła do modelu DOM. Aby uzyskać więcej informacji, zobacz [ładowanie danych z czytnika](../../../../docs/standard/data/xml/load-data-from-a-reader.md).|  
|Sprawdzanie poprawności kodu XML, ponieważ jest załadowana.|Mogą być sprawdzone danych XML załadowane do modelu DOM, ponieważ jest on załadowany. Odbywa się przy użyciu sprawdzania poprawności <xref:System.Xml.XmlReader>. Aby uzyskać więcej informacji na temat weryfikowania XML, ponieważ jest on załadowany, zobacz [sprawdzania poprawności dokumentu XML w modelu DOM](../../../../docs/standard/data/xml/validating-an-xml-document-in-the-dom.md).|  
  
 W poniższym przykładzie przedstawiono XML ładowany z <xref:System.Xml.XmlDocument.LoadXml%2A> — metoda i dane zapisane następnie w pliku tekstowym o nazwie `data.xml`.  
  
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
  
## <a name="see-also"></a>Zobacz też  
 [Modelu obiektu dokumentu XML modelu DOM)](../../../../docs/standard/data/xml/xml-document-object-model-dom.md)
