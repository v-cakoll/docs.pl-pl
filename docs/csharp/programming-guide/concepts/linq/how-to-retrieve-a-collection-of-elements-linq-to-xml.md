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
# <a name="how-to-retrieve-a-collection-of-elements-linq-to-xml-c"></a><span data-ttu-id="bd247-104">Jak pobrać kolekcję elementów (LINQ to XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="bd247-104">How to retrieve a collection of elements (LINQ to XML) (C#)</span></span>
<span data-ttu-id="bd247-105">W tym temacie przedstawiono <xref:System.Xml.Linq.XContainer.Elements%2A> metodę.</span><span class="sxs-lookup"><span data-stu-id="bd247-105">This topic demonstrates the <xref:System.Xml.Linq.XContainer.Elements%2A> method.</span></span> <span data-ttu-id="bd247-106">Ta metoda pobiera kolekcję elementów podrzędnych elementu.</span><span class="sxs-lookup"><span data-stu-id="bd247-106">This method retrieves a collection of the child elements of an element.</span></span>  
  
## <a name="example"></a><span data-ttu-id="bd247-107">Przykład</span><span class="sxs-lookup"><span data-stu-id="bd247-107">Example</span></span>  
 <span data-ttu-id="bd247-108">Ten przykład wykonuje iterację przez elementy podrzędne `purchaseOrder` elementu.</span><span class="sxs-lookup"><span data-stu-id="bd247-108">This example iterates through the child elements of the `purchaseOrder` element.</span></span>  
  
 <span data-ttu-id="bd247-109">W tym przykładzie zastosowano następujący dokument XML: [przykładowy plik XML: typowe zamówienie zakupu (LINQ to XML)](./sample-xml-file-typical-purchase-order-linq-to-xml-1.md).</span><span class="sxs-lookup"><span data-stu-id="bd247-109">This example uses the following XML document: [Sample XML File: Typical Purchase Order (LINQ to XML)](./sample-xml-file-typical-purchase-order-linq-to-xml-1.md).</span></span>  
  
```csharp  
XElement po = XElement.Load("PurchaseOrder.xml");  
IEnumerable<XElement> childElements =  
    from el in po.Elements()  
    select el;  
foreach (XElement el in childElements)  
    Console.WriteLine("Name: " + el.Name);  
```  
  
 <span data-ttu-id="bd247-110">Ten przykład generuje następujące dane wyjściowe.</span><span class="sxs-lookup"><span data-stu-id="bd247-110">This example produces the following output.</span></span>  
  
```output  
Name: Address  
Name: Address  
Name: DeliveryNotes  
Name: Items  
```  
  
## <a name="see-also"></a><span data-ttu-id="bd247-111">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="bd247-111">See also</span></span>

- [<span data-ttu-id="bd247-112">Osie LINQ to XML (C#)</span><span class="sxs-lookup"><span data-stu-id="bd247-112">LINQ to XML Axes (C#)</span></span>](./linq-to-xml-axes-overview.md)
