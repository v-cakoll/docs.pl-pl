---
title: "Porady: Catch analizowanie błędów (C#)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-csharp
ms.topic: article
ms.assetid: bfb612d4-5605-48ef-8c93-915cf9d5dcfb
caps.latest.revision: "3"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: e541a004833ccd2aaecfd4ea13652b03a1270186
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="how-to-catch-parsing-errors-c"></a>Porady: Catch analizowanie błędów (C#)
W tym temacie przedstawiono sposób wykrywania źle sformułowany lub nieprawidłowy XML.  
  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]jest implementowane za pomocą <xref:System.Xml.XmlReader>. Jeśli źle sformułowany lub nieprawidłowy kod XML jest przekazany do [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)], podstawowa <xref:System.Xml.XmlReader> klasy spowoduje zgłoszenie wyjątku. Różne metody analizy kodu XML, takich jak <xref:System.Xml.Linq.XElement.Parse%2A?displayProperty=nameWithType>, nie Przechwytuj wyjątków; wyjątek może być następnie zgłoszony przez aplikację.  
  
## <a name="example"></a>Przykład  
 Poniższy kod próbuje nieprawidłowe dane XML analizy:  
  
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
  
 Po uruchomieniu tego kodu zwraca następujący wyjątek:  
  
```  
The 'Contacts' start tag on line 1 does not match the end tag of 'Contcts'. Line 5, position 13.  
```  
  
 Aby uzyskać informacje dotyczące wyjątków, które można oczekiwać, że <xref:System.Xml.Linq.XElement.Parse%2A?displayProperty=nameWithType>, <xref:System.Xml.Linq.XDocument.Parse%2A?displayProperty=nameWithType>, <xref:System.Xml.Linq.XElement.Load%2A?displayProperty=nameWithType>, i <xref:System.Xml.Linq.XDocument.Load%2A?displayProperty=nameWithType> metody ma zostać zgłoszony, zobacz <xref:System.Xml.XmlReader> dokumentacji.  
  
## <a name="see-also"></a>Zobacz też  
 [Analiza kodu XML (C#)](../../../../csharp/programming-guide/concepts/linq/parsing-xml.md)
