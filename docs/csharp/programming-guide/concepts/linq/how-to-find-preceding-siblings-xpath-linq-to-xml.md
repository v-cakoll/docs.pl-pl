---
title: 'Instrukcje: Znajdź poprzednie elementy równorzędne (XPath-LINQ to XML)C#()'
ms.date: 07/20/2015
ms.assetid: b281ff99-d08a-43d0-bea1-eff831b2f8ae
ms.openlocfilehash: 2af2e08fa692142d2932a427f48ba5d323d7a848
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/04/2019
ms.locfileid: "70253659"
---
# <a name="how-to-find-preceding-siblings-xpath-linq-to-xml-c"></a><span data-ttu-id="2d274-102">Instrukcje: Znajdź poprzednie elementy równorzędne (XPath-LINQ to XML)C#()</span><span class="sxs-lookup"><span data-stu-id="2d274-102">How to: Find Preceding Siblings (XPath-LINQ to XML) (C#)</span></span>
<span data-ttu-id="2d274-103">W tym temacie porównano `preceding-sibling` oś XPath [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] z osią <xref:System.Xml.Linq.XNode.ElementsBeforeSelf%2A?displayProperty=nameWithType> podrzędną.</span><span class="sxs-lookup"><span data-stu-id="2d274-103">This topic compares the XPath `preceding-sibling` axis to the [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] child <xref:System.Xml.Linq.XNode.ElementsBeforeSelf%2A?displayProperty=nameWithType> axis.</span></span>  
  
 <span data-ttu-id="2d274-104">Wyrażenie XPath:</span><span class="sxs-lookup"><span data-stu-id="2d274-104">The XPath expression is:</span></span>  
  
 `preceding-sibling::*`  
  
 <span data-ttu-id="2d274-105">Zwróć uwagę, że wyniki obu <xref:System.Xml.XPath.Extensions.XPathSelectElements%2A> i <xref:System.Xml.Linq.XNode.ElementsBeforeSelf%2A?displayProperty=nameWithType> są w kolejności dokumentu.</span><span class="sxs-lookup"><span data-stu-id="2d274-105">Note that the results of both <xref:System.Xml.XPath.Extensions.XPathSelectElements%2A> and <xref:System.Xml.Linq.XNode.ElementsBeforeSelf%2A?displayProperty=nameWithType> are in document order.</span></span>  
  
## <a name="example"></a><span data-ttu-id="2d274-106">Przykład</span><span class="sxs-lookup"><span data-stu-id="2d274-106">Example</span></span>  
 <span data-ttu-id="2d274-107">Poniższy przykład umożliwia znalezienie `FullAddress` elementu, a następnie pobranie poprzednich elementów `preceding-sibling` przy użyciu osi.</span><span class="sxs-lookup"><span data-stu-id="2d274-107">The following example finds the `FullAddress` element, and then retrieves the previous elements using the `preceding-sibling` axis.</span></span>  
  
 <span data-ttu-id="2d274-108">W tym przykładzie zastosowano następujący dokument XML: [Przykładowy plik XML: Klienci i zamówienia (LINQ to XML)](./sample-xml-file-customers-and-orders-linq-to-xml-2.md).</span><span class="sxs-lookup"><span data-stu-id="2d274-108">This example uses the following XML document: [Sample XML File: Customers and Orders (LINQ to XML)](./sample-xml-file-customers-and-orders-linq-to-xml-2.md).</span></span>  
  
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
  
 <span data-ttu-id="2d274-109">Ten przykład generuje następujące wyniki:</span><span class="sxs-lookup"><span data-stu-id="2d274-109">This example produces the following output:</span></span>  
  
```output  
Results are identical  
<CompanyName>Great Lakes Food Market</CompanyName>  
<ContactName>Howard Snyder</ContactName>  
<ContactTitle>Marketing Manager</ContactTitle>  
<Phone>(503) 555-7555</Phone>  
```  
