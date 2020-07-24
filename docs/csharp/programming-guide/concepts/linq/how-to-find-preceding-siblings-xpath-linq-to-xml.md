---
title: Jak znaleźć poprzednie elementy równorzędne (XPath-LINQ to XML) (C#)
description: Ten przykład w języku C# porównuje oś Poprzednia elementu równorzędnego ze ścieżką do LINQ to XML podrzędnej osi XNode. ElementsBeforeSelf.
ms.date: 07/20/2015
ms.assetid: b281ff99-d08a-43d0-bea1-eff831b2f8ae
ms.openlocfilehash: 4150c94fe1e30e7a72bb53b4c6c12481ee0bad19
ms.sourcegitcommit: 04022ca5d00b2074e1b1ffdbd76bec4950697c4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/23/2020
ms.locfileid: "87103454"
---
# <a name="how-to-find-preceding-siblings-xpath-linq-to-xml-c"></a>Jak znaleźć poprzednie elementy równorzędne (XPath-LINQ to XML) (C#)
W tym temacie porównano `preceding-sibling` oś XPath z [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] osią podrzędną <xref:System.Xml.Linq.XNode.ElementsBeforeSelf%2A?displayProperty=nameWithType> .  
  
 Wyrażenie XPath:  
  
 `preceding-sibling::*`  
  
 Zwróć uwagę, że wyniki obu <xref:System.Xml.XPath.Extensions.XPathSelectElements%2A> i <xref:System.Xml.Linq.XNode.ElementsBeforeSelf%2A?displayProperty=nameWithType> są w kolejności dokumentu.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład umożliwia znalezienie `FullAddress` elementu, a następnie pobranie poprzednich elementów przy użyciu `preceding-sibling` osi.  
  
 W tym przykładzie zastosowano następujący dokument XML: [przykładowy plik XML: Customers i Orders (LINQ to XML)](./sample-xml-file-customers-and-orders-linq-to-xml-2.md).  
  
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
  
 Ten przykład generuje następujące wyniki:  
  
```output  
Results are identical  
<CompanyName>Great Lakes Food Market</CompanyName>  
<ContactName>Howard Snyder</ContactName>  
<ContactTitle>Marketing Manager</ContactTitle>  
<Phone>(503) 555-7555</Phone>  
```  
