---
title: 'Instrukcje: Przechwytywanie błędów analizy (C#)'
ms.date: 07/20/2015
ms.assetid: bfb612d4-5605-48ef-8c93-915cf9d5dcfb
ms.openlocfilehash: 094485b24cdccee7898bd0344aa7c100e26bf4e9
ms.sourcegitcommit: 155012a8a826ee8ab6aa49b1b3a3b532e7b7d9bd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2019
ms.locfileid: "66487488"
---
# <a name="how-to-catch-parsing-errors-c"></a><span data-ttu-id="2399a-102">Instrukcje: Przechwytywanie błędów analizy (C#)</span><span class="sxs-lookup"><span data-stu-id="2399a-102">How to: Catch Parsing Errors (C#)</span></span>
<span data-ttu-id="2399a-103">W tym temacie pokazano, jak wykryć XML źle sformułowana lub jest nieprawidłowy.</span><span class="sxs-lookup"><span data-stu-id="2399a-103">This topic shows how to detect badly formed or invalid XML.</span></span>  
  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] <span data-ttu-id="2399a-104">jest implementowana przy użyciu <xref:System.Xml.XmlReader>.</span><span class="sxs-lookup"><span data-stu-id="2399a-104">is implemented using <xref:System.Xml.XmlReader>.</span></span> <span data-ttu-id="2399a-105">Jeśli źle sformułowany lub nieprawidłowy XML jest przekazywany do [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)], podstawowe <xref:System.Xml.XmlReader> klasy spowoduje zgłoszenie wyjątku.</span><span class="sxs-lookup"><span data-stu-id="2399a-105">If badly formed or invalid XML is passed to [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)], the underlying <xref:System.Xml.XmlReader> class will throw an exception.</span></span> <span data-ttu-id="2399a-106">Różne metody analizy XML, takie jak <xref:System.Xml.Linq.XElement.Parse%2A?displayProperty=nameWithType>, nie Przechwytuj wyjątek; wyjątek, następnie może zostać przechwycony przez aplikację.</span><span class="sxs-lookup"><span data-stu-id="2399a-106">The various methods that parse XML, such as <xref:System.Xml.Linq.XElement.Parse%2A?displayProperty=nameWithType>, do not catch the exception; the exception can then be caught by your application.</span></span>  
  
## <a name="example"></a><span data-ttu-id="2399a-107">Przykład</span><span class="sxs-lookup"><span data-stu-id="2399a-107">Example</span></span>  
 <span data-ttu-id="2399a-108">Poniższy kod próbuje przeanalizować nieprawidłowy kod XML:</span><span class="sxs-lookup"><span data-stu-id="2399a-108">The following code tries to parse invalid XML:</span></span>  
  
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
  
 <span data-ttu-id="2399a-109">Po uruchomieniu tego kodu, zgłasza następujący wyjątek:</span><span class="sxs-lookup"><span data-stu-id="2399a-109">When you run this code, it throws the following exception:</span></span>  
  
```  
The 'Contacts' start tag on line 1 does not match the end tag of 'Contcts'. Line 5, position 13.  
```  
  
 <span data-ttu-id="2399a-110">Dla informacji o wyjątkach, których można oczekiwać, że <xref:System.Xml.Linq.XElement.Parse%2A?displayProperty=nameWithType>, <xref:System.Xml.Linq.XDocument.Parse%2A?displayProperty=nameWithType>, <xref:System.Xml.Linq.XElement.Load%2A?displayProperty=nameWithType>, i <xref:System.Xml.Linq.XDocument.Load%2A?displayProperty=nameWithType> metody throw, zobacz <xref:System.Xml.XmlReader> dokumentacji.</span><span class="sxs-lookup"><span data-stu-id="2399a-110">For information about the exceptions that you can expect the <xref:System.Xml.Linq.XElement.Parse%2A?displayProperty=nameWithType>, <xref:System.Xml.Linq.XDocument.Parse%2A?displayProperty=nameWithType>, <xref:System.Xml.Linq.XElement.Load%2A?displayProperty=nameWithType>, and <xref:System.Xml.Linq.XDocument.Load%2A?displayProperty=nameWithType> methods to throw, see the <xref:System.Xml.XmlReader> documentation.</span></span>  
  