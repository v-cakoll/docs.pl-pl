---
title: 'Instrukcje: Znajdowanie poprzednich elementów równorzędnych (XPath-LINQ to XML) (C#)'
ms.date: 07/20/2015
ms.assetid: b281ff99-d08a-43d0-bea1-eff831b2f8ae
ms.openlocfilehash: 42663e1c90f7a7a829e858cfc8e20cdcb2ad2d36
ms.sourcegitcommit: 155012a8a826ee8ab6aa49b1b3a3b532e7b7d9bd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2019
ms.locfileid: "66485452"
---
# <a name="how-to-find-preceding-siblings-xpath-linq-to-xml-c"></a><span data-ttu-id="85590-102">Instrukcje: Znajdowanie poprzednich elementów równorzędnych (XPath-LINQ to XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="85590-102">How to: Find Preceding Siblings (XPath-LINQ to XML) (C#)</span></span>
<span data-ttu-id="85590-103">W tym temacie porównano XPath `preceding-sibling` osi [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] podrzędnych <xref:System.Xml.Linq.XNode.ElementsBeforeSelf%2A?displayProperty=nameWithType> osi.</span><span class="sxs-lookup"><span data-stu-id="85590-103">This topic compares the XPath `preceding-sibling` axis to the [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] child <xref:System.Xml.Linq.XNode.ElementsBeforeSelf%2A?displayProperty=nameWithType> axis.</span></span>  
  
 <span data-ttu-id="85590-104">Wyrażenie XPath jest:</span><span class="sxs-lookup"><span data-stu-id="85590-104">The XPath expression is:</span></span>  
  
 `preceding-sibling::*`  
  
 <span data-ttu-id="85590-105">Należy pamiętać, że wyniki zarówno <xref:System.Xml.XPath.Extensions.XPathSelectElements%2A> i <xref:System.Xml.Linq.XNode.ElementsBeforeSelf%2A?displayProperty=nameWithType> znajdują się w kolejności dokumentu.</span><span class="sxs-lookup"><span data-stu-id="85590-105">Note that the results of both <xref:System.Xml.XPath.Extensions.XPathSelectElements%2A> and <xref:System.Xml.Linq.XNode.ElementsBeforeSelf%2A?displayProperty=nameWithType> are in document order.</span></span>  
  
## <a name="example"></a><span data-ttu-id="85590-106">Przykład</span><span class="sxs-lookup"><span data-stu-id="85590-106">Example</span></span>  
 <span data-ttu-id="85590-107">Poniższy przykład umożliwia znalezienie `FullAddress` elementu, a następnie pobierze poprzednich elementów przy użyciu `preceding-sibling` osi.</span><span class="sxs-lookup"><span data-stu-id="85590-107">The following example finds the `FullAddress` element, and then retrieves the previous elements using the `preceding-sibling` axis.</span></span>  
  
 <span data-ttu-id="85590-108">W tym przykładzie użyto następujący dokument XML: [Przykładowy plik XML: Klienci i zamówienia (LINQ to XML)](../../../../csharp/programming-guide/concepts/linq/sample-xml-file-customers-and-orders-linq-to-xml-2.md).</span><span class="sxs-lookup"><span data-stu-id="85590-108">This example uses the following XML document: [Sample XML File: Customers and Orders (LINQ to XML)](../../../../csharp/programming-guide/concepts/linq/sample-xml-file-customers-and-orders-linq-to-xml-2.md).</span></span>  
  
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
  
 <span data-ttu-id="85590-109">Ten przykład generuje następujące wyniki:</span><span class="sxs-lookup"><span data-stu-id="85590-109">This example produces the following output:</span></span>  
  
```  
Results are identical  
<CompanyName>Great Lakes Food Market</CompanyName>  
<ContactName>Howard Snyder</ContactName>  
<ContactTitle>Marketing Manager</ContactTitle>  
<Phone>(503) 555-7555</Phone>  
```  
