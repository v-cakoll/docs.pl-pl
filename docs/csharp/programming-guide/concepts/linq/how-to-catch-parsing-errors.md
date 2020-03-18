---
title: Jak wychwycić błędy analizy (C#)
ms.date: 07/20/2015
ms.assetid: bfb612d4-5605-48ef-8c93-915cf9d5dcfb
ms.openlocfilehash: 1a05037892061dec85e7837472e8ec13e076724b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "74141479"
---
# <a name="how-to-catch-parsing-errors-c"></a>Jak wychwycić błędy analizy (C#)
W tym temacie pokazano, jak wykryć źle utworzony lub nieprawidłowy kod XML.  
  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]jest realizowany <xref:System.Xml.XmlReader>za pomocą . Jeśli źle utworzone lub nieprawidłowy Kod [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]XML jest <xref:System.Xml.XmlReader> przekazywany do , podstawowa klasa zgłosi wyjątek. Różne metody, które analizują XML, takie jak <xref:System.Xml.Linq.XElement.Parse%2A?displayProperty=nameWithType>, nie przechwycić wyjątek; wyjątek może zostać przechwycony przez aplikację.  
  
## <a name="example"></a>Przykład  
 Poniższy kod próbuje przeanalizować nieprawidłowy kod XML:  
  
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
  
 Aby uzyskać informacje na temat wyjątków, <xref:System.Xml.Linq.XElement.Load%2A?displayProperty=nameWithType>których <xref:System.Xml.Linq.XDocument.Load%2A?displayProperty=nameWithType> można się spodziewać <xref:System.Xml.XmlReader> <xref:System.Xml.Linq.XElement.Parse%2A?displayProperty=nameWithType>, <xref:System.Xml.Linq.XDocument.Parse%2A?displayProperty=nameWithType>, i metody, aby rzucić, zapoznaj się z dokumentacją.  
  