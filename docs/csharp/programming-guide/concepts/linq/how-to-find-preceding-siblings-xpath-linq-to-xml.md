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
# <a name="how-to-find-preceding-siblings-xpath-linq-to-xml-c"></a>Instrukcje: Znajdź poprzednie elementy równorzędne (XPath-LINQ to XML)C#()
W tym temacie porównano `preceding-sibling` oś XPath [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] z osią <xref:System.Xml.Linq.XNode.ElementsBeforeSelf%2A?displayProperty=nameWithType> podrzędną.  
  
 Wyrażenie XPath:  
  
 `preceding-sibling::*`  
  
 Zwróć uwagę, że wyniki obu <xref:System.Xml.XPath.Extensions.XPathSelectElements%2A> i <xref:System.Xml.Linq.XNode.ElementsBeforeSelf%2A?displayProperty=nameWithType> są w kolejności dokumentu.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład umożliwia znalezienie `FullAddress` elementu, a następnie pobranie poprzednich elementów `preceding-sibling` przy użyciu osi.  
  
 W tym przykładzie zastosowano następujący dokument XML: [Przykładowy plik XML: Klienci i zamówienia (LINQ to XML)](./sample-xml-file-customers-and-orders-linq-to-xml-2.md).  
  
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
  
```  
Results are identical  
<CompanyName>Great Lakes Food Market</CompanyName>  
<ContactName>Howard Snyder</ContactName>  
<ContactTitle>Marketing Manager</ContactTitle>  
<Phone>(503) 555-7555</Phone>  
```  
