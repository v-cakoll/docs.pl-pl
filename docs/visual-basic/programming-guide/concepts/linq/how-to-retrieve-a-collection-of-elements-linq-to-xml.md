---
title: 'Instrukcje: Pobieranie kolekcji elementów (LINQ to XML) (Visual Basic)'
ms.date: 07/20/2015
ms.assetid: 2269f9de-8fb9-4666-b8a1-a4e754fa6a81
ms.openlocfilehash: 53572ac3c80e012b95527d32da28c8685cd8cfd3
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "58833643"
---
# <a name="how-to-retrieve-a-collection-of-elements-linq-to-xml-visual-basic"></a>Instrukcje: Pobieranie kolekcji elementów (LINQ to XML) (Visual Basic)
W tym temacie przedstawiono <xref:System.Xml.Linq.XContainer.Elements%2A> metody. Ta metoda pobiera kolekcję elementów podrzędnych elementu.  
  
## <a name="example"></a>Przykład  
 Ten przykład wykonuje iterację przez elementy podrzędne `purchaseOrder` elementu.  
  
 W tym przykładzie użyto następujący dokument XML: [Przykładowy plik XML: Typowe zamówienie zakupu (LINQ to XML)](../../../../visual-basic/programming-guide/concepts/linq/sample-xml-file-typical-purchase-order-linq-to-xml.md).  
  
```vb  
Dim po As XElement = XElement.Load("PurchaseOrder.xml")  
Dim childElements As IEnumerable(Of XElement)  
childElements = _  
    From el In po.Elements() _  
    Select el  
For Each el As XElement In childElements  
    Console.WriteLine("Name: " & el.Name.ToString())  
Next  
```  
  
 Ten przykład generuje następujące dane wyjściowe.  
  
```  
Name: Address  
Name: Address  
Name: DeliveryNotes  
Name: Items  
```  
  
## <a name="see-also"></a>Zobacz także

- [LINQ do osi XML (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/linq-to-xml-axes.md)
