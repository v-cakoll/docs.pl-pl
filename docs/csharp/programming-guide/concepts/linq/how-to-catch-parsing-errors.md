---
title: Jak wychwycić błędy analizy (C#)
ms.date: 07/20/2015
ms.assetid: bfb612d4-5605-48ef-8c93-915cf9d5dcfb
ms.openlocfilehash: 1a05037892061dec85e7837472e8ec13e076724b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "74141479"
---
# <a name="how-to-catch-parsing-errors-c"></a><span data-ttu-id="e06f6-102">Jak wychwycić błędy analizy (C#)</span><span class="sxs-lookup"><span data-stu-id="e06f6-102">How to catch parsing errors (C#)</span></span>
<span data-ttu-id="e06f6-103">W tym temacie pokazano, jak wykryć źle utworzony lub nieprawidłowy kod XML.</span><span class="sxs-lookup"><span data-stu-id="e06f6-103">This topic shows how to detect badly formed or invalid XML.</span></span>  
  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]<span data-ttu-id="e06f6-104">jest realizowany <xref:System.Xml.XmlReader>za pomocą .</span><span class="sxs-lookup"><span data-stu-id="e06f6-104">is implemented using <xref:System.Xml.XmlReader>.</span></span> <span data-ttu-id="e06f6-105">Jeśli źle utworzone lub nieprawidłowy Kod [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]XML jest <xref:System.Xml.XmlReader> przekazywany do , podstawowa klasa zgłosi wyjątek.</span><span class="sxs-lookup"><span data-stu-id="e06f6-105">If badly formed or invalid XML is passed to [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)], the underlying <xref:System.Xml.XmlReader> class will throw an exception.</span></span> <span data-ttu-id="e06f6-106">Różne metody, które analizują XML, takie jak <xref:System.Xml.Linq.XElement.Parse%2A?displayProperty=nameWithType>, nie przechwycić wyjątek; wyjątek może zostać przechwycony przez aplikację.</span><span class="sxs-lookup"><span data-stu-id="e06f6-106">The various methods that parse XML, such as <xref:System.Xml.Linq.XElement.Parse%2A?displayProperty=nameWithType>, do not catch the exception; the exception can then be caught by your application.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e06f6-107">Przykład</span><span class="sxs-lookup"><span data-stu-id="e06f6-107">Example</span></span>  
 <span data-ttu-id="e06f6-108">Poniższy kod próbuje przeanalizować nieprawidłowy kod XML:</span><span class="sxs-lookup"><span data-stu-id="e06f6-108">The following code tries to parse invalid XML:</span></span>  
  
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
  
 <span data-ttu-id="e06f6-109">Po uruchomieniu tego kodu zgłasza następujący wyjątek:</span><span class="sxs-lookup"><span data-stu-id="e06f6-109">When you run this code, it throws the following exception:</span></span>  
  
```console  
The 'Contacts' start tag on line 1 does not match the end tag of 'Contcts'. Line 5, position 13.  
```  
  
 <span data-ttu-id="e06f6-110">Aby uzyskać informacje na temat wyjątków, <xref:System.Xml.Linq.XElement.Load%2A?displayProperty=nameWithType>których <xref:System.Xml.Linq.XDocument.Load%2A?displayProperty=nameWithType> można się spodziewać <xref:System.Xml.XmlReader> <xref:System.Xml.Linq.XElement.Parse%2A?displayProperty=nameWithType>, <xref:System.Xml.Linq.XDocument.Parse%2A?displayProperty=nameWithType>, i metody, aby rzucić, zapoznaj się z dokumentacją.</span><span class="sxs-lookup"><span data-stu-id="e06f6-110">For information about the exceptions that you can expect the <xref:System.Xml.Linq.XElement.Parse%2A?displayProperty=nameWithType>, <xref:System.Xml.Linq.XDocument.Parse%2A?displayProperty=nameWithType>, <xref:System.Xml.Linq.XElement.Load%2A?displayProperty=nameWithType>, and <xref:System.Xml.Linq.XDocument.Load%2A?displayProperty=nameWithType> methods to throw, see the <xref:System.Xml.XmlReader> documentation.</span></span>  
  