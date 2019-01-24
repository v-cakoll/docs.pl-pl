---
title: 'Instrukcje: Przechwytywanie błędów analizy (C#)'
ms.date: 07/20/2015
ms.assetid: bfb612d4-5605-48ef-8c93-915cf9d5dcfb
ms.openlocfilehash: 2f56ca48278f9ad8b38f8564f54a379cc09f94ef
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54515865"
---
# <a name="how-to-catch-parsing-errors-c"></a>Instrukcje: Przechwytywanie błędów analizy (C#)
W tym temacie pokazano, jak wykryć XML źle sformułowana lub jest nieprawidłowy.  
  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] jest implementowana przy użyciu <xref:System.Xml.XmlReader>. Jeśli źle sformułowany lub nieprawidłowy XML jest przekazywany do [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)], podstawowe <xref:System.Xml.XmlReader> klasy spowoduje zgłoszenie wyjątku. Różne metody analizy XML, takie jak <xref:System.Xml.Linq.XElement.Parse%2A?displayProperty=nameWithType>, nie Przechwytuj wyjątek; wyjątek, następnie może zostać przechwycony przez aplikację.  
  
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
  
 Po uruchomieniu tego kodu, zgłasza następujący wyjątek:  
  
```  
The 'Contacts' start tag on line 1 does not match the end tag of 'Contcts'. Line 5, position 13.  
```  
  
 Dla informacji o wyjątkach, których można oczekiwać, że <xref:System.Xml.Linq.XElement.Parse%2A?displayProperty=nameWithType>, <xref:System.Xml.Linq.XDocument.Parse%2A?displayProperty=nameWithType>, <xref:System.Xml.Linq.XElement.Load%2A?displayProperty=nameWithType>, i <xref:System.Xml.Linq.XDocument.Load%2A?displayProperty=nameWithType> metody throw, zobacz <xref:System.Xml.XmlReader> dokumentacji.  
  
## <a name="see-also"></a>Zobacz także

- [Analizowanie kodu XML (C#)](../../../../csharp/programming-guide/concepts/linq/parsing-xml.md)
