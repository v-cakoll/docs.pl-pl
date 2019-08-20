---
title: 'Instrukcje: Pobieranie kolekcji elementów (LINQ to XML) (C#)'
ms.date: 07/20/2015
ms.assetid: b849668c-7976-4974-b8e1-1cd587d34258
ms.openlocfilehash: 0ca40b77a78f155292dfbb26471442450bf16b9b
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/19/2019
ms.locfileid: "69592640"
---
# <a name="how-to-retrieve-a-collection-of-elements-linq-to-xml-c"></a><span data-ttu-id="87884-102">Instrukcje: Pobieranie kolekcji elementów (LINQ to XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="87884-102">How to: Retrieve a Collection of Elements (LINQ to XML) (C#)</span></span>
<span data-ttu-id="87884-103">W <xref:System.Xml.Linq.XContainer.Elements%2A> tym temacie przedstawiono metodę.</span><span class="sxs-lookup"><span data-stu-id="87884-103">This topic demonstrates the <xref:System.Xml.Linq.XContainer.Elements%2A> method.</span></span> <span data-ttu-id="87884-104">Ta metoda pobiera kolekcję elementów podrzędnych elementu.</span><span class="sxs-lookup"><span data-stu-id="87884-104">This method retrieves a collection of the child elements of an element.</span></span>  
  
## <a name="example"></a><span data-ttu-id="87884-105">Przykład</span><span class="sxs-lookup"><span data-stu-id="87884-105">Example</span></span>  
 <span data-ttu-id="87884-106">Ten przykład wykonuje iterację przez elementy `purchaseOrder` podrzędne elementu.</span><span class="sxs-lookup"><span data-stu-id="87884-106">This example iterates through the child elements of the `purchaseOrder` element.</span></span>  
  
 <span data-ttu-id="87884-107">W tym przykładzie zastosowano następujący dokument XML: [Przykładowy plik XML: Typowe zamówienie zakupu (LINQ to XML)](./sample-xml-file-typical-purchase-order-linq-to-xml-1.md).</span><span class="sxs-lookup"><span data-stu-id="87884-107">This example uses the following XML document: [Sample XML File: Typical Purchase Order (LINQ to XML)](./sample-xml-file-typical-purchase-order-linq-to-xml-1.md).</span></span>  
  
```csharp  
XElement po = XElement.Load("PurchaseOrder.xml");  
IEnumerable<XElement> childElements =  
    from el in po.Elements()  
    select el;  
foreach (XElement el in childElements)  
    Console.WriteLine("Name: " + el.Name);  
```  
  
 <span data-ttu-id="87884-108">Ten przykład generuje następujące dane wyjściowe.</span><span class="sxs-lookup"><span data-stu-id="87884-108">This example produces the following output.</span></span>  
  
```  
Name: Address  
Name: Address  
Name: DeliveryNotes  
Name: Items  
```  
  
## <a name="see-also"></a><span data-ttu-id="87884-109">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="87884-109">See also</span></span>

- [<span data-ttu-id="87884-110">Osie LINQ to XML (C#)</span><span class="sxs-lookup"><span data-stu-id="87884-110">LINQ to XML Axes (C#)</span></span>](./linq-to-xml-axes-overview.md)
