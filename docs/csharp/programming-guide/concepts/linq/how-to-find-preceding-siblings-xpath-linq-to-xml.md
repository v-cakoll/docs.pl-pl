---
title: Jak znaleźć poprzednie elementy równorzędne (XPath-LINQ do XML) (C#)
ms.date: 07/20/2015
ms.assetid: b281ff99-d08a-43d0-bea1-eff831b2f8ae
ms.openlocfilehash: 08fc2073f76f37bd0381a05a7969d1c7748d6252
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "74141059"
---
# <a name="how-to-find-preceding-siblings-xpath-linq-to-xml-c"></a><span data-ttu-id="19f30-102">Jak znaleźć poprzednie elementy równorzędne (XPath-LINQ do XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="19f30-102">How to find preceding siblings (XPath-LINQ to XML) (C#)</span></span>
<span data-ttu-id="19f30-103">W tym temacie porównano oś XPath `preceding-sibling` z osią podrzędna. [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] <xref:System.Xml.Linq.XNode.ElementsBeforeSelf%2A?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="19f30-103">This topic compares the XPath `preceding-sibling` axis to the [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] child <xref:System.Xml.Linq.XNode.ElementsBeforeSelf%2A?displayProperty=nameWithType> axis.</span></span>  
  
 <span data-ttu-id="19f30-104">Wyrażenie XPath jest następujące:</span><span class="sxs-lookup"><span data-stu-id="19f30-104">The XPath expression is:</span></span>  
  
 `preceding-sibling::*`  
  
 <span data-ttu-id="19f30-105">Należy zauważyć, że <xref:System.Xml.XPath.Extensions.XPathSelectElements%2A> <xref:System.Xml.Linq.XNode.ElementsBeforeSelf%2A?displayProperty=nameWithType> wyniki obu i są w kolejności dokumentu.</span><span class="sxs-lookup"><span data-stu-id="19f30-105">Note that the results of both <xref:System.Xml.XPath.Extensions.XPathSelectElements%2A> and <xref:System.Xml.Linq.XNode.ElementsBeforeSelf%2A?displayProperty=nameWithType> are in document order.</span></span>  
  
## <a name="example"></a><span data-ttu-id="19f30-106">Przykład</span><span class="sxs-lookup"><span data-stu-id="19f30-106">Example</span></span>  
 <span data-ttu-id="19f30-107">Poniższy przykład znajduje `FullAddress` element, a następnie pobiera poprzednie `preceding-sibling` elementy przy użyciu osi.</span><span class="sxs-lookup"><span data-stu-id="19f30-107">The following example finds the `FullAddress` element, and then retrieves the previous elements using the `preceding-sibling` axis.</span></span>  
  
 <span data-ttu-id="19f30-108">W tym przykładzie użyto następującego dokumentu XML: [Przykładowy plik XML: Klienci i zamówienia (LINQ do XML).](./sample-xml-file-customers-and-orders-linq-to-xml-2.md)</span><span class="sxs-lookup"><span data-stu-id="19f30-108">This example uses the following XML document: [Sample XML File: Customers and Orders (LINQ to XML)](./sample-xml-file-customers-and-orders-linq-to-xml-2.md).</span></span>  
  
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
  
 <span data-ttu-id="19f30-109">Ten przykład generuje następujące wyniki:</span><span class="sxs-lookup"><span data-stu-id="19f30-109">This example produces the following output:</span></span>  
  
```output  
Results are identical  
<CompanyName>Great Lakes Food Market</CompanyName>  
<ContactName>Howard Snyder</ContactName>  
<ContactTitle>Marketing Manager</ContactTitle>  
<Phone>(503) 555-7555</Phone>  
```  
