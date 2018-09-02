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
# <a name="how-to-catch-parsing-errors-visual-basic"></a><span data-ttu-id="d2dd6-102">Porady: Przechwytywanie błędów (Visual Basic) analizy</span><span class="sxs-lookup"><span data-stu-id="d2dd6-102">How to: Catch Parsing Errors (Visual Basic)</span></span>
<span data-ttu-id="d2dd6-103">W tym temacie pokazano, jak wykryć XML źle sformułowana lub jest nieprawidłowy.</span><span class="sxs-lookup"><span data-stu-id="d2dd6-103">This topic shows how to detect badly formed or invalid XML.</span></span>  
  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]<span data-ttu-id="d2dd6-104"> jest implementowana przy użyciu <xref:System.Xml.XmlReader>.</span><span class="sxs-lookup"><span data-stu-id="d2dd6-104"> is implemented using <xref:System.Xml.XmlReader>.</span></span> <span data-ttu-id="d2dd6-105">Jeśli źle sformułowany lub nieprawidłowy XML jest przekazywany do [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)], podstawowe <xref:System.Xml.XmlReader> klasy spowoduje zgłoszenie wyjątku.</span><span class="sxs-lookup"><span data-stu-id="d2dd6-105">If badly formed or invalid XML is passed to [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)], the underlying <xref:System.Xml.XmlReader> class will throw an exception.</span></span> <span data-ttu-id="d2dd6-106">Różne metody analizy XML, takie jak <xref:System.Xml.Linq.XElement.Parse%2A?displayProperty=nameWithType>, nie Przechwytuj wyjątek; wyjątek, następnie może zostać przechwycony przez aplikację.</span><span class="sxs-lookup"><span data-stu-id="d2dd6-106">The various methods that parse XML, such as <xref:System.Xml.Linq.XElement.Parse%2A?displayProperty=nameWithType>, do not catch the exception; the exception can then be caught by your application.</span></span>  
  
 <span data-ttu-id="d2dd6-107">Błędy analizy należy pamiętać, że nie można uzyskać, korzystając z literałów XML.</span><span class="sxs-lookup"><span data-stu-id="d2dd6-107">Note that you cannot get parse errors if you use XML literals.</span></span> <span data-ttu-id="d2dd6-108">Kompilator Visual Basic będzie przechwytywać błędy XML źle sformułowana lub jest nieprawidłowy.</span><span class="sxs-lookup"><span data-stu-id="d2dd6-108">The Visual Basic compiler will catch errors of badly formed or invalid XML.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d2dd6-109">Przykład</span><span class="sxs-lookup"><span data-stu-id="d2dd6-109">Example</span></span>  
 <span data-ttu-id="d2dd6-110">Poniższy kod próbuje przeanalizować nieprawidłowy kod XML:</span><span class="sxs-lookup"><span data-stu-id="d2dd6-110">The following code tries to parse invalid XML:</span></span>  
  
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
  
 <span data-ttu-id="d2dd6-111">Po uruchomieniu tego kodu, zgłasza następujący wyjątek:</span><span class="sxs-lookup"><span data-stu-id="d2dd6-111">When you run this code, it throws the following exception:</span></span>  
  
```  
The 'Contacts' start tag on line 1 does not match the end tag of 'Contcts'. Line 5, position 13.  
```  
  
 <span data-ttu-id="d2dd6-112">Dla informacji o wyjątkach, których można oczekiwać, że <xref:System.Xml.Linq.XElement.Parse%2A?displayProperty=nameWithType>, <xref:System.Xml.Linq.XDocument.Parse%2A?displayProperty=nameWithType>, <xref:System.Xml.Linq.XElement.Load%2A?displayProperty=nameWithType>, i <xref:System.Xml.Linq.XDocument.Load%2A?displayProperty=nameWithType> metody throw, zobacz <xref:System.Xml.XmlReader> dokumentacji.</span><span class="sxs-lookup"><span data-stu-id="d2dd6-112">For information about the exceptions that you can expect the <xref:System.Xml.Linq.XElement.Parse%2A?displayProperty=nameWithType>, <xref:System.Xml.Linq.XDocument.Parse%2A?displayProperty=nameWithType>, <xref:System.Xml.Linq.XElement.Load%2A?displayProperty=nameWithType>, and <xref:System.Xml.Linq.XDocument.Load%2A?displayProperty=nameWithType> methods to throw, see the <xref:System.Xml.XmlReader> documentation.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d2dd6-113">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="d2dd6-113">See Also</span></span>  
 [<span data-ttu-id="d2dd6-114">Analizowanie kodu XML (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="d2dd6-114">Parsing XML (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/parsing-xml.md)
