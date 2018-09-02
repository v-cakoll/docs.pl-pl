---
title: 'Porady: Przechwytywanie błędów (Visual Basic) analizy'
ms.date: 07/20/2015
ms.assetid: 22e9068e-ea58-447b-816e-cd1852c11787
ms.openlocfilehash: aa72b914d4640410a4d47ba49e774dcee31a54c0
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/01/2018
ms.locfileid: "43406551"
---
# <a name="how-to-catch-parsing-errors-visual-basic"></a>Porady: Przechwytywanie błędów (Visual Basic) analizy
W tym temacie pokazano, jak wykryć XML źle sformułowana lub jest nieprawidłowy.  
  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] jest implementowana przy użyciu <xref:System.Xml.XmlReader>. Jeśli źle sformułowany lub nieprawidłowy XML jest przekazywany do [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)], podstawowe <xref:System.Xml.XmlReader> klasy spowoduje zgłoszenie wyjątku. Różne metody analizy XML, takie jak <xref:System.Xml.Linq.XElement.Parse%2A?displayProperty=nameWithType>, nie Przechwytuj wyjątek; wyjątek, następnie może zostać przechwycony przez aplikację.  
  
 Błędy analizy należy pamiętać, że nie można uzyskać, korzystając z literałów XML. Kompilator Visual Basic będzie przechwytywać błędy XML źle sformułowana lub jest nieprawidłowy.  
  
## <a name="example"></a>Przykład  
 Poniższy kod próbuje przeanalizować nieprawidłowy kod XML:  
  
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
  
 Po uruchomieniu tego kodu, zgłasza następujący wyjątek:  
  
```  
The 'Contacts' start tag on line 1 does not match the end tag of 'Contcts'. Line 5, position 13.  
```  
  
 Dla informacji o wyjątkach, których można oczekiwać, że <xref:System.Xml.Linq.XElement.Parse%2A?displayProperty=nameWithType>, <xref:System.Xml.Linq.XDocument.Parse%2A?displayProperty=nameWithType>, <xref:System.Xml.Linq.XElement.Load%2A?displayProperty=nameWithType>, i <xref:System.Xml.Linq.XDocument.Load%2A?displayProperty=nameWithType> metody throw, zobacz <xref:System.Xml.XmlReader> dokumentacji.  
  
## <a name="see-also"></a>Zobacz też  
 [Analizowanie kodu XML (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/parsing-xml.md)
