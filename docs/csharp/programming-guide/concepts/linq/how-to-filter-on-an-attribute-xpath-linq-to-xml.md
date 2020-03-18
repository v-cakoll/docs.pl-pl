---
title: Jak filtrować atrybut (XPath-LINQ do XML) (C#)
ms.date: 07/20/2015
ms.assetid: 208d6256-1bd7-4237-b2c9-909f26dfd0e2
ms.openlocfilehash: ab2cd439f4dd1454de4fa565658ef5dac14b8c22
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "74141274"
---
# <a name="how-to-filter-on-an-attribute-xpath-linq-to-xml-c"></a><span data-ttu-id="3e957-102">Jak filtrować atrybut (XPath-LINQ do XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="3e957-102">How to filter on an attribute (XPath-LINQ to XML) (C#)</span></span>
<span data-ttu-id="3e957-103">W tym temacie pokazano, jak uzyskać elementy podrzędne o określonej nazwie i z atrybutem o określonej wartości.</span><span class="sxs-lookup"><span data-stu-id="3e957-103">This topic shows how to get the descendant elements with a specified name, and with an attribute with a specified value.</span></span>  
  
 <span data-ttu-id="3e957-104">Wyrażenie XPath jest następujące:</span><span class="sxs-lookup"><span data-stu-id="3e957-104">The XPath expression is:</span></span>  
  
 `.//Address[@Type='Shipping']`  
  
## <a name="example"></a><span data-ttu-id="3e957-105">Przykład</span><span class="sxs-lookup"><span data-stu-id="3e957-105">Example</span></span>  
 <span data-ttu-id="3e957-106">W tym przykładzie znajduje wszystkie elementy `Address`podrzędne `Type` o nazwie i z atrybutem o wartości "Wysyłka".</span><span class="sxs-lookup"><span data-stu-id="3e957-106">This example finds all descendants elements with the name of `Address`, and with a `Type` attribute with a value of "Shipping".</span></span>  
  
 <span data-ttu-id="3e957-107">W tym przykładzie użyto następującego dokumentu XML: [Przykładowy plik XML: wiele zamówień zakupu (LINQ do XML).](./sample-xml-file-multiple-purchase-orders-linq-to-xml.md)</span><span class="sxs-lookup"><span data-stu-id="3e957-107">This example uses the following XML document: [Sample XML File: Multiple Purchase Orders (LINQ to XML)](./sample-xml-file-multiple-purchase-orders-linq-to-xml.md).</span></span>  
  
```csharp  
XDocument po = XDocument.Load("PurchaseOrders.xml");  
  
// LINQ to XML query  
IEnumerable<XElement> list1 =  
    from el in po.Descendants("Address")  
    where (string)el.Attribute("Type") == "Shipping"  
    select el;  
  
// XPath expression  
IEnumerable<XElement> list2 = po.XPathSelectElements(".//Address[@Type='Shipping']");  
  
if (list1.Count() == list2.Count() &&  
        list1.Intersect(list2).Count() == list1.Count())  
    Console.WriteLine("Results are identical");  
else  
    Console.WriteLine("Results differ");  
foreach (XElement el in list1)  
    Console.WriteLine(el);  
```  
  
 <span data-ttu-id="3e957-108">Ten przykład generuje następujące wyniki:</span><span class="sxs-lookup"><span data-stu-id="3e957-108">This example produces the following output:</span></span>  
  
```output  
Results are identical  
<Address Type="Shipping">  
  <Name>Ellen Adams</Name>  
  <Street>123 Maple Street</Street>  
  <City>Mill Valley</City>  
  <State>CA</State>  
  <Zip>10999</Zip>  
  <Country>USA</Country>  
</Address>  
<Address Type="Shipping">  
  <Name>Cristian Osorio</Name>  
  <Street>456 Main Street</Street>  
  <City>Buffalo</City>  
  <State>NY</State>  
  <Zip>98112</Zip>  
  <Country>USA</Country>  
</Address>  
<Address Type="Shipping">  
  <Name>Jessica Arnold</Name>  
  <Street>4055 Madison Ave</Street>  
  <City>Seattle</City>  
  <State>WA</State>  
  <Zip>98112</Zip>  
  <Country>USA</Country>  
</Address>  
```  
