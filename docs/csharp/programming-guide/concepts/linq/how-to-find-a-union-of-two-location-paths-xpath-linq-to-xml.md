---
title: 'Instrukcje: Znajdź Unię dwóch ścieżek lokalizacji (XPath-LINQ to XML) (C#)'
ms.date: 07/20/2015
ms.assetid: 069622d3-2b58-4919-8903-710a564c0788
ms.openlocfilehash: 9fc88a8784958294ba6077893a5d54110de335a0
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/19/2019
ms.locfileid: "69593744"
---
# <a name="how-to-find-a-union-of-two-location-paths-xpath-linq-to-xml-c"></a><span data-ttu-id="a139c-102">Instrukcje: Znajdź Unię dwóch ścieżek lokalizacji (XPath-LINQ to XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="a139c-102">How to: Find a Union of Two Location Paths (XPath-LINQ to XML) (C#)</span></span>
<span data-ttu-id="a139c-103">Wyrażenie XPath umożliwia znalezienie związku z wynikami dwóch ścieżek lokalizacji XPath.</span><span class="sxs-lookup"><span data-stu-id="a139c-103">XPath allows you to find the union of the results of two XPath location paths.</span></span>  
  
 <span data-ttu-id="a139c-104">Wyrażenie XPath:</span><span class="sxs-lookup"><span data-stu-id="a139c-104">The XPath expression is:</span></span>  
  
 `//Category|//Price`  
  
 <span data-ttu-id="a139c-105">Można osiągnąć te same wyniki przy użyciu <xref:System.Linq.Enumerable.Concat%2A> standardowego operatora zapytań.</span><span class="sxs-lookup"><span data-stu-id="a139c-105">You can achieve the same results by using the <xref:System.Linq.Enumerable.Concat%2A> standard query operator.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a139c-106">Przykład</span><span class="sxs-lookup"><span data-stu-id="a139c-106">Example</span></span>  
 <span data-ttu-id="a139c-107">Ten przykład umożliwia znalezienie wszystkich `Category` elementów i wszystkich `Price` elementów i połączenie ich w jedną kolekcję.</span><span class="sxs-lookup"><span data-stu-id="a139c-107">This example finds all of the `Category` elements and all of the `Price` elements, and concatenates them into a single collection.</span></span> <span data-ttu-id="a139c-108">Należy zauważyć, [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] że zapytanie <xref:System.Xml.Linq.Extensions.InDocumentOrder%2A> wywołuje w celu uporządkowania wyników.</span><span class="sxs-lookup"><span data-stu-id="a139c-108">Note that the [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] query calls <xref:System.Xml.Linq.Extensions.InDocumentOrder%2A> to order the results.</span></span> <span data-ttu-id="a139c-109">Wyniki obliczania wyrażenia XPath również są w kolejności dokumentu.</span><span class="sxs-lookup"><span data-stu-id="a139c-109">The results of the XPath expression evaluation are also in document order.</span></span>  
  
 <span data-ttu-id="a139c-110">W tym przykładzie zastosowano następujący dokument XML: [Przykładowy plik XML: Dane liczbowe (LINQ to XML)](./sample-xml-file-numerical-data-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="a139c-110">This example uses the following XML document: [Sample XML File: Numerical Data (LINQ to XML)](./sample-xml-file-numerical-data-linq-to-xml.md).</span></span>  
  
```csharp  
XDocument data = XDocument.Load("Data.xml");  
  
// LINQ to XML query  
IEnumerable<XElement> list1 =  
    data  
    .Descendants("Category")  
    .Concat(  
        data  
        .Descendants("Price")  
    )  
    .InDocumentOrder();  
  
// XPath expression  
IEnumerable<XElement> list2 = data.XPathSelectElements("//Category|//Price");  
  
if (list1.Count() == list2.Count() &&  
        list1.Intersect(list2).Count() == list1.Count())  
    Console.WriteLine("Results are identical");  
else  
    Console.WriteLine("Results differ");  
foreach (XElement el in list1)  
    Console.WriteLine(el);  
```  
  
 <span data-ttu-id="a139c-111">Ten przykład generuje następujące wyniki:</span><span class="sxs-lookup"><span data-stu-id="a139c-111">This example produces the following output:</span></span>  
  
```  
Results are identical  
<Category>A</Category>  
<Price>24.50</Price>  
<Category>B</Category>  
<Price>89.99</Price>  
<Category>A</Category>  
<Price>4.95</Price>  
<Category>A</Category>  
<Price>66.00</Price>  
<Category>B</Category>  
<Price>.99</Price>  
<Category>A</Category>  
<Price>29.00</Price>  
<Category>B</Category>  
<Price>6.99</Price>  
```  
  