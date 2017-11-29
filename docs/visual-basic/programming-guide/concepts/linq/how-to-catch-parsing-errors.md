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
# <a name="how-to-catch-parsing-errors-visual-basic"></a><span data-ttu-id="ea9ee-102">Porady: Catch analizowanie błędów (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="ea9ee-102">How to: Catch Parsing Errors (Visual Basic)</span></span>
<span data-ttu-id="ea9ee-103">W tym temacie przedstawiono sposób wykrywania źle sformułowany lub nieprawidłowy XML.</span><span class="sxs-lookup"><span data-stu-id="ea9ee-103">This topic shows how to detect badly formed or invalid XML.</span></span>  
  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]<span data-ttu-id="ea9ee-104">jest implementowane za pomocą <xref:System.Xml.XmlReader>.</span><span class="sxs-lookup"><span data-stu-id="ea9ee-104"> is implemented using <xref:System.Xml.XmlReader>.</span></span> <span data-ttu-id="ea9ee-105">Jeśli źle sformułowany lub nieprawidłowy kod XML jest przekazany do [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)], podstawowa <xref:System.Xml.XmlReader> klasy spowoduje zgłoszenie wyjątku.</span><span class="sxs-lookup"><span data-stu-id="ea9ee-105">If badly formed or invalid XML is passed to [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)], the underlying <xref:System.Xml.XmlReader> class will throw an exception.</span></span> <span data-ttu-id="ea9ee-106">Różne metody analizy kodu XML, takich jak <xref:System.Xml.Linq.XElement.Parse%2A?displayProperty=nameWithType>, nie Przechwytuj wyjątków; wyjątek może być następnie zgłoszony przez aplikację.</span><span class="sxs-lookup"><span data-stu-id="ea9ee-106">The various methods that parse XML, such as <xref:System.Xml.Linq.XElement.Parse%2A?displayProperty=nameWithType>, do not catch the exception; the exception can then be caught by your application.</span></span>  
  
 <span data-ttu-id="ea9ee-107">Należy pamiętać, że nie można przeanalizować błędy użycie literałów XML.</span><span class="sxs-lookup"><span data-stu-id="ea9ee-107">Note that you cannot get parse errors if you use XML literals.</span></span> <span data-ttu-id="ea9ee-108">Kompilator Visual Basic będzie przechwytywać błędy źle sformułowany lub nieprawidłowy XML.</span><span class="sxs-lookup"><span data-stu-id="ea9ee-108">The Visual Basic compiler will catch errors of badly formed or invalid XML.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ea9ee-109">Przykład</span><span class="sxs-lookup"><span data-stu-id="ea9ee-109">Example</span></span>  
 <span data-ttu-id="ea9ee-110">Poniższy kod próbuje nieprawidłowe dane XML analizy:</span><span class="sxs-lookup"><span data-stu-id="ea9ee-110">The following code tries to parse invalid XML:</span></span>  
  
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
  
 <span data-ttu-id="ea9ee-111">Po uruchomieniu tego kodu zwraca następujący wyjątek:</span><span class="sxs-lookup"><span data-stu-id="ea9ee-111">When you run this code, it throws the following exception:</span></span>  
  
```  
The 'Contacts' start tag on line 1 does not match the end tag of 'Contcts'. Line 5, position 13.  
```  
  
 <span data-ttu-id="ea9ee-112">Aby uzyskać informacje dotyczące wyjątków, które można oczekiwać, że <xref:System.Xml.Linq.XElement.Parse%2A?displayProperty=nameWithType>, <xref:System.Xml.Linq.XDocument.Parse%2A?displayProperty=nameWithType>, <xref:System.Xml.Linq.XElement.Load%2A?displayProperty=nameWithType>, i <xref:System.Xml.Linq.XDocument.Load%2A?displayProperty=nameWithType> metody ma zostać zgłoszony, zobacz <xref:System.Xml.XmlReader> dokumentacji.</span><span class="sxs-lookup"><span data-stu-id="ea9ee-112">For information about the exceptions that you can expect the <xref:System.Xml.Linq.XElement.Parse%2A?displayProperty=nameWithType>, <xref:System.Xml.Linq.XDocument.Parse%2A?displayProperty=nameWithType>, <xref:System.Xml.Linq.XElement.Load%2A?displayProperty=nameWithType>, and <xref:System.Xml.Linq.XDocument.Load%2A?displayProperty=nameWithType> methods to throw, see the <xref:System.Xml.XmlReader> documentation.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ea9ee-113">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="ea9ee-113">See Also</span></span>  
 [<span data-ttu-id="ea9ee-114">Analiza kodu XML (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="ea9ee-114">Parsing XML (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/parsing-xml.md)
