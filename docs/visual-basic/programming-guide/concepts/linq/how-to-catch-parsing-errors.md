---
title: 'Instrukcje: Błędy analizy catch (Visual Basic)'
ms.date: 07/20/2015
ms.assetid: 22e9068e-ea58-447b-816e-cd1852c11787
ms.openlocfilehash: a0c0749e8bc6d3fb1a71595778bfc5effaaf8533
ms.sourcegitcommit: da2dd2772fcf32b44eb18b1cbe8affd17b1753c9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/27/2019
ms.locfileid: "71352943"
---
# <a name="how-to-catch-parsing-errors-visual-basic"></a>Porady: Błędy analizy catch (Visual Basic)
W tym temacie pokazano, jak wykryć źle sformułowany lub nieprawidłowy kod XML.  
  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] jest implementowana przy użyciu <xref:System.Xml.XmlReader>. Jeśli nieprawidłowo sformułowany lub nieprawidłowy kod XML jest przenoszona do [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)], bazowa Klasa <xref:System.Xml.XmlReader> zwróci wyjątek. Różne metody, które analizują XML, takie jak <xref:System.Xml.Linq.XElement.Parse%2A?displayProperty=nameWithType>, nie przechwytują wyjątku; wyjątek może następnie być przechwytywany przez aplikację.  
  
 Należy zauważyć, że nie można uzyskać błędów analizy, jeśli używasz literałów XML. Kompilator Visual Basic przechwytuje błędy źle uformowanego lub nieprawidłowego kodu XML.  
  
## <a name="example"></a>Przykład  
 Następujący kod próbuje przeanalizować nieprawidłowego kodu XML:  
  
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
  
 Po uruchomieniu tego kodu zgłasza następujący wyjątek:  
  
```console  
The 'Contacts' start tag on line 1 does not match the end tag of 'Contcts'. Line 5, position 13.  
```  
  
 Aby uzyskać informacje o wyjątkach, które można zgłosić <xref:System.Xml.Linq.XElement.Parse%2A?displayProperty=nameWithType>, <xref:System.Xml.Linq.XDocument.Parse%2A?displayProperty=nameWithType>, <xref:System.Xml.Linq.XElement.Load%2A?displayProperty=nameWithType> i <xref:System.Xml.Linq.XDocument.Load%2A?displayProperty=nameWithType> metod zgłaszania, zobacz dokumentację dotyczącą <xref:System.Xml.XmlReader>.  
  
## <a name="see-also"></a>Zobacz także

- [Analizowanie kodu XML (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/parsing-xml.md)
