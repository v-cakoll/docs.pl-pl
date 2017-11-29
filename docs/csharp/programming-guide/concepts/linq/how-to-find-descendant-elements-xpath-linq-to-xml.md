---
title: "Porady: znajdowanie elementów podrzędnych (XPath-LINQ do XML) (C#)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-csharp
ms.topic: article
ms.assetid: b318da39-bb8b-4c56-a019-e13b12b01831
caps.latest.revision: "3"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 3d3551054b345d9ec1d18b33f697cf5c139bfab6
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="how-to-find-descendant-elements-xpath-linq-to-xml-c"></a>Porady: znajdowanie elementów podrzędnych (XPath-LINQ do XML) (C#)
W tym temacie pokazano, jak można uzyskać elementów podrzędnych o określonej nazwie.  
  
 Wyrażenie XPath jest `//Name`.  
  
## <a name="example"></a>Przykład  
 W tym przykładzie znajduje wszystkie elementy podrzędne o nazwie `Name`.  
  
 W tym przykładzie użyto następujących dokumentu XML: [przykładowego pliku XML: wiele zakupów (LINQ do XML)](../../../../csharp/programming-guide/concepts/linq/sample-xml-file-multiple-purchase-orders-linq-to-xml.md).  
  
```csharp  
XDocument po = XDocument.Load("PurchaseOrders.xml");  
  
// LINQ to XML query  
IEnumerable<XElement> list1 = po.Root.Descendants("Name");  
  
// XPath expression  
IEnumerable<XElement> list2 = po.XPathSelectElements("//Name");  
  
if (list1.Count() == list2.Count() &&  
        list1.Intersect(list2).Count() == list1.Count())  
    Console.WriteLine("Results are identical");  
else  
    Console.WriteLine("Results differ");  
foreach (XElement el in list1)  
    Console.WriteLine(el);  
```  
  
 Ten przykład generuje następujące wyniki:  
  
```  
Results are identical  
<Name>Ellen Adams</Name>  
<Name>Tai Yee</Name>  
<Name>Cristian Osorio</Name>  
<Name>Cristian Osorio</Name>  
<Name>Jessica Arnold</Name>  
<Name>Jessica Arnold</Name>  
```  
  
## <a name="see-also"></a>Zobacz też  
 [LINQ do XML dla użytkowników XPath (C#)](../../../../csharp/programming-guide/concepts/linq/linq-to-xml-for-xpath-users.md)
