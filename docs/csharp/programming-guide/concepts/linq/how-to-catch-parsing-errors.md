---
title: Jak przechwytywać błędy analizy (C#)
description: Ten LINQ to XML przykład w języku C# wykrywa nieprawidłowo sformułowany lub nieprawidłowy kod XML. LINQ to XML używa elementu XmlReader, który zgłasza wyjątek dla nieprawidłowo sformułowanego lub nieprawidłowego kodu XML.
ms.date: 07/20/2015
ms.assetid: bfb612d4-5605-48ef-8c93-915cf9d5dcfb
ms.openlocfilehash: 0a891097322ef6acce062ea927692b01cc425e6c
ms.sourcegitcommit: 04022ca5d00b2074e1b1ffdbd76bec4950697c4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/23/2020
ms.locfileid: "87105404"
---
# <a name="how-to-catch-parsing-errors-c"></a><span data-ttu-id="a4162-104">Jak przechwytywać błędy analizy (C#)</span><span class="sxs-lookup"><span data-stu-id="a4162-104">How to catch parsing errors (C#)</span></span>
<span data-ttu-id="a4162-105">W tym temacie pokazano, jak wykryć źle sformułowany lub nieprawidłowy kod XML.</span><span class="sxs-lookup"><span data-stu-id="a4162-105">This topic shows how to detect badly formed or invalid XML.</span></span>  
  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]<span data-ttu-id="a4162-106">jest zaimplementowany przy użyciu <xref:System.Xml.XmlReader> .</span><span class="sxs-lookup"><span data-stu-id="a4162-106">is implemented using <xref:System.Xml.XmlReader>.</span></span> <span data-ttu-id="a4162-107">Jeśli nieprawidłowo sformułowany lub nieprawidłowy kod XML jest przenoszona do [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] , <xref:System.Xml.XmlReader> Klasa bazowa zgłosi wyjątek.</span><span class="sxs-lookup"><span data-stu-id="a4162-107">If badly formed or invalid XML is passed to [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)], the underlying <xref:System.Xml.XmlReader> class will throw an exception.</span></span> <span data-ttu-id="a4162-108">Różne metody, które analizują XML, takie jak <xref:System.Xml.Linq.XElement.Parse%2A?displayProperty=nameWithType> , nie przechwytują wyjątku; wyjątek może zostać przechwycony przez aplikację.</span><span class="sxs-lookup"><span data-stu-id="a4162-108">The various methods that parse XML, such as <xref:System.Xml.Linq.XElement.Parse%2A?displayProperty=nameWithType>, do not catch the exception; the exception can then be caught by your application.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a4162-109">Przykład</span><span class="sxs-lookup"><span data-stu-id="a4162-109">Example</span></span>  
 <span data-ttu-id="a4162-110">Następujący kod próbuje przeanalizować nieprawidłowego kodu XML:</span><span class="sxs-lookup"><span data-stu-id="a4162-110">The following code tries to parse invalid XML:</span></span>  
  
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
  
 <span data-ttu-id="a4162-111">Po uruchomieniu tego kodu zgłasza następujący wyjątek:</span><span class="sxs-lookup"><span data-stu-id="a4162-111">When you run this code, it throws the following exception:</span></span>  
  
```console  
The 'Contacts' start tag on line 1 does not match the end tag of 'Contcts'. Line 5, position 13.  
```  
  
 <span data-ttu-id="a4162-112">Informacje o wyjątkach, w których można oczekiwać, <xref:System.Xml.Linq.XElement.Parse%2A?displayProperty=nameWithType> , <xref:System.Xml.Linq.XDocument.Parse%2A?displayProperty=nameWithType> <xref:System.Xml.Linq.XElement.Load%2A?displayProperty=nameWithType> , i metod zgłaszania <xref:System.Xml.Linq.XDocument.Load%2A?displayProperty=nameWithType> , znajdują się w <xref:System.Xml.XmlReader> dokumentacji.</span><span class="sxs-lookup"><span data-stu-id="a4162-112">For information about the exceptions that you can expect the <xref:System.Xml.Linq.XElement.Parse%2A?displayProperty=nameWithType>, <xref:System.Xml.Linq.XDocument.Parse%2A?displayProperty=nameWithType>, <xref:System.Xml.Linq.XElement.Load%2A?displayProperty=nameWithType>, and <xref:System.Xml.Linq.XDocument.Load%2A?displayProperty=nameWithType> methods to throw, see the <xref:System.Xml.XmlReader> documentation.</span></span>  
  