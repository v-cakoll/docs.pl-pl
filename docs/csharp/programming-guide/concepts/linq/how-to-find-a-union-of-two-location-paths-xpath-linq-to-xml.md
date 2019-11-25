---
title: Jak znaleźć Unię dwóch ścieżek lokalizacji (XPath-LINQ to XML) (C#)
ms.date: 07/20/2015
ms.assetid: 069622d3-2b58-4919-8903-710a564c0788
ms.openlocfilehash: 17a3310f367cb68b3b80b1a3f30af40428f6d2c7
ms.sourcegitcommit: fbb8a593a511ce667992502a3ce6d8f65c594edf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/16/2019
ms.locfileid: "74141209"
---
# <a name="how-to-find-a-union-of-two-location-paths-xpath-linq-to-xml-c"></a><span data-ttu-id="4ff64-102">Jak znaleźć Unię dwóch ścieżek lokalizacji (XPath-LINQ to XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="4ff64-102">How to find a union of two location paths (XPath-LINQ to XML) (C#)</span></span>
<span data-ttu-id="4ff64-103">Wyrażenie XPath umożliwia znalezienie związku z wynikami dwóch ścieżek lokalizacji XPath.</span><span class="sxs-lookup"><span data-stu-id="4ff64-103">XPath allows you to find the union of the results of two XPath location paths.</span></span>  
  
 <span data-ttu-id="4ff64-104">Wyrażenie XPath:</span><span class="sxs-lookup"><span data-stu-id="4ff64-104">The XPath expression is:</span></span>  
  
 `//Category|//Price`  
  
 <span data-ttu-id="4ff64-105">Można osiągnąć te same wyniki przy użyciu standardowego operatora zapytań <xref:System.Linq.Enumerable.Concat%2A>.</span><span class="sxs-lookup"><span data-stu-id="4ff64-105">You can achieve the same results by using the <xref:System.Linq.Enumerable.Concat%2A> standard query operator.</span></span>  
  
## <a name="example"></a><span data-ttu-id="4ff64-106">Przykład</span><span class="sxs-lookup"><span data-stu-id="4ff64-106">Example</span></span>  
 <span data-ttu-id="4ff64-107">Ten przykład znajduje wszystkie elementy `Category` i wszystkie elementy `Price` i łączy je w jedną kolekcję.</span><span class="sxs-lookup"><span data-stu-id="4ff64-107">This example finds all of the `Category` elements and all of the `Price` elements, and concatenates them into a single collection.</span></span> <span data-ttu-id="4ff64-108">Należy zauważyć, że zapytanie [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] wywołuje <xref:System.Xml.Linq.Extensions.InDocumentOrder%2A> w celu uporządkowania wyników.</span><span class="sxs-lookup"><span data-stu-id="4ff64-108">Note that the [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] query calls <xref:System.Xml.Linq.Extensions.InDocumentOrder%2A> to order the results.</span></span> <span data-ttu-id="4ff64-109">Wyniki obliczania wyrażenia XPath również są w kolejności dokumentu.</span><span class="sxs-lookup"><span data-stu-id="4ff64-109">The results of the XPath expression evaluation are also in document order.</span></span>  
  
 <span data-ttu-id="4ff64-110">Ten przykład używa następującego dokumentu XML: [przykładowy plik XML: dane liczbowe (LINQ to XML)](./sample-xml-file-numerical-data-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="4ff64-110">This example uses the following XML document: [Sample XML File: Numerical Data (LINQ to XML)](./sample-xml-file-numerical-data-linq-to-xml.md).</span></span>  
  
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
  
 <span data-ttu-id="4ff64-111">Ten przykład generuje następujące wyniki:</span><span class="sxs-lookup"><span data-stu-id="4ff64-111">This example produces the following output:</span></span>  
  
```output  
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
  