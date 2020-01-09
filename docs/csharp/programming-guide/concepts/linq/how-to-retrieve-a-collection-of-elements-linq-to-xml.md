---
title: Jak pobrać kolekcję elementów (LINQ to XML) (C#)
ms.date: 07/20/2015
ms.assetid: b849668c-7976-4974-b8e1-1cd587d34258
ms.openlocfilehash: 89799b17115fb56a93bda5fbc144b21b334a6974
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/25/2019
ms.locfileid: "75345016"
---
# <a name="how-to-retrieve-a-collection-of-elements-linq-to-xml-c"></a><span data-ttu-id="dc558-102">Jak pobrać kolekcję elementów (LINQ to XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="dc558-102">How to retrieve a collection of elements (LINQ to XML) (C#)</span></span>
<span data-ttu-id="dc558-103">W tym temacie przedstawiono metodę <xref:System.Xml.Linq.XContainer.Elements%2A>.</span><span class="sxs-lookup"><span data-stu-id="dc558-103">This topic demonstrates the <xref:System.Xml.Linq.XContainer.Elements%2A> method.</span></span> <span data-ttu-id="dc558-104">Ta metoda pobiera kolekcję elementów podrzędnych elementu.</span><span class="sxs-lookup"><span data-stu-id="dc558-104">This method retrieves a collection of the child elements of an element.</span></span>  
  
## <a name="example"></a><span data-ttu-id="dc558-105">Przykład</span><span class="sxs-lookup"><span data-stu-id="dc558-105">Example</span></span>  
 <span data-ttu-id="dc558-106">Ten przykład wykonuje iterację elementów podrzędnych elementu `purchaseOrder`.</span><span class="sxs-lookup"><span data-stu-id="dc558-106">This example iterates through the child elements of the `purchaseOrder` element.</span></span>  
  
 <span data-ttu-id="dc558-107">W tym przykładzie zastosowano następujący dokument XML: [przykładowy plik XML: typowe zamówienie zakupu (LINQ to XML)](./sample-xml-file-typical-purchase-order-linq-to-xml-1.md).</span><span class="sxs-lookup"><span data-stu-id="dc558-107">This example uses the following XML document: [Sample XML File: Typical Purchase Order (LINQ to XML)](./sample-xml-file-typical-purchase-order-linq-to-xml-1.md).</span></span>  
  
```csharp  
XElement po = XElement.Load("PurchaseOrder.xml");  
IEnumerable<XElement> childElements =  
    from el in po.Elements()  
    select el;  
foreach (XElement el in childElements)  
    Console.WriteLine("Name: " + el.Name);  
```  
  
 <span data-ttu-id="dc558-108">Ten przykład generuje następujące dane wyjściowe.</span><span class="sxs-lookup"><span data-stu-id="dc558-108">This example produces the following output.</span></span>  
  
```output  
Name: Address  
Name: Address  
Name: DeliveryNotes  
Name: Items  
```  
  
## <a name="see-also"></a><span data-ttu-id="dc558-109">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="dc558-109">See also</span></span>

- [<span data-ttu-id="dc558-110">Osie LINQ to XML (C#)</span><span class="sxs-lookup"><span data-stu-id="dc558-110">LINQ to XML Axes (C#)</span></span>](./linq-to-xml-axes-overview.md)
