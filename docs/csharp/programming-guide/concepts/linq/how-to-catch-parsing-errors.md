---
title: 'Instrukcje: Błędy analizy catch (C#)'
ms.date: 07/20/2015
ms.assetid: bfb612d4-5605-48ef-8c93-915cf9d5dcfb
ms.openlocfilehash: 4195ff50d1b4d23cd9eb07fc27f20861d1504672
ms.sourcegitcommit: 2d792961ed48f235cf413d6031576373c3050918
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/31/2019
ms.locfileid: "70204146"
---
# <a name="how-to-catch-parsing-errors-c"></a><span data-ttu-id="baebd-102">Instrukcje: Błędy analizy catch (C#)</span><span class="sxs-lookup"><span data-stu-id="baebd-102">How to: Catch Parsing Errors (C#)</span></span>
<span data-ttu-id="baebd-103">W tym temacie pokazano, jak wykryć źle sformułowany lub nieprawidłowy kod XML.</span><span class="sxs-lookup"><span data-stu-id="baebd-103">This topic shows how to detect badly formed or invalid XML.</span></span>  
  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]<span data-ttu-id="baebd-104">jest zaimplementowany przy <xref:System.Xml.XmlReader>użyciu.</span><span class="sxs-lookup"><span data-stu-id="baebd-104">is implemented using <xref:System.Xml.XmlReader>.</span></span> <span data-ttu-id="baebd-105">Jeśli nieprawidłowo sformułowany lub nieprawidłowy kod XML jest [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]przenoszona do <xref:System.Xml.XmlReader> , Klasa bazowa zgłosi wyjątek.</span><span class="sxs-lookup"><span data-stu-id="baebd-105">If badly formed or invalid XML is passed to [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)], the underlying <xref:System.Xml.XmlReader> class will throw an exception.</span></span> <span data-ttu-id="baebd-106">Różne metody, które analizują XML, takie <xref:System.Xml.Linq.XElement.Parse%2A?displayProperty=nameWithType>jak, nie przechwytują wyjątku; wyjątek może zostać przechwycony przez aplikację.</span><span class="sxs-lookup"><span data-stu-id="baebd-106">The various methods that parse XML, such as <xref:System.Xml.Linq.XElement.Parse%2A?displayProperty=nameWithType>, do not catch the exception; the exception can then be caught by your application.</span></span>  
  
## <a name="example"></a><span data-ttu-id="baebd-107">Przykład</span><span class="sxs-lookup"><span data-stu-id="baebd-107">Example</span></span>  
 <span data-ttu-id="baebd-108">Następujący kod próbuje przeanalizować nieprawidłowego kodu XML:</span><span class="sxs-lookup"><span data-stu-id="baebd-108">The following code tries to parse invalid XML:</span></span>  
  
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
  
 <span data-ttu-id="baebd-109">Po uruchomieniu tego kodu zgłasza następujący wyjątek:</span><span class="sxs-lookup"><span data-stu-id="baebd-109">When you run this code, it throws the following exception:</span></span>  
  
```console  
The 'Contacts' start tag on line 1 does not match the end tag of 'Contcts'. Line 5, position 13.  
```  
  
 <span data-ttu-id="baebd-110">Informacje o <xref:System.Xml.Linq.XElement.Parse%2A?displayProperty=nameWithType>wyjątkach <xref:System.Xml.Linq.XDocument.Load%2A?displayProperty=nameWithType> <xref:System.Xml.XmlReader> , <xref:System.Xml.Linq.XDocument.Parse%2A?displayProperty=nameWithType>wktórych można oczekiwać,, ,imetodzgłaszania,znajdująsięwdokumentacji.<xref:System.Xml.Linq.XElement.Load%2A?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="baebd-110">For information about the exceptions that you can expect the <xref:System.Xml.Linq.XElement.Parse%2A?displayProperty=nameWithType>, <xref:System.Xml.Linq.XDocument.Parse%2A?displayProperty=nameWithType>, <xref:System.Xml.Linq.XElement.Load%2A?displayProperty=nameWithType>, and <xref:System.Xml.Linq.XDocument.Load%2A?displayProperty=nameWithType> methods to throw, see the <xref:System.Xml.XmlReader> documentation.</span></span>  
  