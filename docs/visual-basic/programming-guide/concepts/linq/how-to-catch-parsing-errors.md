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
# <a name="how-to-catch-parsing-errors-visual-basic"></a><span data-ttu-id="22ea9-102">Instrukcje: Przechwytywanie błędów analizy (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="22ea9-102">How to: Catch Parsing Errors (Visual Basic)</span></span>
<span data-ttu-id="22ea9-103">W tym temacie pokazano, jak wykryć źle sformułowany lub nieprawidłowy kod XML.</span><span class="sxs-lookup"><span data-stu-id="22ea9-103">This topic shows how to detect badly formed or invalid XML.</span></span>  
  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]<span data-ttu-id="22ea9-104">jest zaimplementowany przy użyciu <xref:System.Xml.XmlReader> .</span><span class="sxs-lookup"><span data-stu-id="22ea9-104">is implemented using <xref:System.Xml.XmlReader>.</span></span> <span data-ttu-id="22ea9-105">Jeśli nieprawidłowo sformułowany lub nieprawidłowy kod XML jest przenoszona do [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] , <xref:System.Xml.XmlReader> Klasa bazowa zgłosi wyjątek.</span><span class="sxs-lookup"><span data-stu-id="22ea9-105">If badly formed or invalid XML is passed to [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)], the underlying <xref:System.Xml.XmlReader> class will throw an exception.</span></span> <span data-ttu-id="22ea9-106">Różne metody, które analizują XML, takie jak <xref:System.Xml.Linq.XElement.Parse%2A?displayProperty=nameWithType> , nie przechwytują wyjątku; wyjątek może zostać przechwycony przez aplikację.</span><span class="sxs-lookup"><span data-stu-id="22ea9-106">The various methods that parse XML, such as <xref:System.Xml.Linq.XElement.Parse%2A?displayProperty=nameWithType>, do not catch the exception; the exception can then be caught by your application.</span></span>  
  
 <span data-ttu-id="22ea9-107">Należy zauważyć, że nie można uzyskać błędów analizy, jeśli używasz literałów XML.</span><span class="sxs-lookup"><span data-stu-id="22ea9-107">Note that you cannot get parse errors if you use XML literals.</span></span> <span data-ttu-id="22ea9-108">Kompilator Visual Basic przechwytuje błędy źle uformowanego lub nieprawidłowego kodu XML.</span><span class="sxs-lookup"><span data-stu-id="22ea9-108">The Visual Basic compiler will catch errors of badly formed or invalid XML.</span></span>  
  
## <a name="example"></a><span data-ttu-id="22ea9-109">Przykład</span><span class="sxs-lookup"><span data-stu-id="22ea9-109">Example</span></span>  
 <span data-ttu-id="22ea9-110">Następujący kod próbuje przeanalizować nieprawidłowego kodu XML:</span><span class="sxs-lookup"><span data-stu-id="22ea9-110">The following code tries to parse invalid XML:</span></span>  
  
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
  
 <span data-ttu-id="22ea9-111">Po uruchomieniu tego kodu zgłasza następujący wyjątek:</span><span class="sxs-lookup"><span data-stu-id="22ea9-111">When you run this code, it throws the following exception:</span></span>  
  
```console  
The 'Contacts' start tag on line 1 does not match the end tag of 'Contcts'. Line 5, position 13.  
```  
  
 <span data-ttu-id="22ea9-112">Informacje o wyjątkach, w których można oczekiwać, <xref:System.Xml.Linq.XElement.Parse%2A?displayProperty=nameWithType> , <xref:System.Xml.Linq.XDocument.Parse%2A?displayProperty=nameWithType> <xref:System.Xml.Linq.XElement.Load%2A?displayProperty=nameWithType> , i metod zgłaszania <xref:System.Xml.Linq.XDocument.Load%2A?displayProperty=nameWithType> , znajdują się w <xref:System.Xml.XmlReader> dokumentacji.</span><span class="sxs-lookup"><span data-stu-id="22ea9-112">For information about the exceptions that you can expect the <xref:System.Xml.Linq.XElement.Parse%2A?displayProperty=nameWithType>, <xref:System.Xml.Linq.XDocument.Parse%2A?displayProperty=nameWithType>, <xref:System.Xml.Linq.XElement.Load%2A?displayProperty=nameWithType>, and <xref:System.Xml.Linq.XDocument.Load%2A?displayProperty=nameWithType> methods to throw, see the <xref:System.Xml.XmlReader> documentation.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="22ea9-113">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="22ea9-113">See also</span></span>

- [<span data-ttu-id="22ea9-114">Analizowanie kodu XML (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="22ea9-114">Parsing XML (Visual Basic)</span></span>](parsing-xml.md)
