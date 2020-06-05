---
title: 'Instrukcje: przechwytywanie błędów analizy'
ms.date: 07/20/2015
ms.assetid: 22e9068e-ea58-447b-816e-cd1852c11787
ms.openlocfilehash: c0b46d7df270dd6f081a0c736b6978088cfbd9c0
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84375151"
---
# <a name="how-to-catch-parsing-errors-visual-basic"></a>Instrukcje: Przechwytywanie błędów analizy (Visual Basic)
W tym temacie pokazano, jak wykryć źle sformułowany lub nieprawidłowy kod XML.  
  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]jest zaimplementowany przy użyciu <xref:System.Xml.XmlReader> . Jeśli nieprawidłowo sformułowany lub nieprawidłowy kod XML jest przenoszona do [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] , <xref:System.Xml.XmlReader> Klasa bazowa zgłosi wyjątek. Różne metody, które analizują XML, takie jak <xref:System.Xml.Linq.XElement.Parse%2A?displayProperty=nameWithType> , nie przechwytują wyjątku; wyjątek może zostać przechwycony przez aplikację.  
  
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
  
 Informacje o wyjątkach, w których można oczekiwać, <xref:System.Xml.Linq.XElement.Parse%2A?displayProperty=nameWithType> , <xref:System.Xml.Linq.XDocument.Parse%2A?displayProperty=nameWithType> <xref:System.Xml.Linq.XElement.Load%2A?displayProperty=nameWithType> , i metod zgłaszania <xref:System.Xml.Linq.XDocument.Load%2A?displayProperty=nameWithType> , znajdują się w <xref:System.Xml.XmlReader> dokumentacji.  
  
## <a name="see-also"></a>Zobacz też

- [Analizowanie kodu XML (Visual Basic)](parsing-xml.md)
