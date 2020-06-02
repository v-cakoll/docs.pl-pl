---
title: Wczytywanie dokumentu XML do modelu DOM
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
ms.assetid: a4fb291f-5630-49ba-a49a-5b66c3b71e49
ms.openlocfilehash: 02338d72f51d3a7507c0dfa030383399b9e213f6
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/02/2020
ms.locfileid: "84282405"
---
# <a name="reading-an-xml-document-into-the-dom"></a>Wczytywanie dokumentu XML do modelu DOM
Informacje XML są odczytywane w pamięci z różnych formatów. Można go odczytać z ciągu, strumienia, adresu URL, czytnika tekstu lub klasy pochodnej <xref:System.Xml.XmlReader> .  
  
 <xref:System.Xml.XmlDocument.Load%2A>Metoda przenosi dokument do pamięci i ma dostępne przeciążone metody, aby pobrać dane z każdego z różnych formatów. Istnieje również <xref:System.Xml.XmlDocument.LoadXml%2A> Metoda, która odczytuje dane XML z ciągu.  
  
 Różne <xref:System.Xml.XmlDocument.Load%2A> metody mają wpływ na to, które węzły są tworzone podczas ładowania Document Object Model XML (dom). W poniższej tabeli wymieniono różnice między niektórymi <xref:System.Xml.XmlDocument.Load%2A> metodami i tematami.  
  
|Podmiot|Temat|  
|-------------|-----------|  
|Tworzenie białych węzłów spacji|Obiekt użyty do załadowania modelu DOM ma wpływ na białe miejsce i znaczące węzły odstępu wygenerowane w modelu DOM. Aby uzyskać więcej informacji, zobacz [biały znak i znaczący biały znak podczas ładowania modelu dom](white-space-and-significant-white-space-handling-when-loading-the-dom.md).|  
|Ładowanie kodu XML począwszy od określonego węzła lub ładowanie całego dokumentu XML|Za pomocą <xref:System.Xml.XmlDocument.Load%2A?displayProperty=nameWithType> danych metody można ładować z określonego węzła do modelu DOM. Aby uzyskać więcej informacji, zobacz [ładowanie danych z czytnika](load-data-from-a-reader.md).|  
|Sprawdzanie poprawności kodu XML w trakcie jego ładowania|Dane XML ładowane do modelu DOM mogą być zweryfikowane w miarę ich ładowania. Jest to realizowane przy użyciu walidacji <xref:System.Xml.XmlReader> . Aby uzyskać więcej informacji na temat walidacji kodu XML w trakcie jego ładowania, zobacz [Walidacja dokumentu XML w modelu dom](validating-an-xml-document-in-the-dom.md).|  
  
 Poniższy przykład pokazuje, że kod XML jest ładowany przy użyciu <xref:System.Xml.XmlDocument.LoadXml%2A> metody, a dane są następnie zapisywane w pliku tekstowym o nazwie `data.xml` .  
  
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

- [XML Document Object Model (DOM)](xml-document-object-model-dom.md)
