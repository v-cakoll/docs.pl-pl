---
title: Jak znaleźć element główny (XPath-LINQ do XML) (C#)
ms.date: 07/20/2015
ms.assetid: 4fd824e0-4d39-429b-b092-f6a5c046ee6c
ms.openlocfilehash: 1c5526f436b5b9d88ca359ef7e0fc04c5c3cf43c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "75345949"
---
# <a name="how-to-find-the-root-element-xpath-linq-to-xml-c"></a>Jak znaleźć element główny (XPath-LINQ do XML) (C#)
W tym temacie pokazano, jak uzyskać [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]element główny z XPath i .  
  
 Wyrażenie XPath jest następujące:  
  
 `/PurchaseOrders`  
  
## <a name="example"></a>Przykład  
 W tym przykładzie znajduje element główny.  
  
 W tym przykładzie użyto następującego dokumentu XML: [Przykładowy plik XML: wiele zamówień zakupu (LINQ do XML).](./sample-xml-file-multiple-purchase-orders-linq-to-xml.md)  
  
```csharp  
XDocument po = XDocument.Load("PurchaseOrders.xml");  
  
// LINQ to XML query  
XElement el1 = po.Root;  
  
// XPath expression  
XElement el2 = po.XPathSelectElement("/PurchaseOrders");  
  
if (el1 == el2)  
    Console.WriteLine("Results are identical");  
else  
    Console.WriteLine("Results differ");  
Console.WriteLine(el1.Name);  
```  
  
 Ten przykład generuje następujące wyniki:  
  
```output  
Results are identical  
PurchaseOrders  
```  
