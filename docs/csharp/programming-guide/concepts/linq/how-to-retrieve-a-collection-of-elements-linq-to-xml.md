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
# <a name="how-to-retrieve-a-collection-of-elements-linq-to-xml-c"></a><span data-ttu-id="d62ab-102">Instrukcje: Pobieranie kolekcji elementów (LINQ to XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="d62ab-102">How to: Retrieve a Collection of Elements (LINQ to XML) (C#)</span></span>
<span data-ttu-id="d62ab-103">W tym temacie przedstawiono <xref:System.Xml.Linq.XContainer.Elements%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="d62ab-103">This topic demonstrates the <xref:System.Xml.Linq.XContainer.Elements%2A> method.</span></span> <span data-ttu-id="d62ab-104">Ta metoda pobiera kolekcję elementów podrzędnych elementu.</span><span class="sxs-lookup"><span data-stu-id="d62ab-104">This method retrieves a collection of the child elements of an element.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d62ab-105">Przykład</span><span class="sxs-lookup"><span data-stu-id="d62ab-105">Example</span></span>  
 <span data-ttu-id="d62ab-106">Ten przykład wykonuje iterację przez elementy podrzędne `purchaseOrder` elementu.</span><span class="sxs-lookup"><span data-stu-id="d62ab-106">This example iterates through the child elements of the `purchaseOrder` element.</span></span>  
  
 <span data-ttu-id="d62ab-107">W tym przykładzie użyto następujący dokument XML: [Przykładowy plik XML: Typowe zamówienie zakupu (LINQ to XML)](../../../../csharp/programming-guide/concepts/linq/sample-xml-file-typical-purchase-order-linq-to-xml-1.md).</span><span class="sxs-lookup"><span data-stu-id="d62ab-107">This example uses the following XML document: [Sample XML File: Typical Purchase Order (LINQ to XML)](../../../../csharp/programming-guide/concepts/linq/sample-xml-file-typical-purchase-order-linq-to-xml-1.md).</span></span>  
  
```csharp  
XElement po = XElement.Load("PurchaseOrder.xml");  
IEnumerable<XElement> childElements =  
    from el in po.Elements()  
    select el;  
foreach (XElement el in childElements)  
    Console.WriteLine("Name: " + el.Name);  
```  
  
 <span data-ttu-id="d62ab-108">Ten przykład generuje następujące dane wyjściowe.</span><span class="sxs-lookup"><span data-stu-id="d62ab-108">This example produces the following output.</span></span>  
  
```  
Name: Address  
Name: Address  
Name: DeliveryNotes  
Name: Items  
```  
  
## <a name="see-also"></a><span data-ttu-id="d62ab-109">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="d62ab-109">See also</span></span>

- [<span data-ttu-id="d62ab-110">LINQ do XML osi (C#)</span><span class="sxs-lookup"><span data-stu-id="d62ab-110">LINQ to XML Axes (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/linq-to-xml-axes-overview.md)
