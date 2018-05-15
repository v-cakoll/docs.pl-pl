---
title: 'Porady: pobierania kolekcję elementów (LINQ do XML) (Visual Basic)'
ms.date: 07/20/2015
ms.assetid: 2269f9de-8fb9-4666-b8a1-a4e754fa6a81
ms.openlocfilehash: 7ebc33ec8d1901ecb795f63b2fd9812d1acba347
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-retrieve-a-collection-of-elements-linq-to-xml-visual-basic"></a><span data-ttu-id="4d850-102">Porady: pobierania kolekcję elementów (LINQ do XML) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="4d850-102">How to: Retrieve a Collection of Elements (LINQ to XML) (Visual Basic)</span></span>
<span data-ttu-id="4d850-103">W tym temacie przedstawiono <xref:System.Xml.Linq.XContainer.Elements%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="4d850-103">This topic demonstrates the <xref:System.Xml.Linq.XContainer.Elements%2A> method.</span></span> <span data-ttu-id="4d850-104">Ta metoda pobiera kolekcję elementów podrzędnych danego elementu.</span><span class="sxs-lookup"><span data-stu-id="4d850-104">This method retrieves a collection of the child elements of an element.</span></span>  
  
## <a name="example"></a><span data-ttu-id="4d850-105">Przykład</span><span class="sxs-lookup"><span data-stu-id="4d850-105">Example</span></span>  
 <span data-ttu-id="4d850-106">W tym przykładzie iteruje elementy podrzędne `purchaseOrder` elementu.</span><span class="sxs-lookup"><span data-stu-id="4d850-106">This example iterates through the child elements of the `purchaseOrder` element.</span></span>  
  
 <span data-ttu-id="4d850-107">W tym przykładzie użyto następujących dokumentu XML: [przykładowego pliku XML: typowe zamówienia zakupu (LINQ do XML)](../../../../visual-basic/programming-guide/concepts/linq/sample-xml-file-typical-purchase-order-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="4d850-107">This example uses the following XML document: [Sample XML File: Typical Purchase Order (LINQ to XML)](../../../../visual-basic/programming-guide/concepts/linq/sample-xml-file-typical-purchase-order-linq-to-xml.md).</span></span>  
  
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
  
 <span data-ttu-id="4d850-108">W tym przykładzie tworzy następujące dane wyjściowe.</span><span class="sxs-lookup"><span data-stu-id="4d850-108">This example produces the following output.</span></span>  
  
```  
Name: Address  
Name: Address  
Name: DeliveryNotes  
Name: Items  
```  
  
## <a name="see-also"></a><span data-ttu-id="4d850-109">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="4d850-109">See Also</span></span>  
 [<span data-ttu-id="4d850-110">LINQ do osi XML (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="4d850-110">LINQ to XML Axes (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/linq-to-xml-axes.md)
