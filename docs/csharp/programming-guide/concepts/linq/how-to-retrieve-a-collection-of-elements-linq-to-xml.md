---
title: Jak pobrać kolekcję elementów (LINQ do XML) (C#)
ms.date: 07/20/2015
ms.assetid: b849668c-7976-4974-b8e1-1cd587d34258
ms.openlocfilehash: 89799b17115fb56a93bda5fbc144b21b334a6974
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "75345016"
---
# <a name="how-to-retrieve-a-collection-of-elements-linq-to-xml-c"></a>Jak pobrać kolekcję elementów (LINQ do XML) (C#)
W tym temacie <xref:System.Xml.Linq.XContainer.Elements%2A> przedstawiono metodę. Ta metoda pobiera kolekcję elementów podrzędnych elementu.  
  
## <a name="example"></a>Przykład  
 W tym przykładzie itecyzuje `purchaseOrder` przez elementy podrzędne elementu.  
  
 W tym przykładzie użyto następującego dokumentu XML: [Przykładowy plik XML: Typowe zamówienie zakupu (LINQ do XML).](./sample-xml-file-typical-purchase-order-linq-to-xml-1.md)  
  
```csharp  
XElement po = XElement.Load("PurchaseOrder.xml");  
IEnumerable<XElement> childElements =  
    from el in po.Elements()  
    select el;  
foreach (XElement el in childElements)  
    Console.WriteLine("Name: " + el.Name);  
```  
  
 W tym przykładzie tworzy następujące dane wyjściowe.  
  
```output  
Name: Address  
Name: Address  
Name: DeliveryNotes  
Name: Items  
```  
  
## <a name="see-also"></a>Zobacz też

- [LINQ do osi XML (C#)](./linq-to-xml-axes-overview.md)
