---
title: "Porady: filtrowanie atrybutów (XPath-LINQ do XML) (C#)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-csharp
ms.topic: article
ms.assetid: 208d6256-1bd7-4237-b2c9-909f26dfd0e2
caps.latest.revision: "3"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 3ae49f729b46bd794eb614f90ab83fc80d4021a6
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="how-to-filter-on-an-attribute-xpath-linq-to-xml-c"></a><span data-ttu-id="78ecd-102">Porady: filtrowanie atrybutów (XPath-LINQ do XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="78ecd-102">How to: Filter on an Attribute (XPath-LINQ to XML) (C#)</span></span>
<span data-ttu-id="78ecd-103">W tym temacie pokazano, jak można uzyskać elementów podrzędnych o określonej nazwie i z atrybutem o określonej wartości.</span><span class="sxs-lookup"><span data-stu-id="78ecd-103">This topic shows how to get the descendant elements with a specified name, and with an attribute with a specified value.</span></span>  
  
 <span data-ttu-id="78ecd-104">Wyrażenie XPath jest:</span><span class="sxs-lookup"><span data-stu-id="78ecd-104">The XPath expression is:</span></span>  
  
 `.//Address[@Type='Shipping']`  
  
## <a name="example"></a><span data-ttu-id="78ecd-105">Przykład</span><span class="sxs-lookup"><span data-stu-id="78ecd-105">Example</span></span>  
 <span data-ttu-id="78ecd-106">W tym przykładzie znajduje wszystkie elementy podrzędne elementy o nazwie `Address`oraz `Type` atrybutu o wartości "Wysyłki".</span><span class="sxs-lookup"><span data-stu-id="78ecd-106">This example finds all descendants elements with the name of `Address`, and with a `Type` attribute with a value of "Shipping".</span></span>  
  
 <span data-ttu-id="78ecd-107">W tym przykładzie użyto następujących dokumentu XML: [przykładowego pliku XML: wiele zakupów (LINQ do XML)](../../../../csharp/programming-guide/concepts/linq/sample-xml-file-multiple-purchase-orders-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="78ecd-107">This example uses the following XML document: [Sample XML File: Multiple Purchase Orders (LINQ to XML)](../../../../csharp/programming-guide/concepts/linq/sample-xml-file-multiple-purchase-orders-linq-to-xml.md).</span></span>  
  
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
  
 <span data-ttu-id="78ecd-108">Ten przykład generuje następujące wyniki:</span><span class="sxs-lookup"><span data-stu-id="78ecd-108">This example produces the following output:</span></span>  
  
```  
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
  
## <a name="see-also"></a><span data-ttu-id="78ecd-109">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="78ecd-109">See Also</span></span>  
 [<span data-ttu-id="78ecd-110">LINQ do XML dla użytkowników XPath (C#)</span><span class="sxs-lookup"><span data-stu-id="78ecd-110">LINQ to XML for XPath Users (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/linq-to-xml-for-xpath-users.md)
