---
title: 'Instrukcje: Znajdź poprzednie elementy równorzędne (XPath-LINQ to XML)C#()'
ms.date: 07/20/2015
ms.assetid: b281ff99-d08a-43d0-bea1-eff831b2f8ae
ms.openlocfilehash: d47a2d72efd8891108999d5576da52eb2b6285b1
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/19/2019
ms.locfileid: "69593436"
---
# <a name="how-to-find-preceding-siblings-xpath-linq-to-xml-c"></a><span data-ttu-id="082af-102">Instrukcje: Znajdź poprzednie elementy równorzędne (XPath-LINQ to XML)C#()</span><span class="sxs-lookup"><span data-stu-id="082af-102">How to: Find Preceding Siblings (XPath-LINQ to XML) (C#)</span></span>
<span data-ttu-id="082af-103">W tym temacie porównano `preceding-sibling` oś XPath [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] z osią <xref:System.Xml.Linq.XNode.ElementsBeforeSelf%2A?displayProperty=nameWithType> podrzędną.</span><span class="sxs-lookup"><span data-stu-id="082af-103">This topic compares the XPath `preceding-sibling` axis to the [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] child <xref:System.Xml.Linq.XNode.ElementsBeforeSelf%2A?displayProperty=nameWithType> axis.</span></span>  
  
 <span data-ttu-id="082af-104">Wyrażenie XPath:</span><span class="sxs-lookup"><span data-stu-id="082af-104">The XPath expression is:</span></span>  
  
 `preceding-sibling::*`  
  
 <span data-ttu-id="082af-105">Zwróć uwagę, że wyniki obu <xref:System.Xml.XPath.Extensions.XPathSelectElements%2A> i <xref:System.Xml.Linq.XNode.ElementsBeforeSelf%2A?displayProperty=nameWithType> są w kolejności dokumentu.</span><span class="sxs-lookup"><span data-stu-id="082af-105">Note that the results of both <xref:System.Xml.XPath.Extensions.XPathSelectElements%2A> and <xref:System.Xml.Linq.XNode.ElementsBeforeSelf%2A?displayProperty=nameWithType> are in document order.</span></span>  
  
## <a name="example"></a><span data-ttu-id="082af-106">Przykład</span><span class="sxs-lookup"><span data-stu-id="082af-106">Example</span></span>  
 <span data-ttu-id="082af-107">Poniższy przykład umożliwia znalezienie `FullAddress` elementu, a następnie pobranie poprzednich elementów `preceding-sibling` przy użyciu osi.</span><span class="sxs-lookup"><span data-stu-id="082af-107">The following example finds the `FullAddress` element, and then retrieves the previous elements using the `preceding-sibling` axis.</span></span>  
  
 <span data-ttu-id="082af-108">W tym przykładzie zastosowano następujący dokument XML: [Przykładowy plik XML: Klienci i zamówienia (LINQ to XML)](./sample-xml-file-customers-and-orders-linq-to-xml-2.md).</span><span class="sxs-lookup"><span data-stu-id="082af-108">This example uses the following XML document: [Sample XML File: Customers and Orders (LINQ to XML)](./sample-xml-file-customers-and-orders-linq-to-xml-2.md).</span></span>  
  
```csharp  
XElement co = XElement.Load("CustomersOrders.xml");  
  
XElement add = co.Element("Customers").Element("Customer").Element("FullAddress");  
  
// LINQ to XML query  
IEnumerable<XElement> list1 = add.ElementsBeforeSelf();  
  
// XPath expression  
IEnumerable<XElement> list2 = add.XPathSelectElements("preceding-sibling::*");  
  
if (list1.Count() == list2.Count() &&  
        list1.Intersect(list2).Count() == list1.Count())  
    Console.WriteLine("Results are identical");  
else  
    Console.WriteLine("Results differ");  
foreach (XElement el in list2)  
    Console.WriteLine(el);  
```  
  
 <span data-ttu-id="082af-109">Ten przykład generuje następujące wyniki:</span><span class="sxs-lookup"><span data-stu-id="082af-109">This example produces the following output:</span></span>  
  
```  
Results are identical  
<CompanyName>Great Lakes Food Market</CompanyName>  
<ContactName>Howard Snyder</ContactName>  
<ContactTitle>Marketing Manager</ContactTitle>  
<Phone>(503) 555-7555</Phone>  
```  
