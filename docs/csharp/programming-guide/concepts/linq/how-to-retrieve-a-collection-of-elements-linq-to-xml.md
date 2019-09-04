---
title: 'Instrukcje: Pobieranie kolekcji elementów (LINQ to XML) (C#)'
ms.date: 07/20/2015
ms.assetid: b849668c-7976-4974-b8e1-1cd587d34258
ms.openlocfilehash: fef12745bd608622f071f72049f242405d17ed7d
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/04/2019
ms.locfileid: "70253419"
---
# <a name="how-to-retrieve-a-collection-of-elements-linq-to-xml-c"></a>Instrukcje: Pobieranie kolekcji elementów (LINQ to XML) (C#)
W <xref:System.Xml.Linq.XContainer.Elements%2A> tym temacie przedstawiono metodę. Ta metoda pobiera kolekcję elementów podrzędnych elementu.  
  
## <a name="example"></a>Przykład  
 Ten przykład wykonuje iterację przez elementy `purchaseOrder` podrzędne elementu.  
  
 W tym przykładzie zastosowano następujący dokument XML: [Przykładowy plik XML: Typowe zamówienie zakupu (LINQ to XML)](./sample-xml-file-typical-purchase-order-linq-to-xml-1.md).  
  
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
  
## <a name="see-also"></a>Zobacz także

- [Osie LINQ to XML (C#)](./linq-to-xml-axes-overview.md)
