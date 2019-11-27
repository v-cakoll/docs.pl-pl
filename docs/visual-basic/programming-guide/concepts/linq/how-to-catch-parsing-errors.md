---
title: 'Instrukcje: Przechwytywanie błędów analizy'
ms.date: 07/20/2015
ms.assetid: 22e9068e-ea58-447b-816e-cd1852c11787
ms.openlocfilehash: 14c4f76c5f10616f9346084cda276e2862b2b41d
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/22/2019
ms.locfileid: "74353343"
---
# <a name="how-to-catch-parsing-errors-visual-basic"></a><span data-ttu-id="98fc9-102">Instrukcje: Przechwytywanie błędów analizy (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="98fc9-102">How to: Catch Parsing Errors (Visual Basic)</span></span>
<span data-ttu-id="98fc9-103">W tym temacie pokazano, jak wykryć źle sformułowany lub nieprawidłowy kod XML.</span><span class="sxs-lookup"><span data-stu-id="98fc9-103">This topic shows how to detect badly formed or invalid XML.</span></span>  
  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] <span data-ttu-id="98fc9-104">jest implementowana przy użyciu <xref:System.Xml.XmlReader>.</span><span class="sxs-lookup"><span data-stu-id="98fc9-104">is implemented using <xref:System.Xml.XmlReader>.</span></span> <span data-ttu-id="98fc9-105">Jeśli nieprawidłowo sformułowany lub nieprawidłowy kod XML jest przenoszona do [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)], bazowa Klasa <xref:System.Xml.XmlReader> zgłosi wyjątek.</span><span class="sxs-lookup"><span data-stu-id="98fc9-105">If badly formed or invalid XML is passed to [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)], the underlying <xref:System.Xml.XmlReader> class will throw an exception.</span></span> <span data-ttu-id="98fc9-106">Różne metody, które analizują XML, takie jak <xref:System.Xml.Linq.XElement.Parse%2A?displayProperty=nameWithType>, nie przechwytują wyjątku; wyjątek może następnie być przechwytywany przez aplikację.</span><span class="sxs-lookup"><span data-stu-id="98fc9-106">The various methods that parse XML, such as <xref:System.Xml.Linq.XElement.Parse%2A?displayProperty=nameWithType>, do not catch the exception; the exception can then be caught by your application.</span></span>  
  
 <span data-ttu-id="98fc9-107">Należy zauważyć, że nie można uzyskać błędów analizy, jeśli używasz literałów XML.</span><span class="sxs-lookup"><span data-stu-id="98fc9-107">Note that you cannot get parse errors if you use XML literals.</span></span> <span data-ttu-id="98fc9-108">Kompilator Visual Basic przechwytuje błędy źle uformowanego lub nieprawidłowego kodu XML.</span><span class="sxs-lookup"><span data-stu-id="98fc9-108">The Visual Basic compiler will catch errors of badly formed or invalid XML.</span></span>  
  
## <a name="example"></a><span data-ttu-id="98fc9-109">Przykład</span><span class="sxs-lookup"><span data-stu-id="98fc9-109">Example</span></span>  
 <span data-ttu-id="98fc9-110">Następujący kod próbuje przeanalizować nieprawidłowego kodu XML:</span><span class="sxs-lookup"><span data-stu-id="98fc9-110">The following code tries to parse invalid XML:</span></span>  
  
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
  
 <span data-ttu-id="98fc9-111">Po uruchomieniu tego kodu zgłasza następujący wyjątek:</span><span class="sxs-lookup"><span data-stu-id="98fc9-111">When you run this code, it throws the following exception:</span></span>  
  
```console  
The 'Contacts' start tag on line 1 does not match the end tag of 'Contcts'. Line 5, position 13.  
```  
  
 <span data-ttu-id="98fc9-112">Informacje o wyjątkach, w których można oczekiwać, że <xref:System.Xml.Linq.XElement.Parse%2A?displayProperty=nameWithType>, <xref:System.Xml.Linq.XDocument.Parse%2A?displayProperty=nameWithType>, <xref:System.Xml.Linq.XElement.Load%2A?displayProperty=nameWithType>i <xref:System.Xml.Linq.XDocument.Load%2A?displayProperty=nameWithType> metod zgłaszania, zapoznaj się z dokumentacją <xref:System.Xml.XmlReader>.</span><span class="sxs-lookup"><span data-stu-id="98fc9-112">For information about the exceptions that you can expect the <xref:System.Xml.Linq.XElement.Parse%2A?displayProperty=nameWithType>, <xref:System.Xml.Linq.XDocument.Parse%2A?displayProperty=nameWithType>, <xref:System.Xml.Linq.XElement.Load%2A?displayProperty=nameWithType>, and <xref:System.Xml.Linq.XDocument.Load%2A?displayProperty=nameWithType> methods to throw, see the <xref:System.Xml.XmlReader> documentation.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="98fc9-113">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="98fc9-113">See also</span></span>

- [<span data-ttu-id="98fc9-114">Analizowanie kodu XML (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="98fc9-114">Parsing XML (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/parsing-xml.md)
