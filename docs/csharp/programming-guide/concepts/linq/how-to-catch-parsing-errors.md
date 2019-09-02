---
title: 'Instrukcje: Błędy analizy catch (C#)'
ms.date: 07/20/2015
ms.assetid: bfb612d4-5605-48ef-8c93-915cf9d5dcfb
ms.openlocfilehash: 4195ff50d1b4d23cd9eb07fc27f20861d1504672
ms.sourcegitcommit: 2d792961ed48f235cf413d6031576373c3050918
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/31/2019
ms.locfileid: "70204146"
---
# <a name="how-to-catch-parsing-errors-c"></a>Instrukcje: Błędy analizy catch (C#)
W tym temacie pokazano, jak wykryć źle sformułowany lub nieprawidłowy kod XML.  
  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]jest zaimplementowany przy <xref:System.Xml.XmlReader>użyciu. Jeśli nieprawidłowo sformułowany lub nieprawidłowy kod XML jest [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]przenoszona do <xref:System.Xml.XmlReader> , Klasa bazowa zgłosi wyjątek. Różne metody, które analizują XML, takie <xref:System.Xml.Linq.XElement.Parse%2A?displayProperty=nameWithType>jak, nie przechwytują wyjątku; wyjątek może zostać przechwycony przez aplikację.  
  
## <a name="example"></a>Przykład  
 Następujący kod próbuje przeanalizować nieprawidłowego kodu XML:  
  
```csharp  
try {  
    XElement contacts = XElement.Parse(  
        @"<Contacts>  
            <Contact>  
                <Name>Jim Wilson</Name>  
            </Contact>  
          </Contcts>");  
  
    Console.WriteLine(contacts);  
}  
catch (System.Xml.XmlException e)  
{  
    Console.WriteLine(e.Message);  
}  
```  
  
 Po uruchomieniu tego kodu zgłasza następujący wyjątek:  
  
```console  
The 'Contacts' start tag on line 1 does not match the end tag of 'Contcts'. Line 5, position 13.  
```  
  
 Informacje o <xref:System.Xml.Linq.XElement.Parse%2A?displayProperty=nameWithType>wyjątkach <xref:System.Xml.Linq.XDocument.Load%2A?displayProperty=nameWithType> <xref:System.Xml.XmlReader> , <xref:System.Xml.Linq.XDocument.Parse%2A?displayProperty=nameWithType>wktórych można oczekiwać,, ,imetodzgłaszania,znajdująsięwdokumentacji.<xref:System.Xml.Linq.XElement.Load%2A?displayProperty=nameWithType>  
  