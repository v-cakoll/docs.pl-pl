---
title: Jak pobrać kolekcję elementów (LINQ to XML) (C#)
description: Metoda elementy w języku C# Pobiera kolekcję elementów podrzędnych elementu. Ten LINQ to XML przykład wykonuje iterację elementów podrzędnych elementu.
ms.date: 07/20/2015
ms.assetid: b849668c-7976-4974-b8e1-1cd587d34258
ms.openlocfilehash: 4f9b6ae4713af9ce1a4eeb5257f57cd9724f68b2
ms.sourcegitcommit: 04022ca5d00b2074e1b1ffdbd76bec4950697c4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/23/2020
ms.locfileid: "87103362"
---
# <a name="how-to-retrieve-a-collection-of-elements-linq-to-xml-c"></a>Jak pobrać kolekcję elementów (LINQ to XML) (C#)
W tym temacie przedstawiono <xref:System.Xml.Linq.XContainer.Elements%2A> metodę. Ta metoda pobiera kolekcję elementów podrzędnych elementu.  
  
## <a name="example"></a>Przykład  
 Ten przykład wykonuje iterację przez elementy podrzędne `purchaseOrder` elementu.  
  
 W tym przykładzie zastosowano następujący dokument XML: [przykładowy plik XML: typowe zamówienie zakupu (LINQ to XML)](./sample-xml-file-typical-purchase-order-linq-to-xml-1.md).  
  
```csharp  
XElement po = XElement.Load("PurchaseOrder.xml");  
IEnumerable<XElement> childElements =  
    from el in po.Elements()  
    select el;  
foreach (XElement el in childElements)  
    Console.WriteLine("Name: " + el.Name);  
```  
  
 Ten przykład generuje następujące dane wyjściowe.  
  
```output  
Name: Address  
Name: Address  
Name: DeliveryNotes  
Name: Items  
```  
  
## <a name="see-also"></a>Zobacz też

- [Osie LINQ to XML (C#)](./linq-to-xml-axes-overview.md)
