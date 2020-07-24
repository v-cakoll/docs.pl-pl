---
title: Jak przechwytywać błędy analizy (C#)
description: Ten LINQ to XML przykład w języku C# wykrywa nieprawidłowo sformułowany lub nieprawidłowy kod XML. LINQ to XML używa elementu XmlReader, który zgłasza wyjątek dla nieprawidłowo sformułowanego lub nieprawidłowego kodu XML.
ms.date: 07/20/2015
ms.assetid: bfb612d4-5605-48ef-8c93-915cf9d5dcfb
ms.openlocfilehash: 0a891097322ef6acce062ea927692b01cc425e6c
ms.sourcegitcommit: 04022ca5d00b2074e1b1ffdbd76bec4950697c4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/23/2020
ms.locfileid: "87105404"
---
# <a name="how-to-catch-parsing-errors-c"></a>Jak przechwytywać błędy analizy (C#)
W tym temacie pokazano, jak wykryć źle sformułowany lub nieprawidłowy kod XML.  
  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]jest zaimplementowany przy użyciu <xref:System.Xml.XmlReader> . Jeśli nieprawidłowo sformułowany lub nieprawidłowy kod XML jest przenoszona do [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] , <xref:System.Xml.XmlReader> Klasa bazowa zgłosi wyjątek. Różne metody, które analizują XML, takie jak <xref:System.Xml.Linq.XElement.Parse%2A?displayProperty=nameWithType> , nie przechwytują wyjątku; wyjątek może zostać przechwycony przez aplikację.  
  
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
  
 Informacje o wyjątkach, w których można oczekiwać, <xref:System.Xml.Linq.XElement.Parse%2A?displayProperty=nameWithType> , <xref:System.Xml.Linq.XDocument.Parse%2A?displayProperty=nameWithType> <xref:System.Xml.Linq.XElement.Load%2A?displayProperty=nameWithType> , i metod zgłaszania <xref:System.Xml.Linq.XDocument.Load%2A?displayProperty=nameWithType> , znajdują się w <xref:System.Xml.XmlReader> dokumentacji.  
  