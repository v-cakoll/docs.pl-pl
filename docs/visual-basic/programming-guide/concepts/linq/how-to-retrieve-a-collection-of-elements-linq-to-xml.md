---
title: 'Instrukcje: pobieranie kolekcji elementów (LINQ to XML)'
ms.date: 07/20/2015
ms.assetid: 2269f9de-8fb9-4666-b8a1-a4e754fa6a81
ms.openlocfilehash: 592ef68206df59bc848644d0a62bf0efdb10609e
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/22/2019
ms.locfileid: "74347582"
---
# <a name="how-to-retrieve-a-collection-of-elements-linq-to-xml-visual-basic"></a><span data-ttu-id="a7b00-102">Instrukcje: pobieranie kolekcji elementów (LINQ to XML) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="a7b00-102">How to: Retrieve a Collection of Elements (LINQ to XML) (Visual Basic)</span></span>
<span data-ttu-id="a7b00-103">W tym temacie przedstawiono metodę <xref:System.Xml.Linq.XContainer.Elements%2A>.</span><span class="sxs-lookup"><span data-stu-id="a7b00-103">This topic demonstrates the <xref:System.Xml.Linq.XContainer.Elements%2A> method.</span></span> <span data-ttu-id="a7b00-104">Ta metoda pobiera kolekcję elementów podrzędnych elementu.</span><span class="sxs-lookup"><span data-stu-id="a7b00-104">This method retrieves a collection of the child elements of an element.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a7b00-105">Przykład</span><span class="sxs-lookup"><span data-stu-id="a7b00-105">Example</span></span>  
 <span data-ttu-id="a7b00-106">Ten przykład wykonuje iterację elementów podrzędnych elementu `purchaseOrder`.</span><span class="sxs-lookup"><span data-stu-id="a7b00-106">This example iterates through the child elements of the `purchaseOrder` element.</span></span>  
  
 <span data-ttu-id="a7b00-107">W tym przykładzie zastosowano następujący dokument XML: [przykładowy plik XML: typowe zamówienie zakupu (LINQ to XML)](../../../../visual-basic/programming-guide/concepts/linq/sample-xml-file-typical-purchase-order-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="a7b00-107">This example uses the following XML document: [Sample XML File: Typical Purchase Order (LINQ to XML)](../../../../visual-basic/programming-guide/concepts/linq/sample-xml-file-typical-purchase-order-linq-to-xml.md).</span></span>  
  
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
  
 <span data-ttu-id="a7b00-108">Ten przykład generuje następujące dane wyjściowe.</span><span class="sxs-lookup"><span data-stu-id="a7b00-108">This example produces the following output.</span></span>  
  
```console  
Name: Address  
Name: Address  
Name: DeliveryNotes  
Name: Items  
```  
  
## <a name="see-also"></a><span data-ttu-id="a7b00-109">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="a7b00-109">See also</span></span>

- [<span data-ttu-id="a7b00-110">Osie LINQ to XML (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="a7b00-110">LINQ to XML Axes (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/linq-to-xml-axes.md)
