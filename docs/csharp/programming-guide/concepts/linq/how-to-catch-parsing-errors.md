---
title: Jak przechwytywać błędy analizy (C#)
ms.date: 07/20/2015
ms.assetid: bfb612d4-5605-48ef-8c93-915cf9d5dcfb
ms.openlocfilehash: 1a05037892061dec85e7837472e8ec13e076724b
ms.sourcegitcommit: fbb8a593a511ce667992502a3ce6d8f65c594edf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/16/2019
ms.locfileid: "74141479"
---
# <a name="how-to-catch-parsing-errors-c"></a><span data-ttu-id="c3383-102">Jak przechwytywać błędy analizy (C#)</span><span class="sxs-lookup"><span data-stu-id="c3383-102">How to catch parsing errors (C#)</span></span>
<span data-ttu-id="c3383-103">W tym temacie pokazano, jak wykryć źle sformułowany lub nieprawidłowy kod XML.</span><span class="sxs-lookup"><span data-stu-id="c3383-103">This topic shows how to detect badly formed or invalid XML.</span></span>  
  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] <span data-ttu-id="c3383-104">jest implementowana przy użyciu <xref:System.Xml.XmlReader>.</span><span class="sxs-lookup"><span data-stu-id="c3383-104">is implemented using <xref:System.Xml.XmlReader>.</span></span> <span data-ttu-id="c3383-105">Jeśli nieprawidłowo sformułowany lub nieprawidłowy kod XML jest przenoszona do [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)], bazowa Klasa <xref:System.Xml.XmlReader> zgłosi wyjątek.</span><span class="sxs-lookup"><span data-stu-id="c3383-105">If badly formed or invalid XML is passed to [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)], the underlying <xref:System.Xml.XmlReader> class will throw an exception.</span></span> <span data-ttu-id="c3383-106">Różne metody, które analizują XML, takie jak <xref:System.Xml.Linq.XElement.Parse%2A?displayProperty=nameWithType>, nie przechwytują wyjątku; wyjątek może następnie być przechwytywany przez aplikację.</span><span class="sxs-lookup"><span data-stu-id="c3383-106">The various methods that parse XML, such as <xref:System.Xml.Linq.XElement.Parse%2A?displayProperty=nameWithType>, do not catch the exception; the exception can then be caught by your application.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c3383-107">Przykład</span><span class="sxs-lookup"><span data-stu-id="c3383-107">Example</span></span>  
 <span data-ttu-id="c3383-108">Następujący kod próbuje przeanalizować nieprawidłowego kodu XML:</span><span class="sxs-lookup"><span data-stu-id="c3383-108">The following code tries to parse invalid XML:</span></span>  
  
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
  
 <span data-ttu-id="c3383-109">Po uruchomieniu tego kodu zgłasza następujący wyjątek:</span><span class="sxs-lookup"><span data-stu-id="c3383-109">When you run this code, it throws the following exception:</span></span>  
  
```console  
The 'Contacts' start tag on line 1 does not match the end tag of 'Contcts'. Line 5, position 13.  
```  
  
 <span data-ttu-id="c3383-110">Informacje o wyjątkach, w których można oczekiwać, że <xref:System.Xml.Linq.XElement.Parse%2A?displayProperty=nameWithType>, <xref:System.Xml.Linq.XDocument.Parse%2A?displayProperty=nameWithType>, <xref:System.Xml.Linq.XElement.Load%2A?displayProperty=nameWithType>i <xref:System.Xml.Linq.XDocument.Load%2A?displayProperty=nameWithType> metod zgłaszania, zapoznaj się z dokumentacją <xref:System.Xml.XmlReader>.</span><span class="sxs-lookup"><span data-stu-id="c3383-110">For information about the exceptions that you can expect the <xref:System.Xml.Linq.XElement.Parse%2A?displayProperty=nameWithType>, <xref:System.Xml.Linq.XDocument.Parse%2A?displayProperty=nameWithType>, <xref:System.Xml.Linq.XElement.Load%2A?displayProperty=nameWithType>, and <xref:System.Xml.Linq.XDocument.Load%2A?displayProperty=nameWithType> methods to throw, see the <xref:System.Xml.XmlReader> documentation.</span></span>  
  