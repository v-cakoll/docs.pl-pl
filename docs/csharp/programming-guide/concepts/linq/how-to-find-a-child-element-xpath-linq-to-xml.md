---
title: Jak znaleźć element podrzędny (XPath-LINQ do XML) (C#)
ms.date: 07/20/2015
ms.assetid: 4fa6182d-6196-4ed1-9c9e-82949ff89c71
ms.openlocfilehash: 37ce6c9d91d4edf2576ccddabd1d7f14a96b0a33
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "74141237"
---
# <a name="how-to-find-a-child-element-xpath-linq-to-xml-c"></a><span data-ttu-id="10d02-102">Jak znaleźć element podrzędny (XPath-LINQ do XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="10d02-102">How to find a child element (XPath-LINQ to XML) (C#)</span></span>
<span data-ttu-id="10d02-103">W tym temacie porównano oś elementu [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] <xref:System.Xml.Linq.XContainer.Element%2A> podrzędnego XPath z metodą.</span><span class="sxs-lookup"><span data-stu-id="10d02-103">This topic compares the XPath child element axis to the [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] <xref:System.Xml.Linq.XContainer.Element%2A> method.</span></span>  
  
 <span data-ttu-id="10d02-104">Wyrażenie XPath `DeliveryNotes`jest .</span><span class="sxs-lookup"><span data-stu-id="10d02-104">The XPath expression is `DeliveryNotes`.</span></span>  
  
## <a name="example"></a><span data-ttu-id="10d02-105">Przykład</span><span class="sxs-lookup"><span data-stu-id="10d02-105">Example</span></span>  
 <span data-ttu-id="10d02-106">W tym przykładzie `DeliveryNotes`znajduje element podrzędny .</span><span class="sxs-lookup"><span data-stu-id="10d02-106">This example finds the child element `DeliveryNotes`.</span></span>  
  
 <span data-ttu-id="10d02-107">W tym przykładzie użyto następującego dokumentu XML: [Przykładowy plik XML: wiele zamówień zakupu (LINQ do XML).](./sample-xml-file-multiple-purchase-orders-linq-to-xml.md)</span><span class="sxs-lookup"><span data-stu-id="10d02-107">This example uses the following XML document: [Sample XML File: Multiple Purchase Orders (LINQ to XML)](./sample-xml-file-multiple-purchase-orders-linq-to-xml.md).</span></span>  
  
```csharp  
XDocument cpo = XDocument.Load("PurchaseOrders.xml");  
XElement po = cpo.Root.Element("PurchaseOrder");  
  
// LINQ to XML query  
XElement el1 = po.Element("DeliveryNotes");  
  
// XPath expression  
XElement el2 = po.XPathSelectElement("DeliveryNotes");  
// same as "child::DeliveryNotes"  
// same as "./DeliveryNotes"  
  
if (el1 == el2)  
    Console.WriteLine("Results are identical");  
else  
    Console.WriteLine("Results differ");  
Console.WriteLine(el1);  
```  
  
 <span data-ttu-id="10d02-108">Ten przykład generuje następujące wyniki:</span><span class="sxs-lookup"><span data-stu-id="10d02-108">This example produces the following output:</span></span>  
  
```output  
Results are identical  
<DeliveryNotes>Please leave packages in shed by driveway.</DeliveryNotes>  
```  
  