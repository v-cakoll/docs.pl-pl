---
title: "Porady: Catch analizowanie błędów (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 22e9068e-ea58-447b-816e-cd1852c11787
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 82b7c51aa8d0f9f64094211c56875e6595607c00
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="how-to-catch-parsing-errors-visual-basic"></a>Porady: Catch analizowanie błędów (Visual Basic)
W tym temacie przedstawiono sposób wykrywania źle sformułowany lub nieprawidłowy XML.  
  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]jest implementowane za pomocą <xref:System.Xml.XmlReader>. Jeśli źle sformułowany lub nieprawidłowy kod XML jest przekazany do [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)], podstawowa <xref:System.Xml.XmlReader> klasy spowoduje zgłoszenie wyjątku. Różne metody analizy kodu XML, takich jak <xref:System.Xml.Linq.XElement.Parse%2A?displayProperty=nameWithType>, nie Przechwytuj wyjątków; wyjątek może być następnie zgłoszony przez aplikację.  
  
 Należy pamiętać, że nie można przeanalizować błędy użycie literałów XML. Kompilator Visual Basic będzie przechwytywać błędy źle sformułowany lub nieprawidłowy XML.  
  
## <a name="example"></a>Przykład  
 Poniższy kod próbuje nieprawidłowe dane XML analizy:  
  
```vb  
Try  
    Dim contacts As XElement = XElement.Parse("<Contacts>" & vbCrLf & _  
        "    <Contact>" & vbCrLf & _  
        "        <Name>Jim Wilson</Name>" & vbCrLf & _  
        "    </Contact>" & vbCrLf & _  
        "</Contcts>")  
  
    Console.WriteLine(contacts)  
Catch e As System.Xml.XmlException  
    Console.WriteLine(e.Message)  
End Try  
```  
  
 Po uruchomieniu tego kodu zwraca następujący wyjątek:  
  
```  
The 'Contacts' start tag on line 1 does not match the end tag of 'Contcts'. Line 5, position 13.  
```  
  
 Aby uzyskać informacje dotyczące wyjątków, które można oczekiwać, że <xref:System.Xml.Linq.XElement.Parse%2A?displayProperty=nameWithType>, <xref:System.Xml.Linq.XDocument.Parse%2A?displayProperty=nameWithType>, <xref:System.Xml.Linq.XElement.Load%2A?displayProperty=nameWithType>, i <xref:System.Xml.Linq.XDocument.Load%2A?displayProperty=nameWithType> metody ma zostać zgłoszony, zobacz <xref:System.Xml.XmlReader> dokumentacji.  
  
## <a name="see-also"></a>Zobacz też  
 [Analiza kodu XML (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/parsing-xml.md)
