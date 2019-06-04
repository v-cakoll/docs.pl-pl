---
title: 'Instrukcje: Pobieranie kolekcji elementów (LINQ to XML) (C#)'
ms.date: 07/20/2015
ms.assetid: b849668c-7976-4974-b8e1-1cd587d34258
ms.openlocfilehash: 42d1eaeb5e0ce43d27cd4675f634ab3dfca80a53
ms.sourcegitcommit: 155012a8a826ee8ab6aa49b1b3a3b532e7b7d9bd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2019
ms.locfileid: "66485093"
---
# <a name="how-to-retrieve-a-collection-of-elements-linq-to-xml-c"></a>Instrukcje: Pobieranie kolekcji elementów (LINQ to XML) (C#)
W tym temacie przedstawiono <xref:System.Xml.Linq.XContainer.Elements%2A> metody. Ta metoda pobiera kolekcję elementów podrzędnych elementu.  
  
## <a name="example"></a>Przykład  
 Ten przykład wykonuje iterację przez elementy podrzędne `purchaseOrder` elementu.  
  
 W tym przykładzie użyto następujący dokument XML: [Przykładowy plik XML: Typowe zamówienie zakupu (LINQ to XML)](../../../../csharp/programming-guide/concepts/linq/sample-xml-file-typical-purchase-order-linq-to-xml-1.md).  
  
```csharp  
XElement po = XElement.Load("PurchaseOrder.xml");  
IEnumerable<XElement> childElements =  
    from el in po.Elements()  
    select el;  
foreach (XElement el in childElements)  
    Console.WriteLine("Name: " + el.Name);  
```  
  
 Ten przykład generuje następujące dane wyjściowe.  
  
```  
Name: Address  
Name: Address  
Name: DeliveryNotes  
Name: Items  
```  
  
## <a name="see-also"></a>Zobacz także

- [LINQ do XML osi (C#)](../../../../csharp/programming-guide/concepts/linq/linq-to-xml-axes-overview.md)
